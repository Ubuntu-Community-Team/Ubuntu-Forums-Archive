---
title: "Install ubuntu for dual boot w/windows"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Fritzili on 2009-06-23
I am a beginner user of Linux and could use some help. I have a PC with Windows XP OS formatted 32 bit in NTFS. The internal hard drive has two partitions: the C:/ drive is set as the Active drive and the second partition is set as a Logical drive. I want C:/ drive to remain as the active drive with Windows OS, programs and files. I want to install Ubuntu 9.04 in the second partition, and have it use that entire partition for the OS, the Linux programs and files. I also want the dual boot capacity at startup.

I recently tried to do that myself, and during the installation, it appeared the two partitions were recognized and that Ubuntu would use the second drive. The Windows partition was sized properly, indicated as NTFS, and colored blue,and the second partition was sized properly, indicate by ext3/ext/4 and colored green. So I selected 'install side by side with Windows' ............... obviously the wrong thing to do.

It installed as though there was only one partition. The installation created a small 2.5 GB partition for itself somewhere in the C:/ drive . It doesn't even have enough room for downloads. Also, it is not using the second partition at all. I could use some help sorting it out.

Do I have to un-install what I have now, and re-install the software using some commands to get Ubuntu to place itself in the proper partition and use the entire space?
I was reading on the Forum that I must make sure that Ubuntu knows where it is supposed to go. I didn't see that during the installation. I must have missed something.

Thanks in advance for your help. I am just starting, so I am not too savy with the commands and how to use them yet.

Fritzili

---

### Post by lisati on 2009-06-23
One thing that might help the gurus figure out what's going on in your system is if you go to the command line (Applications->accessories->terminal), enter the following, and post the output:
```
sudo fdisk -l
```
[LIST=1]
[*]That's a littel "ell", not a number one
[*]It will ask for your password: don't worry if your password doesn't show, this is a normal Ubuntu security feature
[/LIST]

---

### Post by LewRockwell on 2009-06-23
> **lisati said:**
> One thing that might help the gurus figure out what's going on in your system is if you go to the command line (Applications->accessories->terminal), enter the following, and post the output:
```
sudo fdisk -l
```
[LIST=1]
[*]That's a littel "ell", not a number one
[*]It will ask for your password: don't worry if your password doesn't show, this is a normal Ubuntu security feature
[/LIST]

please do this via your live-run disk

---

### Post by Polaris96 on 2009-06-23
To set up the initial Linux system, use the installer and select manual partitioning when the partitioner starts.  

Pick the partition that corresponds to your "D" drive, and choose  "/" as your mount point on the menu.  That should do it.  

So far as dumping the 2.5G Linux partition goes, you can probably do it with parted or fdisk, but I don't know if the windows data will hold up.  I don't want to give odds or advice on resizing an NTFS partition.

---

