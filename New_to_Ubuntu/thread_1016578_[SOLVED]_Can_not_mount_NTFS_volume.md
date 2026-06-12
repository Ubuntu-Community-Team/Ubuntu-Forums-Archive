---
title: "[SOLVED] Can not mount NTFS volume"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by siebesadeq on 2008-12-20
Hi.
After reinstalling intrepid I am not able to access my data disk which is formatted as NTFS. This is the error I get when I try to mount:

---

### Post by billgoldberg on 2008-12-20
> **siebesadeq said:**
> Hi.
After reinstalling intrepid I am not able to access my data disk which is formatted as NTFS. This is the error I get when I try to mount:

Boot into Windows and shut it down the correct way.

---

### Post by siebesadeq on 2008-12-21
I'm sorry I forgot to mention I haven't got windows installed.
This disk was accessible After I deleted windows and installed Ubuntu, about 9 months ago. After upgrading to intrepid also no problems. Now I reinstalled intrepid again and since then I get this error.
Thanks for your reply by the way, Bill.

---

### Post by kixome on 2008-12-21
reinstall again, or use a super pe disk to mount and copy all files off of that disk and format it to ext3, If none of that works then you probably, like the error says (have hardware issues) the disk may be corrupted or almost dead, this in the world of computing is not entirely unheard of!

---

### Post by superprash2003 on 2008-12-21
doesnt it give you an option to force mount?

---

### Post by BDNiner on 2008-12-21
Wow, I don't know what the chkdsk like utilities are in linux but I would try and check the HD for errors. Did you have linux installed along side ubuntu before you reinstalled and wiped the hard disk clean? were your hard disks setup in a RAID configuration before you installed Ubuntu. I am guessing no. 

Personally I would stick the hard disk in a windows computer and run check disk if a windows computer is available. Since i don't know what chkdsk like utilities there are for linux. maybe someone else here can chime in with some options.

---

### Post by PmDematagoda on 2008-12-21
You shouldn't need a Windows computer to fix this, just install the ntfsprogs package through Synaptic and then run:-
```
sudo ntfsfix /path/to/drive
```
that should clear it up. The path-to-drive should be given in the error message.

---

### Post by jacobw.uk on 2008-12-21
If it is convinent for you, starting up Windows with the disk plugged in and rebooting it a few times tends the rejig the NTFS and makes it readable again, in my experience anyway.

---

### Post by siebesadeq on 2008-12-24
Thanks for all your reactions.
What I did was I inserted a window PE cd, and accessed the data partition. Then I copied all the files to a usb stick, and thus saved the data.
After that I used Gparted to format the partition to ext3.
I still wasn't able to move files to the new partition, so I opened a terminal and entered sudo nautilus and changed the permissions.
Now everything is as it should be.
Thanks again.

---

