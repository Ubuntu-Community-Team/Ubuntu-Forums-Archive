---
title: "Moving photos from XP"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by audine on 2009-02-22
This is so much fun moving into a world with no windows or gates!  I'm slowly getting everything to work and it is extremely satisfying, especially with my limited computer knowledge.  Right now I'd like to move the photos that I have stored in Windows XP to Ubuntu 8.10.  Is this possible, and can someone point me in the right direction, please?  I've searched but can't seem to find the information I need.

---

### Post by whoop on 2009-02-22
Is the ubuntu machine the same machine as the windows xp machine? In other words are you trying to access a local partition or trying to share files on a network?

---

### Post by shredder12 on 2009-02-22
Well i belive you have xp on another partition in your hard drive..
jst click the "Places" tab on the upper left corner of your screen..
there you will find options like Home documents, Music etc.. 
Under the Computer and cd/dvd creator you will find some names with disk like images..
these are your hard disk partitions... and u would be glad to know that ubuntu can read/write in ntfs or fat32 partitions.. so jst click on any of them and then you will be prompted for password....enter it and there's your data on other partition...
for moving it.. jst do simple cut and paste..
hope this helps..

---

### Post by audine on 2009-02-22
Yes, Ubuntu and XP are on the same computer.

I opened Places>Computer, and unfortunately I don't see anything but Trash and USB under CD/DVD.

---

### Post by carml on 2009-02-22
It looks like you installed Ubuntu using WUbi.
Did you install Ubuntu under Windows?

---

### Post by uprooted on 2009-02-22
make a separate fat32 partition, whatever size you need to transfer all your files, this partition can be used as a swap drive between windows and linux, that way music can be shared by both and such...
oh yeah i believe windows has software that will partition your hard drive...

go into linux make a folder in whatever directory you want

now you have to edit your /etc/fstab so that linux loads the partition 

if you have made the folder in root then the line would look like

/dev/nameofpartition       /nameoffolder     vfat    umask=000       0 0

to find the name of the partition type sudo fdisk -l
to edit the /etc/fstab go to terminal and type sudo gedit /etc/fstab
**warning incorrectly editing fstab might cause improper boot procedure and lots of errors**

anyone have an easier way?

---

### Post by carml on 2009-02-22
Yes,on a dual boot PC Linux can access the other existing partitions,i.e. you don't need to create a partition only to share files between the two OS. :p

---

### Post by audine on 2009-02-22
I installed Ubuntu from the CD I burned from the online download.  I tried Wubi at one time, but couldn't get it to work, kept asking me if I wanted to uninstall.  My system is set up to boot up either OS, dual-boot, right?

When I opened Places>Computer before I wanted to move photos, I could see the XP partition, it's seems to have disappeared?  

I appreciate the help.

---

### Post by Locke_99GS on 2009-02-22
Post the results of these commands:

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by audine on 2009-02-23
sudo fdisk -1
cat /etc/fstab


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c6b2c6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         494       10633    81449550    7  HPFS/NTFS
/dev/sda2           10634       30401   158786460    5  Extended
/dev/sda3               1         493     3959991   82  Linux swap / Solaris
/dev/sda5           10634       30401   158786428+  83  Linux

Partition table entries are not in disk order

---

### Post by suitedaces on 2009-02-23
> **carml said:**
> It looks like you installed Ubuntu using WUbi.
Did you install Ubuntu under Windows?

What is the process for accessing them if you used wubi?

---

### Post by audine on 2009-02-26
finally found my photos --

Places>Computer>File System>Windows>Documents&Settings>My Documents>My Pictures ---

It seems so simple now.  Just couldnt see it before.  Drag and Drop My Pictures over to Pictures, and File Operations starts copying my whole photo and video collection onto my new system. 

Loving Linux!

---

