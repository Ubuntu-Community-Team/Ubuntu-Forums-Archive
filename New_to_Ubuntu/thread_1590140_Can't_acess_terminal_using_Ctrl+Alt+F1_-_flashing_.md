---
title: "Can't acess terminal using Ctrl+Alt+F1 - flashing screen"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by jalbertobr on 2010-10-07
First of all, hi. I'm Joao from Brazil.

Well, I can't really say I'm a total beginner. I used to mess around with Slackware, but that was 10 years ago. I don't remember most things about Linux, but I'm trying to have fun again, this time with Ubuntu.

My question is simple: I miss the good old full screen terminal. Slackware was all about it, and I like to have it ready even knowing that I will seldom use it, as Ubuntu is totally different from what I was used to regarding Linux: my computer was ready to go just after installation.

Trouble is, when I press CTRL+ALT+F1, my screen start flashing. Or just turn white. I can press CTRL+ALT+F7 and get back to GNOME, but I can't have my full screen old school terminal.

Back in the day, issues like this one were usually related to the video configuration. But maybe someone knows a quick fix for that.

My laptop is a generic one, but it has a VIA UniChrome video chipset. It works flawlessly on GNOME.

Some information I got using Ubuntu tools (Checkbox?)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] [1106:3344] (rev 01) 	Subsystem: FIRST INTERNATIONAL Computer Inc Device [1509:4330] 	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 	Latency: 64 (500ns min) 	Interrupt: pin A routed to IRQ 16 	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=64M] 	Region 1: Memory at d1000000 (32-bit, non-prefetchable) [size=16M] 	Capabilities: <access denied> 

Thanks!

---

### Post by TeoBigusGeekus on 2010-10-07
Not actually a solution, but why don't you launch a full screen terminal in gnome?

---

### Post by t0p on 2010-10-07
> **TeoBigusGeekus said:**
> Not actually a solution, but why don't you launch a full screen terminal in gnome?

You're right, it isn't really a solution.  It's good to have the consoles available in case X freezes.

I don't have a solution either...

---

### Post by TeoBigusGeekus on 2010-10-07
Perhaps the suggestions in the following links will help you.
[https://answers.launchpad.net/ubuntu/+question/15560]("https://answers.launchpad.net/ubuntu/+question/15560")
[http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/]("http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/")
[http://ww.ubuntuforums.org/showthread.php?t=1471825]("http://ww.ubuntuforums.org/showthread.php?t=1471825")

---

### Post by jalbertobr on 2010-10-07
Hey guys.

The Fullscreen Xterm option didn't cut it, because of my Slackware roots. I don't even think I'll use, but it helps me to feel home after so many years without Linux.

I didn't read the links provided because I found a solution on google before, thanks anyway!

By the way, here's what I did for anyone interested

1) Open terminal
2) type:

sudo gedit /etc/default/grub

3) you'll find the following line:

#GRUB_GFXMODE=640x480

remove the # before GRUB and put  the screen resolution that you want. I used

GRUB_GFXMODE=1440x900x32

the x32 after 1440x900 is the color option. You can try x16 if your card is old or whatever.

4) just after that one, insert this one from scratch:

GRUB_GFXPAYLOAD_LINUX=keep

5) save changes, leave gedit. Now type:

sudo update-grub

6) Reboot. Profit.

That's it. Thanks!

---

