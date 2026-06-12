---
title: "Flash player no sound"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Desktop_n00b on 2009-09-14
Ok so i looked up forums for adobe flash no sound and tried installing and reinstalling then I tried getting a different flash player and I have tried reinstall ubuntu-restricted-extras, and updating everything but still no sound on newgrounds youtube etc.

any ideas?

---

### Post by LowSky on 2009-09-14
reboot the pc

---

### Post by NoaHall on 2009-09-14
Apparently it can be fixed by changing your sound control - alsa, pulse audio etc. - but i don't know , as I never came across this problem on my machines.

---

### Post by Desktop_n00b on 2009-09-14
I've rebooted plenty of times, its been like this for 2 weeks. I tried all the sound settings too and no luck. Everything works but flash, and i've installed, reinstalled, and so on

---

### Post by soldier4jesus on 2009-09-14
I had a problem with my sound being lower in Ubuntu than what it was in Windows.  I have one of the multimedia keyboards and kept hitting the volume on it, but it was wide open.  I would then have to turn my speakers up pretty loud to be able to hear it good.  I found this on the forums that helped me to correct my sound problem.  You will need to open up a terminal and type in:

gnome-volume-control

This will open up your volume settings.  On mine, the speakers that were labeled as "front" were not all the way up.  I slid the sliders up on them and it fixed my problem.  I hope this helps.

God Bless!!
Wes

---

### Post by Desktop_n00b on 2009-09-14
ok I'll go look at that, and 1 more thing I just noticed my video games have no sound either. So music plays fine, system sounds fine, movies fine, Games no sound, flash no sound.

---

### Post by Desktop_n00b on 2009-09-14
nope still nothing. didn't work

---

### Post by Desktop_n00b on 2009-09-14
ok and now I did something that made all my sound go away on my entire computer. GREAT huh?

---

### Post by LowSky on 2009-09-14
please give us the outputs of this command

```
lspci
```

---

### Post by soldier4jesus on 2009-09-14
There was another post in the forums where someone was having trouble with sound on videos.  Here's the link to that:

[http://ubuntuforums.org/showthread.php?t=1265720&highlight=Flash+player+sound](http://ubuntuforums.org/showthread.php?t=1265720&highlight=Flash+player+sound)

He seemed to be able to get his to start working by following the instructions from this link:

[http://ubuntuforums.org/showthread.php?t=1254328&highlight=flash](http://ubuntuforums.org/showthread.php?t=1254328&highlight=flash)

I don't know if this will help or not. 


God Bless!!
Wes

---

### Post by Desktop_n00b on 2009-09-15
Here is the info you wanted

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:00.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 12)
03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

---

