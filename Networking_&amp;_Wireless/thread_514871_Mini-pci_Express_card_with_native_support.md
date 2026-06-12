---
title: "Mini-pci Express card with native support?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by fastpakr on 2007-08-01
I've spent several days fiddling with the Broadcom 43xx/Dell 1390 mini-pci Express card that came in my new Compaq laptop.  With the help of several other members, it now is detected properly and can see/connect to networks at my home and office.  However, the connection is VERY flaky - it will completely disconnect and reconnect with no warning even when within a few feet of the AP, and running an IPSEC tunnel across the connection is an exercise in futility.  Are there any mini-pci Express cards that are natively supported in 7.04?  The only cards I've found so far in that form factor are the Intel 3945abg, the 1390/43xx card I've already got, and the MSI MN54G/MS6877.  All of these appear to require ndiswrapper or some other backwards way of getting them going.  Is there anything on the market that 'just works'?

---

### Post by raiwo on 2007-08-01
i think intel is the only one which works out of the box (WEP, WPA etc...) for example [http://www.amazon.com/wireless-3945ABG-Mini-pci-Express-Adapter/dp/B000ERK23Y](http://www.amazon.com/wireless-3945ABG-Mini-pci-Express-Adapter/dp/B000ERK23Y) 

i Have tried about 7 or 8 diffrent cards (friends usb & pcmcia cards) and only one worked somehow out of the box (no WPA support tho) so if i were you i would go with intel

---

### Post by fazavon on 2007-08-01
this one worked for me

1.2.2.2. Firmware Packages

As an alternative to running the script, you can install the firmware files from a package. To automatically keep up to date, add this repository line to your /etc/apt/sources.list:

deb [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) dapper-cafuego bcm43xx

and make sure apt knows about the GnuPG key used to sign the packages:

wget [http://ubuntu.cafuego.net/969F3F57.gpg](http://ubuntu.cafuego.net/969F3F57.gpg) -O- | sudo apt-key add -

Then update your package listsings and install the bcm43xx-firmware package.

or download the package directly:

wget -c [http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb](http://ubuntu.cafuego.net/pool/dappe...buntu1_all.deb)

and then install it manually:

sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu1_all.deb

---

### Post by fastpakr on 2007-08-01
Everything I've read on here about the 3945 indicates that it requires ndiswrapper - you're saying that's not the case?

---

### Post by raiwo on 2007-08-01
i have always had this idea that intel support in linux is great but it seems not to be so :(

see [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) for more info.

---

### Post by kevdog on 2007-08-01
You might want to try updating you ndiswrapper version to the svn version to see if that helps. Since you have an inernet connection you would need to install the subversion package.  I can provide more details if possible.  Also where did you actually get the driver for your card???

---

### Post by fastpakr on 2007-08-01
It was pulled from a collection of the XP drivers for the laptop that were posted online by somebody who gave up on Vista.  Filename is bcmwl5.inf, version is 4.100.15.5, with a date of 10/12/2006.  I believe the NDISwrapper version I ended up with was 1.47, but I'll check on that when I can get back to the laptop a little later today.  Thanks for the ideas.

---

### Post by kevdog on 2007-08-01
From what you are telling me your built-in wireless card has a broadcom chipset.  There are a lot of broadcom drivers out there (a ton) and Im not too certain how the differ, however it would be easy to try another driver if you provided more info on your card with:
lspci -nn

If you have ndiswrapper 1.47 installed, then I wouldnt change this.  I think the version from the synaptic repository is 1.38 and this can often times lead to problems.

---

### Post by fastpakr on 2007-08-01
> 00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 02)
Also, I was able to plug my laptop directly into the router this afternoon and the VPN issue persists.  Apparently the wireless issue is just an occasional dropout, unrelated to whatever's going on with my VPN connection.
Edit - resolved VPN issue.  Now just dealing with intermittent connection issues that are more annoying than serious.

---

