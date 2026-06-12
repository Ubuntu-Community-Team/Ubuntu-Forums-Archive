---
title: "Internet @ less than 3KB/s"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by pir on 2008-03-04
Hi all

I have a problem.
My internet connection is working, but it isn't properly.
I have an onboard networkadapter (eth0) which I don't ise.
I plugged in a PCI card (eth1) and in that card, I plugged in my UTP-cable.

On the PC I had first, the internet worked properly, so the cable can't be the 

Problem is, my internet is only working from time tit time, and if it works, it doesn't go >3000bps.

```
karlo@karlo-desktop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 7050
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:a7:27:75:7b
Sending on   LPF/eth1/00:10:a7:27:75:7b
Listening on LPF/eth0/00:1a:4d:5c:97:62
Sending on   LPF/eth0/00:1a:4d:5c:97:62
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.35 -- renewal in 13244 seconds.

```
My syslog keeps telling me this:
```

Mar  4 21:26:59 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Mar  4 21:27:04 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar  4 21:27:05 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Mar  4 21:27:12 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Mar  4 21:27:15 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Mar  4 21:27:21 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Mar  4 21:27:27 karlo-desktop dhclient: No DHCPOFFERS received.
Mar  4 21:27:27 karlo-desktop dhclient: No working leases in persistent database - sleeping.
Mar  4 21:27:27 karlo-desktop avahi-autoipd(eth0)[7745]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Mar  4 21:27:27 karlo-desktop avahi-autoipd(eth0)[7745]: Successfully called chroot().
Mar  4 21:27:27 karlo-desktop avahi-autoipd(eth0)[7745]: Successfully dropped root privileges.
Mar  4 21:27:27 karlo-desktop avahi-autoipd(eth0)[7745]: Starting with address 169.254.6.15
Mar  4 21:27:28 karlo-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Mar  4 21:27:30 karlo-desktop dhclient: No DHCPOFFERS received.
Mar  4 21:27:30 karlo-desktop dhclient: No working leases in persistent database - sleeping.
Mar  4 21:27:32 karlo-desktop avahi-autoipd(eth0)[7745]: Callout BIND, address 169.254.6.15 on interface eth0
Mar  4 21:27:32 karlo-desktop avahi-daemon[5695]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.6.15.
Mar  4 21:27:32 karlo-desktop avahi-daemon[5695]: New relevant interface eth0.IPv4 for mDNS.
Mar  4 21:27:32 karlo-desktop avahi-daemon[5695]: Registering new address record for 169.254.6.15 on eth0.IPv4.
Mar  4 21:27:36 karlo-desktop avahi-autoipd(eth0)[7745]: Successfully claimed IP address 169.254.6.15
```

plz help...

---

### Post by Iowan on 2008-03-05
It appears that eth0 is still active.  Try disabling it - either in BIOS (which will probably make the other card eth0), or by System>Administration>Network>Wired network>  (I have only one card, so don't know how multiple cards look).  You *should* be able to uncheck eth0.
Otherwise, you can edit** /etc/network/interfaces** and either comment out eth0 setup or at least comment out **auto eth0**.

Another way to get to the network setup is to simply click the "Manual network configuration" icon in the upper right corner.

---

