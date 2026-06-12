---
title: "Used space on new drive"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by gallifrey on 2010-02-10
Hi,
    just moved over to Ubuntu Karmic (AMD 64) from Windows, and so far so good. One problem i am having though is that I have a 250 GB external hard drive which I have just formatted to ext4, and it is reporting that 11.8 GB of it is used, even though I have not transferred any files to it yet. 

while I was formatting using mkfs.ext4, it mentioned that 5.00 % was being allocated to Superuser. On checking the drive in nautilus, there seems to be folder called 'Lost+found', which cannot be accessed. Is there anyway to stop this space being taken, or at least, reduce how much space is taken??

Any help would be really appreciated. Thanks :)

---

### Post by RedSingularity on 2010-02-10
If you start nautilus as a Super User can you look inside the lost and found?

---

### Post by gallifrey on 2010-02-10
> **RedSingularity said:**
> If you start nautilus as a Super User can you look inside the lost and found?

I have had a look inside the folder, and it appears to be empty.

---

### Post by RedSingularity on 2010-02-10
Have you tried formating it with another File System and see if that makes a difference?

---

### Post by Miljet on 2010-02-10
Lost+found is simply a directory where lost file fragments are placed when the disk is checked. It will be empty on a new disk. As far as I know, there is no way to remove it.

When you format a new disk a certain portion of the disk is reserved for the file allocation table so files can be found when the disk is used. On a small drive the space used is insignificant, but on larger drives the space used is quite noticeable. It is just the "overhead" of the file system.

You might try a different filesystem. Some have smaller overhead requirements. But they all will require some space for managing the files.

---

### Post by gallifrey on 2010-02-11
Many thanks Miljet and Red Singularity. I will try with a different file system, but at least I have learned something new. :)

---

### Post by philinux on 2010-02-11
> **gallifrey said:**
> Many thanks Miljet and Red Singularity. I will try with a different file system, but at least I have learned something new. :)

A formatted ext4 partition can have it's reserve space modified by using the command tune2fs.

```
sudo tune2fs -m 0 /dev/xxx

```
Would set this to zero. I think I would use 1%.

If you chose to use ext2/3/4 you should also be aware of reserved space. By default ext2/3/4 will reserve 5% of the drives space, which only root is able to write to. This is done so a user cannot fill the drive and prevent critical daemons writing to it

From
[http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/](http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/)

Section 3.

---

### Post by gallifrey on 2010-02-11
> **philinux said:**
> A formatted ext4 partition can have it's reserve space modified by using the command tune2fs.

```
sudo tune2fs -m 0 /dev/xxx

```Would set this to zero. I think I would use 1%.

If you chose to use ext2/3/4 you should also be aware of reserved space. By default ext2/3/4 will reserve 5% of the drives space, which only root is able to write to. This is done so a user cannot fill the drive and prevent critical daemons writing to it

From
[http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/](http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/)

Section 3.

Thank you so much! That has solved my problem perfectly. I had a 1.5 TB drive to add, but was worried about that chunk of space being taken, as I will fill it really quickly.

---

### Post by philinux on 2010-02-11
> **gallifrey said:**
> Thank you so much! That has solved my problem perfectly. I had a 1.5 TB drive to add, but was worried about that chunk of space being taken, as I will fill it really quickly.

Nice one.

Please mark this thread as solved using the thread tools pull down.

---

