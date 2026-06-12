---
title: "Driver problem..."
date: 2010-11-28
forum: New to Ubuntu
---

### Post by joweebee on 2010-11-28
Hello
 
I have an acer travelmate 2420, and have been dual booting xp and edubuntu 9.10. I am getting a new HD, and planning to just install ubuntu 10.10. Is this wise?
 
Also, I remeber spending 3 days getting my wireless driver. I typed something into the terminal and it churned away, downloaded and installed it for me. When I reinstall, where can I easily get the driver from, or is it possible to save the existing driver?
 
I am relatively new to linux, and only know a few basic terminal commands.
 
Thankyou

---

### Post by 12apennachi on 2010-11-28
10.10 had increased wlan driver support, so you might have better luck there. And the best help can be the forums. If the wireless drivers don't work there is always help here. And as for installing 10.10 on a second hd, there is no reason you shouldn't do it.

And if you still want to run xp, you can install it on a virtual machine with Virtualbox. That's what I do. And by the way, do you have a broadcom card? Because I had some trouble with that too but it works fine now.
And before you get your new hd, type in lspci in terminal and it will tell you what driver you have installed on your wlan card, remember that and install it on your new hd with 10.10

---

### Post by joweebee on 2010-11-28
wow, that was fast!
 
Thankyou very much. Is 10.10 stable or should I go for 10.4? I didn't upgrate to that because I heard that it messed up my friends computer.
 
Do you think that a VB is better that dual boot. I've used them both, so vaguely know how to do it!

---

### Post by 12apennachi on 2010-11-28
I have 10.04 and my parents have 10.10. They haven't had problems but I like having LTS for that reason exactly.

VB isn't faster than dual boot, but it is easier and a lot less intrusive.

---

### Post by joweebee on 2010-11-28
Am i right in saying that LTS means long term support, and that that means ubuntu support it for 3 years?
 
Also, can I install the edubuntu stuff from the software manager thingy?

---

### Post by joweebee on 2010-11-28
Just rereading your 1st post, it is a broadcom card, yes.

Also, this is the output from lspci:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
[COLOR=Red]06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

I presume that it is the bit in red that I need. How does this tell me what driver I need to remember?
Also, is there not just a way to save my existing driver for use on my new HD?

---

### Post by Paqman on 2010-11-28
> **joweebee said:**
> Am i right in saying that LTS means long term support, and that that means ubuntu support it for 3 years?


Yup.
 
> 
Also, can I install the edubuntu stuff from the software manager thingy?

Yup. Just install the package edubuntu-desktop.

Re your card, Broadcom 4318 cards aren't a big deal. I used to have a Travelmate with one in. All you need to do is look in the Hardware Drivers tool for the driver it suggests and install that. Easy peasy, although you may (it's been a while) need an internet connection at the time. If so just plug straight into your router until you've got the wifi working.

---

### Post by Locke_99GS on 2010-11-28
On Maverick, if your wireless doesn't function out-of-box, the usual fix (and easiest) is to install the *linux-firmware-nonfree* package, which includes many, many non-free drivers. Make sure that the multiverse repository is enable in the software sources.

```

sudo apt-get install linux-firmware-nonfree

```

---

### Post by joweebee on 2010-11-28
Thankyou [COLOR=red]Locke_99GS, [/COLOR][COLOR=lime]Paqman & [/COLOR][COLOR=blue]12apennachi.[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]Your help so far is very much appreciated. [/COLOR]
 
> Make sure that the multiverse repository is enable in the software sources.
How do I do that - is it obvious when I come to it?
 
> look in the Hardware Drivers tool for the driver it suggests and install that. 
Can you double-click it or something then 'cos atm I have a driver that is up and running, and that bit of software seems to be a bit useless!?

---

### Post by Locke_99GS on 2010-11-28
I'm not on a Maverick machine at the moment, but the software sources can be found from the "Setting" button on the bottom of the Update manager, or also from one of the menus in Software Centre.

---

### Post by joweebee on 2010-11-29
Thanks. Found it. So by following those things I will be able to get my WLAN driver?

Also if I leave this thread alone, can I come back to it later once I have my new hd? Or will it be deleted?

---

