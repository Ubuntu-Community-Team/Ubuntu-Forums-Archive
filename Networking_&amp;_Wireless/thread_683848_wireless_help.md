---
title: "wireless help"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by chezck on 2008-01-31
i have a wireless card DWL-520 installed, but for some reason i can't get it to work, nor i can get wpa to work. please help me with this. i dont see any wireless but in my windows laptop i see it ad i am connected. please help

---

### Post by rje_nc on 2008-01-31
First bit of information you need is what chipset the wireless card uses.  Not all wireless chipsets work well (and a few barely work at all IMO).

Open a terminal and type "lspci" (without the quotes), and pay particular attention to the Ethernet controller lines.  Post this information and someone should be able to point you in the right direction.

Bob

---

### Post by chezck on 2008-02-01
nando@nando-desktop:~/Desktop/1$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200]
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
02:0c.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
02:0d.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)

---

### Post by chezck on 2008-02-04
no one knows?

---

