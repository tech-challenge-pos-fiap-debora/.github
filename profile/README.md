# Tech Challenge POS FIAP · Fase 3

Mapa do **entregável** da oficina mecânica (segurança, escala, IaC, CI/CD e observabilidade).

## Vídeo de demonstração

- [Vídeo da entrega (Google Drive)](https://drive.google.com/file/d/17yfLtCTMPekJBQioYkRF4WaSZbzyA1So/view?usp=sharing)

## Quatro repositórios (código + CI/CD + README)

| Repositório | Papel |
|---|---|
| [app](https://github.com/tech-challenge-pos-fiap-debora/app) | Aplicação NestJS no Kubernetes |
| [lambda-auth](https://github.com/tech-challenge-pos-fiap-debora/lambda-auth) | Function serverless de autenticação + API Gateway |
| [infra-kubernetes](https://github.com/tech-challenge-pos-fiap-debora/infra-kubernetes) | VPC, EKS, ALB, HPA, New Relic (Terraform) |
| [infra-database](https://github.com/tech-challenge-pos-fiap-debora/infra-database) | Banco gerenciado RDS PostgreSQL (Terraform) |

Em cada repo: README, pipeline GitHub Actions e, quando aplicável, Dockerfile.  
`main` protegida — merge só por Pull Request. Collaborator `soat-architecture` nos quatro.

## Autenticação e API Gateway

- API Gateway + Lambda: valida CPF, consulta o cliente e devolve JWT.
- Endpoint: `POST` https://b831ifscuh.execute-api.us-east-1.amazonaws.com/prod/auth/login  
  body: `{ "cpf": "52998224725" }`
- Código e infra: [lambda-auth](https://github.com/tech-challenge-pos-fiap-debora/lambda-auth)

## Infraestrutura

- Cluster Kubernetes (EKS) com HPA — [infra-kubernetes](https://github.com/tech-challenge-pos-fiap-debora/infra-kubernetes)
- Banco gerenciado (RDS PostgreSQL) — [infra-database](https://github.com/tech-challenge-pos-fiap-debora/infra-database)
- Provisionamento com Terraform nos dois repos de infra

## Observabilidade (New Relic)

- Dashboard: [Tech Challenge - Oficina Mecanica (prod)](https://one.newrelic.com/redirect/entity/ODUwODAzNnxWSVp8REFTSEJPQVJEfGRhOjEzMTY1ODM5)
- Latência das APIs, CPU/memória do Kubernetes, healthchecks, alertas de OS, logs JSON com correlação, volume diário e tempo médio por status
- Como está ligado: [OBSERVABILIDADE.md](https://github.com/tech-challenge-pos-fiap-debora/infra-kubernetes/blob/main/docs/OBSERVABILIDADE.md)

## Documentação arquitetural

Ponto de entrada: [arquitetura.md](https://github.com/tech-challenge-pos-fiap-debora/app/blob/main/docs/arquitetura.md)

Inclui diagramas de componentes e sequência, RFCs, ADRs, modelo de dados / ER e justificativa do banco.

## Deploys ativos (Learner Lab ligado)

| O quê | URL |
|---|---|
| Swagger | http://k8s-techchal-api-3be88fc582-917637512.us-east-1.elb.amazonaws.com/api |
| Health | http://k8s-techchal-api-3be88fc582-917637512.us-east-1.elb.amazonaws.com/health/live |
| Login cliente (CPF) | https://b831ifscuh.execute-api.us-east-1.amazonaws.com/prod/auth/login |

## Portal do aluno

No PDF: links desta organização, dos 4 repositórios, do [vídeo](https://drive.google.com/file/d/17yfLtCTMPekJBQioYkRF4WaSZbzyA1So/view?usp=sharing) e da [documentação](https://github.com/tech-challenge-pos-fiap-debora/app/blob/main/docs/arquitetura.md).
