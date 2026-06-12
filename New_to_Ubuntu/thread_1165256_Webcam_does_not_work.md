---
title: "Webcam does not work"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by mosquetero on 2009-05-20
Hi everyone,

I can't use my webcam in Skype because it just displays some kind of green interferences instead of my face! The strange thing is that it used to work correctly when I was using version 8.04 of Ubuntu, but with the 9.04, it does not work. I must add that I had to do nothing in 8.04 for it to work. Can anyone help please? The webcam is called BULLSEYE from the enterprise NGS technology.

---

### Post by albinootje on 2009-05-20
> **mosquetero said:**
>  The webcam is called BULLSEYE from the enterprise NGS technology.

Please post the output of :
```

lspci
lsusb

```

---

### Post by mosquetero on 2009-05-20
lspci gives me this:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

lsusb:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
Bus 005 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thanks

---

### Post by albinootje on 2009-05-20
> **mosquetero said:**
> 
Bus 005 Device 003: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam

Thanks.
See here a bug report + possibly useful comments :
[https://bugs.launchpad.net/ubuntu/+bug/292086?comments=all](https://bugs.launchpad.net/ubuntu/+bug/292086?comments=all)

---

### Post by mosquetero on 2009-05-20
Thank you but, I have never solved any problem using this kind of Ubuntu bugs web. It says that the solution should be:

Make webcams with USB ID 0ac8:303b, such as the Z-Star Microelectronics

Corp. ZC0303 be handled by gspca not the zc0301 driver. The latter does

not seem to handle them anymore in Intrepid.

Do you know how can I do that??

THanks

---

