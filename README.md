# 🛡️ BugShield AI

> Encontre bugs, falhas de segurança e segredos expostos **antes** que o código chegue à produção.

![Status](https://img.shields.io/badge/status-MVP-F26B0F)
![Licença](https://img.shields.io/badge/licen%C3%A7a-MIT-F26B0F)
![PRs](https://img.shields.io/badge/PRs-bem--vindos-F26B0F)

## O problema

Desenvolvedores publicam código com bugs, vulnerabilidades, vazamento de dados e problemas de desempenho sem perceber. Quando o problema aparece, ele já está em produção.

## A solução

O **BugShield AI** analisa cada Pull Request, mostra a gravidade de cada problema e explica, em linguagem simples, exatamente o que precisa ser corrigido. Quando possível, gera o patch pronto.

## Como funciona

1. O desenvolvedor conecta o GitHub.
2. O BugShield analisa o Pull Request.
3. Detecta bugs, vulnerabilidades, segredos expostos e más práticas.
4. Classifica cada achado por gravidade: **Crítico, Alto, Médio ou Baixo**.
5. Sugere uma correção e, quando possível, gera o patch.
6. Gera um relatório que pode ser compartilhado.

## Funcionalidades do MVP

| Módulo | Prioridade | O que faz |
|---|---|---|
| **Security Scanner** | Essencial | Detecta senhas, tokens, chaves de API e vulnerabilidades. |
| **Bug Detector** | Alta | Encontra possíveis erros e condições que podem quebrar o código. |
| **AI Fix Generator** | Alta | Sugere correções com explicações em linguagem simples. |
| **GitHub Integration** | Alta | Analisa Pull Requests automaticamente. |
| **Quality Dashboard** | Média | Mostra pontuação de qualidade e histórico de problemas. |

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Frontend | React + TypeScript |
| Estilização | Tailwind CSS |
| Backend | Supabase |
| Banco de dados | PostgreSQL |
| IA | OpenAI API |
| Integração | GitHub API |
| Segurança | Semgrep + Gitleaks |
| Deploy | Vercel |

## Arquitetura

```
Pull Request (GitHub)
        │  webhook
        ▼
Supabase Edge Function
        │
        ├── Gitleaks  → segredos expostos
        ├── Semgrep   → vulnerabilidades e más práticas
        └── OpenAI    → bugs de lógica, explicação e patch
        │
        ▼
PostgreSQL (achados, pontuação, histórico)
        │
        ├── Comentário no Pull Request
        └── Dashboard + relatório compartilhável
```

## Começando

### Pré-requisitos

- Node.js 20+
- Conta no [Supabase](https://supabase.com)
- Chave da [OpenAI API](https://platform.openai.com)
- Um [GitHub App](https://docs.github.com/pt/apps) criado para o projeto
- [Semgrep](https://semgrep.dev) e [Gitleaks](https://github.com/gitleaks/gitleaks) instalados

### Instalação

```bash
git clone https://github.com/SEU-USUARIO/bugshield-ai.git
cd bugshield-ai
npm install
cp .env.example .env
npm run dev
```

### Variáveis de ambiente

```env
VITE_SUPABASE_URL=
VITE_SUPABASE_ANON_KEY=
OPENAI_API_KEY=
GITHUB_APP_ID=
GITHUB_APP_PRIVATE_KEY=
GITHUB_WEBHOOK_SECRET=
```

> ⚠️ Nunca faça commit do arquivo `.env`. Use as variáveis de ambiente da Vercel e os secrets do Supabase.

## Estrutura sugerida

```
bugshield-ai/
├── src/            # Frontend React + TypeScript
├── supabase/
│   ├── functions/  # Webhook e análise de PR
│   └── migrations/ # Tabelas do PostgreSQL
├── scanners/       # Regras do Semgrep e Gitleaks
└── docs/
```

## Roadmap

- [x] Definição do MVP
- [ ] Conexão com GitHub
- [ ] Security Scanner
- [ ] Bug Detector
- [ ] AI Fix Generator com patch
- [ ] Comentários automáticos no PR
- [ ] Quality Dashboard
- [ ] Relatório compartilhável
- [ ] Suporte a GitLab
- [ ] Regras personalizadas por equipe

## Como contribuir

1. Faça um fork do projeto.
2. Crie uma branch: `git checkout -b minha-feature`.
3. Faça commit das mudanças: `git commit -m "feat: minha feature"`.
4. Envie para o fork: `git push origin minha-feature`.
5. Abra um Pull Request.

Antes de abrir o PR, rode o BugShield no seu próprio código. 😉

## Segurança

Encontrou uma vulnerabilidade no BugShield? Não abra uma issue pública. Envie os detalhes por e-mail para `seguranca@bugshield.ai`.

## Licença

Distribuído sob a licença MIT. Veja o arquivo `LICENSE`.
