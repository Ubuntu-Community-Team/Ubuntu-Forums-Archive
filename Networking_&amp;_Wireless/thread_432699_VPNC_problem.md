---
title: "VPNC problem"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Gujs on 2007-05-04
I have a problem with vpnc. I have to connect to some private network every day just to check something if it is working ok. 

I can connect from my ubuntu 7.04 from my work network, but not from my home network. If I use windows and cisco vpn I can connect even from my home network. Does somebody know what means this error message:
```
sudo vpnc-connect /home/gregor/Home/Drugo/.vpn/buda.vpn 
vpnc-connect: receiving packet: Message too long

```

which I get, when I want to connect from home network with ubuntu 7.04.

Ubuntu was installed on a clean machine and not upgraded!

Thanks

---

### Post by Michael R Head on 2007-05-09
Yeah, I am seeing this, too. On one network, I have a Debian/etch-based router doing NAT, on the other, I have an Ubuntu/dapper-based router also doing NAT. On the dapper-based network, vpnc works fine, on the etch-based network, I get nuttin.

---

### Post by Michael R Head on 2007-05-09
I uncovered the source of my problems. My etch-based router has two ethernet interfaces, eth1 (for the internal network), and eth0 (for the external network). The MTU for eth0 was set to 576 and eth1 was set to 1500. The machine from which I was invoking vpnc was sending out an encrypted and non-fragmentable IPSEC packet which was larger than 576 bytes, so the router rejected the packet from the vpn client. Unfortunately, the vpnc-connect program doesn't do a good job of reporting the resulting ICMP packet, otherwise, it would have been more apparent what was going on. In order to resolve my problem, I merely had to do "sudo ifconfig eth0 mtu 1500" and put "mtu 1500" in my /etc/network/interfaces on the router.

BTW: you may be interested in learning how I figured this out. I installed wireshark on the vpn client machine and ran it while running "sudo vpnc-connect". I could immediately see the reply packet and the message contained within it ("Destination Unreachable (Fragmentation needed)"). After that, I thought to log in to the router and check its MTU.

---

