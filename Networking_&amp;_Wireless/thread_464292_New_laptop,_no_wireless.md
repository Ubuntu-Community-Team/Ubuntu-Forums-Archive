---
title: "New laptop, no wireless"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by FRuMMaGe on 2007-06-04
I just got my new laptop today and installed Dapper and it woks great!  Only thing is, I cannot get ubuntu to detect the in-built 54g Wireless LAN.

I've tried iwconfig but it just says there are no wireless extentions.

What can i do??

---

### Post by stchman on 2007-06-04
> **FRuMMaGe said:**
> I just got my new laptop today and installed Dapper and it woks great!  Only thing is, I cannot get ubuntu to detect the in-built 54g Wireless LAN.

I've tried iwconfig but it just says there are no wireless extentions.

What can i do??

Install Feisty, it is way better with wireless than the previous Ubuntus.  Feisty supported my wireless out of the box on my laptop.

What type of wireless card do you have?

---

### Post by MajinCline on 2007-06-04
First....need to find out what wireless chipset you have. Once you know that you can do some googling around to find how to install the drivers for it, whether it be ndiswrapper or a kernel module. Manufacturers usually don't tell what hardware is really in a laptop so try typing the command ```
lspci
``` to list all the pci cards installed in your laptop. Post the output here and someone who has the card might be able to help you as I only have experience with broadcom and ralink cards.

---

### Post by FRuMMaGe on 2007-06-04
> **MajinCline said:**
> First....need to find out what wireless chipset you have. Once you know that you can do some googling around to find how to install the drivers for it, whether it be ndiswrapper or a kernel module. Manufacturers usually don't tell what hardware is really in a laptop so try typing the command ```
lspci
``` to list all the pci cards installed in your laptop. Post the output here and someone who has the card might be able to help you as I only have experience with broadcom and ralink cards.

```
frummage@frummage-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:06:04.0 FireWire (IEEE 1394): O2 Micro, Inc.: Unknown device 00f7 (rev 02)
0000:06:04.2 0805: O2 Micro, Inc.: Unknown device 7120 (rev 01)
0000:06:04.3 Mass storage controller: O2 Micro, Inc.: Unknown device 7130 (rev 01)
0000:06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

I assume this line is important:
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

By the way, there is a physical switch on my laptop that you can use to turn the wireless on/off.  However, the light to show if it's on doesnt come on.  I assume this is a driver issue.

---

### Post by FRuMMaGe on 2007-06-04
bump

---

### Post by FRuMMaGe on 2007-06-04
bump?

---

### Post by Syke on 2007-06-04
With that Intel chipset, there's a good chance you have an Intel wireless, and it probably won't work out of the box. You'll have to install some drivers after you figure out exactly what device you have.

As mentioned above, you should try Ubuntu 7.04 Feisty out as the wireless support is much improved.

---

### Post by FRuMMaGe on 2007-06-04
still kind find it...

---

