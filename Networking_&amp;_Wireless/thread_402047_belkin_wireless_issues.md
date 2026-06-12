---
title: "belkin wireless issues"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by keidori on 2007-04-05
Well, I loaded ubuntu 6.10 and every thing works except my belkin wireless card. From what ive seen on the forums this device works under the rt2500 driver and that the card should be good to go without installing drivers. Well im a Linux noob so maybe I missed something. Any ways ive looked at the network manager and I can see my wireless card but when I type in an ssid and activate the card I should be good to go right, wrong? When I look at the connection properties my wireless card "eth1" has no signal but im 3ft from my wireless router(and yes I know its case sensitive). The card works with windows fine. Ive also compiled the driver and installed it. But still no signal, I also tried to setup rutilt and got nowhere. Here is some config data

iwconfig

eth1 IEEE 802.11b/g Essid:"" Nickname:"broadcom 4318"
Mode: Managed Access Point invalid
RTS thr: off Fragment thr: off
Link Quality: 0 Signal level: 0 Noise level: 0
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag: 0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

lspci


00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)




when I try "sudo ifup eth1" I get "ifup: interface eth1 already configured"


And when I try "ifconfig: i can not see the wireless card (eth1)



Any ideas?
thanks

---

### Post by JasonCfirefox on 2007-04-05
I have that problem mate, i have the same broadcom 4318 in my wireless card.
I tried lots of fixes with no luck, i hope someone can help us. :? 
my iwconfig says same thing.

---

### Post by JasonCfirefox on 2007-04-05
Hi again i got my card to work by following this link,only thing i have to do now is find out how to get my internet conection going,the net work is going just cant use internet cos one pc is on windows,:confused: .

Anyway here is the link hope it works for you.
[http://ubuntuforums.org/showthread.php?t=399280&highlight=feisty](http://ubuntuforums.org/showthread.php?t=399280&highlight=feisty)

---

