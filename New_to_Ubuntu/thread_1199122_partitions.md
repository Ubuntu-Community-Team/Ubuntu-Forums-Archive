---
title: "partitions"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by WriteGirl on 2009-06-28
So I had issues with Ubuntu 9.04 and I decided to reinstall it from a live CD. However, I'm dualbooting windows XP and Ubuntu. I managed to delete Ubuntu from the partitions and I'm still able to load windows XP, but neither disk manager in windows nor GParted will let me resize the windows partitions to use all of the available space, so I can't reinstall Ubuntu.

Any help would be appreciated. 

Thanks!

---

### Post by LewRockwell on 2009-06-28
you'll need to use Gparted from your liveCD to make alterations to your hard drive

if you want to do "windows things" to your hard drive then you'd need to boot from your windows CD/DVD so, again, your hard drive hasn't been mounted for booting and running of any installed OS(es)

keep us posted!

.

---

### Post by WriteGirl on 2009-06-28
My ultimate goal is to reinstall Ubuntu, but in order to do that, as I understand what I'm doing, I need to undo the partitions that I made to install Ubuntu the first time. So I guess what I'm asking is why can't I resize the Windows partition to take up the whole disk space, so that I can make a new partition when I reinstall Ubuntu. GParted and Disk Management aren't letting me use the empty space that used to be used by Ubuntu until I deleted it. 


Is it possible to install ubuntu into the unallocated space? I assumed that if I tried to install Ubuntu now, it would try to divide the space within windows, like when I originally did it. 

I'm sorry if I'm not explaining what I'm trying to do very clearly.

---

### Post by TeoBigusGeekus on 2009-06-28
Could you please post us the number of your drives, the partitions in them and their sizes?
I'm a little lost...

---

### Post by ahndoruuu on 2009-06-28
Okay, I THINK I know what you're saying/asking, and if my understanding is correct then you don't know what you're doing.
**By no means do you want Windows to take up the entire space**, that would just create more work later when it comes to shrinking it back down.
In Gparted, is your "empty" space called "unallocated"?

If that's the case, and the unallocated space is big enough to accommodate Ubuntu to your tastes, then go ahead and run the Ubuntu installation from the liveCD.  When you're given an option of where you'd like to install, choose "largest continuous free space" and then at the bar at the bottom of the screen you should be able to drag a slider that will determine how big your Ubuntu partition will be, then click Forward.

---

### Post by WriteGirl on 2009-06-28
Ok. I believe I only have one drive. There is 60 gigabytes of unallocated space, which used to be Ubuntu until I deleted it, and there is 14 gigabytes in the partition that I'm running Windows XP in. 

I hope this helps. Thanks.

ETA. ahndoruuu: yes, in GParted the empty space is called unallocated. And yes, I don't really know what I'm doing, but by what you're saying, I can simply use the live CD to install Ubuntu and I'll be fine. 

Thank you!

---

### Post by LewRockwell on 2009-06-28
and even a screen shot of Gparted might be helpful

.

---

### Post by ahndoruuu on 2009-06-28
Okay, follow the instructions in my last post and you're good to go.

---

### Post by LewRockwell on 2009-06-28
you don't need to mess with the windows partition at all

just go ahead and start your installation and use the largest unused space for ubuntu

.

---

### Post by WriteGirl on 2009-06-28
Thank you so much! I'm going to go do that now.

---

### Post by -kg- on 2009-06-28
Well, I'm glad I didn't post my great big post before checking and reading the thread again.

The probably reason you couldn't expand your XP partition is that you had the unallocated space in an Extended partition.  But as ahndoruuu said, you don't need to mess with the XP partition at all (unless you wanted to give it a little more space).

You can see what an Extended partition looks like in GPartEd by going to the link in my signature block and reading the section on Extended Partitions.  It will give you screen shots of what an Extended partition looks like and it's capabilities.

---

