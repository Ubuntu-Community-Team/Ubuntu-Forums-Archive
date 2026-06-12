---
title: "Empty routing table despite dhclient script tries to set it"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by jocsch on 2006-07-26
Hi all,
I have a problem as my servers routing table is not set despite the fact that dhclient-script tries to set it. Maybe this has something to do with the special "first setup in qemu than copy it to the real partition" I described here [http://www.ubuntuforums.org/showthread.php?t=222890](http://www.ubuntuforums.org/showthread.php?t=222890)

But maybe not. That's why I ask this seperately. My eth0 interface is configured correctly by dhclient-script
```

eth0      Link encap:Ethernet  HWaddr YY:YY:YY:YY
          inet addr:85.X.X.X  Bcast:85.X.X.X  Mask:255.255.255.255
          inet6 addr: fe80::XXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1400 (1.3 KiB)  TX bytes:580 (580.0 b)
          Interrupt:177 Base address:0xe400

```
The only special thing here is that the Bcast address is the same as the inet addr, but that's true for the rescue system of this remote server as well, and there everything is fine.

I put a log message in dhclient-script which shows that the following line is executed:
```

 route add default dev eth0 gw 85.X.X.1 

```

But the routing table is empty if I do a route in rc.local to display the table:
```

 Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

Does anybody has an idea where to look or which settings to try?
Please note that this is a remote server and as long as the network is not running I can't reach the command line but can only manipulate the files via a rescue system..

Thanks,
 Markus

---

### Post by jocsch on 2006-07-27
OK, I figured it out by routing the std error stream as well into a file. The problem is the 255.255.255.255 netmask used by my provider. If I follow the tip in the following post

[http://www.ubuntuforums.org/showthread.php?t=200297&highlight=route+add+host](http://www.ubuntuforums.org/showthread.php?t=200297&highlight=route+add+host)

everything works. 

Yuhu, ubuntu installed on a dedicated server ;-)

---

