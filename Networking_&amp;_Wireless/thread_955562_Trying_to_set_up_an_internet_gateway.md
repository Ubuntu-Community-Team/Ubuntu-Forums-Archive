---
title: "Trying to set up an internet gateway"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by expza on 2008-10-22
Current /network/interfaces looks like this :
```

auto lo
iface io inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1
broadcast 192.168.0.255

auto ppp0
iface ppp0 inet ppp
provider international

```

/ppp/peers/international looks like this : (used pppoeconf to set it up and manually renamed it international)
```

noipdefault
defaultroute
replacedefaultroute
hide-password
noauth
nopersist
plugin rp-pppoe.so eth0
unit 0
user "xxxx"

```

when I set ifup ppp0 I get:
ppp0: error while getting interface flags : no such device

ifconfig reports ppp0 being up as well as having an ip address
plog gives me this:
[IMG]http://i74.photobucket.com/albums/i266/mikemullany/DSC00231.jpg[/IMG]

I'm then unable to access the internet from the machine... can't ping or anything.

PLEASE can someone help! I'm desperate! :(

Ubuntu Server 8.04

---

### Post by puppywhacker on 2008-10-22
Your ppp connection seems to be up and running and your image (K850's are cool) showed some packets for both RX / TX. So I'm guessing you are either missing a default route, or you are missing the DNS servers

Could you ping the providers gateway, and google? (I can)
ping 196.209.11.1
ping [www.google.com](www.google.com)

Could you show the routes?
route

If the default route is not there you can add them temporary
route add default gw 196.209.11.1

Could you show your resolve.conf, which DNS servers are there?
cat /etc/resolv.conf

I couldn't check, but I think for your provider, the resolv.conf should have looked like these

search is.co.za
nameserver 196.26.5.8
nameserver 196.4.160.3

goodluck

---

