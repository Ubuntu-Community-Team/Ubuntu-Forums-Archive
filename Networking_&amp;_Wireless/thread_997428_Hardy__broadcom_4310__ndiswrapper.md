---
title: "Hardy : broadcom 4310 : ndiswrapper"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by manij on 2008-11-29
I set up my BC4310 (Dell vostro) with ndiswrapper in hardy. It works well with my linksys wrt 54g. Hoever it has trouble conectin got other access points.

Is there anyway to fix this. It sees the other router but will not connect 

ALso is there a way to have a status bar? with signal strength and connection status?

Thanks

---

### Post by night_fox on 2008-11-29
You could update your kernel then try and install the wireless driver that comes with intrepid. Failing that you could use B43Fwcutter. I had the same problem when I was using ndiswrapper.

---

### Post by manij on 2008-11-29
B43Fwcutter :how do I do this? Is this using the restricted driver?

How do disable ndiswrapper? thanks

---

### Post by night_fox on 2008-11-29
to get rid of ndiswrapper add 'ndiswrapper' to the bottom of /etc/modprobe.d/blacklist

There is a guide at:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
but it might not work. if it doesn't then uninstall it and remove the line from /etc/modprobe.d/blacklist.

You might be better off upgrading to intrepid or getting the driver from intrepid.

---

### Post by Ayuthia on 2008-11-29
The b43 driver does not work with the 4310 card.  You should go ahead and update your computer so that you can access the wl driver for your card.  It should be found under System->Administration->Hardware Drivers called Broadcom STA.  Once it is installed, you can test it by doing the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```
If you are able to connect, you will then need to blacklist ndiswrapper and remove it from /etc/modules.

---

### Post by manij on 2008-11-30
my lspci says it is a BC4312. see below. Does it make a difference?

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
***05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)***
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

---

### Post by Ayuthia on 2008-11-30
You need to check lspci -nn and see if it says [14e4:4315].  If it does, then you need to use the wl driver.  The b43 driver does not support this chipset yet.  The card was identified as a 4310 until 8.04.1 came out and the name changed over to the correct 4312 listing.

---

### Post by manij on 2008-12-04
I'm not one bit happy with IBEX but for the wl driver. 

Is there anyway to backport the wl driver to hardy from ibex?

---

