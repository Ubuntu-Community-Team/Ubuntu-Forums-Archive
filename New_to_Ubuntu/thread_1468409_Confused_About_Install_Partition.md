---
title: "Confused About Install Partition"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by The Artful Dodger on 2010-05-01
Hello:

I am a long-time Windows user that recently upgraded to Win 7. Thinking ahead, I purchased a 1.5 TB hard drive, and created a number of partitions, including one for the Win XP OS, one for the Win 7 OS, and one for (heretofore empty) Ubuntu OS. I also created a partition for each of these operating systems where I can install programs! I intended to have a triple-boot system, Win XP 32-bit, Win 7 64-bit, and Ubuntu 64-bit.

Thes week I had problems printing with Win 7 so I decided to give Ubuntu a go. I downloaded the 64-bit version and began, intending to install on the OS partition I had reserved for Ubuntu. I cannot see how do do that - the installer seems to want to change the size of my Windows partition and install Ubuntu there. I don't need to do that - I have a partition of 40 GB for Ubuntu!

Then I looked at the Pocket Guide only to learn that I shouldn't use the 64-bit version!

Am I missing something? Can this not be done? Do I need to give up on Ubuntu?

Thanks in advance for any advice you can give me!

Sparky

---

### Post by The Cog on 2010-05-01
You can't create a suitable partition using windows. Linux must live on unix-type partitions such as ext3, ext4, jfs. Also, Linux likes to have a swap partition to use for virtual memory.

The easiest thing to do is to use your windows based partitioner and delete that partition you wanted to put Ubuntu on, leaving un-partitioned disk. Then tell the Ubuntu installer to use the free space. It will actually create two partitions in that space - a system partition and a swap partition.

---

### Post by nhasian on 2010-05-01
> **The Artful Dodger said:**
> the installer seems to want to change the size of my Windows partition and install Ubuntu there. I don't need to do that - I have a partition of 40 GB for Ubuntu!

one of the options at the partitioning screen (and the one I ALWAYS choose) is to manually specify the partitions.  i never let the wizard set partitions for me.  this way you can tell it where you want ubuntu

> **The Artful Dodger said:**
> Then I looked at the Pocket Guide only to learn that I shouldn't use the 64-bit version!

If your processor supports 64-bit then yes you should use 64-bit Ubuntu.

dont forget you need a swap partition too.  if you are out of primary partitions, create an extended partition instead.  with such a small partition set aside for ubuntu i would not recommend a separate /home partition either.

---

### Post by The Artful Dodger on 2010-05-02
Hello:

Thank you to "The Cog" and to "nhasian" for your quick replies. I feel so dumb but I guess it is all of the (to me at least) strange terminology! Here's what I got:

1. In Win 7 I deleted the "Ubuntu", 39GB partition; I made a list of all of the sizes of all of the partitions (so I could recognize them since they are not called by the same thing in Ubuntu) and proceeded to attempt to install Ubuntu.
2. I got to the list of the available partitions, including the "free space" which is where I want to install Ubuntu. I clicked it and then "Next"; I got a message about not selecting a root or something. So I went back, selected the "free space" again, and clicked "Add".
3. This is the point where I was faced with a bunch of choices most of which I don't understand:

[LIST]
[*]      Primary or Logical?
[/LIST]

[LIST]
[*]      Location: Beginning or End?
[/LIST]

[LIST]
[*]      Use as:
[/LIST]
[INDENT]
[LIST]
[*]EXT4 journaling file system
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  EXT3 journaling file system
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  Ext2 file system
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  ReiserFS journaling file system
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  JFS
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  XFS
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  FAT 16
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  FAT 32
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                  SWAP area
[/LIST]
[/INDENT]
[LIST]
[*]      Mount Point:
[/LIST]
[INDENT]
[LIST]
[*]/
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /boot
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /home
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /tmp
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /usr
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /var
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /srv
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /opt
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]                         /usr/local
[/LIST]
[/INDENT]Another question that occured is: Should I also delete the Windows  partition that I intend to install Ubuntu applications to?

I am sorry to appear so dumb - perhaps someone who is conversant in both Windows and Ubuntu could put out a Windows to Ubuntu dictionary? Anyway, your continued help is most appreciated!

Thanks in advance for your help.

Sparky

---

### Post by nhasian on 2010-05-02
i'm a long time windows user as well.  I dont understand why you would want to create a separate partition for windows or ubuntu programs.  I would keep the OS & programs on the same partition, and the data on a separate partition.  In Ubuntu, all of your personal data is stored in /home.  so if you want to separate it you would make a 10 gig partition for / (root) and one more partition equaling the size of ram in your computer for the SWAP, and finally the remainder of the disk can be partitioned for /home.

/ (root) and /home should be EXT4 as that is the default filesystem in Ubuntu.

Please be advised you can only have four primary partitions per hard disk.  One of the Primary partitions can be an extended partition where you can further divide it into logical partitions.

---

### Post by The Cog on 2010-05-02
Like I said, if you delete the partition you wanted to install Ubuntu to, then next time you run the installer, it shoud offer the option to use the free space. It won't offer you that option if all the disk is already allocated to existing partitions. Letting the installer use the free space to create its own partitions is the easiest way to install Ubuntu.


That said, if you want to partition manually, here is my suggestion, assuming you have at least 40G to spare:

Create an extended partition in the space. An extended partition is one that can contain logical partitions, overcoming the restriction that hard disks can only contain 4 primary partitions.

In the extended partition, create 4 logical partitions:

1: A 10G partition to use as / - your main system partition.
2: Another 10G partition for future use (next version of Ubuntu?)
3: A 2G linux-swap partition, used for virtual memory
4: Another partition using the rest of the free space, use as /home - where all your data wil go.

There is a special partition type for swap partitions. For partitions 1,2,4, most folk would recommend using ext4, but I've had bad experiences with ext4 and the release notes for Ludid say they've had to do work-rounds to allow for problems with ext4. So I would recommend using jfs instead - it's been very reliable for me.

To illustrate what I mean, I attach a screenshot of gparted (available on the live CD when you choose to try Ubuntu) looking at the netbook I'm on now. You'll notice that the four Linux partitions are inside the extended partition. You might prefer to use gparted to create the partitions and then just tell the installer how to use them, rather than actually creating them with the less intiuitive partition editor in the installer program.

---

