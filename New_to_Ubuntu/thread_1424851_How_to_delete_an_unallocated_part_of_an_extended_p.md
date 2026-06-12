---
title: "How to delete an unallocated part of an extended partition?"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Ubunser on 2010-03-08
I have an extended partition that consists of four smaller parts, two of which are empty now after I deleted Windows. Another two are used by Ubuntu. How do I contract/resize this partitions two the size which is actually in use and fortunately delete two unallocated ones?

---

### Post by koleoptero on 2010-03-08
sudo aptitude install gparted

Then run it from System > Administration > GParted. You can use that to delete unwanted partitions and resize existing ones.

I recommend you backup sensitive data first to another drive though. I've never had any issues with it but better to be safe than sorry.

---

### Post by oldfred on 2010-03-08
You can only edit unmounted partitions. If any part of the extended is mounted it all is. Generally it is better to edit partitions with the liveCD or download and use a gparted liveCD.

---

### Post by Ubunser on 2010-03-09
> **oldfred said:**
> You can only edit unmounted partitions. If any part of the extended is mounted it all is. Generally it is better to edit partitions with the liveCD or download and use a gparted liveCD.

So I guess this is where the problem is. I get the following message 

What shall I do? Is there a way to make changes. I am not sure I know how to edit partitions with live cd, I mean I am sure I don't. I have GParted

---

### Post by Sir Jasper on 2010-03-09
Hi,

You say you have gparted. Is that on your hard drive, or on a CD, or both?

Can you load gparted and just post a screenshot. Then we can explain in more detail and possibly make alternative useful suggestions?

My regards

---

### Post by Ubunser on 2010-03-09
> **Sir Jasper said:**
> Hi,

You say you have gparted. Is that on your hard drive, or on a CD, or both?

Can you load gparted and just post a screenshot. Then we can explain in more detail and possibly make alternative useful suggestions?

My regards

I have GParted on a Hard Drive. And I also have an Ubuntu 9.04 live CD.

---

### Post by Mark Phelps on 2010-03-09
You can't actually "delete" unallocated space; instead, what you can do is the following:
1) Move existing partitions to the left to consolidate the unallocated space
2) Resize the Extended partition to exclude the unallocated space -- now on the right.

You can't do 1) with your installed version of GParted because the partition is mounted.

You should download and burn a GParted LiveCD from distrowatch.com, boot with that, and since no partitions are mounted when you boot from that CD, you should be able to move and resize partitions without any problems.

---

### Post by psusi on 2010-03-09
You just run gparted from the livecd.

---

### Post by Ubunser on 2010-03-09
> **Mark Phelps said:**
> You can't actually "delete" unallocated space; instead, what you can do is the following:
1) Move existing partitions to the left to consolidate the unallocated space
2) Resize the Extended partition to exclude the unallocated space -- now on the right.

You can't do 1) with your installed version of GParted because the partition is mounted.

You should download and burn a GParted LiveCD from distrowatch.com, boot with that, and since no partitions are mounted when you boot from that CD, you should be able to move and resize partitions without any problems.
OK thank you I am rolling my sleeves up and gonna do everything you said and this will be a great experience. Thanks ever more

---

### Post by Ubunser on 2010-03-09
> **psusi said:**
> You just run gparted from the livecd.

Is this gparted live CD the same as Installation CD. I mean can I use my cd that you normally use to install ubuntu for my case with partitions? I once used it this way to reinstall grub when system whent unbootable, is this same case?

---

### Post by audiomick on 2010-03-09
Hi.
Two things would interest me:
What is on the Fat16 partition?
Why do you have /usr on a separate partition?

As has already been mentioned, backup anything important before you start moving partitions around.

Bear in mind that you can't "delete" unallocated space. The fact that the space is unallocated means that the deleting has already been done. What you mean, and what you want to do, is to fill it up. In effect, you want to expand the existing partitions to fill it, or create new ones in the empty space.

It is probably easiest to work from the live CD. If you haven't already found it, gparted is under system> administration. Your swap will be mounted in the live environment, but none of the other partitions should be. You can unmount the swap partition by, I think, right clicking on it and selecting unmount. It isn't hard to do, anyway.

If you are not planning on having a windows install on the drive, there is no reason that I am aware of not to move the start of the extended partition back to the start of the drive. Then it is just a matter of moving the start of the Fat16 ( I assume you want to keep it ) to the start of the extended partition, the end of the Fat16 to the size you want, the start of the next partition to the end of the Fat16, the end to the size you want, and so on.

