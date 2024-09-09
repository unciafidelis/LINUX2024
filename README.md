# LINUX2024

## Sistemas Operativos
Según Wikipedia, podríamos definir a un sistema operativo como un programa
o conjunto de programas de un sistema informático que gestiona los recursos
de hardware y provee servicios a los programas de aplicación de software,
ejecutándose en modo privilegiado respecto de los restantes (aunque puede
que parte de él se ejecute en espacio de usuario).

Esto quiere decir que el sistema operativo es el software que está en contacto
directo con nuestro ordenador, y administra los recursos de hardware por
nosotros, de la manera más eficientemente posible.

## Recursos de hardware
Los recursos de hardware son los dispositivos y periféricos que conforman
nuestra computadora. Entre ellos podríamos distinguir:

- Microprocesador
- Memoria RAM
- Dispositivos de almacenamiento masivo
- Placa madre
- Tarjetas adaptadoras
- Periféricos (teclado, mouse, monitor, impresora, scanner, etc)

Es un error común muy extendido denominar al conjunto completo de
herramientas sistema operativo, es decir, la inclusión en el mismo término de
programas como el explorador de archivos, el navegador web y todo tipo de
herramientas que permiten la interacción con el sistema operativo.

## Modelo de capas
Si pudiéramos definir al software y al ordenador como un modelo de capas
como el siguiente, podríamos entender mejor la ubicación y funcionalidad del
sistema operativo.

El usuario común es quien interactúa, en primera instancia, con las
aplicaciones. Nosotros cuando utilizamos un ordenador abrimos programas, el
navegador web, clientes de correo electrónico, explorador de archivos, clientes
de mensajería instantánea, etc.

Estas aplicaciones necesitan un soporte para poder ejecutarse. Las
aplicaciones necesitamos instalarlas, cargarán sus archivos ejecutables,
archivos de ayuda, páginas de manual, imágenes y recursos complementarios,

Estas aplicaciones, para poder instalarse y ejecutarse, requieren de un software
que organice sus archivos, cree los procesos necesarios para poder ejecutarse,
administre privilegios de usuarios y políticas de seguridad, etc.

Es aquí donde es evidente la funcionalidad del sistema operativo. El sistema
operativo es quien, de alguna forma, gestiona las aplicaciones y nos permite a
nosotros, los usuarios, accederlas de manera transparente.

Ahora bien, las aplicaciones nos permiten a nosotros guardar archivos,
eliminar, cargar fotos, listar contenido de memorias flash, pendrives usb, etc.
Y las aplicaciones pueden hacerlo sin problemas! Esto es porque las
aplicaciones hacen uso de los recursos del sistema operativo para poder
acceder al hardware. Y por último, es el sistema operativo el que, por medio 
de controladores de dispositivo, puede acceder al hardware y operar con él.

Para agregar un poquito más de detalle en la capa del sistema operativo,
podríamos decir que encima del sistema operativo éste mantiene una interfaz
para que las aplicaciones puedan aprovechar sus recursos, mientras que por debajo, 
mantiene controladores de dispositivos para acceder al hardware.

Todas las aplicaciones en el sistema operativo acceden al mismo a través de
una interfaz común, denominada “interfaz de llamadas al sistema”, o “system
call interface” en inglés, y resumida comúnmente como “syscall”.
La interfaz de llamadas al sistema provee a las aplicaciones una serie de
funciones y procedimientos para que las aplicaciones puedan utilizar al sistema
operativo.

Imaginemos un procesador de texto que requiere guardar un archivo en el
disco. El procesador de textos le “pedirá” al sistema operativo guardar el
archivo, el sistema operativo utilizará el controlador o driver del disco para
poder guardar los datos en el disco, y, en el caso de que pueda hacerlo sin
problemas, le notificará a la aplicación la operación exitosa. En el caso de que
falle (disco fallado, errores de comunicación, etc), el sistema operativo le
notificará del error a la aplicación.

Lo mismo ocurre cuando el procesador de textos quiere abrir un archivo, o
leerlo, o modificarlo, etc. Siempre le “pide” al sistema operativo algún recurso.
Esto es una cuestión de diseño, que encapsula, hacia el lado de las
aplicaciones, el funcionamiento interno del sistema operativo, de modo que a
nosotros, como usuarios, nos resulta todo totalmente transparente y
“mágico” :)

