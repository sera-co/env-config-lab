# Cloud Run Mapping

## Configuration Variables

- `LOG_LEVEL=info` -> `gcloud run deploy <SERVICE_NAME> --set-env-vars LOG_LEVEL=info`
- `.env` values -> `gcloud run deploy <SERVICE_NAME> --set-env-vars KEY1=v1,KEY2=v2`

## Secrets

- `API_KEY` -> `gcloud run deploy <SERVICE_NAME> --set-secrets API_KEY=api-key:latest`
- Secrets should be stored in Google Cloud Secret Manager and injected at runtime, not placed in the Dockerfile.

## Validation Mapping

- `docker exec app-fixed printenv` -> Cloud Run revision Variables & Secrets
- `docker history envlab` -> confirms secrets are not baked into the image
- Never use `ENV API_KEY=...` in the Dockerfile for secrets.
