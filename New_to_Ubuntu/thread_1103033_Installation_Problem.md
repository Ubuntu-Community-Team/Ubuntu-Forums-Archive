---
title: "Installation Problem"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by daniell59 on 2009-03-22
I am trying to install ubuntu 8.10 on my second hard drive. 
This is my problem

No root file system.
Please correct this from the partioning menu.

I don't know what this means, or how to correct this.

Thanks

---

### Post by kaixi on 2009-03-22
What option did you choose in the partition manager wizard.

---

### Post by taurus on 2009-03-22
Did you already create partitions on your second harddrive before you tried to install Ubuntu on it?

---

### Post by daniell59 on 2009-03-22
I chose manual.
I left about 50 GIGs on my second hard drive for Ubuntu.

---

### Post by Sef on 2009-03-22
How did you install manually?  Please list the steps.

---

### Post by daniell59 on 2009-03-22
I just followed the screen. After the time zone, when it came to partitions, I selected to do it manually. I know that I am missing something.

Thanks

---

### Post by taurus on 2009-03-22
Make sure you mount whichever partition you want to install Ubuntu to as root filesystem--/.  That's why the installer is complaining because you forgot to mount that partition to /.

---

### Post by kaixi on 2009-03-22
Create 3 partitions:
1. Ext3 - Mount point: /      this is where the system files go. Unless you are going to install a lot of apps (games, software suites) 10-12GB should be enough.
2. Swap     - 1-2 GB
3. Ext3 - Mount point: /home   this is where your user files go. use the remaining space.

---

### Post by daniell59 on 2009-03-22
At this point, my knowledge is lacking.
I am somewhat confused. This is what I previouly did. I partioned my second HD. I gave about 100GIGs for my photos, etc, and left about 50GIGs of empty space for the Ubuntu installation. I am all ears. What should I do from here?

---

### Post by kaixi on 2009-03-22
Create a ext3 partition that uses your 50GB of space and set the mount point (important!) to /

btw, did you create a /home partition?

---

### Post by daniell59 on 2009-03-22
> **taurus said:**
> Make sure you mount whichever partition you want to install Ubuntu to as root filesystem--/.  That's why the installer is complaining because you forgot to mount that partition to /.

forgive my ignorance, how do I do this?

---

### Post by kaixi on 2009-03-22
Select the partition where you want to install ubuntu and click on Creat new partition. After that, a window will pop up. Select ext3 file system and / as the mount point.

---

### Post by daniell59 on 2009-03-22
> **kaixi said:**
> Select the partition where you want to install ubuntu and click on Creat new partition. After that, a window will pop up. Select ext3 file system and / as the mount point.

I assume this is when I am installing Ubuntu?

---

### Post by kaixi on 2009-03-22
> **daniell59 said:**
> I assume this is when I am installing Ubuntu?
Yes.

Now I'm a bit lost as well, what have you done so far with your hard drive?

---

### Post by daniell59 on 2009-03-22
What is a home partition?

---

### Post by kaixi on 2009-03-22
One of the coolest features of Linux is that you can keep all your user files in a separate partition.
A /home partition is a partition that will be automatically mounted by the system when it starts up and it's where all your user files will go. For example, your Desktop folder goes in the /home partition. It's also in this partition where you will store all your files (music, videos, documents, etc.) so if you're going to create one, make sure you give it plenty of space.

---

### Post by daniell59 on 2009-03-22
> **kaixi said:**
> One of the coolest features of Linux is that you can keep all your user files in a separate partition.
A /home partition is a partition that will be automatically mounted by the system when it starts up and it's where all your user files will go. For example, your Desktop folder goes in the /home partition. It's also in this partition where you will store all your files (music, videos, documents, etc.) so if you're going to create one, make sure you give it plenty of space.

To make a long story short, what should I pick when I partition,

As I previously mentioned the choices included.

/
/boot
/home
/tmp

Thanks

---

### Post by blandman3 on 2009-03-22
did you set your root directory when you partitioned?  sometimes you may have to run fdisk, because you need primary drive, logical drive, and extended drive.  You may need to create those in order for ubuntu to recognize the root!

hope this helps:popcorn:

---

### Post by presence1960 on 2009-03-22
> **daniell59 said:**
> At this point, my knowledge is lacking.
I am somewhat confused. This is what I previouly did. I partioned my second HD. I gave about 100GIGs for my photos, etc, and left about 50GIGs of empty space for the Ubuntu installation. I am all ears. What should I do from here?

why don't you do some reading so you can prep before installing Ubuntu. Here are a couple of good sources:

[http://ubuntuforums.org/showthread.php?t=500020&highlight=installation+tutorial](http://ubuntuforums.org/showthread.php?t=500020&highlight=installation+tutorial)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

By your own admission your knowledge is lacking. Reading some how to's will definitely make it easier for you. My first try at Ubuntu I didn't bother to read anything and my first install was a disaster- I lost all my data!

Sorry disregard the first link it is not the correct link. I can't find the correct one right now.

Ok found it with pics too! [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by daniell59 on 2009-03-22
> **blandman3 said:**
> did you set your root directory when you partitioned?  sometimes you may have to run fdisk, because you need primary drive, logical drive, and extended drive.  You may need to create those in order for ubuntu to recognize the root!

hope this helps:popcorn:

Sorry to say that I am lost.

This is what I did.(My knowledge is not great)
On my second drive, I allocated most of the space for my digital photos and etc.
I left about 50 GIGs of unallocated space for Ubuntu. Maybe you can make sense out of this. Thanks in advance.

---

### Post by blandman3 on 2009-03-22
Are you using windows at all to set up the partitions?

---

### Post by blandman3 on 2009-03-22
[http://ubuntuforums.org/showthread.php?t=1090095](http://ubuntuforums.org/showthread.php?t=1090095)

you may want to see this thread, it may be helpful.

---