As far as I know, 37GB is way more than you are likely to need for a /usr partition, although I don't know for sure what a good minimum size is. However, I don't think it really needs to be more than 6GB or so.

---

### Post by audiomick on 2010-03-09
> **Ubunser said:**
> Is this gparted live CD the same as Installation CD. I mean can I use my cd that you normally use to install ubuntu for my case with partitions? I once used it this way to reinstall grub when system whent unbootable, is this same case?
AS mentioned, gparted is installed on the Ubuntu live CD, and you can run it from there if you have an Ubuntu live CD. Gparted is also available as a stand alone live CD, i.e. a bootable CD that only has Gparted on it. This is an alternative to using the Ubuntu live CD.

---

### Post by Sir Jasper on 2010-03-09
Hi,

It seems to me there is no vital urgency and oldfred is a mine of information and good ideas so you might like to await his or other suggestions.

Meanwhile, it would probably help to know if you are planning to use masses more space for music, videos or whatever.

My regards

PS If you have only just installed ´buntu it may be easier to start scratch but you have to be careful not to lose your data and you still have to to decide how best to organize and size your partitions [although you could still make later changes].

My advice would be to keep making  clones or images [for easy recovery and peace of mind] as you you make progress and get ´buntu as you like it. 
You might backup anything important as well.

---

### Post by Ubunser on 2010-03-09
> **audiomick said:**
> Hi.
Two things would interest me:
What is on the Fat16 partition?
Why do you have /usr on a separate partition?

Fat16......I hav no idea how it was created, the only thing I do know is I formatted it to fat16 just to play with it. The /usr I created myself because one blogger explained so on his blog, I guess I won't need that much space too

---

### Post by audiomick on 2010-03-09
> **Ubunser said:**
> Fat16......I hav no idea how it was created, the only thing I do know is I formatted it to fat16 just to play with it. 
OK. If there is no valuable Data in there, I would suggest ditching it. The Fat16 file system is effectively outdated, and only really useful to you if you want to access the partition from a Windows install. Even then, NTFS would be better. If you don't need to keep it for any reason, just erase it.
> 
The /usr I created myself because one blogger explained so on his blog, I guess I won't need that much space tooI am not too sure of the reason for having /usr separate, and can't find it in the Docs off hand, but we'll leave that for now. I would suggest thinking about moving your /home to a separate partition though, since you are already doing partitioning changes. Here is some reading that might help you

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by srs5694 on 2010-03-09
A couple more comments:

First, you might want to consider using Logical Volume Management (LVM). In this scheme, filesystems go in logical volumes within LVM partitions, rather than in partitions directly. The advantage is that logical volumes can be managed much like files, so you don't need to worry about moving them around and positioning them in the way you do with partitions. From your current configuration, you can add any empty partitions to an LVM setup and migrate most of your system to use LVM, then not worry about partitions and their locations. With GRUB Legacy, you only need /boot on a dedicated filesystem partition; everything else can go in the LVM. With GRUB 2, even /boot can go in an LVM (or so I hear; I've not tried it myself). The drawback to all this is increased complexity, and the learning that goes with it.

Second, you might consider switching from MBR to GPT as your partitioning system. GPT does away with the primary/logical distinction entirely, so if you convert your disk to GPT, there'll be no need to resize the extended partition, since it will no longer exist. Ubuntu works fine with GPT, but if you do a "live" conversion (using tools like [gptgen]("https://sourceforge.net/projects/gptgen/") or my own [GPT fdisk](http://www.rodsbooks.com/gdisk/)), you'll need to re-install your boot loader.

Both of these solutions will work nicely on a Linux-only system, but if you multi-boot your computer, there may be issues. Linux's LVM system is understood only by Linux, AFAIK; and although GPT is understood by most modern OSes, Windows can't boot from it, and older OSes don't understand it at all.

---

### Post by Ubunser on 2010-03-09
> **srs5694 said:**
> A couple more comments:

