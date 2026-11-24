# Евгений

**Python Backend · AI Agents · Data Engineering**

Разрабатываю backend-сервисы, пайплайны данных и AI-агентов для e-commerce и автоматизации. Соединяю API, PostgreSQL, фоновые задачи и языковые модели в системы с проверяемыми результатами, сохранением состояния и контролем действий.

Основной фокус — Python и архитектура backend. В проектах также работаю с SQL-аналитикой, оркестрацией, тестированием и интеграцией веб-интерфейсов.

## Проекты

| Проект | Что решает | Что можно оценить в коде |
| --- | --- | --- |
| [E-commerce AI Backend](https://github.com/semenovjenya/ecommerce-ai-backend) | Анализ продаж, рекламы, цен, финансов и запасов; подготовка решений | FastAPI, Redis/RQ, доменные агенты, финансовые расчёты, approval, idempotency и аудит |
| [E-commerce LangGraph Migration](https://github.com/semenovjenya/ecommerce-langgraph-migration) | Выделение агентского runtime из backend и управление состоянием workflow | Пять subgraphs, типизированный state, checkpoints, HTTP tool adapters, ограничения исследовательских вызовов |
| [Wildberries Data Platform](https://github.com/semenovjenya/ETL-WB-portfolio) | Сбор данных маркетплейса, SQL-витрины и прогнозирование | Python ETL, Airflow DAG, PostgreSQL, upsert, контроль свежести, ML-прогнозы и pgvector |
| [Telegram AI Automation](https://github.com/semenovjenya/telegram-ai-automation) | AI-ассистент и сценарии аналитики, размещений и партнёрств в Telegram | LangGraph, FastAPI, Next.js BFF, tenant isolation, история диалогов и demo без внешних credentials |
| [Langfuse Integration](https://github.com/semenovjenya/ai-ecom-langfuse) · private | Наблюдаемость запросов, инструментов и LLM-вызовов в AI-ECOM | Python, Langfuse/OpenTelemetry, вложенные traces, usage и стоимость, управление промптом и фильтрация payload |
| [AI-ECOM MCP](https://github.com/semenovjenya/ai-ecom-mcp) · private | Подключение исследовательских инструментов AI-KAM к Codex через MCP | Python-пакет запуска stdio-сервера, конфигурация подключения и проверка совместимости с backend |

### Backend и бизнес-логика

В [ecommerce-ai-backend](https://github.com/semenovjenya/ecommerce-ai-backend) разделены получение фактов, численные расчёты, модельные объяснения и исполнение действий. Долгие задачи выполняются через workers; результаты и события сохраняются в PostgreSQL. Для управленческих действий предусмотрены согласование, проверка ограничений и защита от повторного исполнения.

### Агентские системы и оптимизация

В [ecommerce-langgraph-migration](https://github.com/semenovjenya/ecommerce-langgraph-migration) представлены работа со state/reducers, восстановление из checkpoints, изоляция контекста и ограниченные исследовательские циклы. Есть запускаемый пример и отдельный [разбор оптимизации evidence](https://github.com/semenovjenya/ecommerce-langgraph-migration/blob/main/docs/OPTIMIZATION.md).

На синтетических наборах компактное представление уменьшает JSON evidence на **76,02% и 67,37%** с точным восстановлением данных. Экономия стоимости LLM. С

### Инженерия данных

[ETL-WB-portfolio](https://github.com/semenovjenya/ETL-WB-portfolio) объединяет загрузку заказов, продаж, остатков, цен, рекламы и финансовых отчётов. Airflow управляет зависимостями и проверкой свежести, SQL формирует аналитические витрины, ML-слой рассчитывает прогнозы на семь дней. Предусмотрена конфигурация нескольких кабинетов продавцов.

### Автоматизация и интеграция интерфейса

В [telegram-ai-automation](https://github.com/semenovjenya/telegram-ai-automation) запрос проходит через Next.js BFF и authentication gateway к AI workflow. JWT хранится в HttpOnly-cookie, история разделяется по tenant, а live-репост требует структурированного подтверждения. Локальный пример показывает три маршрута агента без Telegram-аккаунта и OpenAI-ключа.

### Наблюдаемость и MCP

В [Langfuse Integration](https://github.com/semenovjenya/ai-ecom-langfuse) запросы, доменные инструменты и LLM-вызовы связываются в общую трассу через OpenTelemetry. Интеграция передаёт usage и стоимость из ответа провайдера, управляет версиями промпта и ограничивает содержимое телеметрии. Сбои наблюдаемости не меняют результат бизнес-функций.

[AI-ECOM MCP](https://github.com/semenovjenya/ai-ecom-mcp) предоставляет отдельный Python-пакет запуска исследовательского MCP `ai_kam_research` для Codex. Инструменты чтения данных, SQL, расчётов и исследования SKU исполняет существующий backend AI-ECOM. Совместимость проверяется сравнением ответов при прямом запуске сервера и через пакет.

Оба репозитория приватные; ссылки доступны пользователям с выданными правами.

## Технические навыки

| Направление | Инструменты и практики |
| --- | --- |
| Backend | Python, FastAPI, REST, asyncio, WebSocket/SSE, Redis/RQ |
| Данные | PostgreSQL, SQL, Airflow, ETL, аналитические витрины, pgvector |
| AI | LangGraph, LangChain, OpenAI Agents SDK, RAG, MCP, typed tools, checkpoints |
| Надёжность | Pytest, валидация контрактов, idempotency, обработка сбоев, проверка источников |
| Интеграция и эксплуатация | Docker Compose, Next.js/TypeScript BFF, Prometheus, Langfuse/LangSmith |

## Инженерный подход

- Сохраняю происхождение фактов и различаю нулевое значение, отсутствие данных и гипотезу.
- Финансовые формулы и разрешение внешних действий оставляю в бизнес-коде.
- Проверяю не только успешный сценарий, но и повторную доставку, сбои, ограничения доступа и восстановление.
- Измеряю оптимизации на воспроизводимых примерах и указываю их компромиссы.
- Для портфолио использую очищенные копии, синтетические данные и явное разделение demo и live-интеграций.

## С чего начать знакомство

**Python/backend:** [E-commerce AI Backend](https://github.com/semenovjenya/ecommerce-ai-backend).  
**AI engineering:** [LangGraph runtime и оптимизация](https://github.com/semenovjenya/ecommerce-langgraph-migration).  
**Data engineering:** [ETL и Airflow](https://github.com/semenovjenya/ETL-WB-portfolio).  
**Интеграция продукта:** [Telegram AI Automation](https://github.com/semenovjenya/telegram-ai-automation).

В README каждого проекта есть архитектура, команды запуска, результаты проверок и текущие ограничения.
