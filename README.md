# finishing-a-branch

> Chequeos finales, commits limpios y un PR que se puede revisar.

**Cerrar una rama** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Corre formatter, linter, tipos, pruebas y escaneo de secretos; revisa el propio diff buscando restos de depuración, IDs de prueba o archivos que no deben ir; ordena los commits con Conventional Commits y escribe la descripción del PR. Nunca hace merge ni push a main.

## Objetivo

Que cada PR llegue listo para revisar, con evidencia y sin sorpresas.

## Cuándo usarla

- Terminaste la implementación de una rama
- Vas a abrir o actualizar un PR

## Cuándo no

- Trabajo aún en progreso

## Ejemplo

```text
Cierra la rama feat/ump-consent y prepara el PR.
```

## Cómo se activa

Esta skill **se activa sola**: Claude Code lee su descripción y la carga cuando la tarea coincide. También puedes pedirla por nombre ("usa la skill finishing-a-branch") o invocarla con `/finishing-a-branch:finishing-a-branch` (plugin) o `/finishing-a-branch` (copiada a `.claude/skills/`).

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install finishing-a-branch@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `dev-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [dev-workflow](https://github.com/nvv-dev/dev-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/finishing-a-branch.git /tmp/finishing-a-branch
mkdir -p .claude/skills
cp -R /tmp/finishing-a-branch/skills/finishing-a-branch .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/finishing-a-branch/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/finishing-a-branch
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `finishing-a-branch` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall finishing-a-branch@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/finishing-a-branch`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/finishing-a-branch/SKILL.md`](skills/finishing-a-branch/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/finishing-a-branch/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: [obra/superpowers](https://github.com/obra/superpowers) (finishing-a-development-branch).

## Licencia

MIT.

---

## English

**finishing-a-branch** — Final checks, self-review of the diff, Conventional Commits and a PR description; never merges or pushes to main.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install finishing-a-branch@nvvdev`, or copy `skills/finishing-a-branch/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/finishing-a-branch`. Loads automatically when the task matches its description. Canonical source: [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow). License: MIT.
