---
title: "No DHCPOFFERS received."
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by Footer on 2007-08-26
Can anyone tell me why about every 4-5 minutes I get this entry in my /var/log/syslog file:

```
Aug 26 09:28:00 kubuntu64 dhclient: bound to 192.168.1.110 -- renewal in 41588 seconds.
Aug 26 09:33:03 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 26 09:33:07 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 26 09:33:17 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug 26 09:33:32 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Aug 26 09:33:34 kubuntu64 dhclient: No DHCPOFFERS received.
Aug 26 09:33:34 kubuntu64 dhclient: No working leases in persistent database - sleeping.
Aug 26 09:37:49 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 26 09:37:56 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Aug 26 09:38:10 kubuntu64 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 26 09:38:19 kubuntu64 dhclient: No DHCPOFFERS received.
Aug 26 09:38:19 kubuntu64 dhclient: No working leases in persistent database - sleeping.

```

I have a Linksys WRT54G wireless router (DHCP enabled) and cable modem for Internet.  I've never had any problems with my LAN or getting on the Internet.  The machine is wired to the Linksys router.  I'm running Kubuntu Feisty Fawn 7.04 currently up-to-date from the repositories.

Let me know if any further information is needed.  I've done a lot of searching (in the forums and via Google) but so far, have come up empty on this subject.

Thanks!

---

### Post by Footer on 2007-08-26
I think I may have solved my own problem.  :)

Discovered there are two NICs on the mobo (DUH!), eth0 and eth1.  I've got eth1 hooked up to the Linksys.  eth0 is not hooked up to anything but it was enabled (System Settings --> Network Settings) so I entered Administrator Mode and disabled eth0 and guess what?  The DHCPDISCOVER messages stopped!

One odd thing I'm still trying to figure out is where this IP address was coming from:

```
Aug 26 09:56:14 kubuntu64 avahi-autoipd(eth0)[4497]: Starting with address 169.254.4.118
Aug 26 09:56:20 kubuntu64 avahi-autoipd(eth0)[4497]: Callout BIND, address 169.254.4.118 on interface eth0
Aug 26 09:56:24 kubuntu64 avahi-autoipd(eth0)[4497]: Successfully claimed IP address 169.254.4.118
```

It doesn't seem related to anything (my local network, my network gear -- router/cable modem -- or my cable provider's info.).  Oh well.

Well, hopefully this info. helps others out there who may be getting this message and not know how to fix it!

Thanks!

---

### Post by kevdog on 2007-08-26
This is normal since you have the avahi package installed.  Uninstall the package if you want and most likely those messages will disappear.  Do a google search for avahi to discover what this package is all about.  Im sure my explanation will not be totally correct.

---

