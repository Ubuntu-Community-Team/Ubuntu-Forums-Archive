---
title: "very slow upload speed on 6mbit connection"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by stiankarlsen on 2007-04-01
Hi, I've got an integrated network card on my motherboard (eth0).

I plug in the ethernet cable, and I've got internet.

Ive got a 6Mbit connection, up and down - problem is that when i run different speed tests, i get my 6mbit download, but my upload is stuck at 4kb/s, which is insanely slow.

At first, i figured it to be some virus on one of the windows machines in the house, but when i do speed tests on all of them, i get 6mbit down, and 6mbit up.... basically, the ubuntu 6.10 box is the only one that doesnt work as far as upload speed goes.


Does anybode have any ideas?

---

### Post by stiankarlsen on 2007-04-02
bump

---

### Post by netztier on 2007-04-02
> **stiankarlsen said:**
> bump
[COLOR="DimGray"]
<face mode=red>
[INDENT]<RANT>
I personally consider bumping **lame** :mad:, I get the impression that the poster just wants someone else to solve his problems, hoping that someone has the magic crystal ball to glance into  and pinpoint the cause of a problem that is described very vaguely. Other people's opinion on bumping may vary, of course. Doing a "bump" whith some new info about what the poster has tried, verified, investigated, denied, confirmed, discarded in the meantime would've looked a lot different. Forums are not a "order-a-1-click-solution" service, but based on cooperation.
</RANT>[/INDENT]
</face mode=red>[/COLOR]

Back to what's on topic:

We need more information, please let us know whatever you can find out about the connection you are using.

What kind of connectivity service is this? Is it based on **LAN, WLAN, an ATM PVC or multiple parallel E1/T1 circuits**? Is it a 10 or 100Mbps LAN service and the traffic shaping/rate-limiting to 6Mpbs is done by routers enforcing some QoS policy? Is there some Tunneling involved, such as VPN, IPSec, GRE-Tunneling?

What kind of system is being used for **testing**, what kind of tests did you use? **HTTP, netperf, iPerf, Samba, NFS-mounts?** Do you have interactive access to the system at the other end of your testing tcp- or udp-connection? 

Are there any routers or **firewalls** (local ones such as firestarter included!) involved that possibly block ICMP messages (especially ICMP Type 3 code 4, "Fragmentation needed, but DF bit set") , since this would break **PathMTU discovery**. Knowing the MTU (Maximum Transmission Unit) for a given path to the destination is vital to performance! Interactive access to the system at the other side might help to determine the MTU that can actually be used to do so.

So again: please provide more information!

best regards

Marc

---

