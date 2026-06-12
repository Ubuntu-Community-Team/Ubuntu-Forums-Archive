---
title: "How do I give my Ubuntu partition more space?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Dimitri_Sumlanacht on 2009-11-18
I have just recently installed Ubuntu 9.10 due to all the major bugs in Windows XP along with a rather nasty virus I got in Windows that rendered it pretty much useless.  During installation of Ubuntu I only allotted about 5 gigs of space for the Ubuntu hard disk space and the other 198 or so still sits on the Windows side of the system.  I did this because I still had a lot of things on the Windows side (music, texts, games, ect.) that I did not want deleted with a formatting of the drive, but now I wish to take away space from the Windows side (about 40 or 50 gigs) to make room for more space on the Ubuntu side and I have no idea of any easier way to do this other than uninstalling Ubuntu and then reinstalling it with my wish for space in mind.  So, in short, is there any way for me to move hard disk space from the Windows side to the Ubuntu side without having to do a complete reinstall?

If you can help me with this you are my dear hero. :D

And yes, I am a COMPLETE n00b to Linux and computer coding in general, but I sure do want to learn.

---

### Post by Cheezespread on 2009-11-18
I believe you can free some space from Windows using some partition manager and then use Gparted to extend your current space with that newly unallocated free space. ( I am not sure if that would work ) .

ANyway , you can move data from your old partition to the newly created one.

---

### Post by Elfy on 2009-11-18
Yep - boot with the livecd and you can use the partition editor.

You'll need to shrink the windows partition and then expand the extended partition before you can expand the ubuntu partition, that does though assume you did a default installation. 

If you open a terminal and run 

```
sudo fdisk -l
```

you will find out the partitions you have on your system.

Edit - [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

whole bunch of information there 

It is likely you will need to resize, move 

Also right click the swap partition in the partition editor and turn off swap before you start.

---

### Post by Dimitri_Sumlanacht on 2009-11-18
Where do I find this partition manager?  and do I need to download Gparted or does it come with Ubuntu?

---

### Post by Dimitri_Sumlanacht on 2009-11-18
Thanks Mr. (or Mrs.?) Piskie.  I am going to try that now.

---

### Post by RandomP on 2009-11-18
Gparted is on the liveCD that you used to install ubuntu.

---

### Post by kansasnoob on 2009-11-18
> **Dimitri_Sumlanacht said:**
> Where do I find this partition manager?  and do I need to download Gparted or does it come with Ubuntu?

You'll need to use the Live CD. Gparted is there in System > Administration either under the name Gparted or Partition Editor.

I would first defrag Windows, and I never like to "use" more than about 75% of a Windows partition.

The most helpful thing to give you more specific instructions would be a screenshot of Gparted.

---

