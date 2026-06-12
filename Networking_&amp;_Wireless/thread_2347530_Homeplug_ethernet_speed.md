---
title: "Homeplug ethernet speed"
date: 2016-12-26
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2016-12-26
Folks,

Bit confused with speeds claimed by some homeplugs.

Many say they have a 10/100 mbps ethernet port but claim 500 to 1000 mbps throughput rate.

Now I appreciate these are very optimistic figures and that it apparently includes TX and RX so can be effectively halved but it still exceeds the ethernet port speed.

Anyone able to clarify this point for me please?

Geffers

---

### Post by TheFu on 2016-12-26
Ethernet-over-powerline is full of lies.  Expect 10% of the advertised bandwidth for most modern deployments that aren't in the same room. 
I have a 600Mbps powerline system with GigE ports.  In the same room, max throughput was 220Mbps.  Down the hall, it was 65Mbps. On different floors it was 48-65Mbps.  The good news is that powerline tends to be more stable network, unlike wifi. This is good for streaming.

For Gigabit powerline, I would have expected 300Mbps in the same room, but less than half that for most deployments people actually wanted. A solid 100Mbps would be very acceptable, but yes, it shows that the company knows the real-world limitations of their deployment.  I wish some lawyer would sue with class action status over false advertising so they'd have to publish/advertise realistic bandwidth, not some perfect-lab-conditions-theoritical crap that nobody with copper wiring in their home could achieve.

They are all liars.

---

### Post by Geoff_Lane on 2017-01-02
TheFu, thank you for your opinions, I too am very dubious of manufacturers claims, pictures on boxes of smiling families then when you query performance they ask 'Have you got any electrical equipment nearby', who hasn't nowadays.

I am trying to use a homeplug to move an access point away from some unavoidable electrical equipment and an ethernet cable connection using speedtest.net speed drops from 33mbps download at the router to 3.17mbps with homeplug extension. I would have expected a drop but not that much.

Ah well, experiment more.

Geffers

---

### Post by TheFu on 2017-01-02
Ah ... Have you considered using PoE for the AP?  Ubiquiti makes that really, really easy.  That way only the ethernet needs to be run to the AP device and the router can remain where it is. Plus, Ubiquiti makes some great wifi APs with amazing coverage for most homes. Their LR models are amazing. Of course, if the building has concrete walls, you'll want to stay with powerline.

I found it relatively trivial to run a PoE cable from the home office wiring closet into the attic and into the center of the house. Drilled a fairly small hole and mounted a Ubiquiti AP into the ceiling. Took about 45 min. It covers 2 floors of a 3500 sqft home and some of the yard nicely. This isn't an LR model.  I still much prefer wired - even have a USB3-to-GigE adapter for my chromebook.  There is a huge difference between 80Mbps via WiFi and 920Mbps via either CAT5e.  Just sayin'.
Wifi testing:
```
$ iperf -c hadar
------------------------------------------------------------
Client connecting to hadar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.16 port 53008 connected with 172.22.22.6 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  98.0 MBytes  82.0 Mbits/sec

```
And wired to the same server, from the same chromebook (running Ubuntu 16.04) ... 
```
$ iperf -c hadar
------------------------------------------------------------
Client connecting to hadar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.13 port 58522 connected with 172.22.22.6 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.07 GBytes   921 Mbits/sec

```
Night and day.

For powerline connections, the house wiring matters a bunch.  My house was new in 1994. All copper for power. Centralized breakers.  Older homes in this area have aluminum power lines and really older homes might have both a breaker and fuse box.  Most hops causes more signal drop, I hear.

I don't worry about speedtest results too much. My connection is only 16/3Mbps.  That's nowhere near what my LAN does.

---

### Post by Geoff_Lane on 2017-01-09
> **TheFu said:**
> Ah ... Have you considered using PoE for the AP? 

```
$ iperf -c hadar
------------------------------------------------------------
Client connecting to hadar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.16 port 53008 connected with 172.22.22.6 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  98.0 MBytes  82.0 Mbits/sec

```
And wired to the same server, from the same chromebook (running Ubuntu 16.04) ... 
```
$ iperf -c hadar
------------------------------------------------------------
Client connecting to hadar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.13 port 58522 connected with 172.22.22.6 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.07 GBytes   921 Mbits/sec

```
Night and day.

For powerline connections, the house wiring matters a bunch.  My house was new in 1994. All copper for power. Centralized breakers.  Older homes in this area have aluminum power lines and really older homes might have both a breaker and fuse box.  Most hops causes more signal drop, I hear.

I don't worry about speedtest results too much. My connection is only 16/3Mbps.  That's nowhere near what my LAN does.

I have posted another question on the forum regarding LAN speed and did ask about checking the internal speed, does the packet size have much effect on the figures regarding iperf?

Also, have tried dd if=/dev/zero bs=32 count=1048576 - what is your opinion on this?

Geffers

---

### Post by TheFu on 2017-01-09
iperf is "best case."  Real world transfers will always be slower.  For example, I usually see scp/rsync transfers of 65-78MB/s (624Mbps) between the same machines when wired.

bs=32 is small. I'd use 1-4M.

I always avoid wifi whenever possible.  Did over 1200 wifi deployments in a previous job. There are just so many things that go wrong with wifi all the time that humans don't notice, but the computers all see.  Newer wifi standards help, but none of them compare in real-life to a 100base-tx connection.  They can claim GigE and 1.4G speeds all they want. It won't happen in a house. 802.11ac and 802.11ad are great under ideal situations.  To get that sort of speed over any real distance, we need some $600-$5000 gear on each end. 

IMHO.

But I really don't know anything. Feeling a little crotchety today; sorry.

---

### Post by Geoff_Lane on 2017-01-09
> **TheFu said:**
> iperf is "best case."  Real world transfers will always be slower.  For example, I usually see scp/rsync transfers of 65-78MB/s (624Mbps) between the same machines when wired.

bs=32 is small. I'd use 1-4M.



Thanks for quick reply - I think the 'count' option of count=1048576 gave me about a 32GB throughput. Would you suggest a larger bs and a smaller count?

Geffers

---

