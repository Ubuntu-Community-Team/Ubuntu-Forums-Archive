---
title: "Unable to share drive or folders from Ubuntu 18.06 to W10 or Mac"
date: 2022-02-02
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2022-02-02
Let's start with this:
[https://ubuntuforums.org/showthread.php?t=2441147](https://ubuntuforums.org/showthread.php?t=2441147)

I created this post while back. I'm currently reinstalling these 2 drives I had in a USB3 mounted box to an internal SATA3-connected space. 
While they were in the USB3-connected box, I was able to use GUI and share via SMB. 

As of now, somehow, these are the SAME drives, installed dreict on the motherboard with a SATA cable. They're mounted in "/mnt/Storage 1" and "/mnt/Storage 2". From within Ubuntu they are fully accessible. When you right-click "Properties" and select "Permissions"  you get the drive is owned by "root". No modifiable permissions from there (though I'm sure sudo can bypass this).

I cannot creat a local share point to these two drives. Somehow the message I get back is that no assignable permissions can be modified. 

I don't think "root" as owner is incorrect. I'm sure I could add a user an another owner (actually, not sure about it at all), but would this affect the sharing capability?
Again, I'm sharing to Windows 10 and macOS. I need level 755 access from these machines to the drives. I didn't use to have to type in a password, ever, as in my linked post, perhaps this was some kind of guest access...? 

How to fix this?

EDIT: I juste tried [FONT=Courier New][SIZE=2]sudo chown -R me "Storage 1"[/SIZE][/FONT] but All I get is a summary of "Operation not permitted." Owner & Group is set to root. I'm guessing I have to become root to change ownership to me.

---

### Post by couzin2000 on 2022-02-03
Something else seems to be wrong. I tried [FONT=Courier New]sudo -i[/FONT] and became [FONT=Courier New]root[/FONT]. A simple [FONT=Courier New]mkdir test[/FONT] created a folder on the drive itself. But it's owned by [FONT=Courier New]root[/FONT]. So I tried [FONT=Courier New]chown [/FONT]on my own root-created test folder.
```
chown: you are not the owner of this file - Operation not permitted
```


SO you mean to tell me that AS ROOT' I can't change any permissions or ownership? I can't give away my own files?

And what if I copy the files over to a USB drive? Will the copies be owned by me? Beecause I could copy all the files in there (I do have read-access) and I could copy all of this on a separate drive, then copy them back on a freshly-formatted drive. I ***need ***to regain ownership of these files!

---

### Post by foxsquirrel on 2022-02-04
from the terminal go to the directory holding the file you have problems with and type:
 > ls -l
cut and paste the response.

---

### Post by couzin2000 on 2022-02-05
I was  forced into going a step further, just to ensure I was protecting my data. 
All the data on these 2 disks was a total of 10TB. I copied all of it to a portable drive I own, as a backup. (As soon as those files are copied, I gain full permissions over the copies...weird)
My usb is safe and unplugged.

So now back to the drives. 
I erased the partitions completely, formatted the drives as FAT32. I don't need the extra security, I'm behind a pretty powerful firewall, I'm ok. As sudo -i, I created a folder in root called drives, then created two subfolders called Storage1 and Storage2. I figured out by mounting the drives that when I changed ownership of the 2 folders to myself:myself, that enabled me to change permissions within -- which sounds good.
So I mount the drives. 
Stuck again: regardless of whether the mount folders belong to me, I cannot CREATE a partition on these drives so that I can have full-permission access to it.

I'm sorry, but this isn't normally this complicated. WT is the problem? These are my drives, they are blank, why doesn't Ubuntu give over control?

---

### Post by couzin2000 on 2022-02-05
Should I have partitioned the drive using [FONT=Courier New]gksudo gparted[/FONT]? If I only run [FONT=Courier New]gparted[/FONT] it won't be the same, I presume?

---

