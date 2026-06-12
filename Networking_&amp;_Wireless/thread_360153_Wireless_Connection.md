---
title: "Wireless Connection"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by jasrog on 2007-02-12
I can connect fine via ethernet but now I want connect wireless via my Atheros AR5006EG wireless network but it is not even showing up as a network to enable....I am using a linksys wireless router. What can I do exactly to get online wireless?

---

### Post by ukripper on 2007-02-13
> **jasrog said:**
> I can connect fine via ethernet but now I want connect wireless via my Atheros AR5006EG wireless network but it is not even showing up as a network to enable....I am using a linksys wireless router. What can I do exactly to get online wireless?



type in terminal window 
$ sudo iwconfig 
$ lspci

and paste output here.

also paste text from running this $ sudo gedit /etc/network/interfaces

---

### Post by jasrog on 2007-02-16
When I ran those prompts in terminal this is what came up:lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jason@jason-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by ukripper on 2007-02-19
> **jasrog said:**
> When I ran those prompts in terminal this is what came up:lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jason@jason-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)




Router has nothing to do with your card not being detected. You need to find correct drivers for your card to work. Following links might be helpful:
[http://ubuntuforums.org/showthread.php?t=325899&highlight=Howto+atheros](http://ubuntuforums.org/showthread.php?t=325899&highlight=Howto+atheros)
[http://ubuntuforums.org/showthread.php?t=38972&highlight=Howto+atheros](http://ubuntuforums.org/showthread.php?t=38972&highlight=Howto+atheros)

---

### Post by Lonthong on 2007-02-22
The latest madwifi driver still does not support this card.
Instead, you should try madwifi-ng r 1711 or later. You can download it from [URL="http://snapshots.madwifi.org/madwifi-ng/"]here
[/URL]
If you have restricted-modules already installed, you must disable & uninstall it first
$ sudo ifconfig ath0 down
go to your madwifi folder
$ cd scripts
$ ./madwifi-unload.bash
$ ./find-madwifi-modules.sh /lib/modules/
$ cd ..
$ sudo make
$ sudo make uninstall (just to make sure the older driver will be completely uninstalled)
$ sudo make install
$ sudo modprobe ath_pci
$sudo modprobe wlan_scan_sta
$ sudo ifconfig ath0 up
System - administration - networking: You should now see your wireless device there

---

