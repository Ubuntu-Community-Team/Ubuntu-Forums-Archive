---
title: "Can't connect to internet via router"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by tomasovitch on 2007-07-02
Hi all,

I'm a relative newbie, have just installed 7.04 on an ASUS F3JR laptop as a dual boot with Vista (don't ask) and I'm trying to connect to cable internet via a Netgear RP114 router. It all works fine with Vista, so no hardware/cable probs. I can ping the DHCP and DNS server, but can't connect to the internet with Firefox or the auto update thing. I get server not found in FF and 'can't resolve' in the other.

Here is the output from ifconfig eth0:
eth0      Link encap:Ethernet  HWaddr 00:1A:92:CA:BC:60
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:feca:bc60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1788 (1.7 KiB)  TX bytes:4371 (4.2 KiB)
          Interrupt:16 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

And here is the output from sudo dhclient eth0:
There is already a pid file /var/run/dhclient.pid with pid 5971
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:1a:92:ca:bc:60
Sending on   LPF/eth0/00:1a:92:ca:bc:60
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.4 -- renewal in 125524 seconds.

And this is what /etc/network/interfaces looks like:
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

And finally, cos that's all I can think of for now based on other posts, here is /etc/resolv.conf:
search vic.bigpond.net.au
nameserver 192.168.0.1

Hope someone can help, thx!

---

### Post by Ken_Lewis81 on 2007-07-02
You really don't need to confuse things with a DHCP request for an adapter's IP address and a line specifying the same adapter's IP address.  I suspect that it's wiping out your 'gateway' line when you're assigned the IP address by DHCP.  Comment out the 'address 192...' line and see if that resolves things.

hope helps.
take care.
Ken.

---

### Post by Rui Pais on 2007-07-02
hi,
as long as it has 'iface eth0 inet dhcp' it will use dhcp, no matter what appears in address line. 
(Of course if set to static ip that line need to be fixed cause it's assign the nic on the box the same IP as the router...) 
btw sometimes turning to static ip is enough to solve some net problems.

I would suspect 1st the usual ones, DNS problem or IPV6.

For the IPV6:
```
gksudo gedit /etc/modprobe/blacklist
```
add a line at bottom:
```
blacklist ipv6
```
reboot (not only a login or a network restart. module must be downloaded)

If that didn't work, then for the DNS, try [this how-to here]("http://www.opendns.com/start/ubuntu.php").

---

### Post by tomasovitch on 2007-07-05
Thanks v much guys, OpenDNS fixed it.

---

