---
title: "Network bridging."
date: 2005-06-25
forum: Networking &amp; Wireless
---

### Post by apoth on 2005-06-25
I currently have two interfaces in /etc/network/interfaces:

> 
iface wlan0 inet static
wireless-essid WLAN
address 192.168.1.152
netmask 255.255.255.0
gateway 192.168.1.1
auto wlan0

iface eth0 inet static
address 192.168.7.152
netmask 255.255.255.0
auto eth0


Can someone tell me what to add/change in order to get a working bridge br0 between the two? Thanks.

---

### Post by alastair on 2005-06-25
This sort of thing might not be "configurable" in the interfaces file. But you could start by installed something like "bridge-utils" and checking the man pages and :

[http://bridge.sourceforge.net/howto.html](http://bridge.sourceforge.net/howto.html)

---

### Post by ubuntu_demon on 2005-06-25
[QUOTE=alastair]This sort of thing might not be "configurable" in the interfaces file. But you could start by installed something like "bridge-utils" and checking the man pages and :

[http://bridge.sourceforge.net/howto.html](http://bridge.sourceforge.net/howto.html)[/QUOTE]
 it's possible with interfaces :

I found this in some thread :

> 
iface br0 inet dhcp
    bridge_ports all


You should google a bit more for more background information.

---

### Post by apoth on 2005-06-26
I've done lots of reading. Actually this is a problem that I've always had issues with in Linux over the years.

The closest I've been able to get is:
> 
iface br0 inet dhcp
bridge_ports eth0 wlan0
auto br0


(I found that thread too but the bridge wouldn't work when I specified all interfaces for some reason).

This creates the bridge, it receives an IP address, a machine behind the bridge can ping the bridge (it receives an IP via DHCP) but not ping a machine on the internet which the bridge can. I just can't get past this.

---

