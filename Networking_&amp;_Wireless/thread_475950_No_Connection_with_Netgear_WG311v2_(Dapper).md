---
title: "No Connection with Netgear WG311v2 (Dapper)"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by jgillick on 2007-06-16
I have a Netgear WG311 v2 installed in my machine (running Dapper) but I can't connect to the network.  The Ubuntu Networking dialog says the wireless card is active, but there's no IP assigned and I cannot ping anything.  Here's my setup

```

$iwconfig
lo		no wireless extensions.

etho	no wireless extensions.

wlan0	IEEE 802.11b+/g+ ESSID:"Gillick"  Nickname: "acx v0.3.21"
		Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
		Bit Rate:54 Mb/s   Tx-Power=15 dBs  Sensitivity=1/3
		Retry min limit:7  RTS thr:off
		Power Management:off
		Link Quality=33/100  Signal level=6/100  Noise level=0/100
		Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
		Tx excessive retries:0  Invalid misc:0  Missed beacon:0
		
sit0	no wireless extension
```


Here' s my /etc/network/interfaces file
```


auto wlan0
iface wlan0 inet dhcp
wireless-essid		Gillick
wireless-key		------------------
wireless-channel	6
wireless-mode		managed

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 	192.168.2.10
netmask		255.255.255.0
gateway		192.168.2.1

auto eth1
iface eth1 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

```

I'm able to connect just fine to the wireless router with my MacBook and I used this network card successfully in Windows XP before converting to Ubuntu.

Thanks,
Jeremy

---

### Post by jgillick on 2007-06-18
After searching around on the net for a few more hours I found my answer:
[http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html](http://www.doctort.org/adam/nerd-notes/netgear-wg311v2-wireless-lan-and-ubuntu-dapper.html)

15 minutes later my wireless card was working perfectly.

---

