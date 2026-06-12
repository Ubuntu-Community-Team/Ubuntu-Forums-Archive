---
title: "Wireless works on 64-bit, but not on 32-bit."
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Nicolas.Perrault on 2010-01-10
Hello everyone,

I've installed Ubuntu 9.10 64-bit on my main laptop about a month ago, and everything is just peachy.

I've installed Ubuntu 9.10 32-bit on my second laptop just today. I can't manage to access the internet via wireless, however. I've tried networkmanager, but it does not find anything. It acts as is I was on the moon, and no wireless connection is available anywhere near.

Any help?

---

### Post by Nicolas.Perrault on 2010-01-10
Oh the second computer has a Windows partition installed too. Wireless internet works on Windows, how humiliating...

Thanks!

---

### Post by halitech on 2010-01-10
what kind of laptop are dealing with thats not working? can you open a terminal and post the output of
```
lspci
``` and ```
iwconfig
```

---

### Post by Nicolas.Perrault on 2010-01-10
The laptop that's not working is a Dell Vostro 1400.
No wireless connexion are detected when "iwconfig" is typed.
Loads of random text appear when I type "lspci" is typed.

Any other tricks I can attempt?

Thanks!

Nik

---

### Post by Excedio on 2010-01-10
> **Nicolas.Perrault said:**
> The laptop that's not working is a Dell Vostro 1400.
No wireless connexion are detected when "iwconfig" is typed.
Loads of random text appear when I type "lspci" is typed.
 
Any other tricks I can attempt?
 
Thanks!
 
Nik
 
Can you please copy and paste the output from the lspci? We will need to see it in order to better help you.

---

### Post by LuisGMarine on 2010-01-10
Try hooking up the laptop to an Ethernet cable so that you can post the outputs of those commands.  They will help users further help diagnose and hopefully fix your problem.

---

### Post by halitech on 2010-01-10
> **Nicolas.Perrault said:**
> The laptop that's not working is a Dell Vostro 1400.
No wireless connexion are detected when "iwconfig" is typed.
Loads of random text appear when I type "lspci" is typed.

Any other tricks I can attempt?

Thanks!

Nik

that "random text" may seem random to you but unless you have something screwy with your install, it should help us get you going. If you can't hook up to a wired connection at the moment, you can run this
```
lspci >> ~/Desktop/lspci.txt
```
that will create a text file you can copy to a thumb drive then open and paste from the working connection.

---

### Post by albert s on 2010-01-10
just a thought, but could it be restricted hardware drivers?
having just re-installed / to my friends DELL laptop and having no wireless I got it going again by going to 
SYSTEM>ADMINISTRATION>HARDWARE DRIVERS
it was a B43 chip.

---

### Post by halitech on 2010-01-10
> **albert s said:**
> just a thought, but could it be restricted hardware drivers?
having just re-installed / to my friends DELL laptop and having no wireless I got it going again by going to 
SYSTEM>ADMINISTRATION>HARDWARE DRIVERS
it was a B43 chip.

I just looked up the specs and it has 2 possibilities on the wireless card, an intel or a dell branded card. Even if something is listed in the hardware drivers, will need a wired connection to get them downloaded and working.

---

### Post by albert s on 2010-01-10
> **halitech said:**
> I just looked up the specs and it has 2 possibilities on the wireless card, an intel or a dell branded card. Even if something is listed in the hardware drivers, will need a wired connection to get them downloaded and working.


of course,
I dont mean to step on any of you experienced guys toes, just sometimes its actually the simple basic things that get overlooked.
Im new to all this so just trying to help out with my own n00b experiences of trying to get things to work.

---

### Post by halitech on 2010-01-10
> **albert s said:**
> of course,
I dont mean to step on any of you experienced guys toes, just sometimes its actually the simple basic things that get overlooked.
Im new to all this so just trying to help out with my own n00b experiences of trying to get things to work.

I agree that sometimes we get going in the hard direction instead of taking the easy way but starting at the basics is usually the best idea. Thats why personally I'm looking for the terminal info and then going from there.

---

### Post by sandyd on 2010-01-10
alright.
connect to the internet using ethernet, then 
[[click here]]("apt:/bcmwl-kernel-source,bcmwl-modaliases")

to install the drivers.

or just use the hardware drivers thingy. both do the same thing...

---

### Post by Nicolas.Perrault on 2010-01-10
WOW, I left my computer for a few hours and I already have so many replies, thanks guys! 

