---
title: "Jumps back to DHCP!  ARG!!!"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by cbmeeks on 2007-05-23
I'm new to ubuntu.

I am running Feisty and thought I configured everything for static IP  (it's a server, no gui).

Anyway, all is fine.  The IP is 192.168.222.73

However, the machine been running for 5 days and every so often, the IP changes to an DHCP address!

I issue a /etc/init.d/networking restart and it jumps back to the static IP.

Here is my network interface conf file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.222.73
netmask 255.255.255.0
network 192.168.222.0
broadcast 192.168.222.255
gateway 192.168.222.3


The router is 192.168.222.3 which is also the DHCP server.  The DHCP range is 192.168.222.200 - 240

Any tips?

Thanks!

cbmeeks
[http://www.signaldev.com](http://www.signaldev.com)

---

### Post by weaksauce on 2007-05-25
I had the same problem, but i found the resolution.

you must kill the dhcp client process because each hour or so it will try to renew the dhcp lease. 

From the command line (you may need to run as root or sudo these commands)

#ps aux | grep dhc

dhcp      3749  0.0  0.2   2332   796 ?        S<s  May17   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root     21491  0.0  0.2   2880   808 pts/3    S+   11:52   0:00 grep dhc
#kill -9 <pid> 

where <pid> is the second column  3749 in my case


Cheers

---

