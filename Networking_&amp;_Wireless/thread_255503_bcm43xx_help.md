---
title: "bcm43xx help"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by kk0425 on 2006-09-11
I need some help with my broadcom wireless card (bcm 4306 Rev 3). Im running dapper on a Compaq R4000 with 512MB of ram, AMD 64 Athlon processor and with a built in wireless card.
I've been following many tuturiols and have tried everything short of a clean install of ubuntu dapper. When I follow [this]("http://ubuntuforums.org/showthread.php?t=201902") tutorial i get an invalid driver at this step **ndiswrapper -l** and a fatal error at **sudo ndiswrapper -m**.
Ive also tried using the fwcutter HOWTO written by nickm but that doesn't work either.](*,)  Im fairly new to linux and any help would be appreciated.

---

### Post by fazavon on 2006-09-12
this one worked for me

1.2.2.2. Firmware Packages

As an alternative to running the script, you can install the firmware files from a package. To automatically keep up to date, add this repository line to your /etc/apt/sources.list:

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) dapper-cafuego bcm43xx

and make sure apt knows about the GnuPG key used to sign the packages:

wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

Then update your package listsings and install the bcm43xx-firmware package.

or download the package directly:

wget -c [http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb](http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb)

and then install it manually:

sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb

---

