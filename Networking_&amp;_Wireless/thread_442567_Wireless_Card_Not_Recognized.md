---
title: "Wireless Card Not Recognized"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by wfn on 2007-05-13
Wireless Card Not Recognized

I need a little help !! (New to Unbuntu)

My Panasonic CF-R1 was working great on Unbuntu 10.1. All of the sudden the wireless card (Linksys WPC54G v2) is no longer recofgnised ??? 

I have tried searching the forums, editing files, ndiswrapper re-install, blah, blah, blah. But nothing seems to work. I have posted my lspci & interfaces file (I think that would help). 

Any assistance / suggestions greatly appreciated. Thank you !

****************************
lspci

00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller
00:02.0 VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev c1)
00:03.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 88)
00:03.1 System peripheral: Ricoh Co Ltd R5C575 SD Bus Host Adapter
00:04.0 Communication controller: Matsushita Electric Industrial Co., Ltd. Unknown device 8339
00:07.0 ISA bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
00:09.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

****************************
interfaces

auto lo

iface lo inet loopback


auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

---

### Post by king_arthur on 2007-05-13
Might be the known issue of the blacklisted Realtek module.

However, there are to many NICs active in your "interfaces", and Wlan0 shows up.
So, the info you posted isn't really consistent with your claim.

BTW are you sure it was working with **Unbuntu 10.1** ? 
as there is not such a thing... :)

/P

---

### Post by wfn on 2007-05-14
King_Arthur - thank you for the reply. 

Your right it's Fiesty 7.04 (Apologies for the confusion). 

The issue is exactly that - It seemd to be configured but not working. I am going to try a different card just to make sure it's not the card. 

P.S. I also cleaned up the interfaces file. 

I'll keep you posted.

---

### Post by king_arthur on 2007-05-14
> **wfn said:**
> King_Arthur - thank you for the reply. 

Your right it's Fiesty 7.04 (Apologies for the confusion). 

that's the latest version, it was probably working on Edgy 6.10 (not 7.04).

> **wfn said:**
>  The issue is exactly that - It seemd to be configured but not working. I am going to try a different card just to make sure it's not the card. 

P.S. I also cleaned up the interfaces file. 

I'll keep you posted.
Some modules,  the realtek module among others, on some h/w configuration were crashing the new kernel during boot hence, they have been "blacklisted".
It might be fixed but, of course, swapping your card with a compatible one would make life a lot easier, especially for a newbie.

/P

---

