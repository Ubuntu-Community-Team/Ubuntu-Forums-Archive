---
title: "trying to share files in home ubuntu LAN"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by curl1 on 2008-11-23
Two computers running Ubuntu, connected to a router. 

Trying to backup laptop (7.10) to desktop (8.04), before upgrade. SSH is way too slow (we're talking days, seriously). Samba and NFS are seemingly impossible to set up. 8.04 just does not see these on the Network. 

Used various how-to and online guides. I've spent far too much time on this. ](*,) 

What happened to 'it just works'?

---

### Post by nixscripter on 2008-11-23
I use NFS and flexbackup (a package for incremental backups) regularly, and just let it run overnight. On a switched network (10 Mbps), 10 GB finishes by morning for a full backup. Also, it will do incrementals, so you don't have to do an entire backup every time.

If you don't like NFS, try just using rsync. Again, it does incremental transfers, meaning you only have to spend days on it once.

---

### Post by DGortze380 on 2008-11-23
> **curl1 said:**
> Two computers running Ubuntu, connected to a router. 

Trying to backup laptop (7.10) to desktop (8.04), before upgrade. SSH is way too slow (we're talking days, seriously). Samba and NFS are seemingly impossible to set up. 8.04 just does not see these on the Network. 

Used various how-to and online guides. I've spent far too much time on this. ](*,) 

What happened to 'it just works'?

First things first. Can you ping between the machines? Laptop to desktop and desktop to laptop?

---

### Post by curl1 on 2008-11-24
Thanks for your time to reply. 

After switching both machines' Firestarter off (probably not needed to begin with), was able to ping successfully in both directions and subsequently use Samba.  

The slow transfer speed was due to wireless connection, which for 12GB was estimated at two days! Succeeded using an ethernet cable in less than two hours. SSH would have been just as quick.  

Incidentally, in 7.10's Shared Folders (System/Administration) it is easier to see all the shares (and I'd set up a few in previous attempts) than in 8.04. Shame it is not still there in the later version, as it's difficult to find and delete the failed shares set up on that machine. 

Back to being a happy Ubuntu user again :)

---

