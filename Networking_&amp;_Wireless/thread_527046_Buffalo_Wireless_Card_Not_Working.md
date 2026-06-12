---
title: "Buffalo Wireless Card Not Working"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by dilbert92 on 2007-08-16
Hi everyone!
I just built a new computer, and I can't get the wireless to work in Ubuntu Studio (and SuSE).
I have a Buffalo card, that I have had working in Ubuntu Studio before on a different machine. 

iwconfig sees the card, but I can't see any networks. When I type the SSID in the network box it reads
"rgmweb" but in iwconfig it says SSID 'r'. So what happend to "gmweb"?

Also it works in Windows and a live CD of Back Track 2.

What am I missing? Any help would be great!

Thanks,

Zakk

---

### Post by fazavon on 2007-08-16
this one worked for me

1.2.2.2. Firmware Packages

As an alternative to running the script, you can install the firmware files from a package. To automatically keep up to date, add this repository line to your /etc/apt/sources.list:

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) dapper-cafuego bcm43xx

and make sure apt knows about the GnuPG key used to sign the packages:

wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

Then update your package listsings and install the bcm43xx-firmware package.

or download the package directly:

wget -c [http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb](http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb)

and then install it manually:

sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb

Enjoy!!

---

