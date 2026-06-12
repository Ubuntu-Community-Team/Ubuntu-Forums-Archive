---
title: "Dual Network Card Problem, Ubuntu Feisty"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by sidprak on 2007-08-26
my computer is running ubuntu 7.04 with 2 nic's each card is connected to a different router and both the routers have dhcp servers.  This is the result of [code]/sbin/ifconfig[code]

eth0      Link encap:Ethernet  HWaddr 00:40:05:81:64:E3
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:39992 (39.0 KiB)  TX bytes:18305 (17.8 KiB)
          Interrupt:5 Base address:0x6f00

eth1      Link encap:Ethernet  HWaddr 00:0A:E6:1F:2E:58
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe1f:2e58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:158504547 (151.1 MiB)  TX bytes:34423454 (32.8 MiB)
          Interrupt:11 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6067 (5.9 KiB)  TX bytes:6067 (5.9 KiB)

i see that eth0 is not connected to the one of the routers.  I am able to access the internet using eth1 but I am not able to ping computer that are connected to the other router.  Is there a reason why this is happening?

---

### Post by capitalistpiglet on 2007-08-26
Whats the dhcp scope for the router connected to eth0? Have you tried setting a ip manually for eth0 and if so where you able to ping the router?

---

### Post by sidprak on 2007-08-27
Thanks for the reply!  The DHCP scope for the router connected to eth0 is 192.168.2.100 to 192.168.2.109.  I did try setting the ip address manually and I was not able to ping the router.  I also verified that the router was working properly by successfully pinging it from another computer.

---