## Funciones del sistema operativo

El sistema operativo cumple varias funciones, y dependiendo del sistema que
se trate, pueden haber más o menos.

En general, todos los sistemas operativos cumplen con 5 funcionalidades
básicas, que se detallan a continuación.

## Gestión de procesos

La gestión de procesos del sistema hace referencia a cómo el sistema
operativo trabajará con los programas que ejecutamos.

Antes que nada, deberíamos definir qué es un proceso. Un proceso es un
programa en ejecución. Cuando tenemos un navegador web instalado, Firefox
por ejemplo, sus archivos ejecutables se encuentran en
el disco de la computadora.

Cuando nosotros como usuarios lo ejecutamos (doble
clic generalmente, o por medio de la línea de
comandos), el sistema tomará el ejecutable de la
aplicación, generará lo que se conoce como “mapa de
memoria de un proceso”. A grandes rasgos, y para no entrar en detalle 
por el momento, el sistema operativo toma el binario
ejecutable de la aplicación, y lo copia en la memoria princpal, RAM, del
ordenador, y entonces lo ejecuta.

Ese programa copiado en memoria y en ejecución se conoce como proceso.
Ahora bien, todo esto lo debe ejecutar un procesador. El proceso debe
“procesarse” mediante el dispositivo a tal efecto: el microprocesador.
En un sistema podemos tener muchos procesos corriendo simultáneamente. Es
decir, podemos tener un navegador web, y un editor de textos abiertos a la
vez, sin mencionar que el sistema operativo en si mismo también se compone
de un conjunto de procesos.

El procesador (el núcleo de procesamiento) solo puede ejecutar un proceso a la
vez (en general). Entonces, cómo es que podemos ver tantos procesos
corriendo al mismo tiempo, si el procesador solo puede estar “trabajando” en
uno solo?

Esto es tarea del planificador de procesos del sistema operativo. Esta es la
tarea principal de gestión de procesos del SO.

El planificador es el que toma un proceso, lo carga en el procesador por cierto
tiempo, luego lo cambia por otro proceso, y así sucesivamente, a una velocidad
asombrosa dada por la frecuencia de trabajo del procesador. Este es el factor
principal que hace que como usuarios, veamos varios procesos en simultáneo,
cuando en realidad cada núcleo de procesamiento solo puede ejecutar un
proceso a la vez.

NOTA: cabe aclarar que en la actualidad ya contamos con procesadores
multinucleo, es decir, procesadores que físicamente pueden estar ejecutando
dos, cuatro, ocho, etc, procesos en simultáneo. El sistema operativo se encarga
de trabajar con cada núcleo de la misma manera que lo hace según lo que
acabamos de explicar, y utiliza otras técnicas para optimizar el procesamiento,
tales como Multiprocesamiento simétrico (SMP).

## Gestión de memoria

Todo software que se ejecuten en el sistema debe
estar cargado en la memoria principal, o memoria RAM
(Random Access Memory).

Los datos inicialmente están en el disco. Cómo pasan a
la memoria? Qué ocurre cuando una aplicación o
conjunto de aplicaciones supera, en tamaño, a la
capacidad física de la memoria principal? Por qué un
sistema operativo puede trabajar en un ordenador que
disponga de menos memoria RAM de la necesaria para guardar todo el sistema en si?

Todas estas preguntas las responde el gestor de memoria del sistema
operativo. Es el que se encarga de administrar la memoria virtual del sistema,
permitiendo que las aplicaciones puedan ejecutarse.

Además, el gestor de memoria administra también el espacio de intercambio,
también conocido como swap. Este espacio puede encontrarse físicamente en
un archivo en el disco rígido, o puede ser una partición, y permite, en cualquier
caso, y a grosso modo, almacenar datos que “no entran en RAM”.

Cuando una aplicación necesita cargar más información de la que “cabe” en la
memoria principal, el gestor de memoria libera espacio en RAM para cargar la
aplicación en cuestión. Dicho espacio liberado se almacena en el disco, en el
espacio de intercambio, o swap.

