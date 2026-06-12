---
title: "Wired Network Sleeping woes"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by bikkies on 2007-05-22
Hi there, 
I seem to be encountering a network issue with a new server I bought.  (well i bought 2 similar ones, and its only on one).

Basically, after a few minutes of network inactivity, the adapter seems to go to sleep - i can't ping into it.  When I try to ping out when this happens, the first 5 packets are dropped, and then both in and out work fine.

I've looked at my syslog, dmesg, and a little bit at the bios settings and haven't found anything obvious.

The issue happens pretty quickly -  i stopped my external from pinging the server as i started this post, and by the time i've typed to here, the issue has occurred.

I can't help but feel its something obvious that i've missed, but i'm at a bit of dead end.  any suggestions welcome.

Note: using 6.06 Server LTS with all updates, in 64 bit mode.  Have another very similar server (but not the same) setup fine and without any issues like this.

thanks, 
chris

---

### Post by bikkies on 2007-05-23
In a windows environment, it is possible to disable power management for a network device. 

I'm sure the same is possible in Ubuntu, can anyone suggest how I go about doing this?

Thanks, 
Chris

---

### Post by ibanez88 on 2007-07-19
Have you tried typing in a terminal:  ifup eth0  (or eth1 depending on your setup)?

---

