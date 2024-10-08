### Tiziano Pirez 4to 4ta

# Gestión de Software y Paquetes

## Cuestionario

1. **¿Qué es un paquete de software en GNU/Linux? Explica la diferencia entre un paquete binario y un paquete de código fuente.**
   - Un paquete de software es un conjunto de archivos necesarios para instalar, configurar y ejecutar un programa. La diferencia es que un paquete binario contiene el software precompilado, listo para ejecutarse, mientras que un paquete de código fuente contiene el código fuente que debe ser compilado antes de su instalación.

2. **¿Qué tipos de dependencias puede tener un paquete en Debian? Menciona y describe al menos tres.**
   - **Dependencias:** Un paquete puede depender de otro para funcionar. Ejemplo: `gimp` depende de `gimp-data`.
   - **Recomendaciones:** Un paquete puede recomendar otro para funcionalidades adicionales. Ejemplo: `mozilla-browser` recomienda `mozilla-psm`.
   - **Sugerencias:** Un paquete puede sugerir otro que mejora la funcionalidad, pero no es necesario. Ejemplo: `kmail` sugiere `gnupg`.

3. **¿Cuál es el propósito de un Gestor de Paquetes?**
   - Automatiza la instalación, actualización, configuración y eliminación de paquetes de software, manteniendo un registro de los programas instalados y resolviendo automáticamente las dependencias necesarias.

4. **Explica el proceso de instalación de un paquete utilizando el gestor de paquetes APT.**
   - 1. El usuario solicita la instalación mediante un comando, por ejemplo, `apt-get install nombre_paquete`.
   - 2. El gestor busca el paquete en los repositorios especificados en `/etc/apt/sources.list`.
   - 3. Descarga y desempaqueta el paquete, instalando todos los archivos necesarios.

5. **¿Qué son los repositorios y para qué sirven en la gestión de paquetes?**
   - Los repositorios son servidores que almacenan paquetes de software organizados. Sirven para facilitar la instalación y actualización de software, asegurando que se obtenga de una fuente confiable.

6. **¿Qué tipos de repositorios existen según su licencia? Da un ejemplo de cada uno.**
   - **main:** Paquetes 100% libres. Ejemplo: `deb http://deb.debian.org/debian main`.
   - **non-free:** Paquetes que no son completamente libres. Ejemplo: `deb http://deb.debian.org/debian non-free`.
   - **contrib:** Software libre que depende de software no libre. Ejemplo: `deb http://deb.debian.org/debian contrib`.

7. **¿Qué función tiene el archivo /etc/apt/sources.list en Debian y sus derivados?**
   - Contiene la lista de repositorios de donde se pueden descargar paquetes.

8. **Menciona tres comandos principales del gestor APT y describe brevemente su propósito.**
   - `apt-get install paquete`: Instala un paquete y sus dependencias.
   - `apt-get update`: Actualiza la lista de paquetes disponibles desde los repositorios.
   - `apt-get remove paquete`: Desinstala un paquete del sistema.

9. **¿Qué diferencia hay entre el comando apt-get y dpkg para la instalación de paquetes?**
   - `apt-get` gestiona paquetes y sus dependencias automáticamente, mientras que `dpkg` gestiona paquetes .deb directamente y no resuelve dependencias automáticamente.

10. **Describe los pasos para instalar un programa desde su código fuente en un sistema Debian.**
    1. Descargar el código fuente.
    2. Descomprimir el archivo.
    3. Entrar en el directorio descomprimido.
    4. Ejecutar `./configure` para preparar la compilación.
    5. Ejecutar `make` para compilar el código.
    6. Ejecutar `make install` para instalar el programa.

## Actividad Práctica

1. **Instalación de paquetes con APT:**

   ```bash
   sudo apt-get update
   sudo apt-get install htop
   ```
   Para desinstalar y limpiar el cache:
   ```bash
   sudo apt-get remove htop
   sudo apt-get autoclean
   ```

2. **Manipulación del archivo /etc/apt/sources.list:**
   Abroel archivo con:
   ```bash
   sudo nano /etc/apt/sources.list
   ```
   Agrega la línea:
   ```
   deb http://deb.debian.org/debian buster-backports main contrib non-free
   ```
   Luego actualiza la lista de paquetes:
   ```bash
   sudo apt-get update
   ```

3. **Uso de dpkg para gestionar paquetes locales:**
   - Descarga el paquete .deb de Google Chrome desde su sitio oficial.
   - Instala el paquete con:
   ```bash
   sudo dpkg -i google-chrome-stable_current_amd64.deb
   ```
   Si hay problemas de dependencias:
   ```bash
   sudo apt-get -f install
   ```

4. **Instalación desde código fuente:**
   ```bash
   wget https://www.python.org/ftp/python/3.10.6/Python-3.10.6.tgz
   tar -xzvf Python-3.10.6.tgz
   cd Python-3.10.6
   ./configure
   make
   sudo make install
   ```
