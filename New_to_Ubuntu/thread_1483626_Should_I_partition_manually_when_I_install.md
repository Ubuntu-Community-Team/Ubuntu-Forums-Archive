---
title: "Should I partition manually when I install?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by thomas144 on 2010-05-14
Hi there,
I'm thinking about installing Ubuntu 10.04. I've used the Live CD and USB and I am satisfied with it. I would say my knowledge of Ubuntu is intermediate, but I put this question in Absolute Beginner talk because I feel that this is a fairly beginner question. When I install, I'm not sure if I  should trust Ubuntu to automatically partition my hard drive, or to  manually divide my hard drive. What happens if I resize my Windows  partition inside Windows, leaving empty space, and install Ubuntu to it?  How will the installer create new partitions for Ubuntu? Will I have  the right amount of swap space? I have 3 GB of RAM, and a 250 GB hard  drive with Windows 7. It currently has 3 partitions.

Please help, as a little info will go a long way.

---

### Post by ubunterooster on 2010-05-14
I recommend manual. I've done both but usually the "resize" works fine.

---

### Post by thomas144 on 2010-05-14
Thanks. Do you know how things are partitioned when done automatically?

---

### Post by ubunterooster on 2010-05-14
Just a little I'll start partitoning one so i can give screen shots.

---

### Post by Tholley on 2010-05-14
I would recommend manually... give me a minute and I'll post some good instructions on how.

---

### Post by thomas144 on 2010-05-14
So you're about to install Ubuntu on a computer by manually partitioning the hard drive?

---

### Post by Tholley on 2010-05-14
I'm assuming you want to dual boot with Windows, so here is how...

boot up your Live CD then go into the install.

when you get to the partitioning section:

1. select manual editing of partitions
2. you will see two partitions that are Ubuntu
3. select the ext3 or ext4 partition (whichever format was used)
4. click "edit partition"
5. select "Ext3" from where it says "do not use this partition" (its a  drop down menu) and select the format option
6. select "/" from the mounting drop down menu.
7. click ok.
make sure that the box is checked for formatting on the Ext3 partition.
 don't worry about the "Swap area" because it doesn't change.

then continue installing from there. 

that should work.

Hope this helps!

---

### Post by thomas144 on 2010-05-14
I don't have any Ubuntu-related partitions on my computer, though. One partition is labeled DellUtility another is labeled RECOVERY and the third one is OS. OS is the one that is Windows' main partition. Maybe I'm just confused.

---

### Post by theozzlives on 2010-05-14
use the Windows Disk Manager to resize Windows, then manually partition Ubuntu.

10 GB /
3 GB swap
the rest /home

---

### Post by thomas144 on 2010-05-14
I feel like all of you are getting me somewhere. From what I understand, I would do this:
1. Go to the install. When I get to partitioning, select manually partition.
2. Select the empty space (at this point, I already have freed up some from Windows.)
3. Select "Edit Partition"
4. Select Ext4
5. Set the mount point to / or /home
6. Select "OK"
7. Set swap area to 3 GB (Or maybe 4 or 5 to be safe)
8. Go for it.
This is what I derived from the directions and from the other help? Is there anything wrong?

---

### Post by slibuntu on 2010-05-14
Ok, so you have your empty space already right?

In the partition editor...

Click to create a new partition, make that new partition a SWAP partition of whatever size you want for swap, if you want to hibernate, you'll need as much swap as you have RAM.

Second step, create another new partition, make it EXT4 formatted, and set the mount point to be "/". This is the root partition, make this about 6GB, that'll be plenty.

Lastly create a final third partition, let this partition use up whatever free space is left, and make the mount point /home. Set is as EXT4 also. 

Now you're done, so click to go onto the next step.

---

### Post by Sealbhach on 2010-05-14
> **slibuntu said:**
> Ok, so you have your empty space already right?

In the partition editor...

Click to create a new partition, make that new partition a SWAP partition of whatever size you want for swap, if you want to hibernate, you'll need as much swap as you have RAM.

Second step, create another new partition, make it EXT4 formatted, and set the mount point to be "/". This is the root partition, make this about 6GB, that'll be plenty.

Lastly create a final third partition, let this partition use up whatever free space is left, and make the mount point /home. Set is as EXT4 also. 

Now you're done, so click to go onto the next step.

Yes, this is the way to do it. Makes upgrades so much easier.


.

---

### Post by thomas144 on 2010-05-14
Is there anything wrong? Hello?

---

### Post by ubunterooster on 2010-05-14
> **thomas144 said:**
> Is there anything wrong? Hello?
in step three select all but 3Gb to be ext3; those 3GB will be the SWAP.

Step 5: mount it as "/" not as "/home" (sans quotation marks of course)

Otherwise you are all correct.

---

### Post by slibuntu on 2010-05-14
Look at my post above, if you follow those instructions you should have your install up and running in no time. 

