---
title: "Ubuntu - Windows"
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by ampald on 2005-09-20
I have an cable net connection which is connected to my Linux machine via USB. My bro's computer is running XP and we are connected via a crossover cable. We can ping each other. 

The network card has this information, doing ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:50:8D:E3:82:82
          inet addr:169.254.154.93  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:8dff:fee3:8282/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26164 (25.5 KiB)  TX bytes:18926 (18.4 KiB)
          Base address:0x9000 Memory:f4000000-f4020000

I had to set this IP myself, by going to system>admin>networking and clicking on configure, then checking "this device is configured" then "static IP" and typing that in.

The XP box has an IP of 169.254.154.95. However, it cant connect to the internet. and I cant see it when I go to Places>Network servers>Windows network>TAN(workgroup). On the XP machine, it cant see my computer when I go into workgroup TAN. 

How would i about having the XP machine connect to the net?

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=ampald]I have an cable net connection which is connected to my Linux machine via USB. My bro's computer is running XP and we are connected via a crossover cable. We can ping each other. 

The network card has this information, doing ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:50:8D:E3:82:82
          inet addr:169.254.154.93  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:8dff:fee3:8282/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26164 (25.5 KiB)  TX bytes:18926 (18.4 KiB)
          Base address:0x9000 Memory:f4000000-f4020000

I had to set this IP myself, by going to system>admin>networking and clicking on configure, then checking "this device is configured" then "static IP" and typing that in.

The XP box has an IP of 169.254.154.95. However, it cant connect to the internet. and I cant see it when I go to Places>Network servers>Windows network>TAN(workgroup). On the XP machine, it cant see my computer when I go into workgroup TAN. 

How would i about having the XP machine connect to the net?[/QUOTE]

Your brother should set your computer's eth0 NIC as his default gateway, and you need to enable IP forwarding on your Ubuntu machine.

On the XP machine, you can set the default gateway either by digging through the networking GUI dialogs, or you can use the "route add" command in cmd.exe.

On the Ubuntu machine, you can enable IP forwarding with:
```

$ sudo bash
# echo "1" > /proc/sys/net/ipv4/ip_forward

``` 
This turns on IP forwarding but doesn't last through a reboot.  I forget what file needs to be edited to make this permanent-- you can probably Google it or find it in another forum post if you search for "IP forward".

---

