---
title: "Can not connect to my windows to create bridge"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by f4rm0r on 2014-03-10
Hi there
I have to say, I am utterly surprised by one thing, and that would be that I can not connect to my Desktop that is currently using windows7.
I am using a small laptop right now so I can try to connect to my PC with a ethernet cable and therefore bridge the wireless conection through it.
I have changed in the "edit connections - edit wireles - shared to other computers"
still it does not work to use it.
I have tried everything, using static ip on both machines.
using static ip on only linux/windows.
using auto DHCP on both machines.
nothing, abolutely nothing.
I have disabled ipv6.
still not working.
I have disable ipv6 by adding:
```

net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
```
still does not work.
I changed
```

#net.ipv4.ip_forward=1
to
net.ipv4.ip_forward=1
```

so I am out of ideas!
I did the same thing yesterday, and the day before then, and it worked, but today it simply is not working! :/
I can get the windows to ping this machine (writing from the linux machine) but I can't get the linux to connect to windows.
```

ifconfig eth 0
shows:
Link encap:Ethernet  HWaddr 00:23:5a:de:d6:83  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696 errors:0 dropped:0 overruns:0 carrier:17
          collisions:0 txqueuelen:1000 
          RX bytes:207115 (207.1 KB)  TX bytes:174234 (174.2 KB)
```
so it is not even getting an ip-address to the windows machine.
after I have changed in sysctl I did:
```

sysctl -p /etc/sysctl.conf
```
as it is suggested to do that so the change will become permanent.

I am runnning a live USB stick on this machine since I have ome other troubles with my current linux in this machine, but that I will take another time.
the live version of the linux is:
32-bit 13.10

---

### Post by f4rm0r on 2014-03-18
hello here I am once again, and I manage to solve my problem!
after a few days off my computer I came back and thought:
why not try to use "shared to others computers" on my eth0 on my lappy?
so I did that, and voilá I can now share my internet connection!

now for everyone that comes to this problem, just do what I did and it will all be okey :D (if nothing else is wrong ofc ;3 )

---

