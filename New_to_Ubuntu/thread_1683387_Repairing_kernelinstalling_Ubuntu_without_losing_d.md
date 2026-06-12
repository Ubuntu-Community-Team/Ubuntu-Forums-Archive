---
title: "Repairing kernel/installing Ubuntu without losing data."
date: 2011-02-07
forum: New to Ubuntu
---

### Post by newn on 2011-02-07
Hi everybody.
Finally I got access to the server machine... So I'd like to repair the kernel. It's in panic attack state. Which means, I need to repair it from the grub enviroment.
Or, even better - reinstall Ubuntu, but without losing my data in the HDD. How is that possible?
Using Ubuntu x64 10.

Thanks.

---

### Post by jonnny_j22 on 2011-02-07
did you use seperate logical partitions for /home, /proc, /tmp etc when you set up the system, or is it just all one root partition?

---

### Post by newn on 2011-02-07
I didn't setup the system. But I remember, that there was root/username or home/username... Something like that.

---

### Post by Old *ix Geek on 2011-02-07
How is the hard drive partitioned? If it was done the way *I* think it should be, i.e., with separate partitions for / and /home, you can reinstall the OS at any time [like when upgrades are available] without losing data.

I always partition my drives like this:

/ -- just enough space for the OS plus a comfortable cushion
/home -- large amount of space
/data -- another large amount of space
swap -- a comfortable amount

If the drive was NOT partitioned with separate / and other partitions...you're pretty much screwed. ](*,)  Get out your backup media and start copying files! Once that's done, re-think your partitioning strategy.

---

### Post by jonnny_j22 on 2011-02-07
if not, and your looking at one solid partition, this may help you with your kernel issue:

[http://technotalk.tumblr.com/post/546121052/recovering-kernel-from-crashed-ubuntu-kernel-panic-not-s](http://technotalk.tumblr.com/post/546121052/recovering-kernel-from-crashed-ubuntu-kernel-panic-not-s)

---

### Post by newn on 2011-02-07
Restarted the system and have no control again... -.- Probably I will have to wait one more day for the Administrator to be online for help services and THEN try again. Eh, it makes me angry, that the company can't make KVM work properly...
I will copy the partitions window, since it's RAID. It had 2 partitions I think though. I will screenshot it anyway, I almost have no experience with Linux...

Thanks.

---

### Post by mikewhatever on 2011-02-07
You could probably use an older kernel to boot, and then purge and reinstall the broken one.

---

### Post by newn on 2011-02-07
mikewhatever, that was my first idea, when the system failed to boot actually. Just no knowledge on how to do it.

---

### Post by mikewhatever on 2011-02-08
Press and hold the 'Shift' key after the bios screen, and the grub menu should appear with all available kernels to choose from.

---

### Post by newn on 2011-02-08
Doesn't appear for some reason. :/
I've got this, when tried to reinstall the kernel from GRUB menu though:
[http://img651.imageshack.us/img651/9141/errorzrg.png](http://img651.imageshack.us/img651/9141/errorzrg.png)
Any idea, what could be wrong? :/

---

### Post by rosencrantz on 2011-02-08
Hi newn,
how did you boot and reinstall -  using a live boot and chroot as explained in johnny_j22's link?
There seems to be an old bug with grub2 and RAID systems, did you see [this discussion]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/528670")?

Cheers
rosencrantz

---

### Post by newn on 2011-02-08
Thanks, I might use it, if my server won't work again. Just took and reinstall it. Will have to spend 1 or 2 days making the data from scratch though...
Having troubles with the reinstalled version now, not everything works. Posted a new topic about it.

---

