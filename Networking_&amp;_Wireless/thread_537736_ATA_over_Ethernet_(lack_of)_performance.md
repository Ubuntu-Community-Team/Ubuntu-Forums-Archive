---
title: "ATA over Ethernet (lack of) performance?"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by javahollic on 2007-08-29
Hi All,
I've just got aoetools all setup and a bit underwhelmed by throughput.

Server end is brand new dual dual-core, 8G ram, RAID, Gigabit etc.   With  'hdparm -t' I get 114MB's .  I get around 45MB/s for FTP transfers.  An NFS copy gives 29MB/s.

My exported aoe partition comes from an LVM group, its exported as aoe, and mounted remotely via a single gigabit switch, non-raid single core machine.  Here its created as part of a separate LVM group and has been formatted with reiserfs (as all the file-systems in these tests were).  

Everything seems to be OK, if I do a 'hdparm -t' on the mounted LVM logical volume created in a volume group containing a aoe device, I get a buffered read of 58.54MB, but non buffered reads fail with "Inappropriate ioctl for device".

Doing a file copy to such a mounted partition, yields a throughput (registered on the server) as being ~6MB per second. SIX :mad:

Im sharing the network with IP traffic but there isn't much going on.  Whilst I was doing the 'aoe' file copy test, I ftp'd a 2G file and saw network utilisation go up, throughput reaching 30-50MB/s.  Its related to aoe, not the network.

So, it appears to work but the perfmance is poor, has anyone had experience of aoetools and got more throughput.  

I don't know where to go next with this :(

---

