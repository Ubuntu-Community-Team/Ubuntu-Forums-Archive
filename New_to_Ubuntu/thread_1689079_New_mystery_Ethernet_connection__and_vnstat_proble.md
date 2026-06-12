---
title: "New mystery Ethernet connection  and vnstat problems"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-02-16
Hi All,

Today I installed the latest updates from Ubuntu and restarted the machine.  After I did I noticed Conky was not showing any network activity.  I checked and I was indeed connected to the net.  I noticed that my connection was now listed as eth1-eth0.

I don't know how this happened.

```
eth1-eth0 Link encap:Ethernet  HWaddr 00:19:b9:84:0d:da  
          inet addr:85.89.80.236  Bcast:85.89.81.255  Mask:255.255.254.0
          inet6 addr: fe80::219:b9ff:fe84:dda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15591968 (15.5 MB)  TX bytes:1184941 (1.1 MB)
          Interrupt:17 
```

It had been eth0.  I do have another connection called eth1 which is my wireless and is turned off.

I was able to get Conky to display again by changing the references from eth0 to eth1-eth0.

I'd like to setup vnstat to monitor my usage but when I try to create the database for vnstat using
```
vnstat -u -i eth1-eth0
```

I get this:
```
Error: Unable to read database "/var/lib/vnstat/eth1-eth0".
Error: Unable to write database "/var/lib/vnstat/eth1-eth0"
```

I would really appreciate any help/clarification anyone could give me with this.

---

### Post by GrouchyGaijin on 2011-02-16
Update:

When I rebooted the computer this afternoon eth0 was back.

How can I make sure that vnstat runs at startup?  I seem to have to manually refresh the database with ```
 sudo vnstat -u -i eth0

```to see any changes.

---

### Post by peterintheuk on 2011-06-29
Hi Got the same problem after reinstalling 10.04.1
it used to work sorry [GrouchyGaijin]("http://ubuntuforums.org/member.php?u=1160481"), not much use to you

---

