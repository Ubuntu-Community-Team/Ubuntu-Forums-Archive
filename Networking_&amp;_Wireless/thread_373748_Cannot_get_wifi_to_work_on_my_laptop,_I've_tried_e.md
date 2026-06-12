---
title: "Cannot get wifi to work on my laptop, I've tried everything!"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by Onecat on 2007-03-01
I'm a newbie but I was reading the forums all last night trying to figure this out and I couldn't! My wireless is on ath0 I think (or wifi0?) - It's a Toshiba Laptop. The wireless card is Atheros something. Supposedly and older version of Ubuntu should support my model laptop's wifi. And I do get a strong wifi signal, and also it says data is being sent and recieved, but I cannot connect to the internet in Firefox, etc. I know my wifi works and it should be set on DHCP, because I can connect to it just fine with my PDA. Any help appreciated! Thanks.

---

### Post by CrazyTn on 2007-03-01
I am with you man, this is a pain lol

---

### Post by spd106 on 2007-03-01
Can you please post the output of entering **lspci** at a terminal.

You may have one of the cards that doesn't work with the version of madwifi-ng included in Edgy. So you might have to install madwifi-old to get it working.

---

### Post by Onecat on 2007-03-02
output of lspci:

00:00.0 Host bridge: ATI Tech Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Tech Inc RS480 PCI Brdige
00:04.0 PCI bridge: ATI Tech Inc Unknown Device 5a36
00:13.0 USB Controller: ATI Tech Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Tech Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Tech Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Tech Inc IXP SB400 SMBys Controler (rev 81)
00:14.1 IDE interface: ATI TEch Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI tech inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI tech Inc IXP SB400 PCI-PCI bridge (rev 80)
00:14.5 Multimedia audio controller: ATI tech inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI TEch Inc ATI SB400 - ac 97 modem controller
01:05.0 vga compatable controller: ATI tech inc rc410 (raden xpress 200M]
04:02.0 eternet controller: ATheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
04:04.0 CardBus bridge: ENE Tech Inc CB1410 Cardbus Controller (Rev 01)
04:06.0 Ethernet Controller: Realtek Semiconductor Co., Ltd., TRL-8139/8139C/8139c+ (rev 10)

thats it, sorry for typos

---

### Post by drumkitcat on 2007-03-06
> **spd106 said:**
> Can you please post the output of entering **lspci** at a terminal.

You may have one of the cards that doesn't work with the version of madwifi-ng included in Edgy. So you might have to install madwifi-old to get it working.

Do you know where to get the older version of madwifi?  Also, do you know if there's a list of cards that do not work with the madwifi-ng?

I also have a Toshiba laptop with the Atheros AR5112 rev 01 wireless card, and have not been able to get it working so I'm wondering if it's because the current version of madwifi doesn't support it, but maybe the older version does.

I seem to remember reading something about that somewhere in these forums but I cannot remember where 

Any help would be most appreciated!
thanks!

---

### Post by spd106 on 2007-03-06
You can download the old release from [http://madwifi.org](http://madwifi.org), the build-essential package will also be needed to build the driver modules.
There are guides about doing this for dapper in the forum and wiki.

---

