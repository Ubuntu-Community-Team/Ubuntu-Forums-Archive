---
title: "Accessing Windows from Kubuntu"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Bruv on 2009-01-15
This may be a silly question, but I must ask.
Is it possible to access Windows while running Kubuntu ?
I have many things I would like access to, that are on my dual booted drive but in the Windows partition.
The things I mean are old letters and images etc.
I trying to use as Kubuntu full time and break the Windows habit, but find there are times when the odd file is 'the other side' and have to reboot to refer to it.

Do I have to copy the files I am referring to and transfer them, or is there an alternative method ?

---

### Post by epswinde on 2009-01-15
[http://ubuntuforums.org/showthread.php?t=1039892&highlight=mount+ntfs](http://ubuntuforums.org/showthread.php?t=1039892&highlight=mount+ntfs)

this shows you how to have your windows partitions mounted automatically at startup

---

### Post by Ben Page on 2009-01-15
There are no problems accessing windows partitions from Ubuntu - Kubuntu, you can mount them at startup, but don't have to. When you need to access win partition from Ubuntu, just go to my Computer (from places or desktop if you have a desktop icon) and click on a desired windows partition(thats mounting) and the new drive will appear on your desktop. Another way to import your documents, emails, pictures etc. from windows (if they are in default windows folders) is to just click import files from windows when installing kubuntu on separate partition along with already installed windows. 
But there are probs. when you want to see ext.3 partitions on windows, there are apps to do that, but if you are using windows 7 (like me) its impossible - im waiting for new app for that.

---

### Post by Bruv on 2009-01-15
Very many thanks....Im just going to play around with that.

---

### Post by Bruv on 2009-01-15
I followed the instructions according to this [post]("http://ubuntuforums.org/showpost.php?p=6551622&postcount=2")
but was told I needed to install gksudo and given a script to do so.

I have just tried again and got as far as getting this.......


> bruv@bruv-desktop:~$ sudo mkdir /media/NTFS_Drive
[sudo] password for bruv:
mkdir: cannot create directory `/media/NTFS_Drive': File exists
bruv@bruv-desktop:~$ gksudo gedit /etc/fstab
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
bruv@bruv-desktop:~$

---

### Post by Bruv on 2009-01-16
Does anybody have any ideas how I can fix this problem.
I have googled the line>  "QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'" which returned 465 results, but after reading many, I am none the wiser.

---

### Post by epswinde on 2009-01-18
Please post your /etc/fstab and the output of 
```
sudo fdisk -l
```

---

### Post by Bruv on 2009-01-18
I had given the results of >  gksudo gedit /etc/fstabit was 
>  QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'

The results of sudo fdisk-1 is as follows...
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c5b0c5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5723    45969966    7  HPFS/NTFS
/dev/sda2            5724        9729    32178195    5  Extended
/dev/sda5            9671        9718      385528+  83  Linux
/dev/sda6            9719        9729       88326   82  Linux swap / Solaris
/dev/sda7            5724        9506    30386884+  83  Linux
/dev/sda8            9507        9670     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by epswinde on 2009-01-19
since you're running kde, you dont have gedit installed, nor gksudo.  both are gnome native applications. please post the output of
```
kate /etc/fstab
```

---

### Post by 311005901 on 2009-01-19
I hate to be the simpleton of the thread, but [DropBox]("http://www.getdropbox.com/") works for me.

---

### Post by txcrackers on 2009-01-20
Why give someone else your data when it's all right there on the hard-drive?

---

