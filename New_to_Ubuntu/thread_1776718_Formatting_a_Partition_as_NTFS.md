---
title: "Formatting a Partition as NTFS"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-06-06
I have an external HDD split into 3 partitions. 

One is my main Ubuntu partition, which contains all my Ubuntu goodies and my /home folder(s). Obviously, this is ext4.

The second one is NTFS on which I have files that I use for both Ubuntu and Windows.

The third one is quite small (3.5 Gb) that is currently formatted ext3 (or maybe ext4 - not sure). Originally, I had planned this to be my home partition, but that's way out of date now.

So, because I'm using up storage capacity bl00dy fast, I'd like to reformat that third partition to NTFS, so that Windows can see any files I put on there.

Obviously, I cannot do that in Windows, because Windows can't see the partition at all. So I need to do it in Ubuntu. But how?

(I have a feeling that Gparted might be the answer, but using that makes me horribly nervous!)

---

### Post by Mark Phelps on 2011-06-06
You can use the Partition Editor -- but it's not installed by default anymore.

Once you install it, ensure that the partition you want to manipulate is not mounted.

---

### Post by Dondermans on 2011-06-06
1. Move the files you would like to keep to a different partition.
1. Unmount the partition you intend to format.
2. Open Gparted
3. Right click on the partition you intend to format, click delete

The space will now show up as 'unallocated'. 

Close GParted, boot Windows, use the Windows tool to format the unallocated space as a NTFS-partition.

---

### Post by Roger Allott on 2011-06-06
I ended up using GParted, as suggested at [https://help.ubuntu.com/community/HowtoPartition/ReformattingPartition](https://help.ubuntu.com/community/HowtoPartition/ReformattingPartition)

Oh well, I don't think I've **completely** fugged up my PC!

---

### Post by Roger Allott on 2011-06-06
> **Dondermans said:**
> 
3. Right click on the partition you intend to format, click delete

The space will now show up as 'unallocated'. 

Close GParted, boot Windows, use the Windows tool to format the unallocated space as a NTFS-partition.

Ah. I hadn't spotted your post until after I'd gawn and dunnit all in GParted. D'OH!

What is the advantage of formatting the partition in Windows?

---

### Post by Dondermans on 2011-06-06
Ubuntu uses NTFS-3G to emulate NTFS support, but if you are presented with a choice between using Ubuntu and Windows, I think it would be a sound judgement to manage a filesystem from within its native environment. For NTFS that's Windows.

---

### Post by collisionystm on 2011-06-06
> **Dondermans said:**
> Ubuntu uses NTFS-3G to emulate NTFS support, but if you are presented with a choice between using Ubuntu and Windows, I think it would be a sound judgement to manage a filesystem from within its native environment. For NTFS that's Windows.


Agreed. I have never had a positive experience with any kind of NTFS that was formatted in UBUNTU. It did nothing but muck up the drive. NTFS is a product of Microsoft, therefore, it as the highest rate of success if done within windows.

---

### Post by Mark Phelps on 2011-06-07
I've never had a problem with NTFS-formatted partitions by  GParted when used for sharing data -- but Vista (and now, Win7) are notoriously picky about their filesystems when used for OS partitions.

But, to be safe, as others have already suggested, if you have the means, use MS Windows to format NTFS partitions.

---

### Post by Sidewinder1 on 2011-06-07
Not that it totally follows the topic of this thread, but I seem to remember a windows driver that, once installed in windows, allows at least read and maybe write too, to ext3/ext4 partitions; I can't remember, for the life of me, the name of it though; sorry...

Side

---

