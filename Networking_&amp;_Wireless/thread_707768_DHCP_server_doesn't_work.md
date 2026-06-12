---
title: "DHCP server doesn't work"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Pegasus_from_UA on 2008-02-25
I have instaled the DHCP server.
I have 2 subnet : 
 1. one is a wired net - 192.168.0.0/24
 2. one is a wireless net - 192.168.30.0/24

1-st net is working fine . 2-nd - isn't working.

1-st net has static ip written into /etc/netwirk/interfaces.
I'm make 2-st net up by next script:
```
sudo /sbin/ifconfig ra1 down
sudo /sbin/iwconfig ra1 mode Ad-Hoc
sudo /sbin/iwconfig ra1 rate 11M
sudo /sbin/iwconfig ra1 channel auto
sudo /sbin/ifconfig ra1 192.168.30.10/24
sudo /sbin/iwconfig ra1 essid "DFDFSD"
sudo /sbin/ifconfig ra1 up
```

I connected my laptop to 2-nd net via a wi-fi 1 time only. And after that I can't do this.
I even tried to add 255.255.255.255 host . ([http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server))
And I tried this man ([http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29))

It doesn't work :confused:

there are events into syslog files both a server and a client:

Server:
```
Feb 25 17:48:21 buzdack-server dhcpd: DHCPDISCOVER from 00:18:de:a9:06:65 via ra1
Feb 25 17:48:21 buzdack-server dhcpd: DHCPOFFER on 192.168.20.17 to 00:18:de:a9:06:65 via ra1
Feb 25 17:48:24 buzdack-server dhcpd: DHCPDISCOVER from 00:18:de:a9:06:65 via ra1
Feb 25 17:48:24 buzdack-server dhcpd: DHCPOFFER on 192.168.20.17 to 00:18:de:a9:06:65 via ra1
Feb 25 17:48:27 buzdack-server dhcpd: DHCPDISCOVER from 00:18:de:a9:06:65 via ra1
Feb 25 17:48:27 buzdack-server dhcpd: DHCPOFFER on 192.168.20.17 to 00:18:de:a9:06:65 via ra1
Feb 25 17:48:33 buzdack-server dhcpd: DHCPDISCOVER from 00:18:de:a9:06:65 via ra1
Feb 25 17:48:33 buzdack-server dhcpd: DHCPOFFER on 192.168.20.17 to 00:18:de:a9:06:65 via ra1
Feb 25 17:48:45 buzdack-server dhcpd: DHCPDISCOVER from 00:18:de:a9:06:65 via ra1
Feb 25 17:48:45 buzdack-server dhcpd: DHCPOFFER on 192.168.20.17 to 00:18:de:a9:06:65 via ra1
```

Client : 
```
Feb 25 17:47:31 leos dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Feb 25 17:47:34 leos dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Feb 25 17:47:37 leos dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Feb 25 17:47:43 leos dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Feb 25 17:47:55 leos dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Feb 25 17:48:02 leos dhclient: No DHCPOFFERS received.
Feb 25 17:48:02 leos dhclient: Trying recorded lease 192.168.20.17
Feb 25 17:48:02 leos avahi-autoipd(eth1)[7066]: A routable address has been configured.
Feb 25 17:48:02 leos avahi-autoipd(eth1)[7066]: Callout UNBIND, address 169.254.5.225 on interface eth1
Feb 25 17:48:02 leos avahi-daemon[5338]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.5.225.
Feb 25 17:48:02 leos avahi-daemon[5338]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.20.17.
Feb 25 17:48:02 leos avahi-daemon[5338]: Registering new address record for 192.168.20.17 on eth1.IPv4.
Feb 25 17:48:02 leos avahi-daemon[5338]: Withdrawing address record for 169.254.5.225 on eth1.
Feb 25 17:48:05 leos avahi-autoipd(eth1)[7066]: No longer a routable address configured, restarting probe process.
Feb 25 17:48:05 leos avahi-daemon[5338]: Withdrawing address record for 192.168.20.17 on eth1.
Feb 25 17:48:05 leos avahi-daemon[5338]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.20.17.
Feb 25 17:48:05 leos avahi-daemon[5338]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb 25 17:48:05 leos dhclient: No working leases in persistent database - sleeping.
Feb 25 17:48:10 leos avahi-autoipd(eth1)[7066]: Callout BIND, address 169.254.5.225 on interface eth1
Feb 25 17:48:10 leos avahi-daemon[5338]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.5.225.
Feb 25 17:48:10 leos avahi-daemon[5338]: New relevant interface eth1.IPv4 for mDNS.
Feb 25 17:48:10 leos avahi-daemon[5338]: Registering new address record for 169.254.5.225 on eth1.IPv4.
Feb 25 17:48:14 leos avahi-autoipd(eth1)[7066]: Successfully claimed IP address 169.254.5.225
```
[B]
ANY IDEAS ?[/B]

Please help.
it is ISC DHCP server. I heard it's the best one. Now I don't think so :confused:

---

### Post by Pegasus_from_UA on 2008-02-26
doesn't anyone know ? 0_o

---

### Post by superprash2003 on 2008-02-26
i use firestarter.. it has a great gui for ICS and DHCP..easy to setup

---

### Post by Pegasus_from_UA on 2008-02-27
thanks I'll try it later.

---

