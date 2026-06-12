---
title: "NFS slower than a 1 legged dog on tranquilizers"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Ubuntiac on 2008-01-16
OK I've just set up NFS (for a precise, step by step of what I did see my post at [http://ubuntuforums.org/showthread.php?t=668962](http://ubuntuforums.org/showthread.php?t=668962)).

Now it transfers only a few k a second, and even that is in a single burst every 60 seconds or so with just stalling inbetween.

Any ideas anyone?

---

### Post by amo-ej1 on 2008-01-16
Yeah, don't use NFS ;), nfs is notorious for having problems. Why is it that you _need_ NFS ?

---

### Post by Ubuntiac on 2008-01-16
Ironically because I need a fast network. When set up right, people seem to get speeds double what Samba offers and we shift a lot of very large video files (in the gigabytes)

---

### Post by netztier on 2008-01-16
> **Ubuntiac said:**
> Ironically because I need a fast network.

Then you should test the network first, without NFS nor samba, but raw TCP. Install iPerf from the universe repositories on both server and client computer and test it in both directions, swapping iPerf server (=receiver) and client (=sender) roles.

With good NICs and their proper drivers, good cabling and a reasonable gigabit switch, you should get more than 300Mbir/s in any case.

On FastEthernet, you should get 95Mbit/s.

If speeds keep crawling in the low kbit/s ranges, we should investigate half/full duplex problems. Configuring fixed speed and duplex is more often a bad idea than a good one. As long as you can't configure both ends of a stretch of cable, you should never do this.

regards

Marc

---

