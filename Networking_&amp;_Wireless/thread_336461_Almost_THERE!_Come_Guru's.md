---
title: "Almost THERE! Come Guru's"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by blueprints on 2007-01-11
ok, so after trying to install my drivers manually, i picked my self up and have downgraded to dapper 6.06 and used WheelSpins script to install and load my ipw3945 drivers wich worked beautifully with no errors or anything.now my problem is getting it to connect to my network. ive tried the network settings wich shows my wireless connection and says active.ive configured everyhting i needed to as the ESSID and the WEP and still cannot connect.ive tried network manager and can see all the networks around my area plus mine but connection fails.i believe th daemen is working from this

blueprints88@blueprints88:/sbin$ ps -eaf | grep ipw3945d
root      6430     1  0 12:42 pts/0    00:00:01 /sbin/ipw3945d --quiet
1000     10980  5242  0 14:08 pts/0    00:00:00 grep ipw3945d

BUT I DONT KNOW WHAT TO DO.AND HERE IS SOME MORE INFO.

eth1      Link encap:Ethernet  HWaddr 00:18:DE:55:43:1E
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:25210 errors:0 dropped:1092 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0xc000 Memory:d6000000-d6000fff


IF ANYONE CAN HELP ME TO GET CONNECTED I WOULD APPRECIATE IT GREATLY.THANKS

---

### Post by Paerez on 2007-01-11
Does it show up in System->Administration->Networking?

---

### Post by blueprints on 2007-01-11
yes it does.and when i try to connect,it says conection fails.i believe everyhting is correct im jsut missing a step....

---

### Post by spd106 on 2007-01-11
Does it associate with your AP?

Try **iwconfig**, or maybe start **iwevent** then open a new tab and try **sudo ifdown eth1** followed by** sudo ifup eth1**.

---

### Post by blueprints on 2007-01-11
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:"2wire584"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2468   Missed beacon:0


thats what i get with iwconfig
and ive tried the sudo down and up thing with the same results.
and when i iwevent i get this
Waiting for Wireless Events from interfaces...



any other idea?

---

### Post by Paerez on 2007-01-11
what does:

```
$ sudo iwlist eth1 scanning
```

produce?

---

### Post by blueprints on 2007-01-11
eth1      Scan completed :
          Cell 01 - Address: 00:13:10:B5:83:22
                    ESSID:"HomeRouter"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=20/100  Signal level=-86 dBm
                    Extra: Last beacon: 1436ms ago
          Cell 02 - Address: 00:0C:41:C0:30:8D
                    ESSID:"sandie"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=42/100  Signal level=-75 dBm
                    Extra: Last beacon: 1420ms ago
          Cell 03 - Address: 00:12:88:3E:C6:C9
                    ESSID:"2WIRE584"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              22 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-45 dBm
                    Extra: Last beacon: 1452ms ago
          Cell 04 - Address: 00:11:50:26:38:7F
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=2/100  Signal level=-94 dBm
                    Extra: Last beacon: 4800ms ago
          Cell 05 - Address: 00:09:5B:85:8B:AA
                    ESSID:"Turner2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=11/100  Signal level=-90 dBm
                    Extra: Last beacon: 1420ms ago



i know this means its working,and it shows my router,but i just cant connect

---

### Post by Paerez on 2007-01-11
make sure to connect to the ESSID 2WIRE584 not 2wire584, it is case sensitive.

---

### Post by blueprints on 2007-01-11
Nice,i think it works nice, because on my connection properties,i have full signal strength wich i didnt before and now i am sending and receiveing packets,but got one problem,it still doesnt connect to the internet.when i type in [www.yahoo.com](www.yahoo.com) it looks like its trying to connect but doesnt do anyhting then that? what is going on now? thanks alot for the info before,i am SO CLOSE NOW :)

---

### Post by blueprints on 2007-01-11
also my packets being sent is around 48 compared to my receiving packets wich are aorund 5000

---

### Post by Paerez on 2007-01-11
now what does "ifconfig eth1" say?

---

### Post by blueprints on 2007-01-11
eth1      Link encap:Ethernet  HWaddr 00:18:DE:55:43:1E
          inet addr:192.168.x.xx  Bcast:192.168.x.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe55:431e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8587 errors:309 dropped:3011 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:777196 (758.9 KiB)  TX bytes:9505 (9.2 KiB)
          Interrupt:169 Base address:0xc000 Memory:d6000000-d6000fff


and this is when i am back with my wired connection

---

### Post by blueprints on 2007-01-11
can ANYBODY help???????

---

### Post by Paerez on 2007-01-11
what happens when you "ping google.com"?

---

### Post by blueprints on 2007-01-11
its all good, for some reason when i rebooted,it started working like a whip.its even faster then my ethernet card :) thanks for all the help

---

### Post by Paerez on 2007-01-11
sweet. Have fun.

---

