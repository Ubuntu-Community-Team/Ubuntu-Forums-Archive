---
title: "Can't get a DHCP offer"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Blond on 2008-01-16
I have a dual boot system Windows XP and Kubuntu 7.10

In the past al already noticed that if I restarted my PC from Windows to Linux that I could not get an IP address from my router and therfore had no Internet under Linux. Manually disabling and enabling the ethernet card fixed this problem.
However now since a few days also this does not work anymore.

I'm not able to connect to my router.

Output from IFCONFIG
eth0
      Link encap:Ethernet  HWaddr 00:01:80:4D:41:1F
      inet6 addr: fe80::201:80ff:fe4d:411f/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
      Interrupt:16 Base address:0xa000
lo
      Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:441 errors:0 dropped:0 overruns:0 frame:0
      TX packets:441 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:55707 (54.4 KB)  TX bytes:55707 (54.4 KB)


Can someone help me?

---

### Post by amo-ej1 on 2008-01-16
try to powercycle your router ;)

you could also try to manually release your ip address under windows before booting into linux.

---

### Post by Blond on 2008-01-16
Already tried this. Switch off my router for half a day and resetted it. Still no DHCP offer for Linux

---

