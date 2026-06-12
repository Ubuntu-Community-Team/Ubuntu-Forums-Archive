---
title: "Fujitsu amilo Li 1718"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by roadrash on 2007-09-06
I am having problems getting the wireless networking to work with ubuntu 7.04 fiesty.

This is a new laptop and and I'm told uses a atheros network interface.

I have been looking at a fujitsu forum here: [http://www.amilo-forum.com/forum,9,-Linux+Unix+BSD.html]("http://www.amilo-forum.com/forum,9,-Linux+Unix+BSD.html") but I was unable to get the network working with what was there.

Can someone please guide me with getting it working?

here is the output of lspci:

> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


---

### Post by reckless2k2 on 2007-09-06
query atheros setup in these forums. then you should be fine.

---

### Post by roadrash on 2007-09-07
> query atheros setup in these forums. then you should be fine.

Ok I found this article and followed it through and It seems to have installed everything correctly, but  I still cannot find or connect to any wireless access point.

[http://ubuntuforums.org/showthread.php?p=3205543]("http://ubuntuforums.org/showthread.php?p=3205543")


Can someone please help

---

### Post by reckless2k2 on 2007-09-07
you might want to try this one:


[http://ubuntuforums.org/showthread.php?p=1822454#post182245](http://ubuntuforums.org/showthread.php?p=1822454#post182245)


and know a little about wireless networking just in case like are you cloaked, using wpe, wpa.....yadda...they will all cause issues. probably should have everything open on the wifi router to start and go from there.

---

