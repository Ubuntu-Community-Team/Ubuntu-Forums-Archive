---
title: "help-can't increase Ubuntu partition size"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by collards on 2009-12-01
Hello & thanks again to all advice in a previous thread, which has been so helpful.

Here's where i am now--

I installed Ubuntu onto a drive that had Windows OS -- and most of the Windows partition was unused space. I have backed up my data files & got rid of unneeded stuff.

After carefully reading & re-reading "Ubuntu documentation & GParted help I used GParted to resize (shrink) the windows partition to create the necessary unallocated space --so that I could increase Ubuntu size to 12G--which I read is a good amount.

but after retrying numerous times I am not able to resize Ubuntu into the now unallocated space.

Ubuntu & LInux-swap are both logical partitions inside Extended partition. Status for Linux-swap is active and mounted & status for Extended is busy---probably because of Linux (???) so the resized button remains greyed out.

Here are the details:
Windows /dev/sda1 5.86 G

Unallocated 10.29G

Extended /dev/sda 2.50 G

Ubuntu /dev/sda5 2.33 G

Linux-swap /dev/sda6 172.54 M


My questions:

Is is possible to resize this Extended partition? Is Linux-swap busy because I am using the Live CD?

Do I uninstall & reinstall in the now larger space? or do I delete the Extended partition?

If I am overdoing this, i apologize. i just want to be clear.

thank you,

Collards

---

### Post by Locke_99GS on 2009-12-01
You can't resize a partition that is mounted. If you're using Ubuntu, the partition that it resides on is likely mounted. The simplest (and safest) method to do this would be to do it from the LiveCD; it has gparted. Boot to it, and you should have no problem resizing the partitions.

edit: er, just realised you WERE using the LiveCD, sorry. I tend to use Primary partitions, so this may or may not fly. The extended partition is a container for other partitions, of which sda1 probably doesn't exist within. You'll have to resize the container itself into the newly unallocated space, then the Linux partition within it can be enlarged. Makes sense?

---

### Post by collards on 2009-12-01
Thanks Locke

but I am working from the ubuntu 9.04 CD --using GParted.   is Gparted using the swap file?

---

### Post by Paqman on 2009-12-01
> **collards said:**
> Thanks Locke

but I am working from the ubuntu 9.04 CD --using GParted.   is Gparted using the swap file?

The LiveCD automatically mounts any swap files it finds, to improve performance. To deactivate it in Gparted right click and "swapoff". You should then be able to make your changes.

---

### Post by plucky on 2009-12-01
> Is is possible to resize this Extended partition? Is Linux-swap busy because I am using the Live CD?


It is possible to resize the extended partition,but you have to turn swap off first.By default,the Live CD will mount and use swap and you can't alter a partition that is mounted.

Run Gparted from the Live CD,right click on the swap partition and set swapoff.

Then 

1) Extend the extended Partition into the un-allocated space
2) Move the start of the linux partition into the un-allocated space made when the extended partition was increased.(This event could take a long time as it has to move the data as well)
3) Grow the linx partition into the un-allocated space created at the end of the partition


> Do I uninstall & reinstall in the now larger space? or do I delete the Extended partition?

You might have to re-install grub as the UUID of the linux partition would have changed.(not too sure,as it has been a long time since I have done this)


Good Luck

---

### Post by collards on 2009-12-01
Yes it does make sense.  but please reread.....i want to increase the extended partition which contains the Ubuntu partition.   I must be missing something..

---

### Post by Paqman on 2009-12-01
> **collards said:**
> i want to increase the extended partition which contains the Ubuntu partition.

Plucky's instructions will do that for you.

---

### Post by Locke_99GS on 2009-12-01
The only times swap is used is when you:

1) run out of physical RAM, which shouldn't really happen if you have a gig or so of ram and are only running gparted from the LiveCD. I have 2gig of RAM and have *never* used swap space.

-or-

