---
title: "Unable to play videos in Interprid"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by balaraja on 2009-09-15
I need your help!! Today I formatted my disk and installed Ubuntu Interprid in my laptop. After which I tried to play videos using Firefox/Opera/Epiphany. But for some reasons I dont see any display the video jus gets streamed but not played. Please, let me know the reason for this.

My /etc/X11/xorg.conf is set with default contents. Does the problem exists bcoz of default xorg.conf file. If so here is my o/p for lspci. So please let me know the xorg.conf contents for my configuration. By googling I tried to make changes to xorg.conf, but it didnt help me.

#lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Waiting avidly for a reply. Thanks in advance :)

Thanks,
Bala.

---

### Post by DasEi on 2009-09-15
sudo apt-get install vlc mozplugger ubuntu-restriceted-extras

vlc, standalone mediaplayer for almost everything
u-r-extras bunch of codecs, flashsupply for browsers, n stuff
mozplugger  allows ff to use extern players

also google ubuntu perfect desktop fo a general walkthrough
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

if your graphics in general are in order,   flash is another corner then xorg

---

### Post by balaraja on 2009-09-15
Thanks for your reply!!

I am concerned about playing youtube videos.I have installed Adobe Flash player but still im unable to play it.

---

### Post by Cresho on 2009-09-15
64bit system?

---

### Post by balaraja on 2009-09-15
Nope its 32 bit.

---

### Post by balaraja on 2009-09-15
I installed Adobe flash player 10 from their site.

---

### Post by balaraja on 2009-09-15
The problem is solved now :) I uninstalled gnash and mozilla-plugin-gnash since it luks like these packages conflict with adobe-flashplugin.

---

