---
title: "Realtek 8139D unrecognized"
date: 2006-08-06
forum: Networking &amp; Wireless
---

### Post by amarpeluri on 2006-08-06
common problem but not a solution yet !

lspci :
0000:02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:05.0 Ethernet controller: Unknown device 1904:2031 (rev 01)

i have a wireless as well as a lan card 

ifconfig -a:
ath0      Link encap:Ethernet  HWaddr 00:03:2F:25:07:32
          inet addr:172.17.9.214  Bcast:172.17.9.255  Mask:255.255.254.0
          inet6 addr: fe80::203:2fff:fe25:732/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6723 errors:742 dropped:0 overruns:0 frame:742
          TX packets:2052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:2078319 (1.9 MiB)  TX bytes:357438 (349.0 KiB)
          Interrupt:193 Memory:f8ac0000-f8ad0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tried modprobe 8139c/too to no avail

even tried ndiswrapper with windows drivers but it didnt work

tried compiling src drivers but they dint work.

wireless works without a hitch.

whenever i insert a module it doesnt show up in ifconfig 
with ndiswrapper, it showed only driver installed , but dint say hardware present

even tried turning acpi off *edited grub etc* but dint know what to do after that.

inserted modules again but once more they dint work. me at my wits ends

**groc want help**

---

