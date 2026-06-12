---
title: "nothing but static"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Mr.Kuchinawa on 2009-03-31
No matter what I set the pcm or master to, theres nothing but static. The noise dissapears if I mute "front"

What to do? I'd like some sound, please.

---

### Post by halitech on 2009-03-31
what kind of hardware?

whats the results of```
lspci
``` and ```
aplay -l
```

---

### Post by Mr.Kuchinawa on 2009-03-31
```
simen@simen-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Network controller: RaLink Unknown device 0781
03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

```

```
simen@simen-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

It's an Asus 1000h with 8.04 + arrays kernel. It worked fine until today, so somebody may have accidentally fiddled with something...

---

### Post by Mr.Kuchinawa on 2009-04-01
Bump

---

### Post by philinux on 2009-04-01
I assume you've checked in sys>prefs>sound. Try the autodetect setting and try the test buttons.

---

### Post by kansasnoob on 2009-04-01
I'd follow the Hardy specific steps here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Assuming you are using Hardy as your sig indicates.

---

### Post by Mr.Kuchinawa on 2009-04-01
Thanks everyone. Disabling "front mic" solved it. Not that I know why..

---

