---
title: "2 Karmics, only need one"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by itendo on 2010-04-10
due to a system meltdown, i currently have two karmic installations and need to get rid of one of them. since i just got grub up and running again i am afraid of doing anything rash that would mess up log in. however, its 80 gig i want to reclaim, and i think it is causing user permission errors (though im sure ts something else doing that).

how do i safely erase the one partition?

---

### Post by lockalidiot on 2010-04-10
I suppose your best bet is to use gParted live-cd to do that.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Just remember to always back up your data!

---

### Post by bear24rw on 2010-04-10
dont even really need live-cd, unless you want to merge them i suppose

---

### Post by ranch hand on 2010-04-10
It is not a good idea to do any major work on a mounted drive and particularly not from that drive.  This is why it is recommended to use the live CD.  The one you installed from will do the job.

Gparted is in System>Administration.

You could shrink that partition and leave it so that you  can do any experimenting on an OS you can afford to ruin.

---

### Post by lockalidiot on 2010-04-10
> **ranch hand said:**
> 
You could shrink that partition and leave it so that you  can do any experimenting on an OS you can afford to ruin.
That is what I did with my system. I have Ubuntu 9.10 as my main OS with about 450BG, Windows 7(for gaming) with about 350GB and Ubuntu 10.04 Beta 2 (testing) with 30GB... :)

---

### Post by drs305 on 2010-04-10
I also like gparted for doing this kind of operation. 

First, it lets you see graphically how your system is partitioned. 

Second, it's pretty easy to see which partition contains your Ubuntu installation in use (it will have the key icon to the left of the partition in the lower pane). 

You can also ensure you don't (or do) have a separate /home partition.

You can unmount partitions (have a "key" icon). If gparted won't let you umount it with all other apps closed, further investigation should be performed before you delete it.

One final thing. Before rebooting, if you have deleted a partition, make sure it isn't listed in fstab. You will have to manually open the fstab file to check the contents. If a deleted partition is still referenced in fstab and set to automount, your computer is going to complain when you try to reboot.

A technique I used before rebooting is to run the following commands to make sure my fstab is going to work:
```
sudo umount -a  # You will get various 'busy' messages, that's ok. Look for 'real' partitions.
sudo mount -a  # You shouldn't get any errors. If you do, investigate which entry is causing problems
```

---

### Post by itendo on 2010-04-12
@drs305 i took your suggestion, used gparted to remove the partition and double checked the mount procs no errors. thanks for the help, im glad my grub records updated correctly and booted up correctly.

now that this hole is plugged, cant wait to see where the water starts leaking next!

---

