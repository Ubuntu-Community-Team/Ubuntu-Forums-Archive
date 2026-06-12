---
title: "No Sound"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by ounvme2 on 2010-01-25
I am brand new Ubuntu user. I just installed Ubuntu 9.10 on my gateway laptop. What do I do to fix this?

---

### Post by themusicalduck on 2010-01-25
Which model laptop exactly? If we know the model, it'll be easier to check what might be causing the problem.

First thing to try is to open a terminal, (Applications > Accessories) and type in ```
alsamixer
``` and check that all levels are turned up.

If that doesn't work, then hit escape to exit alsamixer and type in ```
lspci
``` and post the contents here.

---

### Post by ounvme2 on 2010-01-25
I have a Gateway P-6860FX


lin@lin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800M GTS] (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

---

### Post by ounvme2 on 2010-01-25
tried alsamixer and confirmed all is up.

---

### Post by themusicalduck on 2010-01-25
I did a bit of searching about and it looks like there was a bug with this hardware when Karmic was very new. Since you've only just installed it, have you installed any updates yet? An updated version of Karmic is more likely to work better than a new install.

A quick way to do updates is to first run this command in the terminal ```
sudo apt-get update
``` (you'll need to put your password in too) and then hit alt+f2, type in ```
update-manager
``` and then hit enter. You can install updates from there.

---

### Post by themusicalduck on 2010-01-25
Also forgot to add that you might need to restart after installing the updates.

---

### Post by ounvme2 on 2010-01-25
Ok, I did the update as above. Still don't have sound. Rebooted. Still don't have sound. Also, I have tried the System Testing without any fix, as well.

---

### Post by themusicalduck on 2010-01-25
Ok, this might work for you.

In the terminal type ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this line onto the end of the text file that comes up: ```
options snd-hda-intel probe_mask=1
``` and save it.

Then restart the PC.

---

### Post by gnack on 2010-01-25
Also see this thread:

[http://ubuntuforums.org/showthread.phpt=1346644&highlight=6860FX+sound](http://ubuntuforums.org/showthread.phpt=1346644&highlight=6860FX+sound)

---

### Post by ounvme2 on 2010-01-25
put the line in but it didn't work after reboot. The link didn't take me to a thread.
thx.

---

### Post by mörgæs on 2010-01-25
Here is the thread mentioned above:
[http://ubuntuforums.org/showthread.php?t=1346644](http://ubuntuforums.org/showthread.php?t=1346644)

---

### Post by ounvme2 on 2010-01-25
read thru the thread. tried a few things mentioned there and other google searches. Still no sound. right-clicked on speaker icon, went to preferences and noticed that under hardware tab there is nothing to configure. Is that normal?

---

### Post by mörgæs on 2010-01-27
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by coral66 on 2010-01-27
I installed WUBI yesterday, had the same problem, apparently no sound. Looked in System --> Preferences --> Sound and the Mute box was ticked. Unticked, sound works fine. Hope this helps.

---

