---
title: "How to install Google Earth on Lubuntu?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by MarsbarloveR on 2010-11-06
How is Google Earth installed on Lubuntu? For some reason (the reason being that i am a noob) i cant seem to figure it out.

Any hints/tips are much apreciated. Thanks!

---

### Post by Hovercat on 2010-11-06
Have you tried using WINE?

---

### Post by Soul-Sing on 2010-11-06
First thing to know is your video/graphics card, and does it support 3d acceleration?
Without direct rendering you'r problab. not able to run the program in a decent way.

---

### Post by oldos2er on 2010-11-06
> **Hovercat said:**
> Have you tried using WINE?

Why would one do that? The native Linux version works fine.

To the OP: There are two ways; you can download GoogleEarthLinux.bin from Google, or you can enable the Medibuntu repository (medibuntu.org) and install it using Ubuntu Software Center or apt-get.

---

### Post by godspeedmav on 2010-11-09
You could follow this guide: **_[http://ubuntuguide.net/how-to-install-google-earth-in-ubuntu-10-10-maverick](http://ubuntuguide.net/how-to-install-google-earth-in-ubuntu-10-10-maverick)_**

As the HOWTO is meant for 64bit version, you could leave out ```
sudo apt-get install ia32-libs lib32nss-mdns
``` part or if yours is also 64 bit, follow the rest of the tutorial. 

And what I've found out is you also need to install ```
sudo apt-get install ttf-dejavu ttf-bitstream-vera
``` if you don't have it already, before you follow the last command of the HOWTO.

And of course please check if your video/graphic card support 3D acceleration. ;)

---