Allright so I'm on my second computer right now, connected via ethernet cable. Here's the text that appears when I type ''lspci'' on the terminal:




00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)



I would also like to mention that Ubuntu has given me a warning about a: ''serious kernel problem''.

Thanks so much for your help ;)

---

### Post by sandyd on 2010-01-10
```

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```yep. thats the wifi card.
just click the link in post #12 or use hardware drivers and a miracle should instantly happen. (might require you to restart in some cases though)

---

### Post by sandyd on 2010-01-10
> **Nicolas.Perrault said:**
> <snip>
I would also like to mention that Ubuntu has given me a warning about a: ''serious kernel problem''.

Thanks so much for your help ;)
that doesn't sound good...

---

### Post by halitech on 2010-01-10
ok, you do have a broadcom wireless chip 

[color="red"]0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)[/color]

so try checking hardware drivers first and see if it is listed there. If it is, just click on it to activate, let it download the drivers, reboot and disconnect the wired connection and you *should* be online with the wireless.

edit: you may want to do all the updates while on the wired connection before installing the wireless, it might take care of the kernel issue (I hope)

---

### Post by Nicolas.Perrault on 2010-01-10
@carlee:

When I click on your link it says: 

Could not find package 'bcmwl-kernel-source'.


Once closed, an other message appears:

Package 'bcmwl-modaliases' is already installed.


As for the drivers, it says:

No proprietary drivers are in use on this system.


Is all of this bad? I'll reinstall if necessary, I'm all ears... Thanks for caring :D

---

### Post by sandyd on 2010-01-10
> **Nicolas.Perrault said:**
> @carlee:

When I click on your link it says: 

Could not find package 'bcmwl-kernel-source'.


Once closed, an other message appears:

Package 'bcmwl-modaliases' is already installed.


As for the drivers, it says:

No proprietary drivers are in use on this system.


Is all of this bad? I'll reinstall if necessary, I'm all ears... Thanks for caring :D
hmm...
what happens if you search in synaptic for "bcmwl"?
there should be two packages starting with that...
both of them should be installed.
im thinking my slinky apt-urls are suffering from something....

EDIT:
It may be the kernel problem you mentioned that is causing these problems. This is because the Broadcom STA (wl) drivers are compiled into the kernel.
what kernel are you using?
type ```
uname -a
```

---

### Post by Nicolas.Perrault on 2010-01-11
Oh Yeah!!! Awesome! It works! I'm writing this with my wireless connection on my second computer!!! Thanks everyone you're all awesome!

By the way, the thing that worked was to follow carlee's link, plus to use Synaptic and update everything I could. Then I restarted my computer and voila!:D:D:D

OH, I'm so happy! Ubuntu for the win!:P:):D;)

Thanks a lot everyone!

Nick

---

### Post by Nicolas.Perrault on 2010-03-27
Hi, it's me again with a replica of the problem I had two and a half months ago. The computer you helped me with works just great. This is another computer though, still a Dell. A Dell INSPIRON 6000 to be exact.

When running "lscpi" I get:

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
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


Any link to a driver I could install?

---

### Post by sandyd on 2010-03-27
> **Nicolas.Perrault said:**
> Hi, it's me again with a replica of the problem I had two and a half months ago. The computer you helped me with works just great. This is another computer though, still a Dell. A Dell INSPIRON 6000 to be exact.

When running "lscpi" I get:

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
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


Any link to a driver I could install?
[http://ubuntuforums.org/showthread.php?t=803986](http://ubuntuforums.org/showthread.php?t=803986)

---

### Post by Nicolas.Perrault on 2010-03-27
Once again, thanks so much! It worked!

---

### Post by Nicolas.Perrault on 2010-04-17
I'd like to install a wireless driver on debian on my Sony Vaio VGN-390J. Typing "lspci" gives me:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:02.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:02.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:02.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)


Which Driver should I use, and where can I get it from? Thank you!

(By the way, where do you get these links from)

---

### Post by cjazz on 2010-04-18
> **Nicolas.Perrault said:**
> Which Driver should I use, and where can I get it from? Thank you!

You might try [this link.]("http://ubuntuforums.org/archive/index.php/t-1017451.html")


> (By the way, where do you get these links from)

Thanks for asking. I did a Google search on "Intel 5100 wireless Ubuntu."

---

