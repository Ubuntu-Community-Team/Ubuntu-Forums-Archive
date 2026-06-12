---
title: "Not entirely sure if wireless is 100%"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Cheule on 2006-11-16
Hi peeps. I'm using Dapper 6.06 on my Sony Vaio PCGFX702, and I'd like your input on things to try to fix some minor problems I've been having with wireless.

I recently bought a netgear WG511v2 so I can roam about the house with the laptop. Now, due to my having a "Made in China" V2 card which uses the Marvell chipset, I have to use ndiswrapper to even get it to work at all.

First problem: Since installing ndiswrapper et al to get the wireless card going, I now have a bootup problem whereby sometimes the laptop freezes at the point where networking is attempting to enable itself. Unplugging the card before booting the laptop fixes the problem, but it's not exactly elegant. Once booted, I can just pop in the card and off I go. This happens on 8 out of 10 bootups. Similar problem happens while shutting down (sometimes) and also when browsing. Sometimes the machine will just lock. :(

Second problem: A minor issue I grant you, but the signal strength bar is always at 100%. I've even left my house and walked down the road without so much as a drop. Somehow I think it's telling porkies, as when I boot into Windows (it's a dual booter) the signal strength is all over the place. Just wanted to know wether it's borked or not.

Third problem: Typing 192.168.0.1 into the address bar to access the router no longer works on the laptop, all I get is a timeout. I temporarily fixed it by making the laptop's IP permanent instead of DHCP, but the next time I booted up the problem came back. The address works for all my wired desktops though.
Thanks in advance for any input!

---

### Post by FrodoB on 2006-11-16
First problem: Are you using the latest version of ndiswrapper, did you get your drivers from their hardware list? If not then first upgrade to the latest version of ndiswrapper. And it that does not resolve it then look into their driver source.

Second problem: Many ndiswrapper drivers do not have everything implemented. Using the latest version may improve this a well.

Third problem:  Sounds like you are connected to the AP, but you do not have your dhcp route set yet. Perhaps sudo dhclient will get you one?

---

### Post by Cheule on 2006-11-16
First off thanks for the input :)

1) I've installed ndiswrapper and related tools using Synaptic, they are all v1.8, as far as I can gather that's the newest. As for the drivers, I used the XP ones that came on the installation CD that shipped with the card.

2) Shame, although it's nice to think I'm getting a 100% signal everywhere :D

3) sudo dhclient gives this:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/08:00:46:6e:fc:95
Sending on   LPF/eth0/08:00:46:6e:fc:95
Listening on LPF/wlan0/00:14:6c:8f:25:c5
Sending on   LPF/wlan0/00:14:6c:8f:25:c5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.7 -- renewal in 36362 seconds.

Only thing is, the laptop's IP is 192.168.0.10!

---

### Post by FrodoB on 2006-11-16
> **Cheule said:**
> 

Only thing is, the laptop's IP is 192.168.0.10!



You mean it was 192.168.0.10

---

### Post by FrodoB on 2006-11-16
I did see a WG511T that used a Marvell pre-N chipset on the ndiswrapper site:

Card: NetGear WN511T 300mbps RangeMax Next (PCMCIA Card)

    * Chipset: Marvell Pre-N
    * pciid: 11ab:2a02
    * Driver: Driver for Netgear WN511T ([http://firmware.netgear-forum.com/index.php?dlfile=705)](http://firmware.netgear-forum.com/index.php?dlfile=705)), Version 08/29/2006, 3.0
    * Other: Tested with ndiswrapper 1.7 (utils) and 1.8 (drivers) for Kubuntu (Live DVD).
    * Other: The lspci command says: "Ethernet Controller: Marvel Technology Group Ltd: Unknown device 2a02 (rev 03)" 

Have you looked at the NetGear site to see if a later driver is available for your device?

---

### Post by dbott67 on 2006-11-16
The 100% signal strength is a known issue with ndiswrapper.

As for the IP address, please post the output of cat /etc/network/iterfaces:
```
dbott@edgy:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

[B]auto wlan0
iface wlan0 inet [COLOR="Red"]dhcp[/COLOR][/B]
```

If you have a line like the one above, every time you reboot your computer it will try to obtain an IP address automatically.  For static IP, the line should look like this:
```
auto wlan0
iface wlan0 inet **static**
address 192.168.0.10
netmask 255.255.255.0
...
```

-Dave

---

