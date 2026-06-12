---
title: "Not detecting network cards"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by mathfreak123 on 2008-11-04
Hey, I installed Ubuntu onto my system using Wubi. However, the system is unable to detect the network cards (wired and wireless).

What should I do? My network cards are a

-Marvell Yukon 88E8040T PCI-E Fast Ethernet Controller
-Intel(R)PRO/Wireless 3945ABG Network Connection

---

### Post by cariboo on 2008-11-05
Could you paste the output of:

```
sudo lshw -C network
```

You will have to type this in a Applications-->Accessories-->Terminal. Just highlight the output and use the middle mouse button to paste.

Jim

---

### Post by mathfreak123 on 2008-11-05
Here's the output for the file.

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945

---

### Post by mathfreak123 on 2008-11-06
Bumping for help

---

### Post by mathfreak123 on 2008-11-06
bump

---

### Post by cariboo on 2008-11-07
According to your listing the driver for your wirless card is loaded. Can you paste the output of

```
sudo iwconfig
```

Jim

---

### Post by mathfreak123 on 2008-11-07
Output for sudo iwconfig:

lo        no wireless extensions.

---

### Post by mysticofjesus on 2008-11-07
I've got the same problem, and I get the same outputs to those commands, except for the product and vendor fields.

I've got an ASUS Eee 1000H with Ubuntu eee.

---

### Post by cariboo on 2008-11-07
It looks like none of yoour devices are being detected although the correct driver is loaded for your wireless device. Try in a terminal:

```
sudo iwconfig
```

Thats as far as I can go until I can run out to my shop and grab a wireless device.

Jim

---

### Post by mathfreak123 on 2008-11-07
Isn't that the same command that you suggested in the last post, though?

---

### Post by cariboo on 2008-11-08
Lets try a different tack. What is the output of:

```
lspci
```

Because now that I look at the output of:

```
sudo lshw -C network
```

It looks like you wireless card is trying to use a firewire driver

Jim

---

### Post by mathfreak123 on 2008-11-09
Output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by mathfreak123 on 2008-11-16
bump

---

### Post by VanDu on 2008-11-16
Can you try this? [[COLOR="Red"]LINK[/COLOR]]("http://ubuntuforums.org/showthread.php?t=983780")

---

### Post by mathfreak123 on 2008-11-19
Well, I'm still using 8.04. I'm not using 8.10.

---

