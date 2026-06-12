---
title: "Interfaces file... wifi gateway ip?"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by ShayneOSU on 2006-10-13
Hello all.  

On my Dapper desktop, I have ethernet and wifi.  The ethernet (eth0) has Internet through a cable modem.  I'm hoping to share that connection through the wifi.  I'm setting up the wifi network as static on 192.168.0.x, since DHCP has been giving me fits.  My question, though, is... in my /etc/network/interfaces file, what do I set as the gateway for the wifi (eth1) connection?  Eth0's is automatically set, and I know the other systems in the house should have the Dapper desktop's ip as their gateway... but what is the desktop's wifi supposed to use?  Here's my interfaces file:

```

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
wireless-essid JamieAndShayne
wireless-mode ad-hoc
wireless-rate 11MB

```

As of right now, all of the other systems see the ad-hoc wifi network, but they aren't able to get any data from it, and none of the systems can ping each other.  I'm curious about the "network 192.168.0.0" portion, too.  Am I setting up the network incorrectly?  

I'd appreciate any help you can give.

---

