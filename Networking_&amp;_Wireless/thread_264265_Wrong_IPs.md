---
title: "Wrong IPs"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by Eggbanjo on 2006-09-24
i have 2 NIC cards in my machine, one is dhcp, other is static - i know that one will be 192.168.0.2 and the other is 10.0.0.4.
 However ifconfig shows as 169's. i know the IPs are working as a) i can connect to the internet, and b) i can connect to my lan.

Any ideas?

---

### Post by spd106 on 2006-09-24
Do you have zeroconf installed? This will do the link local addressing that you see. Usually ifconfig will only show one ip address per interface. Try **ip addr**.

---

### Post by Eggbanjo on 2006-09-24
yeah i have zeroconf installed, tried the ip addr you said got: 

2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:11:d8:45:06:3d brd ff:ff:ff:ff:ff:ff
    inet 169.254.132.184/16 brd 169.254.255.255 scope link eth0
    inet 192.168.0.101/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::211:d8ff:fe45:63d/64 scope link
       valid_lft forever preferred_lft forever

how do i get everything to see the 2nd address rather than the local link?

---

### Post by spd106 on 2006-09-24
As far as I know everything should still work okay. I found that running dhclient again replaces the 169.x with the 192.x address again, but it's really only cosmetic. I'm not sure why this even happens, I forget how I even came across it, perhaps it's a bug? 

In the end I removed zeroconf since it's only really useful with a laptop and/or wifi. Plus Avahi works ok on it's own.

I suppose it's worth checking that **ip route** shows the 192.x in the default gateway. If not then you could always change it manually or add it to the /etc/network/interfaces file as a post-up, assuming that you use it.

---

### Post by spd106 on 2006-09-25
It turns out this problem is well known upstream on Debian, [http://wiki.debian.org/ZeroConf](http://wiki.debian.org/ZeroConf). 
There has been a bug filed though it's not clear how progress will continue [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=307480](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=307480).

---

### Post by Eggbanjo on 2006-09-25
in the end i too uninstalled zeroconf, because i have gdesklets running to show me the dchp ip from the router.
 Because if by some chance (and it has happened before) the router decides to change the IP it screws up my portforwarding.

Cheers for the replies!

---

