---
title: "Wireless Access Point"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by salemboot on 2007-05-13
Using a wireless card to serve internet to other devices (wii, pc, etc).

I must say that all the tutorials I've read have the following scenarious.
1. ethernet internet connection with wireless serve
2. ethernet internet and ethernet serve

See the problem is I've got wireless internet (sprint via ppp0) and i would like to serve this to my wireless devices.   I've done it before but this time it doesn't seem to be cooperating.

The specifics:
I've got the card in master mode and a key has been provided to secure it.

My chipset is atheros (ath0).   ifconfig lists ath0 and wifi0

I assign ath0 an ip of 192.168.0.1

I execute dhcpd3 ath0  and it promptly changes ath0's ip to 192.168.0.20

My dhcpd.conf has a subnet set up.


subnet 192.168.0.0 netmask 255.255.255.0{
	range 192.168.0.1 192.168.0.20;
	option routers 192.168.0.1;
	option domain-name-servers @private, @private;
	option broadcast-address 192.168.0.255;
	default-lease-time 600;
	max-lease-time 7200;
}


I've tried using my other pc to see what ip it gets issued.  I think the main problem is that its not issuing IP's.  Becuase it seems my windows box never gets one or if it does its something similar to 169.25.xx.xx   which is what it does when it has no clue.

I tested dhcp with the ethernet as the server and it works great. I can masquerade internet fine.  

Its worked before but I forgot what settings I used on the dhcpd.conf.

All comments and help are welcomed. 

Thanks

---

### Post by salemboot on 2007-10-28
Solved.

ifconfig eth0 down

ifconfig ath0 up


apparently it was moving the traffic through eth0.

---

