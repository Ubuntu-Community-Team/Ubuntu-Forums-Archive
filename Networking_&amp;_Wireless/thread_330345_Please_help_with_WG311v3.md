---
title: "Please help with WG311v3"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by vinoloco on 2007-01-03
OK, there are enough threads in various discussion groups that I shouldn't be having issues with this but....

I have a new Netgear WG311v3 PCI card and I'm trying to get it to work with Edgy.  The best thread points to a method described here:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29)

I follow all the steps including making and installing the newest ndiswrapper, etc. but when I get to issuing the "iwconfig" command I get only the following:

/WG311v3 V1.0/Driver/Windows XP$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

with no wlan0 notation.

I know the hardware is recognized with and "lspci":

lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)



Anybody out there have a clue how to debug this one?  All help will be appreciated.

-- vino

---