## Gestión de almacenamiento
La administración del almacenamiento masivo hace referencia a todas las
tareas que lleva a cabo el sistema operativo para
gestionar discos, memorias extraibles, pendrives usb, y
demás dispositivos de almacenamiento persistente.
Cuando conectamos un pendrive usb, el gestor de
almacenamiento se encarga de montarlo, y permitir el
acceso al contenido por medio de la administración de
sistemas de archivos.

Cuando almacenamos o modificamos la información
del dispositivo, también es el gestor de
almacenamiento quien se dedica a la administración
de estas tareas.

Gestión de Entrada/Salida y comunicaciones
Esta parte del sistema operativo se encarga de la administración de
dispositivos de periféricos.

Aquí el sistema operativo gestiona las
pulsaciones de teclado, los datos enviados a una
impresora, la información que es llevada a un
monitor por medio de la tarjeta de gráficos, los
datos que son comunicados con dispositivos
externos, y hasta la gestión de la entrada y
salida de datos desde los dispositivos internos, como la memoria RAM y 
los dispositivos de almacenamiento.
Los primeros sistemas informáticos utilizaban solamente tarjetas perforadas y
teletipos como únicos dispositivos de E/S.
Luego se estandarizó el uso de teclados, monitores y discos rígidos para
amenizar la interacción del ordenador con el usuario.
En la actualidad la cantidad de dispositivos que pueden interactuar con una
computadora es enorme. Entre ellos se cuenta con discos rígidos, discos
compactos, DVDs, memorias externas USB, teclados, ratones, dispositivos de
video juegos, tarjetas de red, módem, tarjetas de sonido y de video,
impresoras, cámaras de fotografía, altavoces, micrófonos, etc.

Debido a la gran variedad de dispositivos que puede administrar una
computadora, existen controladores diferentes para cada uno de ellos.

Es así que le sistema operativo maneja de manera distinta a cada uno de los
dispositivos de E/S.

Básicamente, hay tres clases de dispositivos, que se detallan a continuación.
• Dispositivos legibles por el humano: que son aptos para la
comunicación con el usuario. Tales dispositivos son teclados, pantallas,
mouse o impresoras.

• Dispositivos legibles por la máquina: adecuados para comunicarse
con equipos electrónicos tales como discos, unidades de cinta magnética
o sensores.

• Dispositivos de comunicación: aptos para comunicarse con
dispositivos lejanos, tales como líneas digitales, módem o antenas.
Es aquí donde podemos englobar también a la gestión de comunicaciones
dentro de la administración de dispositivos de entrada/salida, puesto que, los
datos que enviamos y recibimos en una red o con dispositivos conectados
remotamente es, dentro de todo, entrada/salida.

## Clasificación de los sistemas operativos
Existen varias clasificaciones de los sistemas operativos, según diferentes
tópicos y autores. Aquí se hará una clasificación según conceptos
fundamentales, y que resultan de interés para este apartado.

Según disponibilidad del código fuente
El código fuente de una aplicación es el o los archivos que escribe el
programador, la receta que usa el programador para decirle a la computadora
qué tiene que hacer la aplicación.

El programador escribe las aplicaciones, y luego (no vienen al caso los detalles
por ahora) ese código fuente se convierte en código binario ejecutable.
El sistema operativo también es una serie de programas que alguna vez fueron
escritos por uno o varios programadores, y luego fueron convertidos en el
sistema que estamos utilizando.

Ahora bien, podríamos estar utilizando un sistema operativo, y disponer
además del código que escribió el programador para saber qué hace
internamente el sistema, o cómo el programador resuelve los problemas.
O no, podríamos solamente tener el sistema operativo funcional, y no tener
acceso a esa receta interna que utilizó el programador.

En el primer caso estamos hablando de sistemas operativos abiertos,
algunos ejemplos son GNU/Linux, FreeBSD, OpenBSD, GNU/Hurd, etc.

En el segundo, donde no podemos ver el código, se habla de sistemas
operativos cerrados. Ejemplos, DOS, Windows, Mac OS X, Unix, etc.
Más adelante ahondaremos en los conceptos de software libre, open
source, código fuente y licencias de software.

Los sistemas operativos podemos comprarlos, pueden venir pre-instalados en
la computadora que adquirimos, podemos descargarlos desde Internet e
instalarlos, o puede pasárnoslo un amigo, por ejemplo.

Ahora, no en todos los casos estamos pagando por tenerlo y utilizarlo, y no en
todos los casos existe alguien responsable a quien reclamarle si las cosas no
van bien.

