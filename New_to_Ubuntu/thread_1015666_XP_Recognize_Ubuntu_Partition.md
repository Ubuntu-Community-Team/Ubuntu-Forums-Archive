---
title: "XP Recognize Ubuntu Partition?"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by thetrevorharmon on 2008-12-19
Hello! I've tried finding the answer to this question, but can XP recognize my Ubuntu partition? Can I install something so it can? It isn't right now. I'm running a dual boot xp/ubuntu with ubuntu 8.04

---

### Post by craigaa on 2008-12-19
Your Ubuntu partition is probably an ext3 partition.

Windows only natively supports FAT and NTFS partitions.

Fortunately, you can add ext3 support to windows using ext2ifs.

Please be warned, be careful how you use ext2ifs and make sure that you fully understand how it works and the implications.

Visit: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by hayden92 on 2008-12-19
No, Windows won't see partitions that are not formatted in FAT32 or ntfs.

---

### Post by AnimalMagic on 2008-12-19
Short answer - No! 

DiskInternals have a reader which can access Ext3 patitions from XP. There are also others available on the net.

---

### Post by jay li on 2008-12-19
I'm not sure but I think you could do that with third party software, which means it will cost you money. 
But wait, maybe someone else knows a better way.

---

### Post by mikeserv on 2008-12-19
Yes, it certainly can, but you'll have to install a driver for it.  You can look for ext2ifs, which is good, but it can have some problems with unusual partition sizes (something to do with rounding the number of blocks on the partition).  Or you can try ext2fsd (which is what I use, for the aforementioned reason).

You can find the first one, which is easier to install and set up, so long as it works, here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

And for the second, look here: [http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd](http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd)

Good luck!

-Mike

---

### Post by Michael.Godawski on 2008-12-19
hi
do you really need to access ext3 from windows?
This access in not really perfected yet.

Would not a usual share with the windows box suffice?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mikeserv on 2008-12-19
It's a dual boot situation, so no, he can't.  But your idea would be preferable, otherwise.

-Mike

---

### Post by talsemgeest on 2008-12-19
> **craigaa said:**
> Your Ubuntu partition is probably an ext3 partition.

Windows only natively supports FAT and NTFS partitions.

Fortunately, you can add ext3 support to windows using ext2ifs.

Please be warned, be careful how you use ext2ifs and make sure that you fully understand how it works and the implications.

Visit: [http://www.fs-driver.org/](http://www.fs-driver.org/)
Etx2ifs no longer works with Ubuntu-formatted ext3 partitions.

---

### Post by Michael.Godawski on 2008-12-19
> **mikeserv said:**
> It's a dual boot situation, so no, he can't.  But your idea would be preferable, otherwise.

-Mike
touché.:p

---

### Post by porchrat on 2008-12-19
Why not just create a small FAT32 or NTFS partition and place what you need to share in there?  Then Windows can read it.

---

### Post by zvacet on 2008-12-19
> Etx2ifs no longer works with Ubuntu-formatted ext3 partitions.

It worked for me few days ago.

---

### Post by talsemgeest on 2008-12-19
> **zvacet said:**
> It worked for me few days ago.
On a drive formatted through ibex?

---

### Post by zvacet on 2008-12-19
> On a drive formatted through ibex?

No,I have Hardy installed,but for some reasons I needed Windows couple days ago.I installed them and after that I used [http://www.fs-driver]("http://www.fs-driver.org/") and it worked.

---

### Post by talsemgeest on 2008-12-19
> **zvacet said:**
> No,I have Hardy installed,but for some reasons I needed Windows couple days ago.I installed them and after that I used [http://www.fs-driver]("http://www.fs-driver.org/") and it worked.
Yeah, the ext3 format seems to have changed with intrepid. When you try to read it with ext2ifs it comes up as an unformatted drive.

---

### Post by jerome1232 on 2008-12-19
Just to note all those tools that let Windows mount ext3 partitions are actually mounting the partition as ext2, so no journaling when working with the partition from Windows.

I would personally create a third data partition formated as ntfs, fat32 has a 4gb file size limit and ntfs has a journal so I do not see a reason to use fat32 over ntfs, then use it to share data between the two operating systems.

---

### Post by mike2357 on 2008-12-19
I've been using "Linux Reader", which is a third-party free product, and provides read-only access.  Web site:

[http://www.diskinternals.com/linux-reader/]("http://www.diskinternals.com/linux-reader/")

---

### Post by thetrevorharmon on 2008-12-20
So question, if I used the Ubuntu Live CD, and took like 4gb ish memory from the XP partition and formatted it with FAT as a "shared" partition, then both ubuntu and XP could recognize it? would XP freak out at all? i have it up to date.

---

### Post by logos34 on 2008-12-20
should work fine.

[http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32](http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32)

edit: now that I've read the entire thread, I think Talsemgeest is right.  

There's fs-driver for windows side (r+w ext2/3).  And ntfs-3g for linux (write support for ntfs), it's solid.  So there's really no need for you to make a separate fat32, although you can if you want and it will work fine

---

### Post by talsemgeest on 2008-12-20
Well since NTFS support has matured considerably in the last few years, it might be advisable to just use your xp partition instead of a shared partition. That way, XP will be able to read it and so will ubuntu, without having to make any new partitions.

---

