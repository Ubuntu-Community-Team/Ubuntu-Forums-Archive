---
title: "Samba suddenly slower"
date: 2015-07-08
forum: Networking &amp; Wireless
---

### Post by Roy_Wesseling on 2015-07-08
Hello,

My samba transferspeed suddenly dropped to 1-2MB/s. It was 11MB/s. That's the max the network should transfer with. 
But on my server the speed dropped and on my laptop the speed dropped too. Does anyone have the same issue? 
It happened with Ubuntu 14.04.02LTS and 15.04 (?).
The transfer speed from HDD to HDD is 100MB/s

So that couldn't be it..

Does anyone have some advice?

Thanks in advance!

---

### Post by Daniel_Pinel on 2015-07-16
Did you try to reset your network connection on the server/laptop and reset the router?

---

### Post by tgalati4 on 2015-07-17
Unplug any other machines from the network and measure the speeds again.  You want to make sure it's not a broadcast storm that happens when you have several machines all advertising shares (bonjour, avahi, etc).

Also, make sure the share is mounted via /etc/fstab and not Nautilus.  For some reason shares connected with Nautilus can be really slow--perhaps user access control or something else.  You see a lot of discussion on the forums about slow SAMBA performance, but few real solutions.

Install *iperf* on both machines and run some metrics.  You can search the forums for examples of ways to use *iperf*.

---

