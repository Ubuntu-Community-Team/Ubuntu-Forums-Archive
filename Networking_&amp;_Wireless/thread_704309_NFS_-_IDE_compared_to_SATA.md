---
title: "NFS - IDE compared to SATA"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by notwen on 2008-02-22
I have a Debian Etch box running NFS and currently sharing 3 SATA HDDs(250GB x2 & 320GB).  I have acquired a freebie IDE 750GB HDD.  I was wanting to move the majority of my music over to the IDE HDD from 2 of the SATA HDDs, but was concerned w/ streaming music from the IDE HDD over NFS.  Would I see a hit in performance as far as streaming files(mainly mp3s) from the IDE HDD?  I would like to free up my SATA HDDS for bigger files such as xvid/divx, isos and general backups.

---

### Post by dca on 2008-02-22
I've never seen any performance differences w/ either HDD technology (when used in a RAID)  because most of the performance was based on the RAID itself...
 
RAID-0 is the fastest because it's based on two drives hammering data.  The problem is there's no failsafe if one of the drives conks out. Te info is striped across both...
 
RAID 1 & 5 is what I use depending on how many HDD(s) the server has avail to it, RAID1 can do 2 or more, RAID5 three or more...
 
Again, even if it's something as low level as a media storage device (versus mission critical app server or db server) I'm always concerned about data loss, there's no way in hell I'm gonna' spend all that money again on iTunes...

---

### Post by notwen on 2008-02-22
> **dca said:**
> Again, even if it's something as low level as a media storage device (versus mission critical app server or db server) I'm always concerned about data loss, there's no way in hell I'm gonna' spend all that money again on iTunes...

Agreed.  I backup most everything using mondo every 3 weeks or so.  Thanks for your thoughts.  =]

---

