---
title: "Limiting traffic on specific ports"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by SagaciousKJB on 2007-12-23
I'm looking for a way to specify incoming and outgoing bandwidth limits for specific ports.  I looked up how to do this in shorewall ( front-end for IPtables an the Linux Kernel's QoS service that I'm using as my router ), but from reading the documentation [http://www.shorewall.net/traffic_shaping.htm#Intro](http://www.shorewall.net/traffic_shaping.htm#Intro) I'm not sure if it's what I'm looking for.

This is telling me that you can't limit the bandwidth on incoming connections, and then talks about the "maximum" bandwidth as being defined only when the link is idle.  So, is this really something I could use to say, make sure that port 80 is only using 30 kB/s of my upload pipe and ssh only 15 kB/s, or something in that scenario with this guide, or am I looking for something else?

Just for clarity, what I want to do is limit ports like 80 or 22 ( web and ssh ) to certain outgoing speeds through my linux router.  I'd like control over incoming speeds too, but I'm mostly worried about outgoing.  Is there anything I could use to limit specific ports for both incoming and outgoing packets?

---

### Post by GS2 on 2007-12-23
Have not tried this, and the document is a few years old - but could be worth a try 
[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html#AEN](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html#AEN)

---

### Post by SagaciousKJB on 2007-12-23
Hmm, that uses the same underlying features that shorewall uses.  I was kind of wondering if there was a realtime program I could use to do this.

---

### Post by work.jupiter on 2008-04-23
This is an example of the solution with Shorewall. It works well, tested.

Limit the outgoing traffic on Port 80 to 600 kilobits/s
---

I'm using Ubuntu 6.06 LTS Server ed. and Shorewall 3.0.4.

I just modified these files, without kernel conf/recomp, whithout setting env vars, without dirty tricks :)

```
#/etc/shorewall/tcrules

#MARK   SOURCE          DEST            PROTO   PORT(S) CLIENT  USER    TEST
#                                                       PORT(S)
80      eth1    0.0.0.0/0       tcp     80
80      eth1    0.0.0.0/0       udp     80
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

Explanation: MARK = class id = 80. Can be any other integer value independently of the S/D PORT. SOURCE can be an interface or an adress, as the DEST. 0.0.0.0/0 mean all.
So I specified the 80 class as "anybody connects to interface eth1 on the port 80.

```
#/etc/shorewall/tcclasses

#INTERFACE      MARK    RATE    CEIL    PRIORITY        OPTIONS
eth1    80      250kbit         600kbit         3       default
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

Explanation: On interface eth1 there is a 600 kilobits/s limit. The priority doesn't matter since this is the only limitation. The system (my machine) tries to serve at least 250kilobit/s to the clients.

```
#/etc/shorewall/tcdevices

#INTERFACE      IN-BANDWITH     OUT-BANDWIDTH
eth1            10mbit          1mbit
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

You can set here the all-available-bandwith.

Port 22 and incoming traffic limitations (SOURCE = your machine) can be configured similarly (3-3 more rows in tcrules and tcclasses).

> I'm looking for a way to specify incoming and outgoing bandwidth limits for specific ports. I looked up how to do this in shorewall ( front-end for IPtables an the Linux Kernel's QoS service that I'm using as my router ), but from reading the documentation [http://www.shorewall.net/traffic_shaping.htm#Intro](http://www.shorewall.net/traffic_shaping.htm#Intro) I'm not sure if it's what I'm looking for.

SagaciousKJB: You were looking for that after all. I constructed my config using that doc.

I hope this would be helpful.

I know it's April and 5 months passed since SagaciousKJB asked. But I think this topic wasn't closed/answered, and I just saw it today.

---

