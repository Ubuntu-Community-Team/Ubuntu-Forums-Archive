---
title: "Networking troubles - not even lo up after system start-up!"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by GolerGkA on 2006-11-24
Hello, veryone. I've got a rather mysterious trouble, that is possible connected to the bugs in configuration files or smth like that. I've tried to set up routing, LAN and vpn on my home computer, but every time the computer boots even the loopback is down! So, I have to do the following (the results of the commands not shown, it's obvious):
```

sudo ifconfig lo up
sudo dhclient
sudo route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.2.149.254 #Oh, I didn't mention - even the routing table somehow erases! I can't stand it... :mad:
sudo route add -net 212.1.224.0 netmask 255.255.255.0 gw 10.2.149.254
sudo route del default #For setting up default to ppp

``` then I use pptpconfig's graphical interface to connect to vpn server (cos I have no idea how to do that in the terminal even after throughout rtfm of various manuals - may be I'm stupid!) and then
```

route add default dev ppp0
ping gmail.com
PING gmail.com (216.239.57.83) 56(84) bytes of data.
64 bytes from cw-in-f83.google.com (216.239.57.83): icmp_seq=1 ttl=240 time=196 ms
64 bytes from cw-in-f83.google.com (216.239.57.83): icmp_seq=2 ttl=240 time=196 ms
64 bytes from cw-in-f83.google.com (216.239.57.83): icmp_seq=3 ttl=240 time=195 ms

--- gmail.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms


``` - wow! It works!
So, the question is - how can order the Ubuntu do all that stuff itself at the time it boots? I had ASPLinux defore, it really sucks, but it managed to do it! I've tried all the HowTo's, but no result except installation of pptp & pptpconfig...

---

### Post by bapoumba on 2006-11-24
Hi,
I am not quite comfortable with ppp protocol, but the answer probably is in your /etc/network/interfaces file.
Can you post the content of this file ?

---

### Post by GolerGkA on 2006-11-24
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto lo eth0 netbynet
up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.2.149.254 dev eth0
up route add -net 212.1.224.0 netmask 255.255.255.0 gw 10.2.149.254 dev eth0

iface netbynet inet ppp
pre-up ip link set eth0 up
provider netbynet

```

---

### Post by bapoumba on 2006-11-24
> auto lo eth0 netbynet
My guess is that "lo" should not be there. Please back-up your file before edition, so that you can restaure it if necessary.

One other thing is that > iface eth0 inet dhcp
starts dhcp on eth0, wich does not mix up very well with ppp protocol. Do you have a "prepend" line in **/etc/dhcp3/dhclient.conf** ? You probably should comment it out and make it look like :

> prepend domain-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;
with your dns server adresses.

---

