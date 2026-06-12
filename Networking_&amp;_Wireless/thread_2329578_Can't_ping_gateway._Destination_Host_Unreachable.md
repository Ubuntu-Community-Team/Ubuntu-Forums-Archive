---
title: "Can't ping gateway. Destination Host Unreachable"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by sundontshin3 on 2016-07-03
Hello,
I currently am running Dell optiplex 980 ubuntu server 16.04 and have issues with wireless network card. Simply trying to get it connected to the home network.  When i simply try to ping my gateway 192.168.1.1 it returns 
```
From 1921.68.1.25 icmp_seq=1 Destination Host UnReachable
```

my /etc/network/interfaces
```

sources /etc/network/interfaces.d/*

auto lo
face lo net loopback

auto wlp3s0
iface wlp3s0 inet static
address 192.168.1.25
net mask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
wpa-ssid <network name>
wpa-psk <network passcode>
dns-nameservers 192.168.1.1
dns-nameservers 8.8.8.8

```

I previously had ubuntu server 14.04 and NEVER had a network issue. I know it has to be some new implementation between that version and 16.04 bc it even took my time to figure out they changes the wireless interface name from wlan0 to wlp3s0.
Any relevant help or solutions is appreciated.

---

