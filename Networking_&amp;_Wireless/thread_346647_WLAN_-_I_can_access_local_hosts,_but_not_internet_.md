---
title: "WLAN - I can access local hosts, but not internet hosts"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by breakaway on 2007-01-26
Specs:
Vaio VGN-FS48GP with Intel 2200 wireless card.
Distro: Xubuntu 6.06

Problem:
I followed [this guide](http://www.ubuntuforums.org/showthread.php?t=318539), and I can ping local hosts on my LAN, but not internet hosts. 

Seems like a DNS issue.

Here is my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 10.2.254.9
netmask 255.255.255.0
network 10.2.254.0
broadcast 10.2.254.255
gateway 10.2.254.1
dns-nameservers 10.2.254.1
wpa-driver wext
wpa-conf managed
wpa-ssid LOLnet
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <mykey>

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I note that there are more devices in this list than there are in my laptop (I have 1 x Ethernet, 1 x Wireless LAN, 1 x IEEE1394 port). That totals to 3 (4 if you count loopback), not 6 as in the interfaces file.

All the settings for "eth1" (my WLAN) card are correct, but I still can't get internet? 

```
breakaway@thingar:~$ nslookup
>google.com
;; connection timed out; no servers could be reached
>
```

What gives?

Also, how can I also use the guide mentioned in this post to work with my Ethernet connection as well?

Any help appreciated :)

---

### Post by MrHorus on 2007-01-26
```
traceroute www.google.com
``` please.

This will show the path that your packets are taking as it looks like they are being dropped somewhere, likely at your router.

10.2.254.1 is your router, right?

Are you using encryption, if so what form?

If using encryption, does it work with no encryption?

Also, please paste the output of running ```
dhclient
```.

You may need to sudo for some of the above commands btw.

---

### Post by breakaway on 2007-01-26
I have pointed Firefox to my squid proxy (10.2.254.1:3218) and I've got internet connectivity through the proxy. But the machine is unable to resolve anything on its own. As a result, anything that doesn't have proxy support doesn't work. For e.g., typing "ping google.com" into a terminal won't work. apt-get wont work, fortunately, Synaptic Package Manger has proxy support.

```
breakaway@thinger~: traceroute google.com
traceroute: unknown host google.com
```

Its not a packet loss issue, its a DNS issue.

Also, while playing around, I have noticed that I do not have a [color=red]/etc/resolv.conf[/color] file.

It's not an issue with association with the access point, its just that I'm telling it what name server to use, but it refuses to do so.

---

### Post by breakaway on 2007-01-26
Never MInd, Fixed. It turns out that I had mistakenly named the file "reolv.conf" instead of "resolv.conf"

Everything's working perfectly now.

---

