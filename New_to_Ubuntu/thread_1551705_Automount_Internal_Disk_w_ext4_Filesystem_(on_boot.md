---
title: "Automount Internal Disk w/ ext4 Filesystem (on boot)"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by SlimBiggins on 2010-08-12
I have two internal hard disks in my computer, one 20gb for Linux, and an 80gb for storage.

I am trying to automatically mount the 80gb on startup so that certain  applications may access them without me going through the normal mount  procedure.

I read a thread on a similar inquiry, except it was for a NTFS. From  what I understand, the answer lies in editing the /etc/fstab file  correctly and creating a mount point somewhere in the /media/ folder.

My question is what do I need to add to the /etc/fstab file for  automounting an ext4 filesystem? Also, is an ext4 filesytem any better  or worse than a NTFS for storage use?

I could go the trial and error way, but would feel much safer with the forums. Any help is much appreciated.

Thank you,
  SlimBiggins

---

### Post by MooPi on 2010-08-12
First step is to make a backup copy of your /etc/fstab file.  Second open a terminal  ```
sudo blkid
```
The results should look similar to this:```
/dev/sda1: UUID="b3ce4e2a-f862-4f38-9402-00301e1f52a1" TYPE="ext4" 
/dev/sda2: LABEL="WindowsXP" UUID="7EBC9389BC933A9B" TYPE="ntfs" 
/dev/sda3: LABEL="BigBin" UUID="819005e9-fd37-4f2a-91ef-162b7fe9e400" TYPE="ext3" 
/dev/sda5: UUID="9b447b24-4a29-425c-87c5-4068e5ea50e4" TYPE="swap" 
/dev/sdb1: LABEL="Sabrent" UUID="08d3b402-2262-461a-be06-43e2ef52b560" TYPE="ext4" 
```
Now use the info for your second hard drive to edit /etc/fstab. As an example I'll choose my drive /dev/sdb1 Sabrent.```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b3ce4e2a-f862-4f38-9402-00301e1f52a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b447b24-4a29-425c-87c5-4068e5ea50e4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# BigBin /dev/sda3
UUID=819005e9-fd37-4f2a-91ef-162b7fe9e400 /media/BigBin   ext3     user,auto   0     0
# WindowsXP /dev/sda2
UUID=7EBC9389BC933A9B                     /media/WindowsXP    ntfs    user,auto   0    0
[COLOR="Red"]# Sabrent /dev/sdb1
UUID=08d3b402-2262-461a-be06-43e2ef52b560 /media/Sabrent ext4 defaults 0 0[/COLOR]
```
 Create a folder in media and make sure you are owner and have permissions. As an example I own /media/Sabrent  ```
sudo chown MooPi -R /media/Sabrent
```
If you need the drive to be accessible to a Windows install then choose ntfs, otherwise ext4 should be your choice.

---

### Post by SlimBiggins on 2010-08-14
Thank you, MooPi. Works just fine. =)

---

### Post by SlimBiggins on 2010-08-20
i did have one other question. its not really important, but it never  hurts to ask. is there any way i can go about having the disk icon not  appear on the desktop. it just seems useless to have. i'm sure i can  figure a way to do so, but any info would be greatly appreciated.

thank you,
slim biggins

---

### Post by amauk on 2010-08-20
> **SlimBiggins said:**
> i did have one other question. its not really important, but it never  hurts to ask. is there any way i can go about having the disk icon not  appear on the desktop. it just seems useless to have. i'm sure i can  figure a way to do so, but any info would be greatly appreciated.

thank you,
slim biggins
Anything mounted in /media will have an icon on the desktop

If you don't want an icon
mount the partition somewhere other than /media
(Eg. mount it to a folder in your home directory)

---

### Post by SlimBiggins on 2010-08-20
amauk: thanx for the info. i don't know why i didn't think of that. durgh! its always the simple solutions that get overlooked.

- Slim Biggins

---

### Post by Morbius1 on 2010-08-20
I'm fairly certain that if you mount it to somewhere in your home folder the mount icon will also appear. /mnt is a better place I think.

---

### Post by SlimBiggins on 2010-08-22
Kind of answering my own question here, but I thought this would be helpful to anyone else who is doing the same.

If you don't want the mounted disk (in /media/*) to show as an icon on your desktop you can do so without choosing another mount location.

1. Open gconf-editor

2. Goto: apps > nautilus > desktop

3. Uncheck the "volumes_visible" value

Keep in mind this will prevent all inserted media (usb flash, external disk) from being displayed as well.

- Slim Biggins

---

### Post by HelloIndustries on 2010-11-09
I came here via google search looking for the least complex solution to auto-mounting Ext4 partitions after login. Thankfully, this looks to be the answer i've been after.

**@Moopi: **Would the process be the same for an encrypted drive?

Example:

[LIST]
[*]sda = /, /home (Encrypted) and swap partitions, plus another encrypted ext4 partition for data (Data)
[*]sdb = Ext4 encrypted (Media)
[*]sdc = Ext4 encrypted (Data 2)
[/LIST]

---

### Post by sazawal on 2011-05-28
Thanks Moopi, it worked good for me. I have one more question. How would you change the label of an ntfs drive. I tried it with the System>Administration>Disk Utility but didnt work. I also tried ntfsprog from the terminal which changed the label from /media/**** to /media/D but I am still getting the same old label on desktop and on the list of mounted drives. Help.

---

