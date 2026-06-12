---
title: "Ralink rt2500 module not actually working.."
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by ggonmar on 2006-08-26
hi there,
Im new on Linux, so setting up my Wifi connection through Ubuntu is gettin me on my nerves! :P
so, I have installed Ubuntu 5.10 kernel 2.6.12-9-386 and I have a Conceptronic PCI card (C54Ri, v2.0), with chipset Ralink rt2500.

From the first time I ran Ubuntu, it didnt get the PCI card, not on the "networking" part of the Administration's menu, nor on the terminal on "lspci"... actually when I lspci it says: 
[INDENT]0000:0a:00 Network Controller: RaLink: Unknown device 0302[/INDENT]
so I tried tons of manuals around, tons of .tar.gz files, but none worked out...
here are the ones I tried: 

[https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old/DriverAndRaconfigOld#InstallRaconfig](https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old/DriverAndRaconfigOld#InstallRaconfig)
  [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
   [http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download](http://prdownloads.sourceforge.net/rt2400/rt2500-1.1.0-b4.tar.gz?download)
[http://www.ralinktech.com/drivers/Linux/RT2500-Linux-STA-1.4.6.4.tar.gz](http://www.ralinktech.com/drivers/Linux/RT2500-Linux-STA-1.4.6.4.tar.gz)
 

and some more I just cant find the links now :P

anyway, I tried to run them, "make" them and all this, and the most I got was with the "rt2500-1.1.0-b4.tar.gz, which got me to a "./Configure" file. It pops up the Ralink RT2500 Station COnfiguration, and asks for the Linux kernel source directory... after some hours for finding out what path I had to write there, it says "Module install directory: /lib/modules/2.6.12-9-386/kernel/drivers/net

I suppose that at this point I have installed the card, and it should actually recognize it on lspci... but still it doesnt :S

now Im stucked and quite depressed with this ](*,) 

so, could anyone help me out on this? step by step!!!!
if possible, my AIM is "guilleonthenet", and my MSN is "guille_yo@hotmail.com"... and even gtalk -> "ggonzalezmartin"  so... instant messaging might be even more helpful! but mail or forum is just fine :)

please help me!!!

---

### Post by ggonmar on 2006-08-28
hello???

anyone there????? :(

---

### Post by ggonmar on 2006-08-29
hey,
just wanted to say I finally got to install it, but never with the drivers around the net...

way to solve it: install Ubuntu 6.06, it does have the drivers :)

---

