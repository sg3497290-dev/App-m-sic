# Vibe — Android nativo (base inicial)

Este proyecto reemplaza la reproducción HTML temporal por AndroidX Media3/ExoPlayer y `MediaSessionService`.

## Incluye
- Servicio multimedia Android independiente de la Activity, para mantener la reproducción cuando la interfaz se cierra.
- MediaSession de Media3, que proporciona controles compatibles con notificaciones, pantalla bloqueada, auriculares y controles del sistema.
- Selector de documentos de Android (`ACTION_OPEN_DOCUMENT` a través de `OpenMultipleDocuments`) para que el usuario elija explícitamente archivos de audio.
- Solicitud de permiso persistente de lectura para los URI seleccionados cuando el proveedor lo permite.
- Interfaz Jetpack Compose con estética oscura/neón, biblioteca y favoritos.
- No incluye anuncios, SDK de analítica, rastreadores ni permisos de acceso amplio al almacenamiento.

## Abrir y compilar
1. Descarga e instala Android Studio en un ordenador.
2. Abre la carpeta `Vibe_Android_Native` en Android Studio.
3. Espera a que Gradle sincronice y descarga los componentes SDK solicitados.
4. Ejecuta en un dispositivo/emulador Android.
5. Para crear APK: **Build > Build Bundle(s) / APK(s) > Build APK(s)**.

## Notas de desarrollo
- Es una base inicial de proyecto, no un APK ya compilado ni probado en un dispositivo.
- Para distribución real, valida las políticas de foreground service de la versión de Android objetivo y prueba permisos de notificación en Android 13+.
- La selección de documentos evita pedir `READ_MEDIA_AUDIO`/`READ_EXTERNAL_STORAGE`; los URI se guardan en memoria en esta primera versión. La concesión persistente permite guardar una biblioteca serializada en una siguiente iteración.
- Los títulos se derivan de la URI en esta base simple; conviene mejorar lectura de metadatos con `ContentResolver`/`MediaMetadataRetriever`.
- La reproducción en segundo plano y los controles de sistema dependen de las capacidades de Media3/Android y deben verificarse en dispositivos reales.