2) Hibernate the computer, where it must copy the contents or your RAM to swap, where it is recovered the next time you boot.


Now, the LiveCD *will* use any swap space it finds, and when swap is on, you can't work with it. In gparted, right click on your swap space and select "Swapoff" to turn it off, then you will be able to work with it. Turn it back on when your done if you think you might need it before your done with your live session.

edit: I'm slow today.

---

### Post by collards on 2009-12-01
Thanks all,   I just did swap off & it is running.   How will I know if I have to re-install GRUB?    

Also,   I need to increase swap file size.


are these the right steps?

1- -increase Extended partition to fill unallocated space

2- resize Ubuntu partition to fill unallocated space inside extended partition

3- reduce Ubuntu partition on right side about 400MB for swap file (my RAM max is 512)

4 -resize  swap file to file that space


I am working from the CD so please forgive if I delay in responding and please check back with me   

thankyou thankyou

---

### Post by collards on 2009-12-01
Thanks all---Swap off was successful.

I just thought of something:

Would staying online  in the forum interrupt the resizing process?  I have GParted open in another workspace and did swap off there.

should I get out the forum while resizing?

---

### Post by plucky on 2009-12-01
> 2- resize Ubuntu partition to fill unallocated space inside extended partition


You can only move the whole of the partition into the un-allocated space,and then you can grow the rear of the partition,which increases the size of the partition.

> 3- reduce Ubuntu partition on right side about 400MB for swap file (my RAM max is 512)

Just don't allow to partition to take up all the space,I assume the swap partition is located after the linux partition.

Just do one step at a time so mistakes are easier to correct.
Also back up your data.


Good Luck

---

### Post by Paqman on 2009-12-01
> **collards said:**
> 
should I get out the forum while resizing?

Nope. Since you're in the LiveCD Firefox is running completely in RAM. The only thing touching your hard drive is Gparted.

---

### Post by collards on 2009-12-01
Thank you,  Plucky, locke, et all. 

Sorry,  don't know how to do the quotes yet....trying to learn to navigate around & use this forum.

I did what I described in my last message, but didn't apply it yet.   

Now  I have:

 12.79 G  - extended

12.2 G   -    Ubuntu

580.44 M   - Linux swap

Is it recommended that I have a larger swap file?    my RAM is only 516 MB

thank you lifesavers.

---

### Post by Paqman on 2009-12-01
> **collards said:**
> 
Sorry,  don't know how to do the quotes yet....


Hit the quote button, bottom right.

> 
Is it recommended that I have a larger swap file?    my RAM is only 516 MB


With that amount of memory you'll probably be using swap regularly, but you should be ok with 580MB. You can monitor swap usage in the System Monitor, if you find you're using it all up then you can always expand it later.

---

### Post by collards on 2009-12-01
> **Paqman said:**
> Hit the quote button, bottom right.



With that amount of memory you'll probably be using swap regularly, but you should be ok with 580MB. You can monitor swap usage in the System Monitor, if you find you're using it all up then you can always expand it later.


Thank you, let's see if it works for me

What if i only want to quote one sentence? how do I select what I want to quote?

---

### Post by Paqman on 2009-12-01
> **collards said:**
> Thank you, let's see if it works for me

What if i only want to quote one sentence? how do I select what I want to quote?

Highlight the sentence and hit the wee quote button above the box you type in.

Notice the way it puts tags around the text? That's [BBcode]("http://en.wikipedia.org/wiki/Bbcode"), and you can write it in by hand if you want to.

---

### Post by collards on 2009-12-01
> **Paqman said:**
> Highlight the sentence and hit the wee quote button above the box you type in.

Notice the way it puts tags around the text? That's [BBcode]("http://en.wikipedia.org/wiki/Bbcode"), and you can write it in by hand if you want to.


Thank you Paqman.  I am going to stop here because I am going off original topic.  


Thanks everyone!!!!!  I am going to apply my partitiion changes now.

Collards

---

