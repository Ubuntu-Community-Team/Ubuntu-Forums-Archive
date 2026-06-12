---
title: "mounting external HDD"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by cronos on 2010-01-09
My external USB HDD was plugged into my computer since I installed Ubuntu 9.10 on the day it was officially released.  I have never removed the HDD.  Most of my music is stored on the HDD.

Anyway, a few days ago, I had to remove the external HDD. But, when I connected my external HDD again, Songbird reports that it cannot play the music files, because the files cannot be found.

When I look at the /media path, I have noticed that I have two folders with almost identical names.  One folder is called 269E-979C, the other folder is called 269E-979C_

If I try to open 269E-979C, a requester reports, "You do not have the permissions necessary to view the contents of "269E-979C".  However, 269E-979C_ works fine.

How do I clean up the /media folder so that 269E-979C can display the contents of the external HDD and work with Songbird. And how to remove 269E-979C_ ?

---

### Post by aaronp on 2010-01-09
> **cronos said:**
> 
If I try to open 269E-979C, a requester reports, "You do not have the permissions necessary to view the contents of "269E-979C".  However, 269E-979C_ works fine.

How do I clean up the /media folder so that 269E-979C can display the contents of the external HDD and work with Songbird. And how to remove 269E-979C_ ?

The drive should only be mounted in one of these locations. Not sure what has happened here but try typing ```
mount
``` into a terminal and see if the drive is being mounted to /media/269E-979C or /media/269E-979C_.
It is likely to be the latter. If so, you can change your fstab to mount it to the other location:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Before doing that though, the issue you may have here is the permissions.
cd to /media in a terminal and type ```
ls -l
```
It will show you the permissions and owner/group of the original folder.

Theoretically if you use chmod, chgrp and chown to make this match the 'new' underscore version of the folder then change the mountpoint in fstab it should work.

---

### Post by cronos on 2010-01-10
Thanks for the reply, and I am sorry about the delay.  Anyway, I have managed to resolve the issue (maybe it was luck).

After checking the permissions using the ls -l command, I basically ran gksu nautilus, unmounted the external HDD, moved the 269E-979C_ folder to a safe place and changed the permissions of 269E-979C from root to my username, andrew.

Everything works fine.  But, I would like to backup the mount settings, or at least learn where the settings are stored.  I have checked fstab, but it does not have any mount files listed.  This is all I have, which is a swap file and my Ubuntu partition:

UUID=beaf8ff6-f431-4428-a073-f77b8f6c968a swap swap sw 0 0
UUID=8d95225c-4dc9-4099-93de-bdc75a74b09f / ext4 defaults 0 1

---

### Post by aaronp on 2010-01-11
> **cronos said:**
> Thanks for the reply, and I am sorry about the delay.  Anyway, I have managed to resolve the issue (maybe it was luck).

After checking the permissions using the ls -l command, I basically ran gksu nautilus, unmounted the external HDD, moved the 269E-979C_ folder to a safe place and changed the permissions of 269E-979C from root to my username, andrew.

Everything works fine.  But, I would like to backup the mount settings, or at least learn where the settings are stored.  I have checked fstab, but it does not have any mount files listed.  This is all I have, which is a swap file and my Ubuntu partition:

UUID=beaf8ff6-f431-4428-a073-f77b8f6c968a swap swap sw 0 0
UUID=8d95225c-4dc9-4099-93de-bdc75a74b09f / ext4 defaults 0 1

You will need to add a new line to your fstab (back it up first)

The UUID is a unique identifer for the drive that allows it to be found and mounted even if the location or name changes.

Start with this to find the UUID of your drive:

```
sudo blkid
```

Your drive should be listed there with a long unique number
Now, copy and paste the UUID into your fstab, with a line that looks like this after your other lines:

```
UUID=2dee03f0-c329-427b-88a9-b382bdafd033  /media/data  ext3  defaults  0  0
```

obviously replace the UUID with yours, and the mountpoint as well as changing ext3 to whatever filesystem your drive uses (should come up when you use blkid)

Save the fstab then unmount the drive manually.
Use ```
sudo mount -a
``` and the drive should be mounted automatically for you.

If it all works, you can just save a copy of your fstab somewhere as your 'backup' of mount settings.

---

### Post by cronos on 2010-01-11
Thankyou very much for your help.  Followed your instructions.  Works perfectly, thank you.

---

### Post by cronos on 2010-01-12
OpPs! I just discovered a small problem. I cannot copy any files onto the external HDD, because the permissions are wrong.

In the /media folder, I have tried using:
sudo chown andrew:andrew ext1

Now when I type ls -l, I get:
drwxr-xr-x 18 root   root   32768 1970-01-01 10:00 ext1

