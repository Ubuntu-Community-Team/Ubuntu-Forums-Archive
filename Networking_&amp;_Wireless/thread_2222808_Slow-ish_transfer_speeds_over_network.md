---
title: "Slow-ish transfer speeds over network"
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by BigTobster on 2014-05-08
Hi

I am transferring some files over my network using the Python SimpleHTTPServer

```
python -m SimpleHTTPServer
```

The server is a mediocre, 4-5 year old machine AKA David. I don't have the exact specs to hand but it was bargain bucket in 2009 :) 

The client is a big powerful monster of a machine. Big games rig. AKA Goliath.

The router has a theoretical transfer speed of 300Mb/s. It's a TP-Link TL-WR841N.

My actual non-concurrent download speed is ~ 4Mb/s.

This isn't really my area and I was wondering if anyone can explain why this is? All connections are via Ethernet cable. David is connected via Ethernet. Goliath is connected via Ethernet to a Powerline Adapter which in turn is Ethernet connected. Over wireless, I am getting ~1.5Mb/s.

I'm not expecting the full theoretical maximum but surely better than 4Mb/s? Is there anyway to improve this? Why am I getting such a slow connection?

Thanks

---

### Post by TheFu on 2014-05-08
Simplify the network to troubleshoot.  Both systems directly connected to the same router. What does **iperf** show?
Add in 1 more complication and test again with **iperf**.  Still good or slow now? If slow, you've just found the issue.

The protocol used matters tremendously - is this pure HTTP?  Is nginx faster than python?

Simplify and test.  Keep careful notes for every config change, test again.  Keep going until the problem it caused.   Oh ... and wifi can never really be controlled unless you live alone, in the center, of a 3 acre plot + turn off/unplug all household 2.4Ghz and 5.8Ghz devices and the microwave.

Oh ... and are you certain this is Mb/s or MB/s?

---

### Post by BigTobster on 2014-05-08
Thanks for the response.

I didn't even know iperf existed. Thanks! That's awesome :)

In regards to the protocol, it was pure HTTP. Using wget on a local web server. Not willing to mess around with nginx just for that but thanks the hint anyway :)


I did as you suggested and then worked backwards.


The powerline adapter was knocking about 20% throughput off the connection. On a straight through was getting only a few MB/s from the routers theoretical maximum 


On Wireless, the connection was getting battered. Over halved by moving up stairs. Not exactly surprising but still interesting.


A fun exercise is to use wget on a big file/iperf and then run around the house with your laptop and watch what happens. HOURS of fun.


Working backwards I then ironed out a few issues. Mostly, my issues concerned me misreading MB/s and Mbps. You must have sensed that I'm stupid :)
Human failure. The most common and troublesome computer fault!




I'm solved. Thanks TheFu :D

---

### Post by TheFu on 2014-05-09
I learned the same stuff you just learned, in the same way. We are all stupid, sometimes. ;)

Programmers tend to report MB/s. Network and disk devices tend to report Mb/s. It is the way of each different world. We have to recognize the difference and do the conversions.

Wifi sucks. People **think** it is stable, solid, but it isn't.  I've done over 1200 wifi deployments and learned that wifi is fine for light traffic, but not-so-good when a solid, stable, connection is required. There are too many things that interfere with the bandwidth which are outside our control. Just remember that wifi specs are 50% off.  A rule of thumb is that for every wifi device connected to the network, the bandwidth is 50% less - **for every device**.
100 --> 50 --> 25 --> 12.5 --> 6.25 --> 3.125 ..... you get the idea. Web surfing at 3.125Mb/s isn't bad, but streaming a hidef video sucks. Stay wired.

---