First, you might want to consider using Logical Volume Management (LVM). In this scheme, filesystems go in logical volumes within LVM partitions, rather than in partitions directly. The advantage is that logical volumes can be managed much like files, so you don't need to worry about moving them around and positioning them in the way you do with partitions. From your current configuration, you can add any empty partitions to an LVM setup and migrate most of your system to use LVM, then not worry about partitions and their locations. With GRUB Legacy, you only need /boot on a dedicated filesystem partition; everything else can go in the LVM. With GRUB 2, even /boot can go in an LVM (or so I hear; I've not tried it myself). The drawback to all this is increased complexity, and the learning that goes with it.

Second, you might consider switching from MBR to GPT as your partitioning system. GPT does away with the primary/logical distinction entirely, so if you convert your disk to GPT, there'll be no need to resize the extended partition, since it will no longer exist. Ubuntu works fine with GPT, but if you do a "live" conversion (using tools like [gptgen]("https://sourceforge.net/projects/gptgen/") or my own [GPT fdisk](http://www.rodsbooks.com/gdisk/)), you'll need to re-install your boot loader.

Both of these solutions will work nicely on a Linux-only system, but if you multi-boot your computer, there may be issues. Linux's LVM system is understood only by Linux, AFAIK; and although GPT is understood by most modern OSes, Windows can't boot from it, and older OSes don't understand it at all.

I actually am going to multi-boot, and I'd would have been using FreeBSD and Ubuntu together on my laptop for a fortnight by now if I knew how to configure grub to show BSD when booting. This is what I am working at currently< but I need to organize my partitions finely so that it would look like German approach))))

---

### Post by audiomick on 2010-03-09
> **Ubunser said:**
> ...so that it would look like German approach))))
Ordnung muß sein, oder? A good idea, actually. I tried to be as orderly as possible when I set mine up, but I still have to think really hard about what I put where...;)

---

### Post by Ubunser on 2010-03-09
Ok, here's what I got now. But that's not the end. Somebody told this is stupid to have /usr on a separate partition? so how do I transport it to the first partition?

---

### Post by audiomick on 2010-03-10
Hallo.
Having a separate /usr is not stupid as such, in as much as it wont cause you any problems as long as it is big enough. It is just most likely not any advantage to you. I don't really know in which circumstances it might be an advantage, but I think either on a server with lots of users or on a machine with lots of different OSs installed. Anyway, given that if you mess up trying to move it, you are likely to really seriously shoot down your system, I would just shrink it to a reasonable size and leave it for now.

In the situtation you are now in, I would also create a separate /home as described in the link I posted earlier. This is not as "dangerous" as moving /usr, I think, and does bring direct advantages. The main one is, when you next want to do a fresh install (don't doubt it, the day will come...) you can just remount the /home partition, thereby retaining all your user settings and data.

So, just to make sure:
What is now sda5 is your / partition, isn't it? And the one that is /usr is sda3 ?

**If you want to try creating a separate /home:**
You could shrink /sda5 down a bit more if you want. With a separate /home, you only need around 15GB for /. Mine currently has around 6GB in it.
While you are at it, you might want to increase your swap a bit, if you want the Hibernate function to work. Hibernate needs a swap partition a little larger than the amount of RAM you have. If you don't need the Hibernate function, the swap is big enough.
The catch is, you would want to create your new /home and have that transfer completed before you shrink down the / partition.
I would try it this way:
Move sda3, your /usr, down to the end of the drive and shrink it to about 8GB. I don't know for sure, but I think this is still more than enough to go on with.
Create a new /home (following the directions in the link I posted) in the unallocated space.
You could leave it at that, or go on with
Shrink sda5 down to around 15GB, leaving the emtpy space to the right of it.
Move the swap across next to sda5.
Shrink the extended partition down so that there is no more space inside.
Extend the new /home to the left to take over the empty space.

**If you don't want to make a separate /home:**
This is a lot simpler, but means that when you next do a fresh install you will have more work if you want to retain all your settings.

Move your sda3 down to the end of the drive and shrink it down to around 8GB or so. Once again, I don't know for sure, but I think this will be more than enough.
( you could also move it to the left so it is adjacent to the extended partition, but if you have to juggle partition sizes again at a later date, I think it would be more flexible if it were at the end of the drive).

Create a new partition in the empty space.
Mount it at a mount point of your choice, and store all of your Data in there rather than in /home. You can, amongst other things, change the default save path of most applications to a location of your choice, so it is no big deal to make them save to a Data partition instead of in /home, the default setting.

Here is some info on mounting
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

I hope this helps you. I know it is a lot of words...;)

---

