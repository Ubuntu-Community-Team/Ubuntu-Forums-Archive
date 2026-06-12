---
title: "network connection lost - due to Nvidia?"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by tadmorguy on 2007-08-28
Hi,

this is the first time I've installed Ubuntu and I've installed it on a brand new computer.
The computer is connected through modem-router to the ADSL. 
After I've installed Ubuntu I've enabled the "Nvidia accelerated graphics driver" and I noticed that the network is going down after a while (no IP is found using DHCP) , when I turn off the acceleration the computer stays connected.

Can somebody help?

below is the hardware list (lspci):
[I]00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d3 (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
[/I]
thanks,
Guy.

---

### Post by raijinsetsu on 2007-08-28
> **tadmorguy said:**
> Hi,
...
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d3 (rev a1)
...


What do you have for a video card?

---

### Post by Nano Geek on 2007-08-28
That's really odd. 
Now, this is just a wild guess, but it might be that your computer does not have enough power so when your graphics card needs more power, your networking hardware does not get enough. 
As I said, its just a wild guess.

---

### Post by ddrichardson on 2007-08-28
+1 Power - is the card on the PCI bus with the Network - it appears to be.

---

### Post by tadmorguy on 2007-08-29
I have leadtek px7200 which works on the PCI express slot.
On previous installation of ubuntu on this machine I've used "autobuntu" scripts which update the video card driver but I got the same problem with the network connection.

thanks,
Guy.

---

### Post by tadmorguy on 2007-08-29
Just to see if this is a hardware problem, I've installed window XP with all the related drivers (NIC + PCX 7200) and it works fine.
Too bad I can not make it work with Ubuntu :-(

Any other ideas?

thanks,
Guy.

---

### Post by will71110 on 2007-08-29
Could be an IRQ conflict? but I have no idea how to check that in Ubuntu.  

Does your BIOS have an option to use spread spec for the CPU BUS?  Could be recieveing interferance from the card and turning this on or up could  help dappen some noise interferance.

---

### Post by tadmorguy on 2007-09-02
Thanks everyone for the effort,
 
it seems that this is a hardware problem since the screen saver on windows hungs after a while and cause the computer to freeze.

I've gave the computer back to the dealer for fixing it, then I'll try to see if the problem still persist on Ubuntu - hopefully not :-)

Guy.

---

