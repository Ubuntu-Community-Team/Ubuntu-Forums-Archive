---
title: "Bcmwl-kernal-source problems in Lucid"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by hawaiian1der on 2010-04-29
In Karmic and previous versions of Ubuntu I had to install a package in order for my wireless card to work. I'm not sure what the name of it was in previous versions, but the of the two packages, the bcmwl-kernal-source and the bcmwl-modaliases, the kernal source will not install properly. The error says:

```
E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 6

```

I have no idea what that means. Does anyone know the answer that will fix this issue?

---

### Post by cariboo on 2010-04-30
How are you trying to install the package? My Broadcom wifi needs the wl driver, I just went to System->Administration->Hardware Drivers, and selected the driver I needed and let it install.

---

### Post by hawaiian1der on 2010-04-30
I'm installing t from the package manager. It says that the wireless is enabled but there are no networks to connect to, which is impossible because I'm right next to another laptop that has windoze on it and it is connected.

---

### Post by hawaiian1der on 2010-04-30
I don't know if this will help but here:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
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
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by Megaptera on 2010-04-30
Hi,
The fix below worked for me on my Dell Inspiron laptop 1545 with Ubuntu 9.10 and 10.04 (and derivatives). Although it talks about mini I gave it a go & it worked!
Don't forget to re-boot after following the instructions.

Hope this works for you too!

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by hawaiian1der on 2010-04-30
That did not work. I'm right back at the place I was already at. No networks are popping up when I click the network manager icon.

---

### Post by hawaiian1der on 2010-04-30
Does anyone know how to fix this problem?

---

