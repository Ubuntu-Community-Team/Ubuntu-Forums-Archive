---
title: "Bufferbloat reduction?"
date: 2015-11-24
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2015-11-24
Is it possible to improve bufferbloat on ubuntu 14.04 desktop amd 64?

*The Bufferbloat project has largely addressed latency associated with too much buffering in routers. The CoDel and fq_codel algorithms are the first fundamental advance in the state of the art of network Active Queue Management in many, many years. These algorithms have been deployed in millions of computers, and reduce the induced delay from competing traffic on a bottleneck link to the order of 20 msec.*

My bufferbloat is at F (>400ms)  according the speedtest I have just run with DSL Up at 18.94 and down 964.7

I searched to find more informaton on codel and ubuntu. Found [http://manpages.ubuntu.com/manpages/raring/en/man8/tc-fq_codel.8.html](http://manpages.ubuntu.com/manpages/raring/en/man8/tc-fq_codel.8.html) and tried to make command line changes in line with the examples  but failed:

tc qdisc add   dev eth0 root fq_codel
RTNETLINK answers: Operation not permitted
 
and then tried
 tc qdisc add dev eth0 root fq_codel limit  2000  target  3ms  interval
Command line is not complete. Try option "help"

I would appreciate some help on making changes to improve the bufferbloat.

---

### Post by richard-e-brown on 2015-11-27
There are two problems: 

1) The commands aren't entered properly. Looking at the tc-qdisc_fq_codel man page at: [http://manpages.ubuntu.com/manpages//trusty/man8/tc-fq_codel.8.html](http://manpages.ubuntu.com/manpages//trusty/man8/tc-fq_codel.8.html)

[LIST]
[*]The tc command needs to be run as root - use sudo tc ...
[*]The second command is incomplete - the example on the man page has a line break that leaves it incomplete. It should be:
[/LIST]
[FONT=courier new]   tc qdisc add dev eth0 root fq_codel limit  2000  target  3ms  interval 40ms noecn

[/FONT]2) Turning on fq_codel in your computer may not solve your bufferbloat problem, since it needs to be fixed in the bottleneck link of your network. Even after you fix it in your Ubuntu box, your router (and maybe your cable or DSL modem) may be bloated (and they almost always are). To learn more, check out What to do about Bufferbloat at [http://www.bufferbloat.net/projects/cerowrt/wiki/What_to_do_about_Bufferbloat](http://www.bufferbloat.net/projects/cerowrt/wiki/What_to_do_about_Bufferbloat)

---

