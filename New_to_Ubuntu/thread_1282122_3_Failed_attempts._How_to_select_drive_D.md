---
title: "3 Failed attempts. How to select drive D:\"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by nordy on 2009-10-04
Hi,
Just how in the world do I get this thing to install on drive d?
I tried thrice, without any success. I've got WinXp on drive c, and want to install Ubuntu on drive d, but there seems to be no way to choose drive d during the installation. Can u pls help?
WinXp will display a list of partitions when u install. What's the procedure here?
I also tried doing a virtual install and then copying files to a physical drive, but that failed too.
Thanks
~Norman

---

### Post by bwang on 2009-10-04
Are you using Wubi or a real install?
The real installer should allow you to change the device you are installing o. A screen should appear with a list of devices. Note that your drive D:\ in Windows will not be called "D" in Linux, instead, it will have a name like sda, sdb, etc.

---

### Post by 3rdalbum on 2009-10-04
Temporarily disconnect the hard disk that you don't want to install onto, and then report back. On Linux there's no "C:" or "D:" so I'd hate for your confusion over different naming schemes to cause you to install to the wrong disk.

---

### Post by nhasian on 2009-10-04
first of all, i dont recommend disconnecting any drives.  boot off the liveCD and give us the output of these terminal commands:

```
sudo fdisk -l
```

make sure you backup any critical data before installing ubuntu.  Instead of starting the installation of ubuntu from inside windows (wubi) i recommend booting off the LiveCD and installing ubuntu to your 2nd hard disk.  During the installation procedure when it gets to the partitioning part i always select manual.  This way you can have ubuntu installed on the second hard disk.  I also recommend making the root / partition about 10 gigs, a swap partition equal to the size of your ram, and then the rest set to your /home partition.

---

### Post by nordy on 2009-10-10
I don't have 2 hard disks. I only have one, and its a 160 GB HDD divided like this:

C: 30 -> Contains WinXp pro
D: 40 -> Blank, FAT FS(this is where I'd like to install Ubuntu)
E: 40 -> Contains files
f: 40 -> Contains files

I'm trying to install Ubuntu on D:\
I chose manual install and when it comes to the part where I have to select my drive, I can see it there. It shows as 40 GB with 40 GB free. That's the only way I can identify it.

My problem is with what happens next. I have no clue. It asks for root partition and etc etc. How do I continue from this point onwards.

Thanks
~Nordy

---

### Post by 3rdalbum on 2009-10-11
The 40 gigabyte blank drive needs to have its mount point set to /.

So in the manual partitioning bit, where it lists your blank 40 gigabyte partition click it and click the "Edit..." button (it might be called "Modify..."). In the popup menus that you get presented with, choose "Ext4 filesystem" and "Use this partition". In the "mount point" field, just type a forward slash (/). The forward slash means "my file system" in Linux and Unix.

For anyone else reading this thread, actually I take back my suggestion about removing hard disks; I've just remembered why it's not such a great idea.

---

### Post by kansasnoob on 2009-10-11
Give this a look:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by The Cog on 2009-10-11
Probably the easiest thing to do will be to delete that FAT partition that you want to install Ubuntu into (Ubuntu can't install onto FAT anyway). Then in the installer, tell it to use the largest free space. In fact it will create two partitions in that 40G space, but you don't need to worry abut that.

Windows won't recognise either of the new partitions, so D will either disappear to Windows, or maybe the others will shuffle up, depending on Windows own logic.

---

