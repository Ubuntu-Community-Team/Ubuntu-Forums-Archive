---
title: "I want to upgrade but wireless doesn't work"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by startling on 2008-04-21
I've been running Feisty for a while. When Gutsy was released I tried the live cd but it couldn't find my wireless router so I thought I'd wait for Hardy. I just tried the live cd of the latest release candidate (19 April) and the same thing has happened - it can't find the router.

I put the same live cd in a different machine in the office and it found the network after I had entered the SSID, but that does not work in this machine although Feisty finds  the network with no problems.

---

### Post by startling on 2008-04-24
Sorry to reply to my own thread, but since I've had no replies I wonder if my post is missing something? Should I post more information?

Also, I wonder if this is connected: I tried to connect to a different wireless network yesterday but Feisty failed to do so. Booting into Vista (bah!) on the same machine worked instantaneously.

I don't if it helps but Device Manager reports my network connection as an Intel Pro/Wireless 3945 ABG.

---

### Post by startling on 2008-05-28
I'm surprised that there have been no replies to this. Am I doing something wrong or not posting properly?

In case it's helpful, here's some more information: I ran ifconfig eth1 and got what looked to me like a large amount of errors:
          RX packets:13300 errors:4680 dropped:7530 overruns:0 frame:0
          TX packets:5514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17621960 (16.8 MiB)  TX bytes:2213427 (2.1 MiB)
          Interrupt:18 Base address:0xe000 Memory:f0800000-f0800fff 

Is that right? 

I'm sorry to reply to my own thread but I'd really appreciate any pointers to finding a solution. A couple of times recently I've been singing Ubuntu's praises to people, and show it running on my laptop, but when it can't connect to the Internet and I then have to boot into Vista, which works immediately, it's a bit of a shame.

Finally, and perhaps this should be a new thread, but sometimes the LAN fails to appear in Network > Places. The only solution I know is to wait a few minutes or so then try again, and sometimes a few times after that until eventually the Network appears. I find that odd, but haven't a clue how to troubleshoot it.

---

