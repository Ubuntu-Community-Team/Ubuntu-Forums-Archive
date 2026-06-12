---
title: "new 6.06 install - no network!"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by steve_gregory on 2006-11-02
Hi all


Ubuntu newbie here - I installed 6.06 on my dell latitude D820 - I'm on a network that is DHCP.  lo is the only network available in my top bar...the networking panel shows eth0 and eth1 as available, but there's no connection?  I've tried typing in eth0 on the connection properties and it receives, but doesn't send?!?  Any help?

Thanks

---

### Post by MyAnda on 2006-11-02
please open a terminal (Applications>Accessories>Terminal)

type "ifconfig" (without quotes) and post the result

---

### Post by MyAnda on 2006-11-02
found a couple links that might be of interest also
[http://www.ailis.de/~k/docs/delld820/](http://www.ailis.de/~k/docs/delld820/)
[http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/)
[http://www.tktcr.net/?p=4](http://www.tktcr.net/?p=4) (kubuntu, but should be mostly same)

---

### Post by steve_gregory on 2006-11-02
my ethernet card is a Broadcom card, which I understand has some issues (but I'm not sure how to resolve them!).  ifconfig results:


eth0      Link encap:Ethernet  HWaddr 00:15:C5:B5:F6:4D
          inet6 addr: 2001:468:c80:8107:215:c5ff:feb5:f64d/64 Scope:Global
          inet6 addr: fe80::215:c5ff:feb5:f64d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9818 (9.5 KiB)  TX bytes:1118 (1.0 KiB)
          Interrupt:185

eth1      Link encap:Ethernet  HWaddr 00:18:DE:29:EE:06
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:130273 errors:0 dropped:21975 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xc000 Memory:dcfff000-dcffffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22164 (21.6 KiB)  TX bytes:22164 (21.6 KiB)

---

### Post by MyAnda on 2006-11-02
are you wanting to deal with the wireless or wired networking first?
if wired...it does not look like a cable is plugged in (you will see "RUNNING" in the output for the interface like you see for lo)

has the wireless been configured?
System -> Administration -> Networking

also post the output of "lsmod" and "lspci"

---

### Post by Iowan on 2006-11-02
Try
```
sudo dhclient eth0
```
It's not a permanent solution, but it might get you connected.

---

### Post by bmuni on 2006-11-02
Sounds like you need to turn your network interfaces on. Go to System-->Administration-->Networking and enable or configure your lan interfaces. Then do ipconfig -a to ensure that it that either eth0 (hardwired) or eth1 (wireless interface) is running.

---

### Post by bmuni on 2006-11-02
I made a typo in the previous posting ... type ifconfig -a  NOT ipconfig

---

### Post by MyAnda on 2006-11-02
you can take the user out of windows, but it is hard to take the windows out of the user....jk

---

