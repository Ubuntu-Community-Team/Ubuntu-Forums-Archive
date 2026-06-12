---
title: "Best file system for SSD?"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Hospadar on 2009-05-01
Does anyone know of any good references on what the best filesystem is (ext3, xfs, etc, etc) for an SSD (mainly, which filesystem has the fewest writes)

Also I was looking around for references on how to relocate/remove high-write areas like /var/log somewhere else (like /dev/null) to prevent unnecesary writes.

Thanks

---

### Post by ddrichardson on 2009-05-01
I'm using ext3 but setting the noatime option, I've also put a bunch of things in tmpfs to reduce writes. I'd prefer non-journaled and have had good experiences with XFS, I was using ext3 on an SD card but it had problems with resume and I found XFS didn't.

---

### Post by ddrichardson on 2009-05-01
Meant to say, here's fstab entries for three high write offenders:
```
none                   /var/log      tmpfs     defaults,size=10M   0      0
none                   /tmp          tmpfs     defaults,size=100M  0      0
none                   /var/tmp      tmpfs     defaults,size=20M   0      0

```
You might want to look at what Firefox does too - it accesses the disk a lot because of the sqlite dbases its using.

---

### Post by FlyingBuzz on 2009-05-01
I don't think that you have to take care about it so much. SSD works fine with ext4 for me.
Do you know how much read/write operations can it perform? Their amount is HUGE.

---

### Post by ddrichardson on 2009-05-01
Its not just the write cycles, with things like the Aspire One because SSD reads very quickly but writes very slowly it can become a bottleneck and its very effective to tune the amount of disk writes.

---

### Post by lavinog on 2009-05-01
> **ddrichardson said:**
> Meant to say, here's fstab entries for three high write offenders:
```
none                   /var/log      tmpfs     defaults,size=10M   0      0
none                   /tmp          tmpfs     defaults,size=100M  0      0
none                   /var/tmp      tmpfs     defaults,size=20M   0      0

```
You might want to look at what Firefox does too - it accesses the disk a lot because of the sqlite dbases its using.

do you sync your logs or just purge them on reboot?

---

### Post by misfitpierce on 2009-05-01
I would prob say EXT3 but to me imo I'd use EXT3 on any device... I love that format the best, seems to work out the best overall for me so.

---

### Post by blueridgedog on 2009-05-01
> **Hospadar said:**
> Does anyone know of any good references on what the best filesystem is (ext3, xfs, etc, etc) for an SSD 

Well, when setting up my netbook, I used ext2, no swap space and am thinking about tmpfs for Firefox's cache.

---

### Post by ddrichardson on 2009-05-01
@lavinog: I Purge them on this one, rsync them on my main (non-testing system) along with my Firefox profile which _really_ benefits from tmpfs on the Acer Aspire One.

---

### Post by ddrichardson on 2009-05-01
> **blueridgedog said:**
> Well, when setting up my netbook, I used ext2, no swap space and am thinking about tmpfs for Firefox's cache.
I've done it, using rsync to save it before exit and it makes a big difference - no stuttering on the Aspire One.

---

### Post by Paqman on 2009-05-01
> **ddrichardson said:**
> Meant to say, here's fstab entries for three high write offenders:
```
none                   /var/log      tmpfs     defaults,size=10M   0      0
none                   /tmp          tmpfs     defaults,size=100M  0      0
none                   /var/tmp      tmpfs     defaults,size=20M   0      0

```
You might want to look at what Firefox does too - it accesses the disk a lot because of the sqlite dbases its using.

There's a nice little walkthrough for all that lot [here]("http://www.brighthub.com/computing/linux/articles/9170.aspx").

Tbh, i've taken to doing it even though I use a magnetic drive, just for something to do with my RAM.

Limited writes is really only a problem on the older or cheaper SSDs anyway. If you've got one of the proper 2.5" drives (eg:OCZ or Intel) then I wouldn't worry about it too much. The wear leveling system in the drive itself will take care of the problem.

---

### Post by lavinog on 2009-05-01
> **ddrichardson said:**
> @lavinog: I Purge them on this one, rsync them on my main (non-testing system) along with my Firefox profile which _really_ benefits from tmpfs on the Acer Aspire One.

That could be a good option to add to ubuntu.
I think all machines could benefit from reduced hd activity.

---

### Post by blueridgedog on 2009-05-01
As an aside in this thread...are we really concerned with the life of the SSD or are we looking to minimize writes for a write bottlneck?  I use my netbook and SSD drive for light travel related computing and have not really noticed any issue.  

A friend of mine as dual SSD drives in a raid for the boot drive of his high end gaming system, and he is not concerned with either issue.

---

### Post by neu2buntu on 2009-05-01
from what i have seen it sounds like ext2 gives the longest life for your ssd (flash hdd) as it is not accessed as much as ext3....found this from searching about acer aspire one.... but it probably wont matter much as your flash drive can read and write a lot of times before wearing,and you will prob have upgraded your notebook/netbook/laptop by then..... also9 if you have already installed the default ext3 there is a way to change to ext2.....

---

### Post by ddrichardson on 2009-05-02
> **blueridgedog said:**
> As an aside in this thread...are we really concerned with the life of the SSD or are we looking to minimize writes for a write bottlneck?  I use my netbook and SSD drive for light travel related computing and have not really noticed any issue.  

A friend of mine as dual SSD drives in a raid for the boot drive of his high end gaming system, and he is not concerned with either issue.
The Aspire One has two SSD manufacturers, I can't remember who they are but one is quieter and seems so suffer more from bottlenecks. I'd also say this is more apparent in Ubuntu, there's probably a patch in Linpus as Acer have patched a lot of it.

Writes are an issue too to some degree, given its usage (I take it everywhere) its on a lot and theres no harm in maximising its life.

---

### Post by lavinog on 2009-05-02
> **ddrichardson said:**
> but one is quieter

Do SSDs make noise? (I don't have one, but I thought they should be relatively quiet.)


I had a hard drive (magnetic) die when windows started paging to its pagefile(swap) excessively. I would think that running with no swap on a SSD would be good advice.
The only time my computer uses the swap partition is when something went wrong.

---

### Post by ddrichardson on 2009-05-03
Yeah you're right I posted late and am tired, I meant to say that one model has a *noiser* fan and the *faster* SSD. I have the slower SSD (for writes).

I've not had swap on the device since removing Linpus and have never hit any problems despite using tmpfs for a fair few things. Linpus had a 1.5 Gb swap partition which seems excessive given the usage model of these devices and the inclusion of an SSD.

---

