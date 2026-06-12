---
title: "64 bit queston"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by ornothaloapq on 2010-10-10
i am planning on installing10.10 as a duel boot with windows 7on my laptop. the windows 7 is 64bit, should i also install ubuntu 64 bit?

---

### Post by Quackers on 2010-10-10
That sounds reasonable to me :-)

---

### Post by amjjawad on 2010-10-10
> **ornothaloapq said:**
> i am planning on installing10.10 as a duel boot with windows 7on my laptop. the windows 7 is 64bit, should i also install ubuntu 64 bit?

I assume your CPU is 64-bit as long as you have Windows 7 64-bit. In that case, YES :)

---

### Post by ornothaloapq on 2010-10-10
thank you for your fast reply

---

### Post by amjjawad on 2010-10-10
> **ornothaloapq said:**
> thank you for your fast reply

Anytime ;)

---

### Post by ornothaloapq on 2010-10-10
now i have a separate problem. i click on the install icon and when i get to the allocate drive space part of the process i only see two options. i can see "erase and use the entire disk" and "specify partitions manually (advanced)". according to the install instructions on the ubuntu website there looks like there should be 3 options. how do i find the option "install alongside other os"?

---

### Post by Vaphell on 2010-10-10
how many primary partitions are there already? Legacy limitation (which should be killed long time ago) is 4. Many win7 laptops use them all, for example 1 - 100MB boot partition, 2 - C:, 3 - D:, 4 - recovery. Maybe that's the case - it can't create additional partition for ubuntu without destroying existing one, thus that side-by-side option is unavailable at all.
you can post a screenshot with gparted window

---

### Post by ornothaloapq on 2010-10-10
i think that there is four, ill try and get a screen shot.

---

### Post by amjjawad on 2010-10-10
> **Vaphell said:**
> how many primary partitions are there already? Legacy limitation (which should be killed long time ago) is 4. Many win7 laptops use them all, for example 1 - 100MB boot partition, 2 - C:, 3 - D:, 4 - recovery. Maybe that's the case - it can't create additional partition for ubuntu without destroying existing one, thus that side-by-side option is unavailable at all.
you can post a screenshot with gparted window

Never had this problem but someone here has mentioned it the other day. Now, I understand what was going on with him. Thank a lot :)

---

### Post by ornothaloapq on 2010-10-10
screenshots should be attached.

---

### Post by amjjawad on 2010-10-10
> **ornothaloapq said:**
> screenshots should be attached.

Apparently, all your partitions are primary. You need at least to remove one of them, create an extended partition and from there you could create as many logical partitions as you want.

For default Ubuntu Installation, you need two partitions. One is root (/) and the other is (swap). Or perhaps you could create a third partition (/home).

---

### Post by ornothaloapq on 2010-10-10
could you help me set that up because i have no idea how

---

### Post by amjjawad on 2010-10-10
> **ornothaloapq said:**
> could you help me set that up because i have no idea how

Sure thing.

First of all, you need to decide which partition to delete/destroy.
Once you made your mind, just delete it from GParted and the space which was allocated for that partition will be unallocated.

Now, you have say 50GB (for example) unallocated space, right?
Start to create a partition now. Ubuntu by default needs two main partitions and others partitions are optional.
Ubuntu needs:
Root partition
Swap partition (usually your RAM by 2 - example - if your RAM is 2GB then swap partition should be 4GB)

Root partition should be ext4 and mount point /
swap partition is swap

This will help you: [http://www.facebook.com/album.php?aid=37100&id=154937727857763](http://www.facebook.com/album.php?aid=37100&id=154937727857763)

---

### Post by Vaphell on 2010-10-10
first you must find out what these partitions are exactly - maybe you can check in some windows disk manager - and pick the least important.
If you got a setup with primary D: partition, it would be an obvious choice -> kill D:, create extended partition in its place, some optional resizing, recreate D: inside if needed as logical partition, also create partitions for ubuntu root and swap, /home for convenience (all logical).

---

### Post by ornothaloapq on 2010-10-10
i booted up windows and i see that D is labeled "recovery" and E is labeled as "HP tools". i'm assuming that E is the least important. it is only 99.1 mb though.

---

### Post by srs5694 on 2010-10-10
One of those partitions (probably /dev/sda3) holds the equivalent of your Windows installation/recovery DVD set, since the computer makers have become too cheap to provide physical media, instead stealing space from your hard disk for this purpose. The good news is that there's probably a utility on the computer that will let you make recovery DVDs. Use this utility (make two sets for safety). When this is done, the relevant partition will no longer be necessary, and becomes a good candidate for removal. Resize and move other partitions as necessary or convenient, create an extended partition in the free space, and create your Linux partitions as logical partitions inside the extended partition. Most of this is best done using GParted, although it's safer to resize your Windows boot partition using the Windows disk partitioning tool.

---

### Post by ornothaloapq on 2010-10-10
it will take a while for me to all the backups and discs, ill post on this thread when i did that to hopefully get help with making all the new partitions.

---

### Post by amjjawad on 2010-10-10
> **srs5694 said:**
> although it's safer to resize your Windows boot partition using the Windows disk partitioning tool.

I disagree with that. This is not the safest option. Resizing Windows Partition without "defragment" is very bad idea.

On the other hand, I agree to burn the content of the recovery partition on a DVD. Not sure how exactly to access these files (I've never had a laptop) though.

---

### Post by ornothaloapq on 2010-10-14
ok, i have a backup completed. if anyone can help me i was wondering what the next step is. based on past experiences with new versions of ubuntu i am expecting an painful process.

---

### Post by ornothaloapq on 2010-10-14
should i boot from my ubuntu live usb to start? should i use that to delete one partition or windows?

---

