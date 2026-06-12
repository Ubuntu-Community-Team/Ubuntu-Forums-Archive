---
title: "Terminal Commands for Formating,Mounting, and Browsing a second hard drive."
date: 2009-11-20
forum: New to Ubuntu
---

### Post by thebradnetwork on 2009-11-20
I am running Ubuntu 8.04 Server and I am trying to setup a file server so that I can store network files on it. I am running two hard drives in this machine...one is for the OS and the other is trickily for storage. My questions are as follows:

1. What is the best file format to use for doing this ex. ext2, ext3, NTFS, FAT, etc. Also what commands do I need to know to accomplish this.

2. How do I browse the second hard drive from the terminal server?

---

### Post by Baelus on 2009-11-20
This is a good guide:

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

It suggests formatting the disk as ntfs. That way, if you have to move the drive to another pc at least it will be accessible by Windows, if necessary.

What format is the best? In terms of a simple home file server, there really isn't much of a difference among the usual choices, ext2/3, ntfs, xfs, jfs, etc. I would advise against Fat32 as there is a file size limit of 2 Gigs, if I'm remembering things correctly.

Accessing the server via the terminal is usually done through ssh. This is pretty much what you need to get started:

[http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/]("http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/")

---

### Post by nothingspecial on 2009-11-20
sudo mkfs -t (ext3, vfat, xfs, etc,etc) /dev /sd??

sudo - do as root/administrator

mkfs - make a file system (format the drive to)

-t - of the type

Just choose one. See man mkfs for all the options.

/dev/sd?? - if you type sudo fdisk -l the terminal will tell you all the partitions connected to it (mounted or not). Unmount the partition you want to format and choose the /dev/sd?? assigned to it.

2. If you are using linux only I would recommend ext3.

By the way, don`t use mkfs unless you are absolutely sure of what you are doing. It will destroy your data.

---

