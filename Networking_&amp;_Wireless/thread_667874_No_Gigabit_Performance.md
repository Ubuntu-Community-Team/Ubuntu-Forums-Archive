---
title: "No Gigabit Performance"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by xgravix on 2008-01-14
I've been trying to get Gigabit connectivity with my Ubuntu server for a while and nothing seems to be working. The card in the machine is a VIA VT6120 Ethernet adapter. It works fine at gigabit speeds under windows and iPerf shows it running around 700Mbit/sec.

In Ubuntu iperf says that the link is running at 3.25 Mbit/sec which is pretty terrible. Ethtool shows the link has autonegotiated at 1000 Mbit/sec. If I force the card to 100 mbit mode speed actually improves and the link measures at around 80 Mbit/sec. Of course you cannot force 1000 mode due to the ethernet spec.

Is this a driver problem? I notice there are some other guys with cards from different manufacturers posting about the exact same problem, so I suspect it is an ubuntu or kernel bug...

I hope there is a solution because I am really liking the software RAID under linux but without gigabit connectivity that is no good. Unfortunately I cannot add a PCI gigabit card because my PCI bus bandwidth is already maxed out due to the RAID array.

---

### Post by xgravix on 2008-01-18
Here are the results of my iPerf between a Windows Vista box and  the Ubuntu, which is the best I have seen so far:

```

C:\Users\bthomson\Desktop>iperf -c 10.0.1.40 -w 2m
------------------------------------------------------------
Client connecting to 10.0.1.40, TCP port 5001
TCP window size: 2.00 MByte
------------------------------------------------------------
[108] local 10.0.1.60 port 61593 connected with 10.0.1.40 port 5001
[ ID] Interval       Transfer     Bandwidth
[108]  0.0-14.6 sec   250 MBytes   144 Mbits/sec

```

This is with nothing but a cat 6 cable directly connecting the two machines. I am expecting closer to 700 Mbits/sec for these two machines...

Anyone have suggestion for other things I can try? Tuning TCP settings mayhap? Kernel reconfigure? I have tried installing a new driver on the Ubuntu machine (kernel has 1.17 or something, latest via_velocity from via is 1.23) but it will not compile on ubuntu.

---

### Post by tgalati4 on 2008-01-18
You are getting greater than 100 Mbits/sec which is the wall for 100BaseT.  The peak spec may be 1000 Mbits/sec, but actual through put is probably 1/10 of that.  Just like the average throughput of a 100BaseT link is ~10 Mbits/sec and a 10BaseT link is ~1 Mbit/sec.  One would guess that sustained throughput for a 1000BaseT is then around 100 Mbits/sec.

If your car has a maximum speed of 165 mph (as mine does) what makes you think you can drive it that fast continuously?  Mine is governed to only go 143 mph (but it has been confirmed to be limited to 147 mph).  Am I pissed?  Not really, it was a fun ride. One test is worth a thousand expert opinions.

Your confirmed throughput speed (on your local network) is 144 Mbits/sec.  I challenge anyone to show faster results.

---

### Post by xgravix on 2008-01-18
With good cables, a good switch, and some voodoo, gigE throughput is 700Mbit/sec or higher. The theoretical maximum (actual data throughput, not real data rate) is around 900Mbit/sec so yes, there is some overhead. For instance, see these threads and many others: 

[http://ubuntuforums.org/archive/index.php/t-656343.html](http://ubuntuforums.org/archive/index.php/t-656343.html)
[http://ubuntuforums.org/showthread.php?p=4026769](http://ubuntuforums.org/showthread.php?p=4026769)

I'm getting speeds a bit better after some reconfiguration and buying a new switch, but admittedly this feels like voodoo to me...

```

C:\Users\bthomson\Desktop>iperf -t 10 -c 10.0.1.40 -w 100k
------------------------------------------------------------
Client connecting to 10.0.1.40, TCP port 5001
TCP window size:  100 KByte
------------------------------------------------------------
[108] local 10.0.1.60 port 49486 connected with 10.0.1.40 port 5001
[ ID] Interval       Transfer     Bandwidth
[108]  0.0-12.4 sec   529 MBytes   357 Mbits/sec

```

---

### Post by moonlightcheese on 2008-03-07
> **xgravix said:**
> With good cables, a good switch, and some voodoo, gigE throughput is 700Mbit/sec or higher. The theoretical maximum (actual data throughput, not real data rate) is around 900Mbit/sec so yes, there is some overhead. For instance, see these threads and many others: 

[http://ubuntuforums.org/archive/index.php/t-656343.html](http://ubuntuforums.org/archive/index.php/t-656343.html)
[http://ubuntuforums.org/showthread.php?p=4026769](http://ubuntuforums.org/showthread.php?p=4026769)

I'm getting speeds a bit better after some reconfiguration and buying a new switch, but admittedly this feels like voodoo to me...

```

C:\Users\bthomson\Desktop>iperf -t 10 -c 10.0.1.40 -w 100k
------------------------------------------------------------
Client connecting to 10.0.1.40, TCP port 5001
TCP window size:  100 KByte
------------------------------------------------------------
[108] local 10.0.1.60 port 49486 connected with 10.0.1.40 port 5001
[ ID] Interval       Transfer     Bandwidth
[108]  0.0-12.4 sec   529 MBytes   357 Mbits/sec

```

i've been researching this for a minute and got a lot of info.  the speed issues seem to do more with packet size, and MTU.  use jumbo frames (9k instead of the typical 1500) and tweak your packet size from 8192 and increment in x2 increments.  16k seems to be a sweet spot for most people and will net you 71MB/s, which seems what you're after.  i haven't tried it myself yet but i'll be applying a lot of changes to my server at the house tonight.

also, if you're using samba, change SO_SNDBUF SO_RCVBUF in the socket options setting.

edit:
oh... and post those tests backward and forward (run iperf with the ubuntu box as a server and as a client as well) and post em up.  you should see a difference without changing anything since the newer kernels have tcp autotuning turned on by default and you cannot disable it, making the ubuntu box perform faster as a client than as a server.

---

