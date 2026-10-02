<!--
  🚀 Pull Request — Finvix
  Reemplaza <PLACEHOLDER>. Marca [x] solo lo que realmente completaste.
  • Tracking = el rastreador que use el repo, y son dos: Jira (app "GitHub for Jira", clave PEG),
    donde vive el trabajo planificado del board, y el buzón de Issues donde el repo lo tiene abierto.
    El buzón no sustituye a Jira —es la puerta de lo que llega de fuera del board— pero vale como
    registro. Un PR sin ninguna de las dos referencias no tiene dónde registrarse.
  • CODEOWNERS asigna como revisor al team Leads de la organización del repositorio: @finvix/leads ·
    @finvix-governance/leads · @finvix-platform/leads — pertenecer a uno no da revisión en las otras.
    En finvix el ruleset exige esa aprobación; en finvix-governance y finvix-platform no la exige.
    Merge = squash, único método permitido.
  • Labels: los de avisos (`warn/*`) los pone quien revisa cuando aplican; el resto los pone Dependabot
    o la automatización. Ningún proceso los lee para publicar.
  • Ninguna sección se borra: todas se llenan. Lo que no aplica se deja y se marca N/A —si el cambio
    no toca datos personales, la casilla de PII sigue ahí, marcada N/A—.
-->

## 🧭 Tracking

- **Referencia**: `PEG-XXX` ([Jira](https://finvix.atlassian.net/browse/PEG-XXX)) **o** `#<n>`, el
  issue de este repositorio. La que use el repo; si usa las dos, pon las dos.
- **Branch**: `<tipo>/PEG-XXX-<slug>` — o `<tipo>/<slug>` donde el rastro no es Jira
  > Prefijo de rama: `feature`. La versión no se corta en una rama: cada merge a `master` saca su tag
  > `vX.Y.Z` y su release, y el tipo de commit decide qué número sube.
  > Destino: **`master`**, la única rama larga del repo. Ejemplo: `feature/PEG-123-netsuite-validations`
  > 💡 La clave `PEG` es CONVENCIÓN, no candado: ningún ruleset la exige y el aviso de CI que la pide
  > no bloquea. Donde el rastro es Jira, ponla en la rama, los commits y el título del PR; donde es el
  > buzón, referencia el issue en el cuerpo.

- [ ] 🔄 Ticket movido a **"In Review"** — o **N/A**, si el rastro de este repo no es Jira

## 📖 Descripción

<!-- QUÉ cambia y POR QUÉ. Enfócate en la intención y el diseño. -->

## 🏷️ Tipo de Cambio
<!-- Conventional Commits (commitlint.config.mjs — type-enum, 12 tipos). Marca el que corresponda al título del PR. -->

- [ ] ✨ **feat** — Nueva funcionalidad
- [ ] 🐛 **fix** — Corrección de bug
- [ ] 📚 **docs** — Solo documentación
- [ ] 🎨 **style** — Formato / estilo (sin cambio de lógica)
- [ ] ♻️ **refactor** — Cambio de código sin nueva funcionalidad
- [ ] ⚡ **perf** — Mejora de rendimiento
- [ ] 🧪 **test** — Añade o corrige tests
- [ ] 🏗️ **build** — Sistema de build o dependencias externas
- [ ] 👷 **ci** — Pipelines / CI-CD
- [ ] 🔧 **chore** — Configuración, dependencias, mantenimiento
- [ ] ⏪ **revert** — Revierte un cambio anterior
- [ ] 🔖 **release** — Cambio en cómo se versiona o se publica (GitVersion, changelog, release)

> `security` **NO es un tipo** de commitlint (type-enum no lo incluye) — es un **scope** del tier①.
> Hardening/CVE se marca `fix(security): …` o `chore(security): …`, no con un tipo propio.

- [ ] 💥 **BREAKING CHANGE** — Cambio incompatible (footer `BREAKING CHANGE:`, marca también el `semver` mayor)

---

## 🛡️ Seguridad y Riesgos (si aplica)

- [ ] 🔑 **AuthN/AuthZ** — Login y permisos correctos (quién eres + qué puedes hacer)
- [ ] 👤 **Permisos** — Cada rol solo ve/modifica lo permitido
- [ ] ✅ **OWASP Top 10** — Protección contra ataques comunes (SQLi, XSS, etc.)
- [ ] 🐛 **Vulnerabilidades** — Alertas de Dependabot / IDE resueltas o documentadas
      🔗 Las confirmadas se registran en el rastreador del repo — ticket Jira **tipo "Seguridad"** (`PEG-XXX`) o issue propio donde el rastro sea el buzón
- [ ] ⚠️ **Riesgos** — Impactos potenciales identificados, documentados y mitigados (performance, migración, dependencia externa)

### 🔒 Datos sensibles (si aplica)

- [ ] 🔐 **Secrets/API keys** — En Azure Key Vault / secret manager, NO en código (incluye `appsettings`/`local.settings.json`)
- [ ] 👥 **PII** — Nombres, emails, RUTs NO aparecen en logs ni errores

### 📊 Impacto en datos / infraestructura (si aplica)

- [ ] 🗃️ **Migraciones de BD** — Probadas en los anillos previos a producción primero
- [ ] 🔧 **IaC** — Cambios de infraestructura como código (Bicep), no manual desde el portal
- [ ] 🧱 **AVM** — IaC usa módulos **AVM** del registry privado (`crfinvixhub`) cuando existen — no módulos hand-rolled
- [ ] ♻️ **Reusables** — CI/CD usa los **reusables de `devops-actions`** (pin por SHA) — no workflows bespoke
- [ ] 🔑 **Managed Identity** — Las apps usan identidad de Azure, no passwords

## ⏪ Rollback (obligatorio si el cambio llega a producción)

<!-- El rollback no se improvisa: el procedimiento está listo ANTES del deploy. -->

- [ ] 🤖 **Automatizado** — re-deploy de la versión anterior
- [ ] 🛠️ **Manual** — comandos/scripts documentados aquí o enlazados

---

## 📊 Calidad

- [ ] 📊 Coverage revisado en el job `coverage-report` del run (objetivo ≥ 80% — informativo, aún no bloqueante)
- [ ] 🧪 Evidencia de pruebas en el rastreador — sub-tarea `TestCase` o comentario en el ticket Jira; comentario en el issue donde el rastro sea el buzón (capturas/logs)

## 📚 Referencias (si aplica)

- 🔗 <!-- doc, ADR, diseño... -->

---

> ✅ **Listo para revisión.** Revisor: el team **Leads** de la organización del repositorio, vía
> CODEOWNERS — `@finvix/leads` · `@finvix-governance/leads` · `@finvix-platform/leads`. Solo en
> finvix el ruleset exige su aprobación.
> · Merge por **squash**, único método que el ruleset admite en el tronco · Destino: **`master`**, la única rama larga.
