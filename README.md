# Blog de prácticas de Servidores II — Unidad I
Estas practicas fueron llevadas a cabo por mi y mis compañeros de equipo Félix Espejo Alehtse María y Hector Iván Moreno Márquez.

<br>

El propósito del blog es registrar, de manera ordenada, el proceso de preparación de un entorno virtual, instalación y configuración de un servidor Linux, y despliegue de un sistema gestor de bases de datos.

Las prácticas se desarrollaron de forma progresiva: cada actividad utiliza como punto de partida la configuración obtenida en la anterior. De esta manera, se construye un entorno de laboratorio que permite practicar tareas esenciales de administración de servidores.

<br>

## Introducción

La administración de servidores comprende actividades como instalar sistemas operativos, configurar la red, mantener el sistema actualizado, desplegar servicios y controlar el acceso a la información. Para practicar estos procedimientos sin necesitar un equipo físico dedicado, utilizamos **VirtualBox** para crear una máquina virtual en la que instalamos **Ubuntu Server 24.04 LTS**.

Posteriormente, configuramos el sistema desde la terminal y añadimos **MySQL 8.0** para trabajar con bases de datos relacionales. Estas actividades permiten familiarizarnos con herramientas y comandos que se utilizan en entornos de servidor, además de reforzar la importancia de la seguridad, la organización y la verificación de cada configuración.

> **Nota sobre el contenido:** los documentos proporcionados incluyen las prácticas 1 a 5. Las prácticas 1 a 4 están identificadas como parte de la Unidad I; la práctica 5 aparece marcada como Unidad II, por lo que se incluye al final como actividad de continuidad y no como parte de la Unidad I.

<br>

## Objetivos generales

- Preparar un entorno de virtualización para realizar prácticas de administración de servidores.
- Instalar Ubuntu Server y habilitar el acceso remoto mediante SSH.
- Aplicar configuraciones iniciales, actualizaciones y comprobaciones de conectividad.
- Instalar y asegurar MySQL, crear bases de datos y ejecutar operaciones SQL básicas.
- Comprender la administración de usuarios, privilegios y respaldos como parte de la continuidad del trabajo.

<br>

## Herramientas y tecnologías

Durante las prácticas se utilizan las siguientes herramientas:

- **Oracle VM VirtualBox 7.2:** creación y administración de la máquina virtual.
- **VirtualBox Extension Pack:** complemento utilizado junto con la versión correspondiente de VirtualBox.
- **Ubuntu Server 24.04 LTS:** sistema operativo del servidor de laboratorio.
- **OpenSSH Server / SSH:** acceso y administración remota desde otra computadora.
- **APT:** instalación y actualización de paquetes en Ubuntu.
- **MySQL 8.0:** sistema gestor de bases de datos relacional.
- **Terminal de Linux y cliente MySQL:** ejecución de comandos de administración y sentencias SQL.

<br>

## Prácticas de la Unidad I

### Práctica 1. Instalación y configuración de VirtualBox

**Objetivo:** preparar el entorno de virtualización donde se realizarán las actividades posteriores.

En esta práctica se instala VirtualBox y su Extension Pack, verificando que ambos correspondan a la misma versión. También se crea una máquina virtual que servirá como base para instalar Ubuntu Server.

**Actividades principales:**
- Comprobar los requisitos del equipo anfitrión, incluyendo memoria, espacio en disco y soporte de virtualización.
- Instalar VirtualBox y el Extension Pack.
- Crear y configurar la máquina virtual para el laboratorio.
- Definir recursos como memoria RAM, almacenamiento y opciones de red.

**Resultado esperado:** contar con una máquina virtual lista para instalar el sistema operativo del servidor.

**Conceptos clave:** virtualización, hipervisor, máquina virtual, recursos virtuales y configuración de red.

<br>

### Práctica 2. Instalación de Ubuntu Server 24.04 LTS

**Objetivo:** instalar Ubuntu Server en la máquina virtual creada durante la práctica anterior.

Esta actividad transforma la máquina virtual en un entorno de servidor Linux. Durante la instalación se configura el almacenamiento, se crea el usuario administrador y se habilita OpenSSH Server para permitir el acceso remoto.

**Actividades principales:**
- Descargar la imagen ISO de Ubuntu Server 24.04 LTS.
- Iniciar la máquina virtual desde la imagen de instalación.
- Configurar el disco y completar la instalación del sistema.
- Crear las credenciales del usuario administrador.
- Habilitar OpenSSH Server para futuras conexiones remotas.

**Resultado esperado:** disponer de un servidor Ubuntu funcional, accesible desde la consola de VirtualBox y preparado para su configuración inicial.

**Conceptos clave:** distribución Linux, instalación de servidor, usuario administrador, particionado y SSH.

<br>

### Práctica 3. Configuración inicial de Ubuntu Server

**Objetivo:** actualizar y verificar el servidor antes de instalar servicios adicionales.

Después de instalar el sistema operativo, es importante aplicar las actualizaciones disponibles, revisar la conectividad y reconocer los comandos básicos de administración. Esta etapa ayuda a preparar una base estable para la instalación de MySQL.

**Actividades principales:**
- Iniciar sesión en Ubuntu Server.
- Actualizar la lista de paquetes e instalar las actualizaciones disponibles.
- Consultar la identidad del usuario, el nombre del equipo y los directorios.
- Revisar las interfaces y direcciones IP.
- Comprobar la conectividad de red.
- Verificar el estado de servicios y familiarizarse con la administración desde terminal.

