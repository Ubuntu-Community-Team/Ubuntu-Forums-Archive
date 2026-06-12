---
title: "strange network problem"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by philhow on 2008-01-10
I have three machines. Label them A,B,C
A=Sony Vaio with fresh Gutsy install
B=Dell desktop with XP running ethereal network capture 
C=HP laptop with XP
Machines B&C work fine, I'll just use them to illustrate the problem
No wireless is involved. It's all wired networking.

Network setup on A is roaming off, static IP

With A hardwired to B (no hub/switch/router), I can use A to ping B. B captures the ARP and Ping request/replies

With A wired to B through a Hub (repeater, not switch), if I use A to ping B, B captures no traffic. The activity LED on the port connected to A blinks, the activity LED on the port connected to B does not.

Remove the cable from A and plug it into C, then use C to ping B, and B captures all the appropriate traffic.

It would seem that the first test shows that A is configured correctly. The last test seems to show that the Hub and cables are OK. So why does the test in the middle not work?

I've tried this with different cables, different ports on the hub, and different hubs (although the other one was a switch, not a repeater).

Anyone have any ideas? This is a problem because in order to connect to the Internet, I have to go through a hub. Since the Ubuntu machine can't seem to make it through a hub, I can't connect to the Internet.

---

### Post by stalker145 on 2008-01-11
> **philhow said:**
> I have three machines. Label them A,B,C
A=Sony Vaio with fresh Gutsy install
B=Dell desktop with XP running ethereal network capture 
C=HP laptop with XP
Machines B&C work fine, I'll just use them to illustrate the problem
No wireless is involved. It's all wired networking.

Network setup on A is roaming off, static IP

With A hardwired to B (no hub/switch/router), I can use A to ping B. B captures the ARP and Ping request/replies

With A wired to B through a Hub (repeater, not switch), if I use A to ping B, B captures no traffic. The activity LED on the port connected to A blinks, the activity LED on the port connected to B does not.

Remove the cable from A and plug it into C, then use C to ping B, and B captures all the appropriate traffic.

It would seem that the first test shows that A is configured correctly. The last test seems to show that the Hub and cables are OK. So why does the test in the middle not work?

I've tried this with different cables, different ports on the hub, and different hubs (although the other one was a switch, not a repeater).

Anyone have any ideas? This is a problem because in order to connect to the Internet, I have to go through a hub. Since the Ubuntu machine can't seem to make it through a hub, I can't connect to the Internet.

From the sound of it... Are you using straight-through cables or crossovers? Unless things have changed, which they may have, you need to have a crossover to communicate directly PC to PC. Hubs, being simple pass-through, would be causing the signal sent on the TX side of the cable to be delivered to the TX side of the recipient's network card if you were using a crossover with the hub.

I would advise you check each end of your cables to make sure the colors match on both ends. It sounds simple, but it's a classic mistake.

Or maybe your hub's bad...

If that's not the issue, please check back and consider my post a bump ;)

---

### Post by philhow on 2008-01-11
The Sony VAIO appears smart enough to handle straight through or crossover. I've tried both types of cables and I get link in either case. I also get same symptoms in either case.

This morning I wired the Sony direct to my DSL Modem/Router and it was able to see that (same as hardwired to another PC without an intervening hub). I used that connection to perform all updates and install wireshark. Updates all installed fine. Rebooted, everything was fine. Rewired so everybody (machines A,B,C, plus router) were all connected via a switch. The sony went back to not talking to anyone.

With Ethereal/Wireshark running on both machines A and B I tried pinging A from B. On B (the XP box) I saw the ARP requests. On A (the sony) I saw the ARP requests and replies. On both machines I saw random other traffic (various other ARP requests, etc.)

I switched from crossover cable to straight through on the Sony (machine A), rebooted it and observed the same thing.

It appears that when connected directly, I can send and receive. When connected to a hub, I can receive but not send. 

It could be that one set of pins/drivers is bad in the Sony except that when I switch from crossover to straight through cable, I'm using the opposite set of pins. 

Any new ideas?

---

