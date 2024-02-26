# Установка arduino-pico в PlatformIO
# Windows
1. Установить VS Code с [сайта](https://code.visualstudio.com/).
2. Запустить VS Code и во вкладке расширения установить PlatformIO
3. Запустить powershell и ввести команду 
   ```
   git config --system core.longpaths true
   ```
4. Добавить длинные пути в Windows
	* **Способ 1: через PowerShell**
   		Выполнить комманду в PowerShell от имени администратора: 
   		```
		New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
		```
	* **Способ 2: С помощью редактора реестра**
  		Нажать Win+R и ввести `regedit`. Открыть ветку: 
		```
		HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem
		```
		Установить значение параметра `LongPathsEnabled` на 1.
	* **Способ 3: Через редактор политик**
		1. Нажмите клавишу «Windows» и введите gpedit.msc, затем нажмите клавишу «Enter». Это запустит редактор локальной групповой политики.
		2. Перейдите в раздел `«Политика локального компьютера» > «Конфигурация компьютера» > «Административные шаблоны» > «Система» > «Файловая система»`.
		3. Откройте пункт «Включить длинные пути NTFS/Win32» и выберете пункт "Включено".
1. Перезагрузить компьютер.
2. Открыть Visual Studio Code.
3. Открыть меню расширения PlatformIO.
4. Открыть пункт `Quick Access > PIO home > Platforms`.
5.  Нажать `Advanced Instalation`.
6.  Вставить ссылку в поле ввода:
	```
	https://github.com/maxgerhardt/platform-raspberrypi.git
	``` 
7.  Нажать кнопку «Install».
8.  Создать проект.
9.  Если в открывшимся проекте появились ошибки необходимо изменить содержимое файла `platformio.ini` на:
    ```ini
	[env:pico]
	platform = https://github.com/maxgerhardt/platform-raspberrypi.git
	board = pico
	framework = arduino
	board_build.core = earlephilhower
	```
# Linux
1. Установить VS Code.
2. Запустить VS Code и во вкладке расширения установить PlatformIO.
3. Выполнить комманду в терминале:
   ```
   curl -fsSL https://raw.githubusercontent.com/platformio/platformio-core/develop/platformio/assets/system/99-platformio-udev.rules | sudo tee /etc/udev/rules.d/99-platformio-udev.rules
   ```
4. Запустить команду: `sudo service udev restart`
5. Дать пользователю доступ к группам, вместо $USER указать имя пользователя:
	* Debian 
		```
		sudo usermod -a -G dialout $USER
		sudo usermod -a -G plugdev $USER
		```
	* Arch
		```
		sudo usermod -a -G uucp $USER
		sudo usermod -a -G lock $USER
		```
6. Открыть Visual Studio Code.
7. Открыть меню расширения PlatformIO.
8. Открыть пункт `Quick Access > PIO home > Platforms`.
9.  Нажать `Advanced Instalation`.
10. Вставить ссылку в поле ввода:
	```
	https://github.com/maxgerhardt/platform-raspberrypi.git
	``` 
11. Нажать кнопку «Install».
12. Создать проект.
13. Если в открывшимся проекте появились ошибки необходимо изменить содержимое файла `platformio.ini` на:
    ```ini
	[env:pico]
	platform = https://github.com/maxgerhardt/platform-raspberrypi.git
	board = pico
	framework = arduino
	board_build.core = earlephilhower
	```