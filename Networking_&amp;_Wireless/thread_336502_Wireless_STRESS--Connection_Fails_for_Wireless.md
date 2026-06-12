---
title: "Wireless STRESS--Connection Fails for Wireless???"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by blueprints on 2007-01-11
ok, so after trying to install my drivers manually, i picked my self up and have downgraded to dapper 6.06 and used WheelSpins script to install and load my ipw3945 drivers wich worked beautifully with no errors or anything.now my problem is getting it to connect to my network. ive tried the network settings wich shows my wireless connection and says active.ive configured everyhting i needed to as the ESSID and the WEP and still cannot connect.ive tried network manager and can see all the networks around my area plus mine but connection fails.i believe th daemen is working from this

blueprints88@blueprints88:/sbin$ ps -eaf | grep ipw3945d
root 6430 1 0 12:42 pts/0 00:00:01 /sbin/ipw3945d --quiet
1000 10980 5242 0 14:08 pts/0 00:00:00 grep ipw3945d

BUT I DONT KNOW WHAT TO DO.AND HERE IS SOME MORE INFO.

eth1 Link encap:Ethernet HWaddr 00:18E:55:43:1E
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:25210 errors:0 dropped:1092 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:169 Base address:0xc000 Memory:d6000000-d6000fff


IF ANYONE CAN HELP ME TO GET CONNECTED I WOULD APPRECIATE IT GREATLY.THANKS

---

