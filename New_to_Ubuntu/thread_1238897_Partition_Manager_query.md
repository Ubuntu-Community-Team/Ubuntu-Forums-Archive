---
title: "Partition Manager query"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Nigalius on 2009-08-12
Hi, I am still new to Linux having had it on one of the pc's for just over 2 weeks. I currently have Mint7 and Ubuntu. My h/d is total size of apx 370gig and originally divided equally between Mint7 and Ubuntu. I then decided after trying both versions that I wanted to use Mint7 much more so I decide to install 'Partition Editor' on both versions. I then go into Mint7 and take the size of the Ubuntu partition down to about 55gig. I made it smaller by dragging the arrow from the laft towards the right and after it was done it showed the Ubuntu partition as being appx 58.62gig, the unallocated partition as being 125.62gig and the Mint7 partition as being 185.60gig. That was going right to left. I now go into Ubuntu and hoped to be able to make the Mint7 partition bigger so as to take up all of the unallocated partition. But I was not given that option. I could only make it smaller. Can anyone please tell me where I am going wrong. I have tried to read previous postings and done a searcg. I have even 'googled ' it with no joy. So I need to know what Linux version I need to be in to make Mnt partition bigger, I presume I should be in Ubuntu. Then I need to know how to make it bigger using Partition Editor.

Many Thanks

Nigel

---

### Post by starcraft.man on 2009-08-12
For the record, always do partition editing from a live CD in these such cases. Frankly, I always do partition editing from a live CD, makes it easier if I want to modify OS partitions.

See documentation. I'm gonna assume what's happening is the partitions aren't side by side, ergo, freespace can't be merged into the partition. Please see [Old documentation section]("http://gparted.sourceforge.net/documentation.php"), start with general info and read downwards. Pay attention to moving and resizing commands. If there's any questions, ask BEFORE making permanent changes to your partition.

As always, I am not responsible for any lost data in partition changes, Backup and backup again!

---

### Post by CatKiller on 2009-08-13
> **Nigalius said:**
> I now go into Ubuntu and hoped to be able to make the Mint7 partition bigger so as to take up all of the unallocated partition. But I was not given that option. I could only make it smaller.

That sounds like the partition is inside an extended partition. You'll need to make the extended partition larger before you can make any of the partitions inside it larger.

---

