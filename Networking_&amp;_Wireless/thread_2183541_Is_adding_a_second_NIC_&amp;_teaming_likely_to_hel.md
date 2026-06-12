---
title: "Is adding a second NIC &amp; teaming likely to help this?..."
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by leezer32 on 2013-10-25
OK, so please bear with me a tad....
I have a server/ download box- It's a mid-end Core2 box with 8tb worth of drives and the usual bits and bobs running, including backups for all machines on the LAN, video serving etc.

Lately, I've been finding that the network speeds are slowing to a crawl when there's a large amount of stuff going on- The most recent of these had these running:
* Backuppc (No idea of bandwidth)
* Media stream to second PC
* 7mb/s internet download
* About 40 torrents seeding, 400kb/s ish upload

I then attempted to copy a file to one of the network shares, and I was seeing ~6MB/s, rather than the expected ~50MB/s with nothing else running. 

From what I can see, I'm basically running out of bandwidth, and everything grinds to a halt :)
What I'm not clear on is whether adding another PCI-E gigabit NIC and setting up basic round-robin scheduling is likely to help matters at all. 
Everything goes to different drives, and they're strung off a mixture of Intel ACHI ports and a HP-P410 RAID card, so I don't think I'm hitting drive or system bus limitations, but rather something in the network.

Router is a Linksys gigabit model running Tomato.

Thoughts?

---

### Post by tgalati4 on 2013-10-25
You might need to upgrade to a server-grade router/switch.  When the router itself saturates internally, there is little you can do.  Just because it says gigabit on the box does not mean you get gigabit throughput on each port AT THE SAME TIME.

You have to spend a lot more money for server-grade performance.  Adding another network card would just make the situation worse.  How is the quality of the wiring?  Did you hand-crimp the wires yourself?  Are you using at least Cat-6 (or Cat-6a) throughout?

Run *iperf* from different endpoints to validate your current setup.

---

### Post by leezer32 on 2013-10-25
Yeah, it's rather difficult to validate where exactly the bottleneck is, hence why I was posting here :p 

To be exact, the router is a WRT-320N, running a late January build of Shibby's Tomato. With several things going at once, I'm not seeing stupidly excessive router CPU usage there; Is there a better way to measure than that?
All cabling is decent quality CAT5-E, some premade, some terminated with a Krone tool & some hand-crimed.
Both the desktop and the server are direct cabled into the router, the rest of the network runs off several 8-port D-Link unmanaged gigabit switches. Haven't gone jumbo frame due to the Raspberry Pi's :)

iperf gives a relatively consistant bandwidth of 930- 940 Mbits/ Sec from everything except a Raspberry Pi (I'm presuming it's a case of cruddy CPU there) in each direction with the default settings with nothing else running.

---

### Post by houstonbofh on 2013-10-26
First, forget nic teaming to that router.  You need to set up LACP on both ends...

Second, you need to find the bottleneck before you fix it.  Bit torrent can slam a system with IO far before a nic is full.  You will need some kind of monitoring program to see what is flowing over the nic, if the CPU is slammed, disk IO and so on...

---

