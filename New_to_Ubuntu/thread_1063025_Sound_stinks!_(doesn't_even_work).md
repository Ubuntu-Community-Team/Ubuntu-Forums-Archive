---
title: "Sound stinks! (doesn't even work)"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Mitch9654 on 2009-02-07
My sound isn't working
This is my third reinstallation of Ubuntu
The second installation had sound for a little bit
Triple booting with windows XP and Windows 7 beta
Sound works on those
Already reconfigured the alsamixer
Still doesn't work
Please help
Thanks

Mitch9654

---

### Post by bailbath on 2009-02-07
Well you could tell us your hardware!
:p
Ian

---

### Post by diablo75 on 2009-02-07
> **Mitch9654 said:**
> My sound isn't working
This is my third reinstallation of Ubuntu
The second installation had sound for a little bit
Triple booting with windows XP and Windows 7 beta
Sound works on those
Already reconfigured the alsamixer
Still doesn't work
Please help
Thanks

Mitch9654

Please click Applications>Accessories>Terminal and type:

```
lspci
```

Followed by the enter key.  Then copy and paste the output text back here.

---

### Post by Mitch9654 on 2009-02-07
How can I find out my hardware?
(Not sure if ubuntu recognizes it!!!)

---

### Post by Mitch9654 on 2009-02-07
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
02:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
 


happy!!!?!

---

### Post by Mitch9654 on 2009-02-07
when I go into system/preferences sound, and I test the little testers, the only things that work are ES1371 DAC2/ADC and ES1371 DAC1.

...ya...

---

### Post by diablo75 on 2009-02-07
Here's what I'd do if I were you:

Double-click on the volume icon in the upper panel (looks like a speaker, similar to the speaker icon in Windows).

A volume control panel will appear.  Click on the Preferences button at the bottom.

A list of input and output sources will appear, some being checked off, others not.  Check them all off and click ok.

Play some music in the background and while playing with your volume controls, turning up anything that might potentially produce sound, e.g. "Front" and "Front PCM" and "Surround" and "Surround PCM" and "Center" and so on.

---

### Post by Mitch9654 on 2009-02-07
the drum sounds when I start up, and it.. Works!!!

---

### Post by bailbath on 2009-02-08
Thats ok

---

### Post by Mitch9654 on 2009-11-17
upgraded to ubuntu 9.1, and now it doesn't reconize any sound cards...

---

