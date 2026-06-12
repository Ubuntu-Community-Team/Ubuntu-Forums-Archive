---
title: "Installing - Proper way to configure new Partition?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-13
I'm in the process of installing Ubuntu Studio, but I'm not sure what the proper way to configure the new partition I just made is.

Right now it's set as;

#3 primary  92.1 GB B f ext3   /home

Now, I'm setting up a dual-boot. Is this the proper configuration? If not, could someone tell me the proper way to configure the new partition?

Edit; It just occurred to me that including the other drives might be helpful.

#1 primary 8.0 GB      ntfs (this is the recovery drive for Vista)
#2 primary 150.0 GB    ntfs (this is Vista's drive. It was set as bootable prior to my configuring partition #3)

---

### Post by Paqman on 2009-04-13
You need to make at least two partitions to install Ubuntu. One is called swap and needs to be the same size as your RAM. The other is the main partition, called root or /.

/home is a slightly different animal. You can put /home on it's own partition, and a lot of people do because it's a very useful thing to do, but it will cause a problem for you. You can only have four partitions on a drive normally, so between two NTFS partitions, a swap, and an ext3 partition for / you've run out of partitions.

There is a solution. One of the four can be an extended partition which can contain further partitions inside it, breaking the four partitions rule. Obviously that adds a bit of complexity to your partitioning scheme though.

---

### Post by Shazaam on 2009-04-13
There are a multitude of ways (most of which involve personal preference) to partition drives. Here is a good dual-boot link...
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
The way I prefer to do it is to keep any Windows partition(s) primary then make an Extended partition in the remaining free (or unallocated) space. Then I make as many Logical partitions (including one for /swap) as I may need INSIDE of the Extended partition so as to keep from bumping into the 4 Primary partition limit. I don't make a separate /home partition but others swear by it.
This link may also help...
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by Noise... on 2009-04-13
What is the easiest way to set this up? I don't need anything fancy - I just want a straightforward install. 

I'll shrink the #3 down to 89GB to accommodate the swap partition. 

Basically, I have the install running now and I'm on the partition disk step, while using my brother's computer. He needs his computer back, and I need to be able to use mine again ASAP

So, do I keep #3 as bootable and as ext3? How do I configure it for  /?

---

### Post by Noise... on 2009-04-13
Also, will I want the Swap partition at the beginning, or end of the data?

---

### Post by Noise... on 2009-04-13
Anyone? I need advice on this ASAP!

---

### Post by WhiskyChris on 2009-04-13
As far as I know the only partition that needs to be bootable is the first partition on the disk, the bootloader (often called grub) which in turn actually boots your various OSes.

If you would like to keep #1 and #2 and turn #3 into ubuntu then one way would be something like make #3 an extended partition, inside of which you can either just tell the installer to do its own thing, or setup your own root, home, and swap partitions as logical partitions in there. Swap can be anywhere on the drive.

---

### Post by juancarlospaco on 2009-04-13
Whatever if you don't have Swap, works too, not highest performance but works fine.

---

### Post by Noise... on 2009-04-13
> **WhiskyChris said:**
> As far as I know the only partition that needs to be bootable is the first partition on the disk, the bootloader (often called grub) which in turn actually boots your various OSes.

If you would like to keep #1 and #2 and turn #3 into ubuntu then one way would be something like make #3 an extended partition, inside of which you can either just tell the installer to do its own thing, or setup your own root, home, and swap partitions as logical partitions in there. Swap can be anywhere on the drive.

Ok, so #3 will be the full amount of remaining memory?

How do I make it an extended partition, and what do I do to let the installer take over from there?

---

### Post by WhiskyChris on 2009-04-13
I can't remember exactly but I'm sure when you're installing you have to option to point the installer at some free space/a partition/the whole disk and tell it to automatically sort the partitioning out for you. The other option being to do it manually, which it seems is what you're asking about.

My suggestion was to make #3 an extended partition containing all the space you want to give to ubuntu (an extended partition can be thought of as an envelope partition). Inside this envelope you can create "logical" partitions which are the "actual" partitions of which you can have root, home, swap etc.

A basic google search for something like "install ubuntu partitioning" pulls up many pages such as [this one]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html") or [this one]("http://barot.wordpress.com/installing-ubuntu-810/") which guide you through the process.

---

### Post by Noise... on 2009-04-13
> **WhiskyChris said:**
> I can't remember exactly but I'm sure when you're installing you have to option to point the installer at some free space/a partition/the whole disk and tell it to automatically sort the partitioning out for you. The other option being to do it manually, which it seems is what you're asking about.

My suggestion was to make #3 an extended partition containing all the space you want to give to ubuntu (an extended partition can be thought of as an envelope partition). Inside this envelope you can create "logical" partitions which are the "actual" partitions of which you can have root, home, swap etc.

A basic google search for something like "install ubuntu partitioning" pulls up many pages such as [this one]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html") or [this one]("http://barot.wordpress.com/installing-ubuntu-810/") which guide you through the process.

So, with just the 92GB allocated as "free space," would the "Guided - use the largest continuous free space" partitioning method work it out for me without messing with the Windows partitions?

---

### Post by Noise... on 2009-04-13
Ok - I went ahead and selected guided on the free space, and it made two logical partitions - one for / and the other for swap. 

Am I good to proceed with the install? Id so, major :facepalm: at myself for not just doing that sooner. -_-

---

### Post by WhiskyChris on 2009-04-14
All sounds about right - I'm currently trying to sort out how I want to repartition at the moment, but I didn't think the out-of-the-box install was that complex!

---

### Post by Noise... on 2009-04-14
> **WhiskyChris said:**
> All sounds about right - I'm currently trying to sort out how I want to repartition at the moment, but I didn't think the out-of-the-box install was that complex!

Ubuntu Studio doesn't have the nice GUI that standard Ubuntu does, and the wording is a bit more confusing. This is my first experience with installing an OS or repartitioning. If I had known that "guided" would have just done it all for me, I'd have already been on Ubuntu two hours ago. 

Damn my overthinking mind. #-o

The partitions are formatting now. 

Thanks for the help!

---

### Post by WhiskyChris on 2009-04-14
Yeah I've not used Studio before, but glad you got it sorted in the end. I find in general things normally take more time than necessary, rarely less whatever the situation - it's a pain but it's the way of life!

---

