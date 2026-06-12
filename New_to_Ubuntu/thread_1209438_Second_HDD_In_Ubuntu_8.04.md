---
title: "Second HDD In Ubuntu 8.04"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by getitright on 2009-07-10
I already have a 250Gbs SATA HDD on my desktop and have been given a second SATA HDD which I would like to install. The second HDD has a Windows installation on it probably using FAT32. This second HDD will be used purely for files. Can anyone help with information on installing a second HDD. Some of matters that need resolution are:- do I need to format it? If so, how do I do this? How do I get the disc to mount on startup? Any information will be welcome.

---

### Post by Majorix on 2009-07-10
If -and only if- you don't want Windows on that HDD anymore, go ahead and get a copy of an Ubuntu LiveCD or GParted LiveCD and reformat the partition using the provided GParted Partition Editor. You will have to choose a filesystem type to use (like ext3 or ntfs or whatever) while reformatting.

---

### Post by smartbei on 2009-07-10
Firstly, it si probably NTFS (that has been the default format for windows partitions for nearly 9 (10?) years). Check out [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) for how to install a new drive.

---

### Post by whitesmith87 on 2009-07-10
> **getitright said:**
> I already have a 250Gbs SATA HDD on my desktop and have been given a second SATA HDD which I would like to install. The second HDD has a Windows installation on it probably using FAT32. This second HDD will be used purely for files. Can anyone help with information on installing a second HDD. Some of matters that need resolution are:- do I need to format it? If so, how do I do this? How do I get the disc to mount on startup? Any information will be welcome.

You don't need to format it anymore. But even if you format it you can easily get the files with Linux recovery softwares

---

### Post by superprash2003 on 2009-07-10
as mentioned earlier gparted is a great tool to handle drives.. you could do whatever you wish.. although fat32 does not play well with ubuntu.. so go for ntfs if you want it to be accessible by both windows and ubuntu or ext2/ext3 if its going to be used by ubuntu only..

---

### Post by getitright on 2009-07-11
Thanks to all for your advice. I have successfully installed the drive, however when I try to put anything on it I am informed that I do not have the necessary permissions. When I look in Permissions in Preferences the owner is shown as root. How do I change Permissions to my user name?

---

### Post by cjv8888 on 2009-07-11
> **getitright said:**
> Thanks to all for your advice. I have successfully installed the drive, however when I try to put anything on it I am informed that I do not have the necessary permissions. When I look in Permissions in Preferences the owner is shown as root. How do I change Permissions to my user name?

try

> sudo chown -R username:group /path/to/drive

---

### Post by getitright on 2009-07-11
Permission problem has been resolved. Thanks to everyone for the advice.

---

### Post by LewRockwell on 2009-07-11
fyi...

one would be VERY wise to use the secure erase function on ANY used donated/purchased drives that one becomes the primary possessor of...

the liveCD of Parted Magic does this([http://www.partedmagic.com/](http://www.partedmagic.com/))

and, as always, you can learn more about the secure erase function of your hard drive controller by using the search term "secure erase"

and...this is why it's wise...

[http://www.justice4matt.com/](http://www.justice4matt.com/)

[http://www.backwoodshome.com/articles2/duffy104.html](http://www.backwoodshome.com/articles2/duffy104.html)

.

---

