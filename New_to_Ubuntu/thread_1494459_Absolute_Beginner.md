---
title: "Absolute Beginner"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by jtellup on 2010-05-26
**Hello all, I guess I have had it with Windows and am making the jump to Ubuntu, my last time with any linux distro was red hat 4.0 so I guess I have a bit to learn**[B], however so far from what I am seeing I'm impressed
[/B]

---

### Post by -humanaut- on 2010-05-26
So... Whats the question ?

---

### Post by jtellup on 2010-05-27
Well thank you for asking.

I have performed two temporary setups to get the feel for it.

I am now ready for the permanent install, I have a laptop with a 250 gig HD, not used to such large drives.

During the initialization I choose to re set the drives and partition them, I decided on 4 partitions.

first a 60 gig for the root and operating system set as ext4 and as /

next a 175 gig as EXT4 set to home

next a 10 gig ext4 set as temp

and the remainder as swap

When I look at the drives they set up as SDA1 SDA2 and then jump to SDA5 and 6 I'm not sure if this is an issue or not, perhaps the home setup creates hidden partitions? Perhaps in the two test runs I created something I'm not deleting? Or perhaps there is a better way to setup the drive?

I'm working my way through the manual as quickly as I can but have not seen this addressed as of yet.

---

### Post by sadaruwan12 on 2010-05-27
Hope this might help you.

[http://news.softpedia.com/.....]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml")

---

### Post by jtellup on 2010-05-27
thanks, that does help a bit.

from what I am reading it seems that the last two partitions are being created in an extension and this might be what I am seeing, but I also picked up on the recommendation that we should set a /boot partition as the first one, with / right behind that

---

### Post by -humanaut- on 2010-05-27
What i've noticed with Ubiquity is it installs to "Extended Partitions" generally after /(root) unless there specified not too my partition table looks like this:

(primary)
/boot Ext2 1GB (I know, 1GB is HUGE for boot but there was some problems with just 100mb so I was just being safe I can spare a gig)

(primary)
/(root) 25GB (This may seem high as well but fill up a /(root) once and you'll understand)

(extended)
(swap) 5GB

(extended)
/home 228 GB

and

(primary)
|_unmounted_| fat32 5GB (This is an unmounted backup partition that I store extremely important files on that I can't afford to lose I have several other backups made with CD-R's but this is the extremely convenient if I manage to lose all my data which is frequent because I do alot of Alpha/Beta testing)

---

