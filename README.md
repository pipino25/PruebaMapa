La funcionalidad de este código, como se solicita en el documento de pauta, es el lograr añadir la funcionalidad básica de maps a una aplicación en android studio. 
Esto se ha conseguido mediante el uso de 2 activities, una de inicio main que contiene un simple botón para pasar al map. que verifica los permisos consedidos por el usuario, 
solicitando acceso a la ubicación del dispositivo en caso de ser necesario, para luego desplegar en pantalla la ubicación del usuario según el dispositivo.

Archivo de evaluación de seguridad generado por MOBSF
Disponible desde el link: https://drive.google.com/file/d/1PhKv7OV5dhiFaIJ9vXVRoIZtTqWYe0yF/view?usp=sharing

Vulnerabilidades encontradas:
-La aplicación está firmada con un certificado de depuración. Esto es peligroso porque permite a atacantes utilizar herramientas de análisis para descompilar y modificar la aplicación.
-La aplicación permite instalación en Android 7.0 (API 24), que tiene múltiples vulnerabilidades no parcheadas.
-El atributo android:debuggable=true permite que depuradores se conecten fácilmen-te a la aplicación, lo cual puede ser utilizado por atacantes para obtener información sensible o manipular el comportamiento de la app.
-El atributo android:allowBackup=true permite que los datos de la aplicación puedan ser respaldados usando comandos ADB, lo cual pone en riesgo información sensible.
-Un Broadcast Receiver definido en la aplicación es accesible por otras aplicaciones debido a que está configurado como android:exported=true. Aunque está protegido por un permiso (android.permission.DUMP), este no está definido en la aplicación.

Posibles acciones a realizar:
-Firmar con un certificado de producción. Asegúrate de que la aplicación en producción esté firmada con un certificado adecuado (keystore de producción).
-Incrementar la versión mínima de SDK (minSdkVersion). Define en build.gradle un valor de minSdkVersion de al menos API 29 (Android 10), ya que versiones anteriores no reciben actualizaciones de seguridad razonables.
-Realizar pruebas de compatibilidad para garantizar que la aplicación funcione adecuadamente en versiones más recientes de Android.

Buenas prácticas generales
-Realizar análisis de seguridad periódicos. Usa herramientas como SonarQube, Checkmarx, o plugins de seguridad para detectar vulnerabilidades.
-Cifrado de datos sensibles. Cifra información importante almacenada localmente o transmitida a través de redes.
-Uso de ProGuard o R8. Activa la ofuscación del código en los builds de producción para dificultar la ingeniería inversa.
-Manejo de dependencias seguras. Asegúrate de usar versiones actualizadas de bibliotecas para evitar vulnerabilidades conocidas.
-Auditorías de permisos. Reduce los permisos solicitados al mínimo necesario y utiliza permisos de nivel signature siempre que sea posible.

Como ejecutar la aplicación

-Abrir Android Studio.
-Acceder a la pestaña "Git".
-Navegar a la sección "Clone".
-En pestaña "Repository URL" ingresar el link del repositorio.
-Click en "Clone".
-Esperar a que carguen las dependencias.
-En "AndroidManifest" encontrado en las carpetas del proyecto, ingresar una API KEY propia en la sección meta data--> android:value""
-Correr el Código, se desplegará una pantalla con un botón.
-Click en el botón. 
-Se desplegará el mapa con la ubicación que indique la emulación con un marcador.