I tried using gksu nautilus and changing the permissions, but it doesn't seem to make any difference.

Any ideas?  Thanks in advance.

---

### Post by SecretCode on 2010-01-12
What filesystem is the external drive? If it's ext3/4 you could try 
```
sudo chown **+R** andrew:andrew /media/ext1
```
(Don't do this if you have system backups on this drive or anything else that needs permissions preserved.)

If it's ntfs, the mount options may need to be changed. I use lines in fstab like this:
```
UUID=181C0FED1C0FC52A	/media/Data	ntfs-3g	rw,users,umask=0000,auto	0	0
```

---

### Post by cronos on 2010-01-12
I think it is a fat32.  I have never formatted the HDD since I brought it.

---

### Post by SecretCode on 2010-01-12
Have you already created an entry in fstab for it? If so, post it here

---

### Post by cronos on 2010-01-12
UUID=beaf8ff6-f431-4428-a073-f77b8f6c968a swap swap sw 0 0
UUID=8d95225c-4dc9-4099-93de-bdc75a74b09f / ext4 defaults 0 1

UUID=26F6-9596 /media/ext1 vfat defaults  0  0

---

### Post by SecretCode on 2010-01-12
OK, try changing
```
UUID=26F6-9596 /media/ext1 vfat defaults 0 0
```
to
```
UUID=26F6-9596 /media/ext1 vfat rw,users,umask=0000 0 0
```
(but keep a backup of the original fstab)

---

### Post by cronos on 2010-01-12
Bingo! :) It seems to be working ok now.  I can read/write/delete files, etc.

If I type: ls -l, it still shows up with root as user/group, but all the files and folders have full permissions.  Eg:-

drwxrwxrwx 10 root root      16384 2009-10-04 11:07 Nexuiz
-rwxrwxrwx  1 root root  931253731 2009-10-01 17:36 nexuiz-252.zip

Thankyou for your help. :)

---

### Post by danwosere2007 on 2010-01-12
I had this exact same ballache upon first using ubuntu a few years back. I made the complete rookie error (der=P) of not unmounting the drive first, it was a complete and utter arsehole to try and fix, but the support groups such as this forum were awesome and eventually sorted it out. The problem was compounded by the fact that i was going between a windows and linux machine which didnt seem to make my harddrive very happy. Not very happy at all. Good luck with ya problem im sure in a few years youll look back and be like doi. =P. - Obi Dan Kinobi :P

---

### Post by cronos on 2010-01-12
Ubuntu is great.  But, when things go wrong, it can drive you insane, especially if you don't know how to resolve the issue.  And, in my case, just when I thought I resolve something, I discover that I have another issue. :)  I would be lost if I didn't have this fantastic forum to turn to.

Oh, I feel your pain when you had to switch between Windows and Ubuntu.  Same thing happened to me recently, except Windows decided to boot my HDD using PIO instead of DMA, which often took over 8 minutes to boot on the day when I wanted help ASAP. :)  So, resorted to using Damn Small Linux Live CD after losing my patience. :)

The good thing about Ubuntu, etc., is that when something goes wrong, it usually tells you in plain English what is wrong.  And, there are usually ways to fix the problem/s.  I am always learning something new with Ubuntu, which makes Ubuntu fun to use.  As much as I hate dealing with software problems, I know that I can learn from my experience, just like you. :)

My next task is to convince my friends to use Ubuntu, which I have been trying to do for a while. I will not give up though. :)

---

### Post by danwosere2007 on 2010-01-13
Haha yeah good on ya man, i've found myself preaching the good system ubuntu of late to people, don't even realise im doing it, people using windows are all like yeah im running so and so anti-virus software so i've never had a virus...whilst im there nodding along nonchalantly keeping the sentiment "windows is one big disease ridden whore of a virus in its own right" silently to myself, and thinking the people who make the anti-virus software are more than likely the ones creating the damned viruses in the first place. Good way to stay in business though eh?. I know perhaps i come across as sounding fairly experienced with ubuntu. But the first thing and i think a good rule of thumb to live by is,  theres always someone who is more experienced than me , (i.e programmers for instance). Or as one great philosophiser dude quite possibly once said. "True understanding comes from understanding, that you understand very little" Haha well it was something like that anyways, maybe i changed it slightly to make it sound more catchy but there we go ;). One thing about Ubuntu that is cool, you learn as you go along, 2 years ago if youd shown me that terminal screen i'd be like erm o.k this is trippy, but get used to it a little and you'll be sudoing yourself around the shop in no time ;).

*P.s yeah the forums kick *** though, if it wern't for them i don't think it would be 1/100 as easy to pick up the basics as it is =P.

---

