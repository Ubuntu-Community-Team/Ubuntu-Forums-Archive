---
title: "Dual booting with Windows 7 in a laptop with multiple NTFS partitions"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by collisio on 2010-11-17
Hi guys, I've got a laptop with a clean installation of Windows 7 Ultimate. I've made 3 NTFS partitions and installed Windows into C: which has 40GB space. Planning use D: (40GB) as an installation drive (MS Office, Photoshop, etc..), while E: (60GB) will be used for my personal files. 
 
Now I want to dual boot with Ubuntu 10.04. Already checked out few tutorial and found them to be quite usefull, but unfortunately non had what I was quite looking for.
 
Can I install Ubuntu into my C: after shrinking it to make some space?
 
Then can I install my Lynux based software programs (Gimp, Thunderbird, etc,..) into my D: as the way it is now? (Evan I have to shrink the drive to allocate some space for Ubuntu file system, I'm happy with it).
 
Then can I use E: for data storage, like I'm planning to do with Windows?
 
 
And if this all goes well, is there a way to access programs compatible with both operating system like Firefox or OpenOffice from both operating systems, the program being installed only once in the system through either of the two operating systems?
 
 
Thanks in advance guys for helping out this poor soul...

---

### Post by sikander3786 on 2010-11-17
Hi and Welcome to the forums:)

Yes you can install Ubuntu in the space freed up by shrinking C: drive. Use the Windows 7 tool for shrinking and run chkdsk on that drive before proceeding.

You can't install Ubuntu software on an NTFS partition. The only way you can use a NTFS drive in Ubuntu is to use it for sharing data between Ubuntu and Windows.

You can use your E: NTFS drive for data storage.

You'll need to install all the software separately in both the OS. No method of sharing Firefox or OpenOffice or anyother between the two OS :-)

You'll need to create at least 2 partitions in the freed up space i.e,

1. / partition. Filesystem Ext4. Recommended size >8 GB at least.

2. Swap partition. Size = RAM X 2.

---

### Post by Jeanke on 2010-11-17
Hi,

1. Yes, you can shrink C: and create a new partition for Ubuntu installation (but dont make your C: too small or you will get in trouble with Win 7 I think).

2. No, you cannot install ubuntu software on your D: (being NTFS).
You can also shrink down D: and create a new partition (ext2/3/4) for ubuntu software installations. You will have to mark this partition as /usr I think (correct me if I'm wrong).

3. Yes, you can use E: (NTFS) as data storage.

4. No, you cannot use for example a Windows firefox installation in Linux or the other way around, it will have to be installed twice.

Grtz

---

### Post by collisio on 2010-11-17
Thank you so much guys for your quick replies. I think I've got a pretty good idea now. But do you think it's better to leave C: for Windows and it's program installations (MS Office, Photoshop...) and convert the now NTFS D: into Ubuntu file system and install Ubuntu 10.04 and its native programs (Gimp, amaroK...), rather than repartitioning current C: for both operating systems and repartitioning current D: for programs of the 2 operating systems?Thanks.

---

### Post by sikander3786 on 2010-11-17
Yes it would be better to free up some space else where so whatever chance of corrupting Windows is there, you can reduce it.

I think the best option will be to boot into an Ubuntu Live CD and go to Applications > Accessories > Terminal and post the output of

```
sudo fdisk -l
```

and

```
df -h
```

We will have a better idea that way and will be able to advise better.

---

### Post by Jeanke on 2010-11-17
Hi,
youre welcome ;-)

In my personal opinion the idea to use just 3 partitions, Windows, Ubuntu and Data, is good. I have a same setup on my PC.
However, if you would choose for that I would increase the Windows partition (C) to 50gb and use the 30gb that is left for the Ubuntu partition (or maybe even 60/20gb).

Ubuntu doesn't need 40gb and Windows tends to take a lot of space.
My windows partition has now 30gb used space with only Photoshop and MS Office installed (no other programs) and increasing everytime I boot in Windows due to update installations (I have to say I use Windows rarely).
My Ubuntu partition is just 15gb (without swap) and only 5gb is used while I have several additional software installed.

Regards,

---

### Post by oldfred on 2010-11-17
I like keeping things as separate as possible. Use a shared NTFS partition for any data you want in both windows & Ubuntu. I shared my Firefox & Thunderbird profiles in my shared NTFS partition. I do not write, but do read, to my windows system partition. Many windows users suggest a separate data partition for windows, so when you reinstall windows you do not have to reinstall your data. But you still need good backups and run chkdsk every so often like Ubuntu's fsck every 30 boots.

Also use windows tools on windows partitions, but do not attempt to create additional partitions for linux in windows. It may auto convert you from basic to SFS (windows proprietary logical partitions) and then you cannot convert back easily. Use gparted or any other partitioning tools for Linux.

---

### Post by Mark Phelps on 2010-11-17
You should probably start by using the Win7 Disk Management tool to look into shrinking the OS partition.  It will not let you shrink it too far -- but be advised that with only 30GB allocated, you're not going to get much shrinkage.  In my experience, 20GB is about the absolute minimum for a working Win7 installation.

---

### Post by collisio on 2010-11-18
Thanks a lot guys... I've done it;) and both os's working fine. One problem though, how do I connect to the home wireless internet?

It's a HP Pavillion tx1250ea laptop with Broadcom BCM4328 network controller. 

Cheers

---

### Post by Mark Phelps on 2010-11-18
> **collisio said:**
> Thanks a lot guys... I've done it;) and both os's working fine. One problem though, how do I connect to the home wireless internet?

Answers:
1) Start a new thread.  This new problem has nothing to do with dual-booting.
2) Mark this thread as SOLVED.

---

