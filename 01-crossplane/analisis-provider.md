# Análisis del Provider PostgreSQL

## 1. Managed Resources ofrecidos por el provider

| Managed Resource | Descripción |
|---|---|
| **Database** | Crea y gestiona bases de datos PostgreSQL |
| **Role** | Crea y gestiona roles/usuarios PostgreSQL |
| **Grant** | Asigna privilegios sobre objetos de base de datos |
| **Schema** | Crea y gestiona esquemas dentro de bases de datos |
| **Extension** | Habilita extensiones PostgreSQL |

## 2. Campos del recurso `Database`

### Campos requeridos en `spec.forProvider`:

| Campo | Tipo | Descripción |
|---|---|
| `name` | string | Nombre de la base de datos |

### Campos opcionales en `spec.forProvider`:

| Campo | Tipo | Default |
|---|---|---|
| `owner` | string | Usuario actual |
| `encoding` | string | UTF8 |
| `template` | string | template1 |
| `lcCollate` | string | Configuración del sistema |
| `lcCtype` | string | Configuración del sistema |
| `connectionLimit` | integer | -1 (sin límite) |
| `allowConnections` | boolean | true |
| `isTemplate` | boolean | false |

## 3. Información requerida por el ProviderConfig

El ProviderConfig necesita un Secret con formato JSON que contenga:

| Campo | Requerido | Descripción |
|---|---|---|
| `host` | Sí | Dirección del servidor PostgreSQL |
| `port` | Sí | Puerto de conexión |
| `username` | Sí | Usuario con privilegios administrativos |
| `password` | Sí | Contraseña del usuario |
| `database` | Sí | Base de datos inicial de conexión |
| `sslmode` | No | Modo SSL (disable, require, verify-ca, verify-full) |

El Secret debe estar en el namespace `crossplane-system` y ser referenciado con `source: Secret` (case-sensitive).
