---
title: "Sourceforge problems when installing"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by C-Sauron on 2009-09-13
Hi!

Since I've installed the "ubuntu-restricted-extras" thing, every time I install a new application from "Add and remove..." I get an error message about "ttf-mscorefonts-installer". When I watch the "details" during installation, it always appear some kind of error connecting sourceforge. I don't have any idea about what is this. It's very annoying because it makes the download and installation of new applications very long (as it tries to reconnect several times to sourceforge).

Can somebody help me? :confused:

Thanks in advance :)

PS: I'm not sure if this is the correct forum to post this. I posted it here because I'm an "absolute beginner":P

---

### Post by philinux on 2009-09-13
Open a terminal. Apps>accessories>terminal.

Use the following command and post back with the errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by C-Sauron on 2009-09-13
Thanks for your reply!

I did what you tell me and i get this:

```
Obj http://es.archive.ubuntu.com jaunty Release.gpg                       
Obj http://es.archive.ubuntu.com jaunty/main Translation-es               
Obj http://es.archive.ubuntu.com jaunty/restricted Translation-es
Obj http://es.archive.ubuntu.com jaunty/universe Translation-es 
Obj http://es.archive.ubuntu.com jaunty/multiverse Translation-es
Obj http://es.archive.ubuntu.com jaunty-updates Release.gpg     
Ign http://es.archive.ubuntu.com jaunty-updates/main Translation-es
Ign http://es.archive.ubuntu.com jaunty-updates/restricted Translation-es
Ign http://es.archive.ubuntu.com jaunty-updates/universe Translation-es
Ign http://es.archive.ubuntu.com jaunty-updates/multiverse Translation-es
Obj http://es.archive.ubuntu.com jaunty Release                 
Obj http://es.archive.ubuntu.com jaunty-updates Release                        
Obj http://es.archive.ubuntu.com jaunty/main Packages                          
Obj http://es.archive.ubuntu.com jaunty/restricted Packages     
Obj http://es.archive.ubuntu.com jaunty/main Sources            
Obj http://es.archive.ubuntu.com jaunty/restricted Sources      
Obj http://es.archive.ubuntu.com jaunty/universe Packages       
Obj http://es.archive.ubuntu.com jaunty/universe Sources        
Obj http://es.archive.ubuntu.com jaunty/multiverse Packages     
Obj http://es.archive.ubuntu.com jaunty/multiverse Sources      
Obj http://es.archive.ubuntu.com jaunty-updates/main Packages   
Obj http://es.archive.ubuntu.com jaunty-updates/restricted Packages
Obj http://es.archive.ubuntu.com jaunty-updates/main Sources    
Obj http://es.archive.ubuntu.com jaunty-updates/restricted Sources
Obj http://es.archive.ubuntu.com jaunty-updates/universe Packages
Obj http://es.archive.ubuntu.com jaunty-updates/universe Sources
Obj http://es.archive.ubuntu.com jaunty-updates/multiverse Packages
Obj http://es.archive.ubuntu.com jaunty-updates/multiverse Sources
Obj http://security.ubuntu.com jaunty-security Release.gpg      
Ign http://security.ubuntu.com jaunty-security/main Translation-es
Ign http://security.ubuntu.com jaunty-security/restricted Translation-es
Ign http://security.ubuntu.com jaunty-security/universe Translation-es
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-es
Obj http://security.ubuntu.com jaunty-security Release
Obj http://security.ubuntu.com jaunty-security/main Packages
Obj http://security.ubuntu.com jaunty-security/restricted Packages
Obj http://security.ubuntu.com jaunty-security/main Sources
Obj http://security.ubuntu.com jaunty-security/restricted Sources
Obj http://security.ubuntu.com jaunty-security/universe Packages
Obj http://security.ubuntu.com jaunty-security/universe Sources
Obj http://security.ubuntu.com jaunty-security/multiverse Packages
Obj http://security.ubuntu.com jaunty-security/multiverse Sources
Leyendo lista de paquetes... Hecho
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? 
```

I have Ubuntu in Spanish, so I'll try to translate the last few lines into English:

```
Reading package list... Done
Reading package list... Done
Creating premises tree
Reading state information.... Done
0 updated, 0 will be updated, 0 for removing and 0 not updated
1 not fully installated or removed
0B of additional disk space will be used after this operation
¿Do you want to continue [Y/N]? 
```

If I type "Y", it starts doing the same thing as when I try to install other appz. I get this:

