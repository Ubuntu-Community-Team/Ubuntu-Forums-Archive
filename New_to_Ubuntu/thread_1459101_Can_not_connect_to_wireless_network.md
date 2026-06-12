---
title: "Can not connect to wireless network"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by lazbuddie on 2010-04-21
I am running Xubuntu 910 on several IBM think pads, after update auto wireless connect stopped and now I can not connect. Wired connection works fine. 
vpn connections highlight on when I click computers that have an x through them on panel, do I have a setting wrong. Is there a place to look for available net
works

---

### Post by P4man on 2010-04-21
if you right click the network manager, is wireless turned on?
Whats the output of ```
lspci
``` and ```
lsusb
```?

---

### Post by lazbuddie on 2010-04-21
Thanks for answering my post, is this the info you need? I am pretty green , but I am running xbuntu on 70 ibm t302 at our school for the students and have another 70 in the works.
 
1spci: command not found
lisd@lisd57:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
lisd@lisd57:~$ 

1susb: command not found
lisd@lisd57:~$

---

### Post by Homicide on 2010-04-21
lowercase L, not a 1.

---

### Post by lazbuddie on 2010-04-21
> **Homicide said:**
> lowercase L, not a 1.

1susb: command not found
lisd@lisd57:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)


lisd@lisd57:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lisd@lisd57:~$

---

### Post by HarrisonNapper on 2010-04-21
There is probably a button somewhere on the computer to enable/disable wireless. This may be a combination like "Fn+F7" or it may be a little wireless icon above your keyboard. Press it.

Cheers.

---

### Post by lazbuddie on 2010-04-21
No Manuel switch, I tried fn - f7, also tried fn and f4, f3 and f12. I think my problem is related to an update that changed something, because right after update it stopped, works fine in wired

---

### Post by P4man on 2010-04-21
can you reboot and run those commands again before doing anything else? A few hours ago someone had a similar issue caused by a bug in the kill switch that would kill the wifi, but not reactivate it. Only solution was rebooting. When killed his wifi card didnt show up in lspci and lsusb either, but it did after a fresh boot, so please try that first.

---

### Post by anewguy on 2010-04-21
If the above doesn't work, there is another possibility:

IF the update was a new kernel, and IF you had to do make and make install (in other words, build from source) the driver before, you'll probably need to reinstall the driver again.

IF the driver required you to do a modprobe in it's intial installation, you *may* need to do that again.


Do you remember if it just worked "out of the box" before or if you had to install a driver?

If I missed any of this in your thread, sorry.

Dave ;)

---

### Post by lazbuddie on 2010-04-21
> **anewguy said:**
> If the above doesn't work, there is another possibility:

IF the update was a new kernel, and IF you had to do make and make install (in other words, build from source) the driver before, you'll probably need to reinstall the driver again.

IF the driver required you to do a modprobe in it's intial installation, you *may* need to do that again.


Do you remember if it just worked "out of the box" before or if you had to install a driver?

If I missed any of this in your thread, sorry.

Dave ;)

Yes on ordinal install it worked without downloading drivers. Picked up wireless networks. I am running xbuntu 9-10 in a small school in remote  West Texas on over 60 identical T30 IBM lap tops sense Jan 10. I am having multiple computers loose their ability to connect wirelessly. I think it happens after computers are updated the kids tell me.  Thanks

---

### Post by lazbuddie on 2010-04-21
> **P4man said:**
> can you reboot and run those commands again before doing anything else? A few hours ago someone had a similar issue caused by a bug in the kill switch that would kill the wifi, but not reactivate it. Only solution was rebooting. When killed his wifi card didnt show up in lspci and lsusb either, but it did after a fresh boot, so please try that first.

I rebooted and here are the results, this is happening on multiple units Thanks Walt
 
lisd@lisd57:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
lisd@lisd57:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
lisd@lisd57:~$

---

### Post by P4man on 2010-04-22
Hmm.. have you tried booting an older kernel in grub menu?

---

### Post by anewguy on 2010-04-22
> **P4man said:**
> Hmm.. have you tried booting an older kernel in grub menu?

You beat me to my next suggestion!!  ;);)

Dave ;)

---

