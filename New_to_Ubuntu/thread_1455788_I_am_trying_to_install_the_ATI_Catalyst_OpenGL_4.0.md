---
title: "I am trying to install the ATI Catalyst OpenGL 4.0 preview driver for Linux..."
date: 2010-04-16
forum: New to Ubuntu
---

### Post by JCBARCA on 2010-04-16
Hi.
 I am new to Linux and I am trying to install the ATI Catalyst OpenGL 4.0 preview driver for Linux. The problem is that the installer tells me that there not is enough free space to install the driver. However the driver only requires 75 MB and there are several GB of free space.
 I am running Linux Knoppix 6.2 and I have a ATI Mobillity Radeon HD 4650 graphics card.

I type the following into my terminal as a super user:

 root@Microknoppix:/home/fglrx-8.712.3.1# dir
ati-driver-installer-8.712.3.1-x86.x86_64.run  check.sh  doc
root@Microknoppix:/home/fglrx-8.712.3.1# chmod 755 ati-driver-installer-8.712.3.1-x86.x86_64.run
root@Microknoppix:/home/fglrx-8.712.3.1# ./ati-driver-installer-8.712.3.1-x86.x86_64.run
  
 and get the following output:

 Created directory fglrx-install.JkYhDu
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.712.3.1...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.4 and later releases 
cp: cannot stat `x740/usr/X11R6/lib/modules/glesx*': No such file or directory
cp: cannot stat `x740/usr/X11R6/lib/modules/amdxmm*': No such file or directory
find: `install/usr/lib/xorg/modules/glesx*': No such file or directory
find: `install/usr/lib/xorg/modules/amdxmm*': No such file or directory
Removing temporary directory: fglrx-install.JkYhDu
root@Microknoppix:/home/fglrx-8.712.3.1#

 Can someone please tell me what I am doing wrong and how I can install the driver...

---

