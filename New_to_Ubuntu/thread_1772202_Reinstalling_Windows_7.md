---
title: "Reinstalling Windows 7"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by aaron76 on 2011-05-31
I would like to run Propellerheads Reason on my laptop and I haven't been able to do this with WINE so far. If I get a copy of Windows 7, how do I go about creating a dual boot system?
Will the Windows cd give me that option when opened?
Thanks.

---

### Post by mikewhatever on 2011-05-31
No. You'll have to create a partition for it using a Linux live cd.

---

### Post by aaron76 on 2011-05-31
Okay. Thanks for the quick reply. I take it that means a fresh installation of Ubuntu, too.

---

### Post by mikewhatever on 2011-05-31
No, no need to reinstall Ubuntu. Just create an NTFS partition, use it for installing W7, and then use the Ubuntu CD again to fix/reinstall Grub.
[https://help.ubuntu.com/community/Grub2#SIMPLEST%20-%20Copy%20GRUB%202%20Files%20from%20the%20LiveCD](https://help.ubuntu.com/community/Grub2#SIMPLEST%20-%20Copy%20GRUB%202%20Files%20from%20the%20LiveCD)
Don't hesitate to ask if you need help or clarifications with any of that.

---

### Post by aaron76 on 2011-05-31
Thanks again. No doubt I will need more answers :-)

---

### Post by aaron76 on 2011-05-31
I partitioned the drive with the live cd. Now the partition reads "Unallocated space". I don't seem to be able to format it. Any ideas. Probably something silly I'm missing.

---

### Post by aaron76 on 2011-05-31
I managed to format the partition. I hope Windows will detect it as it's NTFS, though I'm not sure if that's how it works.

---

### Post by aaron76 on 2011-05-31
Sorry, one more question. Do I need to flag it as Bootable? Anything else I need to do after formatting it to NTFS?

---

### Post by Linux_junkie on 2011-05-31
You would have been better off installing Windows 7 first then Ubuntu.  That way Ubuntu will autimatically setup partitions for it to use and also the grub To be able to switch between the two OS's at boot.

---

### Post by Mark Phelps on 2011-05-31
> **aaron76 said:**
> Sorry, one more question. Do I need to flag it as Bootable? Anything else I need to do after formatting it to NTFS?

NO -- just install to that partition.  However, if offered the option to reformat that same partition, then do so.  Win7 (like Vista) can be picky about NTFS-formatted partitions.  If you let it reformat the partition, it won't complain later.

Also, it will overwrite your MBR and make itself bootable.

---

### Post by mikewhatever on 2011-05-31
> **Mark Phelps said:**
> NO -- just install to that partition.  However, if offered the option to reformat that same partition, then do so.  Win7 (like Vista) can be picky about NTFS-formatted partitions.  If you let it reformat the partition, it won't complain later.

Also, it will overwrite your MBR and make itself bootable.

+1.
W7's installer should be able to use the newly created ntfs partition. Install it, fix Grub, and you have a dual boot system.

---

### Post by aaron76 on 2011-05-31
Okay, thanks. I guess it would be easier to install Windows first and Ubuntu, but I have Ubuntu set up the way I want and I don't really want to install it all over again. 
Can I fix Grub with a live 10.10 cd even if I'm using 11.04? My Natty cd isn't working and I have a 10.10 cd here but I guess I can always download another...

---

### Post by BlueDon on 2011-05-31
Here's a pretty straightforward guide I found: [http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/)

Edit: This would involve a full reinstallation of both
[ ]("http://www.hackourlife.com/wp-content/uploads/2010/10/Ubuntu-10.10_0261.jpeg")

---

### Post by Mark Phelps on 2011-05-31
> **BlueDon said:**
> Here's a pretty straightforward guide I found: [http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/)

Edit: This would involve a full reinstallation of both
[ ]("http://www.hackourlife.com/wp-content/uploads/2010/10/Ubuntu-10.10_0261.jpeg")

Any Guide that even suggests using the Ubuntu installer or GParted to shrink a Win7 OS partition is asking for trouble ...

---

### Post by mikewhatever on 2011-05-31
> **aaron76 said:**
>  
Can I fix Grub with a live 10.10 cd even if I'm using 11.04? My Natty cd isn't working and I have a 10.10 cd here but I guess I can always download another...
Probably, although the two releases have different Grub versions.

---

### Post by aaron76 on 2011-06-01
Thanks for the help. In the end I installed Windows, then installed Ubuntu alongside it. Everything works fine so far.
Has anyone any idea where or if I can get the Grub themes? Not very important, but they look nice.

---

### Post by BlueDon on 2011-06-03
> **Mark Phelps said:**
> Any Guide that even suggests using the Ubuntu installer or GParted to shrink a Win7 OS partition is asking for trouble ...

good point

EDIT: Holy Berjebus, thought I'd just fell foul of that (played with GParted today - hadn't read your post). Fortunately, an increase in Windows Partition just prompted a chkdsk and nothing worse. Took a worryingly long time to boot, was more than a little anxious...

---

### Post by Jerry N on 2011-06-03
> **Mark Phelps said:**
>   Win7 (like Vista) can be picky about NTFS-formatted partitions.  If you let it reformat the partition, it won't complain later.

I have installed Win 7 in an NTFS partition created by Gparted several times without any problem.  I don't let Win 7 reformat the partition.  I generally pre-partition a drive with Gparted before installing any OS - Win2k, Win XP, Win 7, Linux.

Jerry

---

### Post by marsgorski on 2011-06-03
Hi have a similar problem. I had Ubuntu already in my computer and today I installed W7 in a new partition. Then, I used Rescatux to restore GRUB and now I can boot into Ubuntu again. The problem now is that GRUB is not seeing my Windows 7 partition. How do I fix this? It seems I have to edit menu.lst but I don't know how to do this. When I run sudo fdisk -l in the terminal I get this:

Disk /dev/sda: 160.0 GB, 160041885696
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size  (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb1710f3

    Device      Boot           Start             End              Blocks       Id               System
/dev/sda1                            1          15313     122995680+      83               Linux
/dev/sda2       *             15313         18719        27364352         7               HPFS/NTFS
/dev/sda3                      18720         19457         5927985         5               Extended
/dev/sda5                      18720         19457          5927953+     82              Linux swap / Solaris

Thanks for any help

---

