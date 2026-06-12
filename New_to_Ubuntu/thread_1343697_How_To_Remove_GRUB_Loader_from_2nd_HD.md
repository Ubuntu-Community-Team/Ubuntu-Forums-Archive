---
title: "How To Remove GRUB Loader from 2nd HD?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by SyntaxError77 on 2009-12-02
Hi All,
 
I am having a bit of a problem with my hard drives. I have 1 x 40gb SATA drive and 1 x 160gb IDE drive in my system.
 
I deleted all of the partitions on both hard drives. 160gb is formatted with NTFS and holds my music/videos etc.
 
40gb Hard has been formatted with ext3 and fresh install of Ubuntu. However, when I restart the PC, I get Error 17 on the grub loader. I found that the PC is booting to 160gb first, then 40gb.
 
So, I boot to 40gb first and all is OK, but I don't know why there is a grub loader on the 160gb, which is supposed to be NTFS?
 
How can I remove the grub loader from the 160gb drive? I don't need two grub loaders!

---

### Post by fancypiper on 2009-12-02
Boot with your windows install disk and run fixmbr.

[Microsoft instructions]("http://support.microsoft.com/kb/314458/EN-US/)

---

### Post by SyntaxError77 on 2009-12-02
I need to use fixmbr, even though I don't want any Microsoft OS on my system?
 
If I have to run fixmbr everytime I format the drive with NTFS, is it better to use another file system?
 
Bearing in mind that the drive is a media storage drive I would use FAT32, but the 4gb limit is a pain.

---

### Post by Gene Rodgers on 2009-12-02
You definately have a problem, My slave HD is 200gig and I used windows to format it fat 32 so I could recover the files should windows crash. You cannot use any dos based system to recover NTFS files. Fat 32 works fine with linux so why would you want NTFS for music/video storage?

Gene - w5ffa

---

### Post by falconindy on 2009-12-02
Are you still on 9.04? Can you boot off a liveCD and post the contents of your /boot/grub/menu.lst as well as the output of `sudo fdisk -l`?

You haven't provided a lot of info, but it sounds to me like GRUB is only loaded on 1 drive. But, when it loads, it then tries to point at the media drive, presumably because UUIDs aren't used to identify the drives.

Will the computer boot if you unplug the 160gb drive, either physically through or BIOS?

---

### Post by oldfred on 2009-12-02
I cannot recommend that you use FAT except for USB keys any more. I had a FAT32 for sharing between windows & Ubuntu but lost all files over 4GB and at the time did not know that was a limit.

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

IF you can boot ok having a "wrong" MBR in the other drive should make no difference. It takes up no space and unless you try to boot from it, It will not cause any problem. I do like the recommendation of having an operating system on every drive and that system bootable from that MBR, so if you first drive ever fails you can switch drives and still boot to a system

---

### Post by SyntaxError77 on 2009-12-03
Thanks for the info!

The grub loader seems to have disappeared now, I don't know why, because I haven't changed anything but hey, it's gone.

I need NTFS because I can use the drive in my DVD/DivX player in the living room and I need to store files larger than 4gb (ISO images etc) so FAT32 is out.

---

