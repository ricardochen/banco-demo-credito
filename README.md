# Asistente de crédito bancario — Demo

**EN —** An internal assistant for bank staff. Employees ask about credit processes, rates and approval levels; the assistant answers in seconds and **cites the rule behind every number**, so the answer can be checked instead of trusted. Built with fictional data as a working demo, not a product.

**Demo en vivo:** https://ricardochen.github.io/banco-demo-credito/

---

## El problema

Un colaborador de banco necesita responder "¿a cuánto puede optar este cliente?" o "¿qué nivel aprueba este monto?" y la respuesta vive en manuales de políticas, hojas de tasas y la memoria de un compañero. El resultado es lento y desigual: dos personas dan dos respuestas distintas al mismo caso.

## Qué hace

- Responde en lenguaje natural sobre procesos, tasas y niveles de aprobación.
- Devuelve **la regla que respalda cada cifra**, no solo el número.
- Calcula cuota, monto y nivel de aprobación para un caso concreto.
- Captura el lead cuando el colaborador quiere un diagnóstico.

## Qué demuestra

- **Recuperación anclada a una base de reglas**, no a la memoria del modelo.
- **Cita de la fuente** como requisito de diseño: si la regla no está, el asistente no inventa.
- **Separación entre conversación y captura** (dos edge functions distintas).
- Un flujo de negocio real: la pregunta no termina en la respuesta, termina en una decisión.

## Stack

| Pieza | Dónde | Qué hace |
|---|---|---|
| Frontend | `index.html` + Tailwind (CDN) | Interfaz de chat, casos de ejemplo, captura |
| Motor de consulta | Supabase Edge Function `agente-chat-banco` | Recuperación sobre la base de reglas + respuesta con cita |
| Captura | Supabase Edge Function `agente-lead-banco` | Registro del lead y del caso consultado |

## Correr localmente

```bash
git clone https://github.com/ricardochen/banco-demo-credito
cd banco-demo-credito
open index.html   # o sirve la carpeta con cualquier servidor estático
```

Las edge functions ya están desplegadas; para apuntar a tu propio proyecto, cambia la URL base de Supabase en `index.html`.

## Qué está simulado

- Los datos: tasas, montos y niveles de aprobación son **ficticios**.
- Las reglas: simplificadas para la demo, no corresponden a ninguna entidad real.
- No hay autenticación ni manejo de PII; es una demo pública, no un sistema en producción.
