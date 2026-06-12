---
title: "Help with updating video/graphics drivers"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by robro on 2011-02-12
Hello everyone,
Well i have been noticing some games i have played have low fps/lag,
and well... i have never had any luck finding out how to update my video/graphics driver, :| so i have some questions:
How to update my graphics driver?
How to see what graphics driver i have installed now?
If i do update my drivers, will it be free?

Thanks for your help :)

---

### Post by uRock on 2011-02-12
To find what drivers you have installed go in your menus to System> Administration> Additional Drivers or if you are using Ubuntu 10.04 or older, then System> Administration> Hardware Drivers.

---

### Post by robro on 2011-02-12
the only thing listed there is my wireless driver :|

---

### Post by uRock on 2011-02-12
What GPU/ onboard graphics does your system have?

---

### Post by robro on 2011-02-12
How do i find out?

---

### Post by uRock on 2011-02-12
Open a terminal (Applications> Accessories> Terminal) then enter ```
lspci
``` Then Copy and paste the response here using code tags. (Highlight the text, then click the # button in the ribbon.)

---

### Post by robro on 2011-02-12
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

```

---

### Post by uRock on 2011-02-12
I did a little searching and couldn't find any Linux drivers out there for your graphics.

---

### Post by robro on 2011-02-12
hmm... is there any way to unistall and install new drivers or something like that?

---

### Post by uRock on 2011-02-12
There are no drivers to remove and reinstall, that I know of.

---

### Post by robro on 2011-02-12
:(

---

