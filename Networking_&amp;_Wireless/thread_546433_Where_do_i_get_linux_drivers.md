---
title: "Where do i get linux drivers?"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by uposer111 on 2007-09-08
I installed ubuntu 7.04 on my wifes XPS and she has wireless. Where do i get the wireless driver for here wireless adapter? Here are the belkin drivers on their site [http://www.belkin.com/support/article/?lid=en&pid=F5D8053&aid=8343&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D8053&aid=8343&scid=0)

Thanks

Jeff

---

### Post by kevdog on 2007-09-08
Cant you get them from dell???

This probably is in integrated dell mini-pci card 1300, 1350, 1400, or 1450.  Its most likely a Broadcom chipset

lspci -nn
lshw -C network 

These commands would at least reveal the chipset.

---

### Post by uposer111 on 2007-09-08
Excuse me, i might have wrote that wrong, she does not have wireless in her PC, I belkin wireless router downstairs on my computer and she has a small wireless belkin adapter via USB. F5D8053 Driver is the driver i need when i install it in her windows. i will go try those commands now.

Jeff

---

### Post by uposer111 on 2007-09-08
Here is what i got
lspci -nn
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge [8086:27b0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c1] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV380 [Radeon X600 (PCIE)] [1002:5b62]
01:00.1 Display controller [0380]: ATI Technologies Inc RV380 [Radeon X600] [1002:5b72]
03:08.0 Ethernet controller [0200]: Intel Corporation 82801G (ICH7 Family) LAN Controller [8086:27dc] (rev 01)
03:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]


```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:72:bc:92:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:efbfb000-efbfbfff ioport:ccc0-ccff irq:17


```

---

### Post by kevdog on 2007-09-08
Sorry I misunderstood, those commands arent going to do anygood since its a USB device.  Save the windows drivers since you might need them later.  You are going to have to figure out the chipset of the device.  The only way I know how to do this short of breaking open the case and looking at the chip is to google your device. (Belkin model number chipset).

---

### Post by uposer111 on 2007-09-09
I couldnt find my chipset by googling it, so if you have better luck doing that here is my wireless adaptors info.

Belkin N wireless Adaptor Model:f5d8053

Here is a pic of the chip, hope this helps.

[IMG]http://i74.photobucket.com/albums/i274/levidicus/046.jpg[/IMG]

Thanks for your help.
Jeff

---

### Post by kevdog on 2007-09-09
Well its definitely an Ra chipset.

That pic was pretty cool

The usb ra chipsets either use the rt73 driver or rt2570 driver -- Id bet on rt73.  

Here a link to the thread you want:

Good luck with the glue!

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Reference:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

---

### Post by CapnGimp on 2007-09-19
got a friend to try 4 distros of linux. he has a belkin usb FSD8053 and router. I had him buy it recently when I loaded windows on his computer. NATURALLY, the dang thing has no support in linux. No internet, won't waste time with linux.  same old story.

---

### Post by molicule on 2007-11-01
> **kevdog said:**
> Well its definitely an Ra chipset.

That pic was pretty cool

The usb ra chipsets either use the rt73 driver or rt2570 driver -- Id bet on rt73.  

Here a link to the thread you want:

Good luck with the glue!

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Reference:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

I have the same adapter/w chip-set and i installed both drivers and still cant get online...i believe its a conspiracy!

i also did ndiswrapper and still cant get online

---

### Post by andyeire on 2007-11-20
I have this card (usb) too;

I got it working using ndiswrapper and the belkin drivers.  The belkin drivers come as an exe, contain an MSI that holds the inf and sys file required for ndiswrapper.

The files are rt2870.inf rt2870.sys

Interestingly, it doesn't see my belkin AP (both bought as a bundle) but sees my wireless G and other b/g AP's.  I haven't time to check out switching the belkin AP to b/g only mode, so maybe a problem with n mode support.

---

### Post by intelligentfool on 2007-11-20
> **CapnGimp said:**
> got a friend to try 4 distros of linux. he has a belkin usb FSD8053 and router. I had him buy it recently when I loaded windows on his computer. NATURALLY, the dang thing has no support in linux. No internet, won't waste time with linux.  same old story.

you get what you pay for. oh wait, thats right, you didnt pay anything. 

you could always write the drivers yourself and help others in your situation.

---

