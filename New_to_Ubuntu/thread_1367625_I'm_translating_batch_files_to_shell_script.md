---
title: "I'm translating batch files to shell script"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Glawar on 2009-12-29
I've spent countless hours translating a rough-around-the-edges German game called DS-Lan to English, and making vast improvements to the code and user interface where possible.

The game is browser-based, and played only over a LAN. In order to host a server on windows, I had to run batch files called **apache_start.bat**, **mysql_start.bat**, and **dslan_start.bat**. And to complete installation, I had to run a batch file called **setup_xampp.bat**.

Well, now that I'm switching to Ubuntu (and loving it!) I wanted to be able to host a server on my Ubuntu machine. But I discovered .bat is unique to Windows, and guessed that I would need to translate the file to shell script so the Ubuntu shell could handle it.

Anyway, I figured I could always post the code somewhere and ask someone else to convert it, but I want to learn how to do it myself. So I used [this webpage]("http://tldp.org/LDP/abs/html/dosbatch.html"), and went with my gut instinct where necessary. But after trying to translate just the first one, I was getting error after error while running the shell script file from the terminal, and need expert help.

Anyway, I need assistance with the translation of these four .bat files (following). I would also appreciate some coaching about what I was doing wrong with my .shell file (attached).

**setup_xampp.bat**
```

#!/bin/bash

@ECHO OFF 
COPY apache\bin\php5ts.dll php 
if "%1" == "sfx" ( 
    cd xampplite 
) 
if exist php\php.exe GOTO Normal 
if not exist php\php.exe GOTO Abort 
 
:Abort 
echo Sorry ... cannot find php cli! 
echo Must abort these process! 
pause 
GOTO END 
 
:Normal 
set PHP_BIN=php\php.exe 
set CONFIG_PHP=install\install.php 
%PHP_BIN% -n -d output_buffering=0 %CONFIG_PHP% 
GOTO END 
 
:END 
pause 

```**apache_start.bat**
```

@echo off 
echo Please close this command only for Shutdown 
echo Apache 2 is starting ... 
 
apache\bin\apache.exe 
 
if errorlevel 255 goto finish 
if errorlevel 1 goto error 
goto finish 
 
:error 
echo. 
echo Apache could not be started 
pause 
 
:finish 

```**mysql_start.bat**
```

@echo off 
echo Please dont close Window while MySQL is running 
echo MySQL is trying to start 
echo Please wait  ... 
echo MySQL is starting with mysql\bin\my.cnf (console) 
 
mysql\bin\mysqld --defaults-file=mysql\bin\my.cnf --standalone --console 
 
if errorlevel 1 goto error 
goto finish 
 
:error 
echo. 
echo MySQL could not be started 
pause 
 
:finish 

```**dslan_start.bat**
```

cd htdocs\daemons 
:endlos 
..\..\apache\bin\php.exe event.php 
goto endlos

```

---

### Post by falconindy on 2009-12-29
These aren't really necessary if you setup Apache, Mysql, and PHP properly to begin with. They will run as services and can be controlled either via upstart or /etc/init.d/ rc scripts.

---

### Post by gsocker on 2009-12-29
I'm not an apache/PHP expert, but there are a couple of obvious problems:
  ".dll"(Dynamic Link Library) does not exist in Linux. The equivalent is ".so" (Shared Object/more commonly know as "shared library"). 
It looks like you're trying to run the windows executables. This will not work without WINE(may not work with it either) and is pointless, since Apache, PHP, and MySQL all run on Linux as native programs. 
Also, Linux does not normally use ".exe". Executables are made executable via file permissions, not extensions.

Linux uses forward slashes, not backslashes. Backslashes are used as shell escape characters. You wrote:
```

cp \apache\bin\php5ts.dll php

```
The shell sees:
```

cp pacheinhp5ts.dll php

```

Apache is normally run by an init script during startup. The same goes for MySQL. I believe the PHP library is loaded by Apache if setup correctly(could someone with more LAMP experience flesh this out?)
Typically, you don't need the shell scripts - you just stuff the PHP files in the appropriate location, ensure apache and MySQL are configured correctly, and tell the boot system to auto-start these during boot. Note: do **not** expose this to the internet if you are not **sure** the game is free of security holes. 
If you want to run it as a normal user, be aware that Apache cannot bind to any port below 1024 unless it is started as root via sudo.

There are many bash and Linux/Apache/Mysql tutorials available via Google. These may prove helpful.

---

