---
title: "How do I access an external hard drive from another computer?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by Mainkai on 2011-07-25
Hello. 

I have been using Ubuntu for quite a while now on my older laptop and I recently installed it on my "main" computer as well. The problem is that when I take the 500 GB external hard drive (WD Passport) that I've been using for my laptop and attempt to access it via the "new" Ubuntu installation, I cannot even see the volume because I am apparently not listed as the owner. 

The device has a HPFS/NTFS (0x07) partition type and also has these values in the Disk Utility window:
Type: Ext4 (version 1.0)
Device: /dev/sdb1

I can't remember choosing a passport for the device, nor have I been prompted to input one. 

How do I list myself as the owner on both my computers / remove the protection? Will I have to backup all the data and reformat the drive? 

Please advice, thank you in advance.

EDIT: Would it be possible to re-install Ubuntu on the new computer and just input the exact same Username and password as on the laptop installation? Currently, the username is different.

---

### Post by androssofer on 2011-07-25
so it loads up the icon on the desktop.. then u click it and it says "unsable to open you aren't the owner etc etc?"

if u go into /media and do ls -l it should list the drive and read/write permissions for it, can u put up the results?:

in terminal:

```
cd /media

ls -l
```

---

### Post by skatinjj on 2011-07-25
If I was sharing a mounted device between two computers I would change the permissions of the mount point like this:

```
sudo chmod -R 774 /mnt/usb.drive
```

That will give the owner and group permissions to go everything, but the outsiders can only read.  If outsiders need read, write, and execute the 4 would become a 7 and if outsiders just need read and write the 4 becomes a 6.

The -R switch gives all files and folders in directory /mnt/usb.drive the permissions so if thats not what you want take it out.

And of course, /mnt/usb.drive should be changed to whatever your mount point is.  And I use sudo because I do not know who owns the mount point on your system.

---

### Post by amjjawad on 2011-07-25
Hello and Welcome :)


> **Mainkai said:**
> I can't remember choosing a passport for the device, nor have I been prompted to input one. 


Are you talking about the External HDD or your other Computer?


> Would it be possible to re-install Ubuntu on the new computer and just input the exact same Username and password as on the laptop installation?Yes.

---

### Post by Mainkai on 2011-07-27
> **amjjawad said:**
> Hello and Welcome :)




Are you talking about the External HDD or your other Computer?


Yes.

The external HDD. 

I solved it by using the chown command and now it works perfectly. Thanks for your help, everyone.

---

### Post by amjjawad on 2011-07-27
Glad you managed to fix it :)

Please mark your thread as SOLVED from Thread Tools if you don't have any other question :)

---

