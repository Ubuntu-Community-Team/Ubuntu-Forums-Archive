---
title: "File System Question"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by aufde on 2010-02-11
I'm really new with ubuntu, and just updated it to 9.10. I installed it a while back and just started using it again. I have windows vista as the primary OS. After vista was installed, I made a new partition to install ubuntu onto. All the OS files are on the second partition, but when I try saving something in the ubuntu file system that is greater than the free space on the vista partition, it doesn't let me. 

So my question is, how do I change where the file system is, or what the default save partition is? I can't even see the second partition or get to it, so I can't save to it at all.

Thanks.

---

### Post by nick_goodfate on 2010-02-11
you can see the second partition(ubuntu partition) if you have boot in windows . from ubuntu you can see both ubuntu and windows partition .

---

### Post by Mustard on 2010-02-11
How much free space have you got on the Vista partition?

..and how much free space is on the Ubuntu partition?

I'm just curious, because it sounds like you would have to make a third partition, perhaps using some free space from your Ubuntu partition, if you are going to be able to do the things you want to do.  The third partition would be using the FAT filesystem which could be read by both linux and windows.  You would also need to keep in mind that the FAT filesystem cannot handle a file size of over 4 gb for a single file.  If you are trying to save a single file of over 4gb then the idea I am thinking of won't work at all.

If it was just a case of you wanting to move files between the two, you could download some windows software that would allow windows to see your linux filesystem.  The problem is that you would have to do this in two steps, first download the data to windows then move it to linux.  Given that you are lacking free space on your windows partition, this makes this operation impossible, without a third partition of sufficient size to save your large quantity of data in.

Alternatively, if you have plenty of space in your Ubuntu partition, you could do download some windows software to access your linux partition, then do some housekeeping by way of moving some of your other files over to your linux partition, thereby creating sufficient free space on your Vista partition to save this large file on to.

---

### Post by aufde on 2010-02-12
I have 12.5GB free on my Vista partition, and 79.2GB free on the Ubuntu partition.

What I'm trying to do is move my WoW folder(18GB) from the Vista partition over to the Ubuntu partition. I'm trying to get it to run through Wine, and I read that if it is already installed in Windows, you can copy the files over to the Ubuntu side for it to work. So I found the folder in the Vista partition while booted in Ubuntu and tried copying them over, but it said not enough free space.

When I'm booted in Vista, I can access the second partition like I could any partition. It doesn't recognize that there is an OS installed onto it. I can copy files between them freely while booted in Vista, but I can't even find the second partition while booted in Ubuntu.

---

### Post by lotharmat on 2010-02-12
As far as I know - and I may well be barking up the wrong tree here; Windows may well require as much free space to copy a file as the file itself.

---

### Post by 3rdalbum on 2010-02-12
> **aufde said:**
> When I'm booted in Vista, I can access the second partition like I could any partition. It doesn't recognize that there is an OS installed onto it.

That's very odd, because Vista should not be able to read a partition that Ubuntu resides on. Ext3 and Ext4 are Ubuntu's default filesystems, and neither are readable in Vista.

Did you boot up your computer from the Ubuntu CD to install Ubuntu, or did you put the CD in while Windows was running and use the installer program from there? If the latter, then you have not installed Ubuntu onto its own partition, you have merely installed it into a file on some other partition. The Ubuntu file may be taking up 75 gigabytes or something on a 90 gigabyte partition.

We can probably clear this up by getting you to run this command in the Ubuntu terminal (Applications > Accessories > Terminal):

```
sudo fdisk -l
```

and then post the result here.

---

### Post by aufde on 2010-02-12
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6860e0c3

Device        Boot      Start         End      Blocks          Id    System
/dev/sda1               1              1275     10240000     1c    Hidden W95 FAT32 (LBA)
/dev/sda2      *       1275         20732   156284928    7     HPFS/NTFS
/dev/sda3               20732       38914   146044928    f      W95 Ext'd (LBA)
/dev/sda5               20732       38914   146043904    7     HPFS/NTFS

I don't remember if I installed it through Vista or booted from the disk, it was a long time ago when I installed it.

---

### Post by Mustard on 2010-02-13
I don't see any linux partitions in that at all.  Not even a swap partition.

My guess is that you installed using Wubi?

It must be installed inside the windows partition.

---

### Post by jken146 on 2010-02-13
Is there a file /host ? If there is, you've used wubi.

---

### Post by 3rdalbum on 2010-02-13
No Linux partitions reported - so you've installed Ubuntu within a file, by using the Windows-based installer (Wubi).

Wubi allows a limit of either 15 or 30 gigabytes, if I remember correctly; which probably explains why you can't copy an 18 gigabyte folder into Ubuntu.

Remove Ubuntu using the Windows Add/Remove Programs, boot from an Ubuntu CD and install Ubuntu this way onto the free partition (or tell the installer that you want to resize Windows and create a new partition, if you don't have one already available).

---

### Post by aufde on 2010-02-13
Ok, thanks. I guess ill need to reinstall.

---

