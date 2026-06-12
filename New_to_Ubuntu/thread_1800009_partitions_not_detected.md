---
title: "partitions not detected"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Dr.Joker on 2011-07-08
Hi guys,

I have an external hard drive with about 1 TB of data on it that is important to me. I have two computers. One of them runs Windows 7, the other Ubuntu. When I connect the hard drive to the Windows 7 machine, everything works very smoothly, I can read from it, I can write to it, everything without any problems. It's formatted in NTFS.

However, when I plug it into my other machine, Ubuntu detects it, however I cannot mount it or read or see any data on it, because it detects the whole things as unpartitioned space. Before I do anything it asks me if I want to format it with the master boot record. The same thing also happens if I plug the hard drive into windows 7 on another machine.

Now the problem is, I want to format my first computer, but before I do that, I need to find a way to read the data from my external hard drive on other machines as well. Any suggestions?

---

### Post by Blasphemist on 2011-07-08
I'm thinking that on the machines that can't use the big drive, they already have 4 primary partitions. On ubuntu you can use GParted to determine if that is the case. I'm not in windows right now so I can't give you exact steps but windows disk management will also allow you to see what partitions you have. 4 primary partions is the max and an extended partition counts as a primary. Machines that have used up the primary partitions can often be changed by removing a partition that is no longer needed. For example, I no longer needed the windows recovery partition that would allow me to restore my disk to it's original state, vista. This is because I'd upgraded to win 7 when it came out.

---

### Post by srs5694 on 2011-07-08
It's conceivable that the drive is unpartitioned and just uses a "raw" filesystem. To be certain, try these two commands:

```

sudo blkid /dev/sdb
sudo fdisk -lu /dev/sdb

```

Change "/dev/sdb" to the device's true name, if it's not /dev/sdb. The first command will return one line of information on the filesystem if my hypothesis is correct or nothing if the disk is partitioned. The second command will return information on the partition table if the disk is partitioned or nothing if it's not.

If the disk is used "raw," the simplest solution is to mount it manually:

```

sudo mount -t ntfs-3g -o uid=1000 /dev/sdb /mnt/usb

```

As with the other commands, change /dev/sdb to the device's correct filename, if necessary. Also, this command gives ownership of all files to the user with UID 1000. This is normally the first user you created for Ubuntu, but you may need to adjust it if you've created other accounts, else you'll only be able to access the disk as root.

---

### Post by Wim Sturkenboom on 2011-07-08
> **Blasphemist said:**
> I'm thinking that on the machines that can't use the big drive, they already have 4 primary partitions.I thought that the 4 primary partitions apply to each drive. So an external drive can again have 4 primary partitions.

---

### Post by Blasphemist on 2011-07-08
> **Wim Sturkenboom said:**
> I thought that the 4 primary partitions apply to each drive. So an external drive can again have 4 primary partitions.

My bad, you are right. [http://technet.microsoft.com/en-us/library/dd799232(WS.10).aspx#PartitionRules](http://technet.microsoft.com/en-us/library/dd799232(WS.10).aspx#PartitionRules)

So now I'm anxious to see the results of what was posted just prior to yours.

---

### Post by Dr.Joker on 2011-07-08
Thanks for your suggestions guys. I'll give this a try once I get home. When I originally bought it, I formatted the whole drive in NTFS format, and created one big partition which I named 'Data'. I hope mounting manually will work.

---

### Post by candtalan on 2011-07-08
> **Dr.Joker said:**
> Hi guys,
I have an external hard drive with about 1 TB of data on it that is important to me. I have two computers. One of them runs Windows 7, the other Ubuntu. When I connect the hard drive to the Windows 7 machine, everything works very smoothly, I can read from it, I can write to it, everything without any problems. It's formatted in NTFS.
However, when I plug it into my other machine, Ubuntu detects it, however I cannot mount it or read or see any data on it, because it detects the whole things as unpartitioned space. Before I do anything it asks me if I want to format it with the master boot record. The same thing also happens if I plug the hard drive into windows 7 on another machine.

Now the problem is, I want to format my first computer, but before I do that, I need to find a way to read the data from my external hard drive on other machines as well. Any suggestions?

My recent experience of similar problems suggest that the ntfs is somehow damaged. Ubuntu presumably does not take short cuts in this situation, but Windows will be more confident, it even did not warn me. However, I ran Windows and did an errors check and repair (chkdsk I think?) and it all worked again. Beware, I think some situations with errors may cause loss of data. Also consider the possibility that supposed ntfs damage might be caused by a failing drive.

Good luck.

---

### Post by wildmanne39 on 2011-07-08
Hi,one other thing that I learned from my own experience is if you did not properly eject or unmount the drive from your windows system, it will cause this issue, if that is the case you can enter it with windows and properly disconnect it and it should work, if nothing else is wrong.

---

