---
title: "help with wicd + WEP + ipw2200"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by devnulljp on 2008-06-13
I'm using Kubuntu Hardy on a Thinkpad with a intel Centrino 2200BG using ipw2200, which has been working fine. In an attempt to resolve an issue with knetworkmanager, I installed wicd. It works fine as long as I turn off encryption on my router and make sure the ssid is broadcast. So, hardware and drivers are working OK. But, I can't get it to connect with WEP or WPA enabled. (It worked fine with knetworkmanager with WEP).
Where do I start trying to debug this?

I tried with the WEP key straight or surrounded by quotes -- no difference

Any pointers appreciated...

I edited my /etc/network/interfaces file to look like this according to the wicd faq:
```
auto lo
iface lo inet loopback
```
I'm using the ipw driver in wicd
```
lsmod | grep ipw
ipw2200               146120  0 
ieee80211              35528  1 ipw2200
lsmod | grep ieee
ieee80211              35528  1 ipw2200
ieee80211_crypt         7040  1 ieee80211

```
```
$dmesg | grep ipw
[   32.608629] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   32.608632] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   33.002298] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   37.061278] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

```

EDIT: I just ran through it again and this time did tail -f /var/log/syslog

```
Jun 15 20:40:38 hostname avahi-daemon[5010]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun 15 20:40:38 hostname avahi-daemon[5010]: Withdrawing address record for fe80::20d:60ff:fec9:9060 on eth0.
Jun 15 20:40:38 hostname dhclient: receive_packet failed on eth0: Network is down
Jun 15 20:40:55 hostname kernel: [ 4286.906607] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 15 20:40:55 hostname kernel: [ 4286.910263] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 15 20:40:55 hostname dhclient: There is already a pid file /var/run/dhclient.pid with pid 3132
Jun 15 20:40:55 hostname dhclient: removed stale PID file
Jun 15 20:40:55 hostname dhclient: Internet Systems Consortium DHCP Client V3.0.6
Jun 15 20:40:55 hostname dhclient: Copyright 2004-2007 Internet Systems Consortium.
Jun 15 20:40:55 hostname dhclient: All rights reserved.
Jun 15 20:40:55 hostname dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun 15 20:40:55 hostname dhclient:
Jun 15 20:40:56 hostname dhclient: Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Jun 15 20:40:56 hostname dhclient: Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Jun 15 20:40:56 hostname dhclient: Sending on   Socket/fallback
Jun 15 20:40:57 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun 15 20:41:01 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun 15 20:41:09 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Jun 15 20:41:20 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun 15 20:41:27 hostname dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Jun 15 20:41:28 hostname dhclient: No DHCPOFFERS received.
Jun 15 20:41:28 hostname dhclient: No working leases in persistent database - sleeping.
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Successfully called chroot().
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Successfully dropped root privileges.
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: fopen() failed: Permission denied
Jun 15 20:41:28 hostname avahi-autoipd(eth1)[7242]: Starting with address 169.254.4.40
Jun 15 20:41:33 hostname avahi-autoipd(eth1)[7242]: Callout BIND, address 169.254.4.40 on interface eth1
Jun 15 20:41:33 hostname avahi-daemon[5010]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.4.40.
Jun 15 20:41:33 hostname avahi-daemon[5010]: New relevant interface eth1.IPv4 for mDNS.
Jun 15 20:41:33 hostname avahi-daemon[5010]: Registering new address record for 169.254.4.40 on eth1.IPv4.
Jun 15 20:41:37 hostname avahi-autoipd(eth1)[7242]: Successfully claimed IP address 169.254.4.40
Jun 15 20:41:37 hostname avahi-autoipd(eth1)[7242]: fopen() failed: Permission denied
```

That fopen() failed looks suspicious. It looks like it kinda works, but not quite. It's trying to get an IP address by dhcp, what is weird is that  it gets an IP address of 169.254.4.40, which is not on my network (which is a standard 192.168.1.0/255 private network).
I did a who is on that IP and it bears no resemblance to my ISP / country or anything else either.
Any ideas?

---

