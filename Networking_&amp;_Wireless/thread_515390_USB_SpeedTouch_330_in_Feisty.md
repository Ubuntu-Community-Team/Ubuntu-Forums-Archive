---
title: "USB SpeedTouch 330 in Feisty?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by Xera on 2007-08-01
I'm following [this](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) to try and get my modem to work(It worked in 6.06) but it won't connect - all of the settings are correct and the firmware is installed correctly but still no connection.

Syslog:
> 
Aug  2 03:37:08 jamie-kubuntu RFC1483/2684 bridge: Interface "nas0" created successfully 
Aug  2 03:37:08 jamie-kubuntu RFC1483/2684 bridge: Communicating over ATM 0.0.38, encapsulation: LLC 
Aug  2 03:37:08 jamie-kubuntu RFC1483/2684 bridge: Interface configured
Aug  2 03:37:08 jamie-kubuntu RFC1483/2684 bridge: RFC 1483/2684 bridge daemon started 
Aug  2 03:37:11 jamie-kubuntu avahi-daemon[4869]: Joining mDNS multicast group on interface nas0.IPv4 with address 192.168.0.1.
Aug  2 03:37:11 jamie-kubuntu avahi-daemon[4869]: New relevant interface nas0.IPv4 for mDNS.
Aug  2 03:37:11 jamie-kubuntu avahi-daemon[4869]: Registering new address record for 192.168.0.1 on nas0.IPv4.
Aug  2 03:37:15 jamie-kubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug  2 03:37:21 jamie-kubuntu dhclient: No DHCPOFFERS received.
Aug  2 03:37:21 jamie-kubuntu dhclient: No working leases in persistent database - sleeping.
Aug  2 03:37:21 jamie-kubuntu avahi-autoipd(eth0)[5245]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).
Aug  2 03:37:21 jamie-kubuntu avahi-autoipd(eth0)[5245]: Successfully called chroot().
Aug  2 03:37:21 jamie-kubuntu avahi-autoipd(eth0)[5245]: Successfully dropped root privileges.
Aug  2 03:37:21 jamie-kubuntu avahi-autoipd(eth0)[5245]: fopen() failed: Permission denied
Aug  2 03:37:21 jamie-kubuntu avahi-autoipd(eth0)[5245]: Starting with address 169.254.5.159
Aug  2 03:37:21 jamie-kubuntu pppd[5247]: Plugin rp-pppoe.so loaded.
Aug  2 03:37:21 jamie-kubuntu pppd[5247]: pppd 2.4.4 started by root, uid 0
Aug  2 03:37:21 jamie-kubuntu kernel: [   48.064380] NET: Registered protocol family 10
Aug  2 03:37:21 jamie-kubuntu kernel: [   48.064515] lo: Disabled Privacy Extensions
Aug  2 03:37:21 jamie-kubuntu kernel: [   48.064599] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  2 03:37:23 jamie-kubuntu avahi-daemon[4869]: Registering new address record for fe80::20e:50ff:fec4:f46b on nas0.*.
Aug  2 03:37:25 jamie-kubuntu avahi-autoipd(eth0)[5245]: Callout BIND, address 169.254.5.159 on interface eth0
Aug  2 03:37:25 jamie-kubuntu avahi-daemon[4869]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.159.
Aug  2 03:37:25 jamie-kubuntu avahi-daemon[4869]: New relevant interface eth0.IPv4 for mDNS.
Aug  2 03:37:25 jamie-kubuntu avahi-daemon[4869]: Registering new address record for 169.254.5.159 on eth0.IPv4.
Aug  2 03:37:29 jamie-kubuntu avahi-autoipd(eth0)[5245]: Successfully claimed IP address 169.254.5.159
Aug  2 03:37:29 jamie-kubuntu avahi-autoipd(eth0)[5245]: fopen() failed: Permission denied
Aug  2 03:37:32 jamie-kubuntu kernel: [   58.934407] nas0: no IPv6 routers present
Aug  2 03:37:41 jamie-kubuntu ntpdate[5274]: can't find host ntp.ubuntu.com 
Aug  2 03:37:41 jamie-kubuntu ntpdate[5274]: no servers can be used, exiting
Aug  2 03:37:56 jamie-kubuntu pppd[5247]: Timeout waiting for PADO packets
Aug  2 03:37:56 jamie-kubuntu pppd[5247]: Unable to complete PPPoE Discovery
Aug  2 03:37:56 jamie-kubuntu pppd[5247]: Exit.


Help? :mad:

---

### Post by ugm6hr on 2007-08-02
Maybe try this instead: [http://ubuntuforums.org/showthread.php?t=44763](http://ubuntuforums.org/showthread.php?t=44763)

---

### Post by Xera on 2007-08-02
> **ugm6hr said:**
> Maybe try this instead: [http://ubuntuforums.org/showthread.php?t=44763](http://ubuntuforums.org/showthread.php?t=44763)

I'll try but I'm pretty sure my ISP uses PPPoE.

---

### Post by ugm6hr on 2007-08-02
> **Xera said:**
> I'll try but I'm pretty sure my ISP uses PPPoE.

Oh. Sorry.

---

### Post by Xera on 2007-08-02
> **ugm6hr said:**
> Oh. Sorry.
No problem. :)

---

### Post by matogrosso on 2007-09-25
> **Xera said:**
> No problem. :)

In the UK most ISP's usae PPP0A. Who is yours ?

---

### Post by matogrosso on 2007-09-25
HOWTO SpeedTouch 330 USB modem and Virgin under UBUNTU in the UK.
[http://ubuntuforums.org/showthread.php?t=559395](http://ubuntuforums.org/showthread.php?t=559395)

---

### Post by xxishxx on 2007-09-27
me 2 like above PPPoE

iam from isreal 


who can help me !

---

