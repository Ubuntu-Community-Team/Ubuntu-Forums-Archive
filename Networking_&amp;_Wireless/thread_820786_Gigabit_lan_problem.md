---
title: "Gigabit lan problem??"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by lawi on 2008-06-06
Hi everybody, I have a ASUS M2N-MX K8M890 SOCKET AM2 MICRO-ATX mother board which is stated to have gigabit lan.

I don't feel I get that speed on my gigabit lan at home and need help to verify which driver is used.

lspci gives me 00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) but I don't know what to do with this info.

What I was thinking is that maybe it has loaded a 100Mb driver instead of a 1000Mb??

/lawi

---

### Post by chili555 on 2008-06-06
Is every part of your network gigabit capable? The machine to or from which you are transferring data? The router or switch? If not, then you will get the speed of the weakest link. May we please see which driver is loaded in:```
sudo lshw -C network
```Also, we can gain some clues in:```
sudo ethtool eth0
```Finally, as far as I know, there is no 100Mb/s driver separate from a 1000Mb/s driver; there is simply a driver. The driver is supposed to, but doesn't always, support whatever capabilities the device is capable of.

---

### Post by lawi on 2008-06-07
lshw -C didn't say anything, even tried with output as HTML

ethtool ->

Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

Any ideas?

/lawi

---

### Post by chili555 on 2008-06-07
```
sudo lshw -C network
```> lshw -C didn't say anythingIt takes a few moments to collect all that information; did you give it a few moments? Also, the first letter is lower case L. Is that what you typed?> ---snip---
Speed: 100Mb/s
---snip---
Auto-negotiation: on
---snip---It is running at 100Mb/s, not 1000Mb/s, either in error, or because it has negotiated the rate as the maximum rate at which it can reliably transfer data with another device on the network. You can try:```
sudo ethtool eth0 speed 1000 
```However, if another device on the network has reported it's only able to do 100Mb/s, then you may get errors or other issues. I'd think it's better to troubleshoot the other devices on the network to see why a gigabit device is not operating correctly.

---

### Post by lawi on 2008-06-13
Ok, thanx I try that

---

### Post by ModelM on 2008-06-13
If you look at your output from ethtool you'll see that the adapter is indeed capable of gigabit, but it's not advertising that capability...

 Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full 

So, other devices are connecting at 100, the fastest speed it advertises. I don't know how to fix this, but it might be a place to begin...

---

