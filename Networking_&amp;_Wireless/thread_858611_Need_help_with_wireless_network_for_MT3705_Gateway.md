---
title: "Need help with wireless network for MT3705 Gateway laptop"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by MR.UNOWEN on 2008-07-13
A few day ago I was helping my friend switch to Ubuntu, but I ran into a few annoying problems. First of all I've always been using a desktop computer, so I've never had to deal with wireless internet. The dilemma I'm having is whether I just don't know how to set up a wireless connection on Ubuntu or if Ubuntu just does't recognize the hardware for Ubuntu see any wireless networks. I installed WiFi Radar and it wasn't able to recognize anything. So is it that I don't know what I'm doing or Ubuntu doesn't recognize the hardware? Should I report this as a bug?

---

### Post by PinkFloyd102489 on 2008-07-13
Open a terminal and run this command, then post the output.


```
lspci
```

---

### Post by MR.UNOWEN on 2008-07-15
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
08:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by vendetta red on 2008-07-15
You might try looking at one of these links, looks like they might get you going in the right direction.

[http://ubuntuforums.org/showthread.php?t=846249&highlight=RTL-8185](http://ubuntuforums.org/showthread.php?t=846249&highlight=RTL-8185)

[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

[http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy](http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy)

Hope that helps, post here if one of those ends up working, and good luck!

---

