---
title: "Problem with ubuntu, help needed"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by maverickmunaf on 2009-03-06
Hello guys,

I actually had windows vista installed dell vostro laptop. I wasn't that satisfied with vista, so i tried installing ubuntu as a parallel OS on my laptop. Something has gone wrong with the disk partition, so my vista has been completely removes, thanks as i backed up all my data. I am fine that vista is gone, but the problem here is i can't make my wireless work for me. I guess i am facing the problem with the drivers. Can anyone please tell me how to make my laptop work for me fine with ubuntu on. Is there any chance that i can get my vista back. Please let me know.

Thanks in Advance

Munaf

---

### Post by avtolle on 2009-03-06
We need to know what wireless card your computer has. From the command line (open a terminal by going to Applications>Accessories>Terminal) and input```
lspci
```then paste the results here.

---

### Post by Bladeforger on 2009-03-06
I saw some threads a while back regarding wireless problems and solutions.  Try a search.

Meanwhile, hang in there.  The more you use Ubuntu, the more you'll like it.  There's a learning curve for those of us who have recently migrated from some version of MS Windows, but it's worth the effort--at least I think so.

---

### Post by clive littlewood on 2009-03-06
Hi

When you installed Ubuntu at the partition stage you must have used "guided use entire disc" I'm afraid your vista has gone.    :(

As requested post the info asked above and we will be able help you with your wireless.

Clive

---

### Post by maverickmunaf on 2009-03-06
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Here it goes..........

---

### Post by gtr32 on 2009-03-06
> **maverickmunaf said:**
> 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Maybe this would help:
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

