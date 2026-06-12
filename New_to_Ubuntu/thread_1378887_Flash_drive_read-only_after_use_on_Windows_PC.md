---
title: "Flash drive read-only after use on Windows PC"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by kobudo on 2010-01-12
Ok, so I have a 32gb flash drive that I have taken to work (The work PC is a Windows 2000 machine), and after I brought it home, I plug it into my PC (running Karmic). I have the flash drive formatted as FAT32.

All files that were copied to the flash drive from the Ubuntu box before using the drive on the Win2k box are now read-only. Attempting to change them from read-only displays an error message.  (Could not change the permissions of "disk": error setting permissions: Read-only file system). I have checked the drive in disk utility, and it says the drive is clean. In terminal, I have also tried the check in terminal by running dosfsck -a -v /dev/sdb (where sdb is the drive) and it says this:

```
dosfsck 3.0.3 (18 May 2009)
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
open /dev/sdb:Permission denied
```

At least dosfsck is getting the same lack of permissions.

Anyone know what is causing this? Or how it can be corrected, short of formatting the drive and copying all my files back onto it? Or other tests I can perform if you need more information?

EDIT: Also, I can copy files off of the drive (to, say, my desktop) but I can't add new files. It's kind of acting like a CDrom.

EDIT again: after running dmesg and seeing a bunch of i_pos_0 errors, a search recommended I try the following command:

fsck.vfat /dev/mmcblk0 -a -w

... and again got the "permission denied" result.

---

### Post by kobudo on 2010-01-12
bump? Anyone been able to fix similar issues???

Edit, I also just installed testdisk and poked around, the drive checked out okay there, too.

---

### Post by bcn17 on 2010-01-12
I have not had this problem. 

Maybe open a terminal and try this- 

>cd /media
>ls -l

Find out what the  permissions are for your jump drive and report back here and/or try this:

>sudo chmod -R 700 name.of.folder.drive.mounts.to

This will change the permissions of the folder that the drive mounts to, to be read, write, and executed for the owner of the drive, which should be you. 

If when you did your 'ls -l' there was a root:root and not a yourusername:yourusername then try this command as well to change the owner of the folder.

>sudo chown -R your.user.name:your.user.name /media/name.of.folder.drive.mounts.to

Notice the ":" in the command above.

I would do the above commands with the usb drive NOT plugged in. However, I am not sure if it matters.

---

### Post by clevertomato on 2010-01-26
Read my post at [http://ubuntuforums.org/showthread.php?t=1382173&page=2](http://ubuntuforums.org/showthread.php?t=1382173&page=2)

---

### Post by lisati on 2010-01-26
Don't forget to "safely remove hardware" before disconnecting USB devices!

---

### Post by clevertomato on 2010-01-26
Anyone know WHY Linux can't deal with a flash drive being removed without first clicking "safely remove hardware"? I understand if it was in the middle of writing a file, but otherwise why should it mess things up? Windows can deal with it (I and others have done it safely in Windows many times without negative consequences... nobody I know takes the time to click on "safely remove hardware" for USB flash drives in Windows).

Just curious, cuz it's just another hoop to jump through and when a different OS can gracefully handle it, it makes one wonder.

---

