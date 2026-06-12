---
title: "Just load 10.04 and wired internet won't work"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by Snipas187 on 2010-06-17
So this is my first linux os and I am a super newb.  I can't get my wired internet to work.  I have my computer plugged into a router (Linksys WRT54G2) which is plugged into the modem.  My windows based PCs are working fine for internet (3 wireless and 1 wired).  It appears that Ubuntu isn't setting a gateway or something.  Here are some highlights...

[B]ifconfig:
[/B] eth0 link encap:Ethernet  HWaddr 00:e0:18:26:4e:85
inet6 addr: fe80::22e0:18ff:fe26:4e85/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:57 dropped:0 overruns:0 frame:0
TX packets: 68 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes: 13926 (12.9 KB)
Interrupt:5 Base address: 0x1400

eth0:avahi Link encap:Ethernet HWaddr 00:e0:18:26:4e:85
inet addr: 169:254.6.84 Bcast:169.254.255.255 Mask 255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt: 5 Base address:0x1400
  
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 metric:1
RX packets:4 errors:0 dropped:0 overruns:0 fram:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes: 316 (316.0B) TX bytes 316 (316.0 B)

**Route**
Kernel IP routing table
Destination       Gateway            Genmask           Flag          Metric    Ref  Use  Iface
link-local              *                   255.255.0.0         U             0           0      0     eth0


I'll be honest, not sure what all this means and why under Route it doesn't show in IP address for destination....anyone help a newb out?  I've manually entered IPv4 as suggested by Ubuntu's help after it didn't automatically connect to the internet.  I can not manually enter DHCP as it won't allow me to "apply".

---

### Post by mörgæs on 2010-06-17
Perhaps this will help:
[https://help.ubuntu.com/10.04/internet/C/index.html](https://help.ubuntu.com/10.04/internet/C/index.html)

---

### Post by Iowan on 2010-06-17
The 169.254.X.X address is **avahi** "helping". For whatever reason, DHCP failed. You can try **sudo dhclient eth0** (from a terminal. It'll *probably* confirm "No DHCP offers received"...

---

### Post by Snipas187 on 2010-06-18
Yep, No DHCPOFFERS received.  No working leases in persistent database - sleeping.

Well, unsleep.  Basic troubleshooting isn't helping.  I tried to manually set a DHCP with sudo route add default gw blah blah blah but it wouldn't recognize the command....

---

### Post by Snipas187 on 2010-06-19
Anyone have any ideas??  Or direction on what to try?

---

