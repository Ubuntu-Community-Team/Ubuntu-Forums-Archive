---
title: "Can I backup Ubuntu from windows XP?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by dgg9879 on 2008-12-20
I use Macrium to backup my c drive where I store windows operating system. I know from experience this works really well.

I can't see the ubuntu partition on the drive where it is stored from windows.

I just want to know if backing up the whole drive where ubuntu is stored (along with windows files on a separate partition) with Macrium will work.

---

### Post by shifty_powers on 2008-12-20
possibly. you at least need [http://www.fs-driver.org/](http://www.fs-driver.org/) to even try...

---

### Post by carml on 2008-12-20
I don't know that program,but I know that impossible for Windows see a partition reserved to Linux,because of security settings,while Linux can see all the partitions on your hard disk. :p

---

### Post by shifty_powers on 2008-12-20
> **carml said:**
> I don't know that program,but I know that impossible for Windows see a partition reserved to Linux,because of security settings,while Linux can see all the partitions on your hard disk. :p

no it's not, please see the link i posted...

---

### Post by Duck2006 on 2008-12-20
If you can't find a program to do it from win try part image and do it from linux.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by hyper_ch on 2008-12-20
I'd use dd to make a 1:1 image from a live cd

---

### Post by carml on 2008-12-20
@ shifty_powers
What I mean is that with a file system ext3,using also any packages it's possible access from Linux a partition formatted as NTFS,I didn't mean that the program mentioned could backup also a partition with Linux .:)

---

### Post by BDNiner on 2008-12-20
You cannot see your linux partition because Windows by default cannot read Ext2/3 partitions. You need to install software that Shift_Powers mentioned inorder to read and write to your linux partition from windows. 

I don't know how Macrium backs up data, the only way to find out would be to setup a test environment with a spare hard disk. Since the data is not stored in NTFS I don't know if the backup software would corrupt it when backing up and restoring the entire hard disk. Proceed with caution you don't want to lose any data.

---

### Post by Gone fishing on 2008-12-20
> Re: Can I backup Ubuntu from windows XP?
possibly. you at least need [http://www.fs-driver.org/](http://www.fs-driver.org/) to even try... 

This works well - I use it.

However it will not work with the standard format that Intrepid uses.

Apparently Ext2 IFS only allows 128 byte inodes (this is an older standard for ext3) whilst Intrepid uses larger inodes. I solved the problem by creating my formats using gparted then installing intrepid onto the created partitions.

You could back up your data then format your home partition with:

 mkfs.ext3 -I 128 /dev/your_device

Then copy the data back onto the home partition

---

