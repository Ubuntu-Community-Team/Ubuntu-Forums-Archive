---
title: "Best way to access Freenas server from Ubuntu?"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by kaffemonster on 2007-09-25
I have set up a Freenas server made from an old desktop pc, and now I am connecting to it via SMB - But is that the best way to do it? Is there another protocol with better performance?

I'm running Ubuntu 7.10 on my laptop btw :)

---

### Post by netztier on 2007-09-25
> **kaffemonster said:**
> I have set up a Freenas server made from an old desktop pc, and now I am connecting to it via SMB - But is that the best way to do it? Is there another protocol with better performance?

I'm running Ubuntu 7.10 on my laptop btw :)

My experience with FreeNAS a few months ago was that Samba was horribly slow (2-3 Mbyte/s) while NFS was poor (8-9MByte/s). You might want to try NFS instead of Samba.

Running Ubuntu 6.06LTS, the very same machine [1]  delivered ~15MByte/s with Samba (read and write).  NFS reads were around 30MByte/s (sustained) from the RAID, with peaks of >60MByte/s when serving from cache, but NFS writes were a lot slower.

I don't know if FreeNAS has improved performance-wise since. I was however impressed by its fast startup and that it instantly recongnised my Adaptec RAID controller and it's array, and the Web based GUI is very comfortable.

best regards

Marc


[1]  P-III 500Mhz, 512Mbyte RAM, Intel Gigabit NIC, mix of IDE Disks and  Adaptec 2100S RAID controller with 128MBytes of cache with a 6x36gig RAID10 in an external box.

---

