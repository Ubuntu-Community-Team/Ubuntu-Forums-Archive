---
title: "Cannot connect to my wireless network."
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by hombrepajaro on 2008-06-10
Hi all, I'm new to the forums and a new ubuntu user and let me just say that I love it!

I only have one setback right now I cannot connect to my wireless network. I'm running Ubuntu on a 80/20 partition with windows XP. My computer is  Dell Latitude / D820. 

Could any one show some light on this issue?

I would really much appreciate it!


Thank you!

Adrian Ganem
Monterrey, Mexico

---

### Post by sam_delta on 2008-06-10
hello Adrian, in order to help you out, we need to know which wireless network card you have, to do so, we need you to post the output of the command 'lspci'
so could you please open a terinal (aplications>accessories>terminal) and type the following command and post the output here```
lspci
``` 

pd. im from monterrey too/soy de monterrey tambien :p

sam

---

### Post by hombrepajaro on 2008-06-10
Sam thank you/Gracias!

Is there a way to check this from windows XP?

---

### Post by sam_delta on 2008-06-10
hmm, i dont know, havnt used xp in a long time, but i guess you can check it under contorl panel>system>hardware or something.   since its a dell latitude and not working by default, i guess its a broadcom wireless chipset, but i need to know exactly which model

sam

---

### Post by hombrepajaro on 2008-06-10
Tarjeta mini-pci de red inalambrica WLAN de banda dual 2490 de Dell and another that is disabled called Broadcom NetXteme 57xx Gigabit Controller

i hope this helps.

---

### Post by sam_delta on 2008-06-10
Broadcom NetXteme 57xx Gigabit Controller is the wired connection adapter
dell 2490 WLAN is your wireless card, and dell wireless cards use broadcom chipsets

here is a quick things you can try
1. while in ubuntu. plug in your wired connection and do all available updates (so into system>administration>update manager, click on check, then install)

2. with all the updates made and with the wired connection plugged in, go into system>administration>hardware drivers, there should be a "broadcom wirelesss driver" listed in there, try to enable them and restart your computer.

if there are no drivers listed under system>administration>hardware drivers, post back here 

also, while you are in ubuntu, itll be helpfull if you post the ouptut of the command "lspci" in here as itll give us the exact chipset your dell wireless card is using

sam

---

### Post by hombrepajaro on 2008-06-10
Espero esto te sirva y gracias por toda tu ayuda!

Voy a tratar lo que mencionas arriba. :guitar:


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by sam_delta on 2008-06-10
ok , try it, if it does not work, post here with what happened, and we will install b43-fwcutter

spanish translation>>>>>. ok , intenta, si no funciona, postea aki lo que paso, y intentamos con el driver b43-fwcutter

sam

---

### Post by hombrepajaro on 2008-06-11
I tried it and had no luck connecting to my wireless network. 

What do you think should be the next approach here?

and again GRACIAS!

---

### Post by sam_delta on 2008-06-11
lets try installing b43-fwcutter

with an internet cable plugged in (very important, it wont be able to install without internet connection)

open a terminal and type 
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with 'yes' when asked if want to fetch the firmware

restart your computer and check if it works/or now appears under sys>admin>hardware drivers

sam

---

### Post by hombrepajaro on 2008-06-11
I'll try this when I get home from work! :)

Question: Will this have any impact when trying to run wireless Internet on Windows XP?

---

### Post by sam_delta on 2008-06-11
nop, not in any way,  this will just install b43-fwcutter drivers under linux, wont even touch xp.

if it does not work, we can just uninstall those drivers by typing ```
sudo aptitude remove b43-fwcutter
``` and try diferent drivers, but again ,it will not impact your winxp install

sam

---

### Post by hombrepajaro on 2008-06-11
It Works!

Muchas Gracias!:)

---

### Post by sam_delta on 2008-06-12
glad it works :)
anything else, ill be around
enjoy ubuntu bro

me da gusto que funcione, que disfrutes ubuntu y estamos en contacto para cualquier cosa

sam

---

