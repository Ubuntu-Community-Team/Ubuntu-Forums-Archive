---
title: "[Satellite]Need clarification on TCP parameters"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by CyberOli on 2008-11-12
Hello guys, 

i am quite new in the Linux world so i may ask some stupid questions and i apologize for that in advance ;). 

Let me put the context first: I work in satellite engineering and right now i have to set up a monitoring system in order to check at any time the link availability (bandwidth, IP communication, RF status and so on...). To monitor the link i use a local PC (with Ubuntu 7.04) straight connected to a sat modem.

As you probably know, TCP is not initially designed for high latency network such as satellite. So i have to change some TCP parameters to get the max out of the satellite link.  I don't have problems with that since i succeeded in getting that working. 

Where i do have a problem is in the understanding of the different parameters! 

**/proc/sys/net/ipv4/tcp_mem** --> what's that? Accordig to some source i found it is used to define the min, default and max TCP window size. Until there no problem but then waht's the utility with the value **/proc/sys/net/core/tcp_rmem** 

Same question for **/proc/sys/net/ipv4/tcp_wmem** and **/proc/sys/net/core/tcp_wmem**?

Other thing: i don't get what's **/proc/sys/net/ipv4/tcp_mem**. I have found some explanation on the net saying that it defines the memory allocation for TCP sockets but i don't see how it can have a impact on the upper protocol using TCP (i did several tests and i didn't see the difference). 

Can someone help me clarifying my mind on this. 

In advance thank you!

---

### Post by CyberOli on 2008-11-12
Ok,

i found my happiness : [http://www.acc.umu.se/~maswan/linux-netperf.txt](http://www.acc.umu.se/~maswan/linux-netperf.txt)

Thanks to everyone :D ;).

---

### Post by iponeverything on 2008-11-12
I am glad you found your happiness.  I am still a bit confused though.

Say you have 550 ms latency, so to compensate you send really big packets. Does the satellite modem encapsulate all the traffic before shooting it off into space?  What's the overhead?

---

### Post by CyberOli on 2008-11-13
The TCP segments are the same. The modem is a layer 2 component, so it doesn't change anything to TCP (layer 4). We don't change packet size. IF you do so you will create fragmentation and the only outcome you will get is a throughput decrease. The problem is that TCP has not been designed for high latency link due to its window and its acks. We have to configure the windows such a way it sends a lot of packets before getting acks. If you don't do that then you lose a lot of time before the last packet you sent and the frist ack you receive of your current window. During that time the sender stop sending and as so you don't use your channel anymore and of course, you loose bandwidth. So we have to enlarge the windows depending on the latency and the available bandwidth of your channel in order to always occupy the channel

B = TCPw/RTT

where B is the throughput of your channel (bits), TCPw the size of your windows (bits) and RTT the delay between the sent packet and the received ack to it (s).

By th way i still don't get the **/proc/sys/net/ipv4/TCP_mem** 

PS: Yes the modem use MPEG2 frame, it is a DVB-RCS modem.

---