**Comandos de referencia:**

```bash
sudo apt update
sudo apt upgrade
whoami
hostname
pwd
ls -la
ip addr
ping -c 4 8.8.8.8
systemctl status ssh
```

**Resultado esperado:** tener Ubuntu Server actualizado, con conectividad comprobada y listo para instalar el sistema gestor de bases de datos.

**Conceptos clave:** APT, privilegios `sudo`, interfaz de línea de comandos, direcciones IP, conectividad y servicios.

<br>

### Práctica 4. Instalación y configuración de MySQL 8.0

**Objetivo:** instalar MySQL en Ubuntu Server, aplicar medidas básicas de seguridad y practicar operaciones SQL fundamentales.

En esta práctica se incorpora el servicio de bases de datos al servidor previamente configurado. Después de instalarlo, se verifica su funcionamiento y se realizan ejercicios para crear una base de datos, definir tablas y administrar registros.

**Actividades principales:**
- Instalar el paquete del servidor MySQL.
- Comprobar que el servicio esté activo.
- Ejecutar el procedimiento de seguridad posterior a la instalación, cuando corresponda.
- Acceder al cliente MySQL desde la terminal.
- Crear una base de datos y una tabla para almacenar información de ejemplo.
- Insertar y consultar registros, además de revisar la estructura de las tablas.

**Comandos de referencia:**

```bash
sudo apt install mysql-server
sudo systemctl status mysql
sudo mysql
```

Ejemplos de sentencias SQL:

```sql
SHOW DATABASES;
CREATE DATABASE practica4;
USE practica4;
CREATE TABLE alumnos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL
);
INSERT INTO alumnos (nombre) VALUES ('Alumno de prueba');
SELECT * FROM alumnos;
DESCRIBE alumnos;
```

**Resultado esperado:** contar con MySQL instalado y en ejecución, una base de datos de práctica y experiencia inicial en la ejecución de consultas SQL.

**Conceptos clave:** sistema gestor de bases de datos relacional, SQL, bases de datos, tablas, registros, servicio MySQL y seguridad básica.

<br>

### Práctica 5 Gestión de usuarios, permisos y respaldos en MySQL

**Objetivo** El propósito es administrar cuentas de MySQL mediante el principio de mínimo privilegio y practicar la creación de respaldos y la restauración de bases de datos con `mysqldump`.

**Actividades principales:**
- Crear usuarios específicos para las tareas requeridas.
- Asignar y revisar permisos con `GRANT` y `SHOW GRANTS`.
- Retirar permisos cuando sea necesario mediante `REVOKE`.
- Generar un respaldo de una base de datos.
- Comprobar el archivo de respaldo y practicar su restauración.

**Comandos de referencia:**

```sql
CREATE USER 'usuario_prueba'@'localhost' IDENTIFIED BY 'cambiar_esta_clave';
GRANT SELECT ON practica4.* TO 'usuario_prueba'@'localhost';
SHOW GRANTS FOR 'usuario_prueba'@'localhost';
```

```bash
mysqldump -u root -p practica4 > respaldo.sql
```

> Los nombres de usuario, contraseñas y comandos anteriores son ejemplos. Deben adaptarse al entorno de laboratorio y no utilizarse con contraseñas reales o débiles.

**Conceptos clave:** usuarios, privilegios, mínimo privilegio, respaldo, restauración e integridad de los datos.

<br>

## Relación entre las prácticas

El trabajo sigue una secuencia que permite construir el entorno de manera gradual:

1. **VirtualBox:** se prepara la infraestructura virtual.
2. **Ubuntu Server:** se instala el sistema operativo del servidor.
3. **Configuración inicial:** se actualiza el sistema y se comprueba la conectividad.
4. **MySQL:** se instala el servicio de bases de datos y se realizan operaciones SQL.
5. **Continuidad (Unidad II):** se profundiza en el control de acceso y la protección de los datos mediante respaldos.

Cada etapa depende de que la anterior funcione correctamente. Por ello, es recomendable verificar el resultado de cada práctica antes de continuar con la siguiente.

<br>

## Aprendizajes obtenidos

El desarrollo de estas prácticas permite reforzar los siguientes conocimientos:

- Preparación de máquinas virtuales y asignación de recursos.
- Instalación y configuración inicial de un sistema operativo Linux para servidores.
- Uso de comandos de terminal para administrar archivos, paquetes, red y servicios.
- Acceso remoto a un servidor mediante SSH.
- Instalación y comprobación de un servicio de bases de datos.
- Creación de bases de datos, tablas y registros mediante SQL.
- Importancia de proteger el servidor y limitar los privilegios de cada usuario.
- Necesidad de generar y verificar respaldos para facilitar la recuperación de información.

<br>

## Conclusión

Las prácticas permitieron construir progresivamente un entorno de laboratorio para la administración de servidores. Comenzamos con la virtualización mediante VirtualBox, continuamos con la instalación y preparación de Ubuntu Server y, posteriormente, incorporamos MySQL para trabajar con bases de datos relacionales.

Además de aprender comandos y procedimientos técnicos, el proceso destaca la importancia de comprobar cada configuración, mantener actualizado el sistema y considerar la seguridad desde el inicio. La gestión de usuarios y la realización de respaldos, abordadas en la práctica de continuidad, complementan estas bases y ayudan a comprender mejor las responsabilidades de la administración de servidores.