Cuando compramos un Windows por ejemplo, o una distribución de GNU/Linux
como RedHat o Suse, estamos pagando para que alguien o alguna empresa nos
lo provea, responda a nuestras consultas, y solucione nuestros inconvenientes
con el sistema.

En este caso estamos hablando de sistemas operativos comerciales.
Cuando descargamos una distribución de Linux como Debian, OpenSuse, o
Arch, y la instalamos por nuestra cuenta, nos sale gratis el sistema operativo,
pero no tenemos a ningún responsable directo (generalmente) a quien
consultarle o pedirle soluciones.

En este caso, es la propia comunidad de usuarios en Internet la que provee
información mediante foros, listas de discusión, chats, wikis, etc.
Aquí es donde hablamos de sistemas operativos No comerciales.

1 Una distribución de Linux es un sistema Linux con varias aplicaciones pre-instaladas con
algún propósito. Más adelante en el curso se tratará en detalle.

El objetivo de este curso se basa en aprender a utilizar estos
sistemas, y aprender a interactuar con la comunidad de usuarios y
desarrolladores.

Cuando trabajamos en un sistema operativo, por lo general 
(salvo que estemos utilizando MS-DOS :P) podemos
ejecutar varias aplicaciones al mismo tiempo.
Estas aplicaciones en ejecución dijimos que se denominan procesos, y para el
sistema son tareas en ejecución.

En el caso de que nuestro sistema operativo nos permita ejecutar varios
procesos simultáneamente, estamos hablando de sistemas multitarea. La
mayoría de los sistemas actuales son multitarea.

En el caso de que solo podamos ejecutar un proceso al a vez, es decir,
corremos una aplicación, y para poder ejecutar otra, necesitamos cerrar la
anterior, decimos que estamos en presencia de un sistema monotarea.

Algo similar que con la gestión de tareas, ocurre con los usuarios.
Hoy en día para poder utilizar un sistema operativo tenemos que
autenticarnos, dejar nuestro nombre de usuario y contraseña, o seleccionar un
usuario desde una interfaz gráfica, y escribir nuestra contraseña, o utilizar un
lector de huella dactilar, etc.

Esto es así porque el sistema permite que múltiples usuarios puedan utilizarlo,
puedan tener sus archivos y configuraciones personales, sus historiales de
búsqueda en Internet, etc, utilizando el mismo sistema operativo.

Yo me autentico (o logueo según la jerga) como usuario Diego y pongo mi
contraseña, y entro a mi sesión de usuario. Juan viene y deja su contraseña, y
entra a su sesión, con sus archivos y configuraciones, pero el no puede ver lo
que yo tengo, ni yo lo que usa el.

Esto es gestión de usuarios, y la mayor parte de los sistemas actuales lo
permiten.

En este caso decimos que el sistema es multiusuario. Mientras que el caso
contrario, cuando solamente puede haber un perfil de usuario utilizando el
sistema, como ocurría en Windows 95 por ejemplo, decimos que el sistema es
monousuario.

¿Qué sistemas operativos existen?
Esta pregunta seguramente no tenga una respuesta directa, o si la tiene, es
muchos.

Hoy en día existen muchos sistemas operativos, para diferentes arquitecturas
de computadora, para dispositivos embebidos, para dispositivos móviles,
tablets, laptops, computadoras de escritorio, y además, por si fuera poco,
podemos tener también variaciones de un mismo sistema con cambios y
características diferenciadoras.

Vamos a nombrar algunos sistemas que podemos encontrar, y que resultan de
especial interés por ser sistemas clave.

## Microsoft Windows
Es una familia de sistemas operativos gráficos desarrollados y
comercializados por Microsoft. Consisten en varios sistemas
operativos orientados a varios sectores de la industria. Algunos
de los que hoy en día se encuentran activos son Windows NT,
Windows Embedded y Windows Phone, Windows para
servidores de red, y Windows para estaciones de trabajo de
usuario.

