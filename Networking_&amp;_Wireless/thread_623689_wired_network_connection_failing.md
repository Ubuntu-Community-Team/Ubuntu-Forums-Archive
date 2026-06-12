---
title: "wired network connection failing"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2007-11-26
I just installed ubuntu on an elderly laptop, and pretty much everything works. (I actually installed Dapper, then upgraded, since I like the Dapper installer better... ) The only thing that doesn't is the wired network connection. 

This is strange, as when I used it at home, it was fine. However, at school, I cannot connect to the wired network. It works with my newer laptop, but the old one doesn't find the network. 

To make it even stranger, when I boot windows (I dual boot the old laptop), Windows doesn't find the network either ("Network cable disconnected"). 
The only thing that I can think of is the difference in network cable length. But my new laptop has not problem at school - and the problems only started, even in windows, after installing Ubuntu. Never had this kind of problem before...

lspci:
```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
```

It would really be terrible if the network just happened to have died as I was installing Ubuntu, seeing as it's not my laptop... 

As usual, any and all help greatly appreciated!
Thanks
-K

---

### Post by mellowd on 2007-11-26
Because it works at your school it means the hardware is definately working. Do you use dhcp both at school and at home? It might be that your school has dhcp and home you use a static address or vice versa

---

### Post by Kulgan on 2007-11-26
It's at home that it works. Both places use DHCP - that's how I got my newer comp working. I do exactly the same thing at school with the old laptop as I do at home, and as I do in both locations with the new one, and it just doesn't work. I'd really hate to have to tell the guy that his network card is dead - just when I happened to be installing ubuntu on it - and he can't use it anymore. Since it's a rather old laptop, it's rather hard to get things replaced, and it might not be worth it. But it's still a shame to not be able to use it just because the network is dead... 

As I said, it might be the difference in cable length. The old laptop might just not be able to detect signals if they go beneath a certain signal strength...

But thanks for the reply! 
:D

-K

---

### Post by mellowd on 2007-11-27
It could be, but that depends on the length of cable. Have you tried using a different cable at school?

---

### Post by Kulgan on 2007-11-28
No, I can't, since I don't have access to the router. But what I will do when I get home is try a longer cable. 
Apparently it didn't work at the owner's home either. I don't know how long his ethernet cable is.

---

### Post by mellowd on 2007-11-28
The length of cat5 cable can actually be quite long. Are these good cables though? Cables can be quite dodgy.

The best bet is to try another laptop on the same cable, if it works then its definately something on the laptop

---

