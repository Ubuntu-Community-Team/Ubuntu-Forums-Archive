---
title: "Graphics Card Still in Use?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by EnigmaticCoder on 2010-10-26
My folks' computer is running a bit slow. I think it's the graphics card because I get an error message when the screen saver runs, "Xlib: extension glx missing on display(0:0)" And when I run nvidia-settings, a message box says, "You do not appear to be using  nVidia X driver. Please edit your x configuration file." So I ran nvidia-xconfig and restarted the computer.

As the computer restarted, an error message came up that said I needed to run in low graphics mode. I tried having xubuntu automatically detect settings and create a new xconfig, but that didn't work. I had to restore the xconfig file to the default settings to avoid the low graphics mode error.

One more thing to note: I have the the nVidia driver activated, but I'm still receiving these error messages.

---

### Post by stephanvaningen on 2010-10-26
[LIST]
[*]Which Xubuntu are you running? (10.10, 10.04, 10.04.1, ...)
[*]What's the output of lspci?
[/LIST]

---

### Post by EnigmaticCoder on 2010-10-26
Version
Ubuntu 10.04.1 LTS

$ lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
01:05.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by stephanvaningen on 2010-10-26
Is nvidia-common or other nvidia* packages installed (to check via Synaptic Package Manager)?

---

### Post by EnigmaticCoder on 2010-10-26
Yes nvidia-common, nvidia-173 and more.

---

### Post by EnigmaticCoder on 2010-10-26
Can anyone propose a solution?

---

### Post by stephanvaningen on 2010-10-27
Sorry, I do not see a solution right now... Googling doesn't come up with something useful either it seems.

> **EnigmaticCoder said:**
> Can anyone propose a solution?

---

### Post by ofb on 2010-10-27
I've got that video card on a 10.4 box and have no problems. The Hardware Drivers panel shows I'm using 173, and there's no trouble running nvidia-settings.

Um... have you tried complete removal of the nvidia driver in Synaptic, then let the Hardware Drivers utility detect the card again?

What I'm thinking is perhaps you've got something misconfigured at some point. So the idea is to flush all the settings and start fresh.

But that would still be rather odd and unlikely. Has this machine always had this trouble? Perhaps the card itself has a capacitor that's going bad?

---

### Post by kg4cna on 2010-10-27
Try a different version of the Nvidia driver.. maybe back down one or two.

A~

---

### Post by EnigmaticCoder on 2010-10-27
> **kg4cna said:**
> Try a different version of the Nvidia driver.. maybe back down one or two.

A~

That solved the screen saver and nvidia settings errors. And the computer seems to be moving faster (although I'm not sure it's as fast as it once was). Marking thread as solved.

---