## Unix
Unix (registrado oficialmente como UNIX®) es un sistema
operativo portable, multitarea y multiusuario; desarrollado, en principio, en
1969, por un grupo de empleados de los
laboratorios Bell de AT&T, entre los que
figuran Dennis Ritchie, Ken Thompson y
Douglas McIlroy.1 2
El sistema, junto con todos los derechos
fueron vendidos por AT&T a Novell, Inc. Esta
vendió posteriormente el
software a Santa Cruz
Operation en 1995, y esta, a su vez, lo revendió a Caldera
Software en 2001, empresa que después se convirtió en el
grupo SCO. Sin embargo, Novell siempre argumentó que solo
vendió los derechos de uso del software, pero que retuvo el
copyright sobre "UNIX®". En 2010, y tras una larga batalla
legal, ésta ha pasado nuevamente a ser propiedad de Novell.

Solo los sistemas totalmente compatibles y que se encuentran
certificados por la especificación Single UNIX Specification
pueden ser denominados "UNIX®" (otros reciben la denominación "similar a un
sistema Unix" o "similar a Unix"). En ocasiones, suele usarse el término "Unix
tradicional" para referirse a Unix o a un sistema operativo que cuenta con las
características de UNIX Versión 7 o UNIX System V.

Unix, vale aclarar, es un sistema que dio origen a la mayor parte de los
sistemas operativos de la actualidad. Linux y todas sus distribuciones, FreeBSD,
OpenBSD, Solaris, OS X, HP-UX, etc, son todos sistemas basados en Unix, más
conocidos en la jerga como sistemas *nix.

## GNU/Linux
GNU/Linux es uno de los términos empleados para referirse a la combinación
del núcleo o kernel libre similar a Unix denominado Linux (Creado por Linus Torbalds) con el sistema
operativo GNU (Creado por Richard Stallman). Su desarrollo es uno de los ejemplos más prominentes de
software libre; todo su código fuente puede ser utilizado, modificado y
redistribuido libremente por cualquiera bajo los términos de la GPL (Licencia
Pública General de GNU,) y otra serie de licencias
libres.

A pesar de que "Linux" se denomina en la jerga
cotidiana al sistema operativo, este es en realidad
solo el Kernel (núcleo) del sistema. La verdadera
denominación del sistema operativo es
"GNU/Linux" debido a que el resto del sistema (la
parte fundamental de la interacción entre el
hardware y el usuario) se maneja con las
herramientas del proyecto GNU (www.gnu.org) y
con entornos de escritorio (como GNOME), que
también forma parte del proyecto GNU aunque tuvo un origen independiente.

Como el Proyecto GNU destaca,4 GNU es una distribución, usándose el término
sistema operativo en el sentido empleado en el ecosistema Unix, lo que en
cualquier caso significa que Linux es solo una pieza más dentro de GNU/Linux.
Sin embargo, una parte significativa de la comunidad, así como muchos medios
generales y especializados, prefieren utilizar el término Linux para referirse a la
unión de ambos proyectos.

## Android
Android es un sistema operativo basado en el núcleo Linux.
Fue diseñado principalmente para dispositivos móviles con
pantalla táctil, como teléfonos inteligentes, tablets o
tabléfonos; y también para relojes inteligentes, televisores y
automóviles. Inicialmente fue desarrollado por Android Inc.,
empresa que Google respaldó económicamente y más tarde,
en 2005, la compró.

Android fue presentado en 2007 junto la fundación del Open Handset Alliance
(un consorcio de compañías de hardware, software y telecomunicaciones) para
avanzar en los estándares abiertos de los dispositivos móviles. El primer móvil
con el sistema operativo Android fue el HTC Dream y se vendió en octubre de
2008. Los dispositivos de Android venden más que las ventas combinadas de
Windows Phone e IOS.

## OS X
OS X, antes llamado Mac OS X, es un entorno operativo basado
en Unix, desarrollado, comercializado y vendido por Apple Inc.
Ha sido incluido en su gama de computadoras Macintosh desde
el año de 2002. OS X es el sucesor del Mac OS 9 (la versión final
del Mac OS Classic), el sistema operativo de Apple desde 1984.

Está basado en BSD, y se construyó sobre las tecnologías
desarrolladas en NeXT entre la segunda mitad de los 80's y
finales de 1996, cuando Apple adquirió esta compañía. Técnicamente, no es un
sistema operativo, sino que incluye uno (Darwin, cuyo núcleo es XNU). Desde la
versión Mac OS X 10.5 Leopard para procesadores Intel, el sistema tiene la
certificación UNIX 03.
