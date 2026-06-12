---
title: "Lxde Screen resolution"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Pth518 on 2010-01-23
Hi
i have recently installed LXDE and everything is great but when i try to adjust the screen res it only gives me 2 options. theyr both way to small for my monitor. how do i fix this?

also i have tried to use this:

xrandr -s 1024x768

but it doesnt work (btw i need slightly bigger than that i think.) 

please help. my res is way to small for the screen and makesit difficult to use!

thanks

---

### Post by meborc on 2010-01-24
have you installed your graphics drivers?

if you have nvidia card, install also nvidia-settings package... this lets you modify your graphic settings

---

### Post by halitech on 2010-01-24
what video card do you have? Open a terminal and run
```
lspci
```
and post the info back here

---

### Post by Pth518 on 2010-01-24
im pretty sure i just have a basic chipset :P

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Network controller: RaLink RT2800 802.11n PCI
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


thats what comes up when i type "lspci" in terminal

---

### Post by halitech on 2010-01-24
This is your video card

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

According to a search on the forum, there are lots of posts about it. MAybe this one will help

[http://ubuntuforums.org/showthread.php?t=1362903&highlight=Intel+Corporation+82865G](http://ubuntuforums.org/showthread.php?t=1362903&highlight=Intel+Corporation+82865G)

---

### Post by Pth518 on 2010-01-24
didnt help.. 

i really cant understand why i cant just change res.
why isnt it showing me more than 2 options??

---

### Post by halitech on 2010-01-24
because its not identifying your video card properly so to prevent the system from doing damage to the card or the monitor, it is keeping you to low resolutions. If this is not a laptop you may want to look into getting an Nvidia card which will work better.

---

### Post by Pth518 on 2010-01-24
ok well i dont really want to buy a graphics card cause its not the newest computer out there so im not gonna pay anything towards it really... 

yu know how i would update the drivers on the card?

its possible that theyr outdated and an update might change things

---

### Post by halitech on 2010-01-24
the drivers aren't "on the card" they are software designed to allow the OS (Ubuntu) to talk to the actual hardware and use it. The 2 options I see are trying the beta of 10.04 or dropping back to 8.04 where I believe the intel chips actually worked.

---

### Post by deinerson1 on 2010-04-01
Edit the following file using Accessories --> LXTerminal

[FONT="Courier New"]sudo nano /etc/xdg/lxsession/LXDE/autostart[/FONT]

Add the following line at the end of the file:

[FONT="Courier New"]@xrandr -s 1024x768[/FONT]

Save the file and reboot. This persists the screen resolution between reboots.

---

### Post by Porter321 on 2010-07-23
> **deinerson1 said:**
> Edit the following file using Accessories --> LXTerminal

[FONT=Courier New]sudo nano /etc/xdg/lxsession/LXDE/autostart[/FONT]

Add the following line at the end of the file:

[FONT=Courier New]@xrandr -s 1024x768[/FONT]

Save the file and reboot. This persists the screen resolution between reboots.

Thanks for you information i newly join and your post help me.

---

