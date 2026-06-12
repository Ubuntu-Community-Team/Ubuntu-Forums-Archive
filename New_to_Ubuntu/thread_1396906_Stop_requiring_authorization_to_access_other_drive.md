---
title: "Stop requiring authorization to access other drives?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Mooglefrooglian on 2010-02-02
Hi, I just got Ubuntu and pretty much have it all figured out. The one thing eluding me is that I store all my music on one of my other (Windows) drives and whenever I use the music playing program Songbird, it is unable to access these files every time it starts up. I manually have to import media, and click on the drive, whereupon Ubuntu claims a program is asking for authorization to acess another drive. After giving it my password, everything works again.

Is there any way to auto let Songbird itself through 100% of the time without me giving it a password, or failing that, turn it off completely? (I have no concerns about security - I'm in a small town on protected wireless.)

Edit: Also, Pidgin Instant messenger is a good alternative to GTalk, but it can't send or receive files (everything else works though). Is there any way to correc tthis, or is there an IM client that can send and receive files?

---

### Post by ibuclaw on 2010-02-02
> **Mooglefrooglian said:**
> Hi, I just got Ubuntu and pretty much have it all figured out. The one thing eluding me is that I store all my music on one of my other (Windows) drives and whenever I use the music playing program Songbird, it is unable to access these files every time it starts up. I manually have to import media, and click on the drive, whereupon Ubuntu claims a program is asking for authorization to acess another drive. After giving it my password, everything works again.

Is there any way to auto let Songbird itself through 100% of the time without me giving it a password, or failing that, turn it off completely? (I have no concerns about security - I'm in a small town on protected wireless.)


If the drive is local, then you can include the mounting of it in the file /etc/fstab

Then it will mount automatically whenever you boot.

It's been a while since I last used ntfs, but if you post the output of:
```
sudo blkid
```
and kindly tell us which one is the device for your share, then that should be sufficient to help you get setup.

Regards
Iain

---

### Post by Mooglefrooglian on 2010-02-02
/dev/sda1: UUID="3CC45FB2C45F6D60" LABEL="Why" TYPE="ntfs" 
/dev/sdb1: UUID="662b3697-aa40-4464-ad2a-17b4551e089a" TYPE="ext4" 
/dev/sdb5: UUID="1f7824ae-c6ea-47fc-abb6-9c67dedd1cea" TYPE="swap" 
/dev/sdc1: UUID="C8E85E90E85E7C9E" LABEL="See" TYPE="ntfs" 

"Why" or Y:\ on Windows.

Thanks for your help.

Edit: Looking over, the line I would want to add would be: 
UUID=3CC45FB2C45F6D60 /               ntfs    errors=remount-ro 0       1

Probably. But I'll wait and make sure someone tells me to add that.

Edit: Anything on the GTalk file transfer thing as well?

---

### Post by Morbius1 on 2010-02-02
One way to do it would be like this:

You need to make a mount point for the partition to live in and then instruct fstab to mount it there. 

Open **Terminal**
Type **sudo mkdir /media/WinY**
Type **sudo su**
Type **echo "/dev/sda1 /media/WinY ntfs defaults,umask=007,gid=46 0 0" >> /etc/fstab**
Type [B]mount -a
[/B]
The umask=007 will give the owner ( which will be root ) and group read / write access with no access to anyone else.
The gid=46 will make the group = plugdev which by default is the group of all local users including yourself.

  Another option if you ever plan on sharing this partition across your home network using sharing through nautilus is to take possession of the mount point by adding uid=1000:

**echo "/dev/sda1 /media/WinY ntfs defaults,umask=007,uid=1000,gid=46 0 0" >> /etc/fstab**

You need to verify that the uid number is correct for you by issuing the command **id** in a terminal.

Anyway, that's how I would do it. Am interested on tinivole's thoughts on it.

---

