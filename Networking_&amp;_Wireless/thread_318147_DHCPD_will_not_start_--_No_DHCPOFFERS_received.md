---
title: "DHCPD will not start -- No DHCPOFFERS received"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by stekole on 2006-12-13
Hey all; first off i just wanted to say hi:)

second is my problem: I am installing DHCP onto my ubuntu box to run as a router. Now i get a error coming from my dhclient and my dhcpd server. 
DHCPD will not start -- No DHCPOFFERS received is the error...
if i do a network restart i get this error aswell as if i check my system logs. 

any ideas?

Other info: I have 2 network cards...one is eth0 and it holds the external ip...so eth1 should be sending the ips out for dhcp....

---

### Post by koenn on 2006-12-13
the dhcp client says > No DHCPOFFERS received, right ? If so, that's because there is no dhcp server running (or it is unreachable).

the dhcp server is not running because it did not start. That's what  it says : > DHCPD will not start. 

So you need to fid out why is won't start. 
Probably there is information as to why it wont start in the system logs you mentioned.

---

### Post by linuchsan on 2006-12-13
Post your dhcpd.conf

---

### Post by stekole on 2006-12-13
subnet 192.168.1.0 netmask 255.255.255.0 {
        option netbios-name-servers 192.168.1.1;
        option domain-name-servers 192.168.1.1;
        option domain-name "domain.com";
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.1;
        range 192.168.1.100 192.168.1.130;
        }

---

### Post by linuchsan on 2006-12-13
What do the log files say?

---

### Post by stekole on 2006-12-13
well i did somthing and now some of it works....lol but i get this in the syslog now:

Dec 13 17:24:55 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Dec 13 17:24:55 localhost dhcpd: DHCPDISCOVER from 00:80:c6:f9:ab:e7 via eth1
Dec 13 17:24:55 localhost dhclient: DHCPOFFER from 192.168.1.254
Dec 13 17:24:55 localhost dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Dec 13 17:24:55 localhost dhcpd: DHCPREQUEST for 192.168.1.2 (192.168.1.254) from 00:80:c6:f9:ab:e7 via eth1: unknown lease 192.168.1.2.
Dec 13 17:24:55 localhost dhclient: DHCPACK from 192.168.1.254
Dec 13 17:24:55 localhost dhclient: bound to 192.168.1.2 -- renewal in 97584 seconds.
Dec 13 17:24:56 localhost dhcpd: DHCPOFFER on 192.168.1.130 to 00:80:c6:f9:ab:e7 via eth1
Dec 13 17:25:05 localhost ntpdate[3855]: step time server 82.211.81.145 offset 3.716029 sec
Dec 13 17:25:05 localhost kernel: [17250987.544000] eth1: no IPv6 routers present



ummmm

---

### Post by linuchsan on 2006-12-13
some of it works?

---

### Post by koenn on 2006-12-13
to me that looks like it works.

---

### Post by Iowan on 2006-12-14
It *does* seem a little curious that the lease (192.168.1.2 ) got issued out of the range (192.168.1.100 192.168.1.130).  The DHCP server doesn't appear to be set for static leasing - did dhclient request specific lease? (maybe it's not a problem anyway... but curious!)

---

### Post by koenn on 2006-12-15
```
DHCPREQUEST for 192.168.1.2 (192.168.1.254) from 00:80:c6:f9:ab:e7 via eth1: unknown lease 192.168.1.2.
```

I think it's a renewal of an existing lease (clients start asking renewals at about half the lease time).

---

