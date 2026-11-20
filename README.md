# Seguridad en la Nube: Buenas Prácticas CSA CCM y Ley N.° 29733 (GCP)

Repositorio de respaldo técnico correspondiente al informe de investigación y práctica sobre seguridad en la nube aplicada en **Google Cloud Platform (GCP)**, alineada con la matriz **Cloud Controls Matrix (CCM)** de la **Cloud Security Alliance (CSA)** y la **Ley N.° 29733 (Ley de Protección de Datos Personales – Perú)**.

## Estructura del Repositorio

* `config/sg-plataforma-final.json`: Exportación en formato JSON de las reglas de firewall de VPC endurecidas (*hardening* de red).

## Controles Implementados

1. **Protección de Datos y Cifrado (CSA CCM: DSI / EKM):**
   * Prevención de acceso público forzada (`Public access prevention: Enforced`) en Cloud Storage.
   * Cifrado automático en reposo mediante claves administradas por Google (`Google-managed key`).
2. **Gestión de Identidades y Accesos (CSA CCM: IAM):**
   * Verificación en dos pasos (MFA) activa en la cuenta administradora.
   * Aplicación del principio de mínimo privilegio mediante el rol de solo lectura (`roles/storage.objectViewer`).
3. **Seguridad de Red y Perímetro (CSA CCM: IVS):**
   * Eliminación de exposición pública (`0.0.0.0/0`) en puertos críticos de base de datos (`3306`, `5432`).
   * Restricción del tráfico web a puertos estándar (`80`, `443`) y acceso administrativo SSH (`22`) limitado a una única dirección IP (`/32`).
4. **Auditoría y Trazabilidad (CSA CCM: LOG):**
   * Inspección de registros administrativos (`cloudaudit.googleapis.com/activity`) mediante *Logs Explorer* identificando actor, marca de tiempo, IP de origen y recurso modificado.