The way I detailed makes the most sense because you can do a fresh install when a new version comes out without formatting all your files on the /home partition. 

Have I answered your question or is there something else wrong?

---

### Post by thomas144 on 2010-05-14
I'm surprised how many people are helping me.
Slibuntu, do you mean in the installer's partition editor or a standalone program like GParted?

---

### Post by kansasnoob on 2010-05-14
> **thomas144 said:**
> Hi there,
I'm thinking about installing Ubuntu 10.04. I've used the Live CD and USB and I am satisfied with it. I would say my knowledge of Ubuntu is intermediate, but I put this question in Absolute Beginner talk because I feel that this is a fairly beginner question. When I install, I'm not sure if I  should trust Ubuntu to automatically partition my hard drive, or to  manually divide my hard drive. What happens if I resize my Windows  partition inside Windows, leaving empty space, and install Ubuntu to it?  How will the installer create new partitions for Ubuntu? Will I have  the right amount of swap space? I have 3 GB of RAM, and a 250 GB hard  drive with Windows 7. It currently has 3 partitions.

Please help, as a little info will go a long way.

Never resize Vista or Win 7 with anything but it's own partitioning tools!

[http://www.killertechtips.com/2009/05/05/how-to-resize-partitions-in-windows-7/](http://www.killertechtips.com/2009/05/05/how-to-resize-partitions-in-windows-7/)

Beyond that you must decide :)

There is a benefit to having a separate /home partition as you can then reinstall without losing all of the stuff in /home as long as you choose not to reformat it.

I prefer a SWAP slightly larger than my total RAM, a root partition (designated by "/") no smaller than 6GB, and a /home using the rest of the available space in a dual boot.

Some good pictorial guides (but not exactly right for you):

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by slibuntu on 2010-05-14
> **thomas144 said:**
> I'm surprised how many people are helping me.
Slibuntu, do you mean in the installer's partition editor or a standalone program like GParted?

It's been suggested by another poster that you should only resize Windows with Windows own tools. I've always just used the Ubuntu ones, but maybe it's a good idea to use the built in (into Vista and 7 AFAIK) tools to shrink the Windows partition. 

Then, when you are installing, in the partition editor, follow the steps outlined above.

---

### Post by thomas144 on 2010-05-14
More food for thought. I think this is how it's coming so far:
1. Resize Windows with Windows software (I know that Windows 7 has diskmgmt.msc.)
2. Boot from the live CD and install. When I get to partitioning, make the new partitions inside Windows
3. Install.

I think to get the process right, I can practice this with a flash drive and quit the installation before the last step. I think I might do this tonight or tomorrow. It's getting late, and it's very hot inside my house. Maybe I'll see you tomorrow. Thanks for all your help. I think I might have enough information, or close to that.:)
See ya.

---

### Post by slibuntu on 2010-05-14
> **thomas144 said:**
> More food for thought. I think this is how it's coming so far:
1. Resize Windows with Windows software (I know that Windows 7 has diskmgmt.msc.)
2. Boot from the live CD and install. When I get to partitioning, make the new partitions inside Windows
3. Install.



Make the new partitions inside Windows?? No! Make the new partitions when you are installing Ubuntu through the built in Ubuntu partition manager, Make them when you see the window shown in the image below!

[IMG]http://shanetuohy.com/ubu6.png[/IMG]

---

### Post by JamieWrites on 2010-05-15
Re: the last post - how did you create all of those? The 'add' button was never a clickable option so I was stuck with just what was there and I couldn't create anything new.

---

### Post by miyagison on 2010-05-15
> **thomas144 said:**
> So you're about to install Ubuntu on a computer by manually partitioning the hard drive?
:guitar: .....

---

### Post by theozzlives on 2010-05-15
If you already have 3 partitions, you'll have to make the Ubuntu ones logical, not primary. Your limited to 4 primary partitions.

So you'll have 3 Windows partitions, one extended, and 3 logical Ubuntu partitions.

---

### Post by slibuntu on 2010-05-15
> **JamieWrites said:**
> Re: the last post - how did you create all of those? The 'add' button was never a clickable option so I was stuck with just what was there and I couldn't create anything new.

If you click on the bit that is labeled as "free space" and the add button should become clickable.

---

### Post by thomas144 on 2010-05-15
I went into the installer and messed around without saving my changes. I think I see how it's done. I'll think about marking this thread as solved.

---

### Post by thomas144 on 2010-05-29
[FONT=Arial][SIZE=5]Good news![/SIZE][/FONT]

I installed Ubuntu as a dual boot with Windows 7 yesterday. The installation process worked flawlessly. Today, I got my wireless card working and did some tweaks on GRUB2. The only problem with the whole install is that there are duplicate entries in the GRUB menu. That's a benign annoyance, so I think I'll let that go for now.

[SIZE=4][COLOR=SeaGreen]Overall satisfaction with Ubuntu: High[/COLOR][/SIZE] :mrgreen:

---

