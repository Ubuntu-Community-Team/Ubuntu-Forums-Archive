---
title: "Slow throughout"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by rbrugman on 2005-10-25
Hello,
I'm having trouble with Ubuntu/Linux in general, not only Breezy.  I have a server with a Netgear 10/100 NIC.  On the switch it's connected to, the 100Mb/sec light is on, but the actual throughput of the server is much lower, maybe only 20-30% that at best.  I'm wondering if it's the NIC or if it's the hard drive having to pull the data.  The server is 1.4Ghz with a gig of ram, but it takes about 30 minutes to transfer a DVD image off it.  Can someone help me!

Thanks,
Robert

---

### Post by mlomker on 2005-10-25
Your disk is the limitation if it is a single drive.  One of my expensive HP file servers with a terabyte+ RAID array tops out at about 130 Mb.

You'll get about 20-30 Mb per physical drive until you hit the bandwidth limit of your bus (PCI, whatever).

---

### Post by rbrugman on 2005-10-25
So in essence it's not even worth upgrading my house to Gigabit ethernet in the future, unless I upgrade my drives to those nice 2.0Gb/sec SATA ones.  That would require a new motherboard :(   I guess I'll stick to waiting 30 minutes to transfer a DVD image.

---

### Post by mlomker on 2005-10-26
> So in essence it's not even worth upgrading my house to Gigabit ethernet in the future,

I wouldn't bother.  We use Gigabit to connect our buildings and the utilization on that backbone link averages 5%.

The next 'cool thing' is 100 Mbit wireless.   Since wireless only gets at best half of the advertised speed with errors/encryption/bandwidth sharing the speed improvements there will make a real difference.

---

