---
title: "Verion of installed ubuntu"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by kalaarangan on 2009-05-05
Hi friends,
I am a newbie to ubuntu. I was pleased with reviews on ubuntu and installed 9.04 today using Wubi installer. Everything was fine and i am just starting to explore. I hav a problem,

1. when i try to install adobe reader, i get following message...

dpkg: error processing install_flash_player_10_linux.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 install_flash_player_10_linux.deb


My machine is a hp dv4-1199ee having intel core 2 duo. I was wondered because how the amd64 version of linux can be installed in an i386 machine.

can anyone help me. i need to know options,

1. reason for amd64 installation
2.how to switch to i386 version

thanks,
kalaarangan

---

### Post by binbash on 2009-05-05
you installed 64 bit ubuntu and trying to install a x86 package.That is the error you got.You should install 64 bit version of flash player.

---

### Post by 3rdalbum on 2009-05-05
Add the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and install Acrobat Reader from there. You've obviously installed the 64-bit edition of Ubuntu (known as AMD64 although it also works on Intel 64-bit processors).

---

