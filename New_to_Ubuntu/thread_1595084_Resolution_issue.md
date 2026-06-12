---
title: "Resolution issue"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by kjps86 on 2010-10-12
Hello,

I am completely new to Linux and Ubuntu, so please excuse me if I ask for hefty explanations and so on.

Here's my problem: I have an older desktop unit (circa 2004) that originally came with Windows XP and a 4:3 monitor.  Around 2005 the original monitor gave out and was replaced by a 16x9 monitor.  The CPU did not support widescreen displays, but as I was a poor student at the time I just dealt with it and ignored the screen stretching.

This week I decided to install Ubuntu on the computer.  It went great, and everything works except for the resolution is capped at 800x600.  I've been reading around the forums about editing the xorg.conf file by entering sudo nano /etc/X11/xorg.confbut whenever I open the file it is completely blank.  Am I supposed to fill the file myself?  If so is there a syntax guide I should follow, or am I going about this in a completely wrong manner?

My graphics card is an integrated VIA technologies card.

Thanks

---

### Post by Quackers on 2010-10-12
Welcome to ubuntuforums :-)
Have you tried System > Admin > Hardware Drivers? Is anything listed there for your graphics? I'm not sure if VIA graphics are well supported but I have seen other threads about them. Maybe you could try the Search feature near the top of the forum using VIA as a keyword. Good luck.

---

### Post by sandyd on 2010-10-12
> **kjps86 said:**
> Hello,

I am completely new to Linux and Ubuntu, so please excuse me if I ask for hefty explanations and so on.

Here's my problem: I have an older desktop unit (circa 2004) that originally came with Windows XP and a 4:3 monitor.  Around 2005 the original monitor gave out and was replaced by a 16x9 monitor.  The CPU did not support widescreen displays, but as I was a poor student at the time I just dealt with it and ignored the screen stretching.

This week I decided to install Ubuntu on the computer.  It went great, and everything works except for the resolution is capped at 800x600.  I've been reading around the forums about editing the xorg.conf file by entering sudo nano /etc/X11/xorg.confbut whenever I open the file it is completely blank.  Am I supposed to fill the file myself?  If so is there a syntax guide I should follow, or am I going about this in a completely wrong manner?

My graphics card is an integrated VIA technologies card.

Thanks
post output of
```

lspci
```I think youve got one of those openchrome card thingies, but I better check for sure. could also be chrome9, which there IS a propreity driver for.
p.s. no offence, but VIA cards kinda really suck.(sorry.... had to say that...)

---

### Post by kjps86 on 2010-10-12
Here is the requested output:

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

Given the situation I now find myself in, I'd have to agree with you that the card sucks.  Frankly, when I got this computer it was pretty low-end, but all I really want to do with it now is browse the web, watch some videos, and play some old DOS and SCUMM games.

> **sandyd said:**
> post output of
```

lspci
```I think youve got one of those openchrome card thingies, but I better check for sure. could also be chrome9, which there IS a propreity driver for.
p.s. no offence, but VIA cards kinda really suck.(sorry.... had to say that...)

---

### Post by sandyd on 2010-10-12
> **kjps86 said:**
> Here is the requested output:

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

Given the situation I now find myself in, I'd have to agree with you that the card sucks.  Frankly, when I got this computer it was pretty low-end, but all I really want to do with it now is browse the web, watch some videos, and play some old DOS and SCUMM games.
yeah... your using openchrome.

press ctrl + alt + f1, and run this
```

sudo killall gdm
sudo X -configure

```there will then be a message about where xorg generated the file.
so run
```

sudo mv /path/in/message /etc/X11/xorg.conf
sudo shutdown 0 -r
```then for the resolution, use the "login not centered" portion of this -> [https://help.ubuntu.com/community/OpenChrome#Ubuntu%208.10]("https://help.ubuntu.com/community/OpenChrome#Ubuntu%208.10")
you should specify your own resolution.

good luck ;)

oh, and theirs a propreity driver too, but sadly, it doesn't support your card [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by kjps86 on 2010-10-12
When I enter the "sudo killall gd" command it gives the response "gd: no process found" whether I enter it in a terminal window or via the ctrl+alt+f1 method.  I'm starting to think this may require me to spring for a new video card, or just scrap the project altogether.

> **sandyd said:**
> yeah... your using openchrome.

press ctrl + alt + f1, and run this
```

sudo killall gd,
sudo X -configure

```there will then be a message about where xorg generated the file.
so run
```

sudo mv /path/in/message /etc/X11/xorg.conf
sudo shutdown 0 -r
```then for the resolution, use the "login not centered" portion of this -> [https://help.ubuntu.com/community/OpenChrome#Ubuntu%208.10](https://help.ubuntu.com/community/OpenChrome#Ubuntu%208.10)
you should specify your own resolution.

good luck ;)

oh, and theirs a propreity driver too, but sadly, it doesn't support your card [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by sandyd on 2010-10-12
> **kjps86 said:**
> When I enter the "sudo killall gd" command it gives the response "gd: no process found" whether I enter it in a terminal window or via the ctrl+alt+f1 method.  I'm starting to think this may require me to spring for a new video card, or just scrap the project altogether.
oops.
my bad
super typo
fixed.

---

### Post by ft-Orchard on 2010-10-13
Just my thought: 
[http://wiki.archlinux.org/index.php/Xorg#Monitor_settings](http://wiki.archlinux.org/index.php/Xorg#Monitor_settings)

But I guess you already tried that.

---

### Post by kjps86 on 2010-10-13
Thanks for all the help everyone, the problem isn't fixed yet but hopefully if there is a solution I am closer to it not.

I had not seen that link yet.  Simple question, when I see "etc" in a command line, is that there to prompt me to insert my own path to the file myself, or should I leave that alone?

> **ft-Orchard said:**
> Just my thought: 
[http://wiki.archlinux.org/index.php/Xorg#Monitor_settings](http://wiki.archlinux.org/index.php/Xorg#Monitor_settings)

But I guess you already tried that.

---

