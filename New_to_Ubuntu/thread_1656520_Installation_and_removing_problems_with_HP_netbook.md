---
title: "Installation and removing problems with HP netbook"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by fakhrul12 on 2010-12-31
i`ve already tried using this command

> sudo apt-get install -f

instead...having this kind of resut...

> [FONT=monospace]athirah@athirah-HP-Mini-210-1000:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][FONT=monospace]
[/FONT]

i cant even istall an update and software and all...
can anyone help me with this... :(

*I didnt know if this is netbook remix edition...just ubuntu 10.10 netbook edition if i`m not mistaken...were downloaded yesterday at the main site

---

### Post by Rubi1200 on 2010-12-31
Hi and welcome to the forums :-)

See this for more information:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/655111)

---