C```
onfigurando ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-09-13 18:27:51--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo surfnet.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «surfnet.dl.sourceforge.net»
--2009-09-13 18:28:01--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo mesh.dl.sourceforge.net... 213.203.218.122
Conectando a mesh.dl.sourceforge.net|213.203.218.122|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net [siguiente]
--2009-09-13 18:28:02--  http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolviendo prdownloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «prdownloads.sourceforge.net»
--2009-09-13 18:28:12--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo dfn.dl.sourceforge.net... 194.95.236.6
Conectando a dfn.dl.sourceforge.net|194.95.236.6|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net [siguiente]
--2009-09-13 18:28:12--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:28:22--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo heanet.dl.sourceforge.net... 193.1.193.66
Conectando a heanet.dl.sourceforge.net|193.1.193.66|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net [siguiente]
--2009-09-13 18:28:22--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:28:32--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo jaist.dl.sourceforge.net... 150.65.7.130
Conectando a jaist.dl.sourceforge.net|150.65.7.130|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=jaist.dl.sourceforge.net [siguiente]
--2009-09-13 18:28:33--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=jaist.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:28:43--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo nchc.dl.sourceforge.net... 211.79.60.17
Conectando a nchc.dl.sourceforge.net|211.79.60.17|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net [siguiente]
--2009-09-13 18:28:44--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:28:54--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Conectando a ufpr.dl.sourceforge.net|200.17.202.1|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net [siguiente]
--2009-09-13 18:28:55--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:29:05--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo internode.dl.sourceforge.net... 150.101.135.12
Conectando a internode.dl.sourceforge.net|150.101.135.12|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net [siguiente]
--2009-09-13 18:29:06--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:29:16--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo mesh.dl.sourceforge.net... 213.203.218.122
Conectando a mesh.dl.sourceforge.net|213.203.218.122|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net [siguiente]
--2009-09-13 18:29:16--  http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolviendo prdownloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «prdownloads.sourceforge.net»
--2009-09-13 18:29:26--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo voxel.dl.sourceforge.net... 208.122.31.3, 208.122.31.15, 208.122.31.13, ...
Conectando a voxel.dl.sourceforge.net|208.122.31.3|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net [siguiente]
--2009-09-13 18:29:27--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
--2009-09-13 18:29:37--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolviendo kent.dl.sourceforge.net... 212.219.56.167
Conectando a kent.dl.sourceforge.net|212.219.56.167|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net [siguiente]
--2009-09-13 18:29:37--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... 216.34.181.59
Conectando a downloads.sourceforge.net|216.34.181.59|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [siguiente]
--2009-09-13 18:29:42--  http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolviendo freefr.dl.sourceforge.net... 88.191.250.132
Conectando a freefr.dl.sourceforge.net|88.191.250.132|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 198384 (194K) [application/x-msdownload]
Guardando: «./andale32.exe»

100%[======================================>] 198.384      331K/s   en 0,6s    

2009-09-13 18:29:48 (331 KB/s) - `./andale32.exe' guardado [198384/198384]

--2009-09-13 18:29:48--  http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolviendo kent.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «kent.dl.sourceforge.net»
--2009-09-13 18:29:58--  http://internap.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolviendo internap.dl.sourceforge.net... 69.88.152.3
Conectando a internap.dl.sourceforge.net|69.88.152.3|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Moved Temporarily
Ubicación: http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net [siguiente]
--2009-09-13 18:30:04--  http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net
Resolviendo prdownloads.sourceforge.net... 216.34.181.59
Conectando a prdownloads.sourceforge.net|216.34.181.59|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [siguiente]
--2009-09-13 18:30:10--  http://freefr.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolviendo freefr.dl.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «freefr.dl.sourceforge.net»
--2009-09-13 18:30:20--  http://switch.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolviendo switch.dl.sourceforge.net... 130.59.138.21
Conectando a switch.dl.sourceforge.net|130.59.138.21|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=switch.dl.sourceforge.net [siguiente]
--2009-09-13 18:30:20--  http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolviendo downloads.sourceforge.net... falló: Expiró el tiempo de conexión.
wget: no se puede resolver la dirección del equipo «downloads.sourceforge.net»
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error al procesar ttf-mscorefonts-installer (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
laura@laura-desktop:~$ 
```

Some lines are in Spanish, so if you need me to translate any of them, tell me :)

---

### Post by arochester on 2009-09-13
I remember something like this happening a few years ago. It kept sticking at Anadale. It would be interesting to know which version you are using and how old it is...

I think I got around it be downloading the package from another source e.g. [http://linuxappfinder.com/](http://linuxappfinder.com/) and installing that one instead.

---

### Post by philinux on 2009-09-13
Open synaptic, click on any app then type in ttf-ms and it will highlight the appropriate line.

Click it's green square and choose mark for reinstallation.

---

### Post by C-Sauron on 2009-09-13
I tried the reinstallation, but I still get the same error. Should I try to uninstall it? I don't even know what the heck is "ttf-mscorefonts-installer". I guess it installs fonts from Windows...

> **arochester said:**
> I remember something like this happening a few years ago. It kept sticking at Anadale. It would be interesting to know which version you are using and how old it is...

I think I got around it be downloading the package from another source e.g. [http://linuxappfinder.com/](http://linuxappfinder.com/) and installing that one instead.

I'm using Ubuntu 9.04. I think it's the latest version, I downloaded it from the official website few days ago. I've searched in that website, I found the installer, but when I click "Install Now", a window appears saying that that appz is already installed.

---

### Post by C-Sauron on 2009-09-13
Ok, I "solved" it! I uninstalled the ttf-ms from synaptic, and now I can install and uninstall without that annoying delay.

Thank you very much!

---

