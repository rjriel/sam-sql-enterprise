
# Event Triggered Demo - support tickets

This repo will allow you to set up a quick demo where you can use the Solace Broker Try Me to
send in an event for a new support ticket and receive a summary for possible solutions from the
agent mesh.

## Prerequisites

You need Docker Desktop for this

## Setup

1. Clone this repo
2. Copy the `.env.example` file to `.env`
3. In `.env` update the value for `LLM_SERVICE_API_KEY` to your Solace LLM Key
4. run `docker compose up`

## Demo

1. Once everything is up and running, you should be able to navigate to the broker at [http://localhost:8080/](http://localhost:8080/) (login is `admin`/`admin`)
2. Go to the "Try Me!" tool, connect to both publisher and subscriber (default values should work)
3. Subscribe to `event_mesh/responses/>`
4. Publish the below message to `erp/support/ticket/created/1`
5. It may take a minute to see the response come through

```json
  {
    "ticket_id": "TNEW001",
    "user_id": "U1012",
    "submitted_at": "2025-09-24T09:15:00",
    "issue": "CSV export hangs near completion for large monthly reports and eventually times out",
    "status": "open"
  }
```
