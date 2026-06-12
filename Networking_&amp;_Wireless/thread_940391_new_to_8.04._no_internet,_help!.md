---
title: "new to 8.04. no internet, help!"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by verthandi on 2008-10-07
hi guys.

we just bought a new PC and we decided to install 8.04
on it. installation went without a hitch but there is 
no internet. we are using a DSL connection.

tried the "basic procedure" at ubuntu documentation
and sudo pppoeconf, no results. 
"the access concentrator of your provider did not respond"
also sifted through the forums and couldn't find an answer

PC board is AM2+/AM2 dual core athlon
nvidia chipset mcp61p/mcp61s
with onboard ethernet LAN

_content of /etc/network/interfaces:_

"auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0"

_output of ifconfig:_

eth0     Link encap:Ethernet HWaddr 00:1e:90:e8:37:53
        inet6 addr: fe80:21e:90ff:fee8:3753/64 scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:41 errors:0 dropped:0 overruns:0 frame:0
        TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:5775 (5.6 KB) TX bytes:15531 (15.1KB)
        interrupt:20 Base address:0xe800
 
 eth0:avahi Link encap:Ethernet HWaddr 00:le90:e8:37:53
   inet addr:169.254.6.114 Bcast:169.254.255.255 Mask:255.255.0
   UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
   Interrupt:20 Base address:0xe800

lo      Link encap: Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:1929 errors:0 dropped:0 overruns:0 frame:0
        TX packets:1929 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:100568 (98.2 KB) TX bytes:100568 (98.2 KB)

hope someone can help! TIA!

---

### Post by willca on 2008-10-07
how exactly are you suppose to connect to your ISP?

do you use PPOE for that at all ?

---

### Post by ibizatunes on 2008-10-07
If you connect vai ethernet cable to a ISP like virgin or NTL (in the uk) PPPoE reset your router, with your PC on at it should get a IP  address, if you connect via wireless, you need to install restricted drivers, or your wireless card hasnt been detected!

---

### Post by superprash2003 on 2008-10-07
go to system->admin->network and go to eth0 properties and set it to DHCP mode.. and then post an ifconfig output.. you need to get an ip first.. if you still dont get an ip .. then try static ip instead of dhcp mode.. and enter ip as 192.168.1.10 if your gateway(router) ip is 192.168.1.1 .. or enter ip as 192.168.0.10 if your gateway(router) ip is 192.168.0.1

---

