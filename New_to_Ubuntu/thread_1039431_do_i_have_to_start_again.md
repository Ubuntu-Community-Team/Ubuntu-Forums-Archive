---
title: "do i have to start again?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-14
vista stopped working in my dualboot.  now i have an entirely useless partition.  is it possible to delete the partition and give the freed space to ubuntu or do i have to do a fresh install of ubuntu over the entire disc?

---

### Post by taurus on 2009-01-14
You can use gparted from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), to delete the windows partition and merge that to your Ubuntu.  Again, it depends on the layout of your harddrive.

```
sudo fdisk -l
```

---

### Post by Michael.Godawski on 2009-01-14
hi,

you can use the tool gparted from the Ubuntu Live CD to delete the vista partition and create a ext3 data partition for Ubuntu.

Make sure you delete the right one:P probably the ntfs partition.

---

### Post by mamamia88 on 2009-01-14
ill try that and see how it works brb

---

### Post by twitch2197 on 2009-01-14
it's possible, yeah. but the same thing happened to me and i ended up screwing up GRUB. i had to reinstall ubuntu over everything. just be careful.

---

### Post by cariboo on 2009-01-14
Why not just fix Vista, instead of breaking a working installation. If you have a Vista install CD, boot from it and choose repair at the installation menu.

Jim

---

### Post by mamamia88 on 2009-01-14
oops too bad already deleted vista.  think ill just try to create a slimed down version of vista and run it in vm when i get a chance.  i think i am going to have to reinstall ubuntu all i managed to do was schrink my partition wish me luck

---

### Post by fuser312 on 2009-01-14
is there any way, to merge some part (free space in vista) of windows to ubuntu instead of deleting the whole ntfs drive

---

### Post by mamamia88 on 2009-01-14
oh is there a way to copy my theme to a flash drive?

---

### Post by minsf on 2009-01-14
mamamia, please be sure to close your previous threads if they are solved or irrelevant. in particular, we are still trying to help you here:
[http://ubuntuforums.org/showthread.php?t=1038557&page=2](http://ubuntuforums.org/showthread.php?t=1038557&page=2)
even though it seems like you abandoned that thread.
as we said there, according to your output of "sudo fdisk -l", it seems like you are going to have to:
1. run live cd
2. be sure that the hard disk is unmounted ("sudo umount /dev/sda*")
3. run gpart (that is, the partition editor)
4. delete/shrink the windows partition
5. click "apply"
6. [COLOR="Red"]expand the extended partition to the unallocated space. it is the FRAME of your linux and swap partitions.[/COLOR]
7. click "apply"
8. only then you can expand your linux partition, and click "apply".

maybe someone can help you with taking the linux partition outside of the extended partition.

if you decide to install fresh ubuntu on the entire hard drive, i recommend creating a seperate partition for /home 
an excellent guide (by psychocats) to create a seperate home partition can be found via the link in post #8 in another thread of yours
[http://ubuntuforums.org/showthread.php?t=1039098](http://ubuntuforums.org/showthread.php?t=1039098)
and you should probably close this thread too...

please please keep track of your threads. if you decide to open new threads, at least link them. it will save time for people. for instance, rather than suggesting "sudo fdisk -l" in post #2 here, they could have looked at your output of this command on the other threads and help you better. thanks

---

