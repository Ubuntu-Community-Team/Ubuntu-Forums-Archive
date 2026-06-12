---
title: "How much space left"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by hitmen on 2009-11-15
Hi everyone! I am running a vista host and ubuntu on sun virtualbox.

1) I am not sure how to check the amount of disk space or memory that it has used?

2) I ran belarc advisor and this are my specifications:

Drive:
[SIZE=2]239.58 Gigabytes Usable Hard Drive Capacity
44.32 Gigabytes Hard Drive Free Space

and this is the "local disk volume":
[/SIZE]        [SIZE=2] 


 [SIZE=2]c: (NTFS on drive 0) [/SIZE]
[SIZE=2]119.93 GB[/SIZE] [SIZE=2]3.74 GB free[/SIZE]
[/SIZE]d: (NTFS on drive 0)
119.65GB   40.58GB free

What is the difference between the hard disk capacity and the local disk volume?
What is D: used for? I think I installed ubuntu in C: 

3) Does anyone know how to set the ubuntu to full screen mode in virtual machine?

Thanks in advance.
[SIZE=2]

[/SIZE]

---

### Post by Meskarune on 2009-11-15
install guest additions on windows for virtual box to get full screen mode. 

Hard Drive = Physical hard drive, its like a box

Local Volume = Section of a hard drive, Like if you put a separator in the box, there would be 2 spaces or volumes inside the box. 

A hard drive can only have 4 primary volumes. 

Your hard drive is split into 2 volumes, C and D. You hard drive's total space is 239.58 GB. Partition C is 119.93 GB, Partition D is 119.65 GB. 

[-------------119 GB---------------|--------------------119 GB---------------] toltal 240 GB

In windows D drive is ussually used for backup. 

You reallly should read up on filesystems.... I think windows even has a very conveniet help center to example things more in depth...

---

### Post by garvinrick4 on 2009-11-16
That is a huge Back up which is D: in Vista.
Out of box usually 11 gig about 6.1 or so protected OS backup.
C: is where the /host is for a virtual install. 

Something does not look right. Unless they were re-partioned.

It does not seem like you would have attempted that hitman.

Just press Windows key (the flag) and 1 at same time and look at 
your drives in Vista.

I believe you if that's what it says but something is strange.

Get an 80 dollar 500 gig usb external drive for backups and get that disc space back.
How much room do you use for back-ups and restore points. I would say you have
15% of 250 about 37.5 gig, get rid of them but the last 1.  How much in back-ups, who
knows.  Windows key and f1 at same time a good manual, just type in what you want to know.  Good luck and enjoy

---

### Post by 3rdalbum on 2009-11-16
> **hitmen said:**
> Hi everyone! I am running a vista host and ubuntu on sun virtualbox.

1) I am not sure how to check the amount of disk space or memory that it has used?

There is a directory that contains all the virtual hard disk images associated with Virtualbox. If you're not sure where it is, check in the Virtualbox preferences. Right-Click the hard disk image associated with Ubuntu, go to Properties or whatever it is on Windows, and it should tell you there how much space has been used.

Alternatively, on the Ubuntu guest look at the System Monitor.

> 3) Does anyone know how to set the ubuntu to full screen mode in virtual machine?

I think it's Right-control-F (that is, hold down the right Control key and press F). If you don't get the picture taking up the full screen, then you might need to change the virtual monitor resolution.

---

### Post by hitmen on 2009-11-16
> **garvinrick4 said:**
> That is a huge Back up which is D: in Vista.
Out of box usually 11 gig about 6.1 or so protected OS backup.
C: is where the /host is for a virtual install. 
 
Something does not look right. Unless they were re-partioned.
 
It does not seem like you would have attempted that hitman.
 
Just press Windows key (the flag) and 1 at same time and look at 
your drives in Vista.
 
I believe you if that's what it says but something is strange.
 
Get an 80 dollar 500 gig usb external drive for backups and get that disc space back.
How much room do you use for back-ups and restore points. I would say you have
15% of 250 about 37.5 gig, get rid of them but the last 1. How much in back-ups, who
knows. Windows key and f1 at same time a good manual, just type in what you want to know. Good luck and enjoy
 
Hi garvinrick4,
 
what do you mean by it is wrong? Everything looks fine to me.
 
To the rest: 
BTW, what is the difference between video memory and base memory. I checked virtualbox and found out how much space is taken up but I am not sure what happens AFTER INSTALLATION. More space taken up? 
 
Thanks in advance.

---

