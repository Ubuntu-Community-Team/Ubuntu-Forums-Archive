---
title: "How to make my old /home partition and /boot as default after reinstalling 10.10."
date: 2011-08-24
forum: New to Ubuntu
---

### Post by neiu bee on 2011-08-24
Hi..
After upgrading my system to 10.10 from 10.04, i faced a few problems then i reinstalled 10.10.
As i have some important files about 30GB in "/home" partition, i just re-installed 10.10 without formatting it.
Now my original /home partition is separated and i have to mount  when ever i want to use it. Along side i have a new folder '"lost+found".
Is there a way in which i can use 10.10 as earlier i mean with out every time mounting previous "/home" partition.
I often change da distros. So i want a way in which my data is secured and to access it without any problem.
I mean just like that of windows where when an new OS is installed only da partition that has OS is formatted or changed and rest of the data remains intact.
I found some information regarding this. But since i lost my data sometime following instructions frm that site[not now]. i  need some suggestions. Here is da link that google suggested.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
I have to even connect my old /boot partition as default along with /home to be default.

I dont have any other storage device to back up 30GB of data.

---

### Post by Ghost|BTFH on 2011-08-24
Yes, when you install you have to set it for a custom installation, partition the drive(s) manually and set the old /home partition to again have the mount point of /home but do not allow it to be formatted in the process.

---

### Post by ajgreeny on 2011-08-24
You can just edit /etc/fstab and add the old /home partition by adding lines similar to these, but with your own setup details.
```
# /home was on /dev/sda2 during installation
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /home           ext4    defaults        0       2
```
Change the commented line to suit your /dev/sdx# name, and also find your UUID for /home with ```
sudo blkid
``` then after the edit use command ```
sudo mount -a
``` to remount everything in fstab.  Report back here if there are any problems or errors.

---

### Post by cbowman57 on 2011-08-24
I really wish they would update the installation recommendations for a linux installation.  It's not the /home directory &/or partition that uses all the space & people would like to preserve across installations.  It's the sub-folders, ie. Downloads, Music, Pictures, etc..

It's for that reason that I keep /home on my / partition but mount  & bind other partitions that contain the bulk of my files that I don't wish to lose.

Just an observation & a comment.  Took me over 5 years using linux before I figured out what works best for me.

---

### Post by neiu bee on 2011-08-25
> **Ghost|BTFH said:**
> Yes, when you install you have to set it for a custom installation, partition the drive(s) manually and set the old /home partition to again have the mount point of /home but do not allow it to be formatted in the process.


u want me to go install the OS once again or just assign  /home to the old  partition ??

---

### Post by neiu bee on 2011-08-25
> **cbowman57 said:**
> I really wish they would update the installation recommendations for a linux installation.  It's not the /home directory &/or partition that uses all the space & people would like to preserve across installations.  It's the sub-folders, ie. Downloads, Music, Pictures, etc..

It's for that reason that I keep /home on my / partition but mount  & bind other partitions that contain the bulk of my files that I don't wish to lose.

Just an observation & a comment.  Took me over 5 years using linux before I figured out what works best for me.


Actually its a good idea to store all the imp data in other manually mountable partition. But in this process i have got another folder "Lost+Find"... do i have to delete that as i cannot open it. If not is there any way to open it ?

---

### Post by neiu bee on 2011-08-25
> **ajgreeny said:**
> You can just edit /etc/fstab and add the old /home partition by adding lines similar to these, but with your own setup details.
```
# /home was on /dev/sda2 during installation
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /home           ext4    defaults        0       2
```Change the commented line to suit your /dev/sdx# name, and also find your UUID for /home with ```
sudo blkid
``` then after the edit use command ```
sudo mount -a
``` to remount everything in fstab.  Report back here if there are any problems or errors.


 thank u :)

---

