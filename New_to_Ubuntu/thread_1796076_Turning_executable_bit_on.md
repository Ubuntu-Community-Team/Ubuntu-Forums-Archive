---
title: "Turning executable bit on"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-07-03
How do I turn on the executable bit of executable file in ubuntu 11.04. The file is in flash drive. I also want to enable this for files in NTFS drives.

---

### Post by wolfen69 on 2011-07-03
Right click the file and go to *permissions* tab. Then check off *allow executing file as program*.

---

### Post by Enigmapond on 2011-07-03
2 ways right off the bat.. in the terminal:

```
chmod -x {path of file or folder name}
```

or right-click the folder or file/properties/permissions and change it manually for owner/user to execute.

Hope this helps...

Cheers!

---

### Post by Swagman on 2011-07-03
Which wont work if the file resides on an NTFS drive

---

### Post by Enigmapond on 2011-07-03
> **Swagman said:**
> Which wont work if the file resides on an NTFS drive Really?...Hmm, I just did it both in the terminal and manually...it may not have any bearing on the Windows side..but on Ubuntu it will...

---

### Post by Swagman on 2011-07-03
I tested it before posting

I usually drag over to the Ubuntu side the file which will set the X bit but not if it stays on the NTFS side. 


This question was asked in another thread about wine and was answered thusly

> 

Then open a terminal, type wine and hit the space bar on keyboard

Then with your mouse grab the .exe you wish to run and drop it into the open terminal box

Then simply click your mouse anywhere in the terminal box to return focus and press enter on the keyboard


Now I suspect it's possible to perform a similar function changing the executable.


sod it.. I'll try it..

hang on

---

### Post by Swagman on 2011-07-03
hmmm . I did it..No error message returned but going into it's properties reveals it not set

```
paul@pauls-desktop:~$ sudo chmod +x '/media/Render/VidCapture/07_04_2007 20_41_57.0001/VTS_01.0002.mpg'
[sudo] password for paul: 
paul@pauls-desktop:~$

```

Over to someone more experienced methinks

---

### Post by Morbius1 on 2011-07-03
Linux cannot change permissions or ownership of a file on an ntfs partition outside of a mount or in fstab. 

If this is all about wine, wine doesn't care or is even capable of determining if a given file has a linux executable bit set. The problem is something called cautious-launcher. 

Here's 3 ways to fix the problem:[http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

---

### Post by RobikShrestha on 2011-07-03
It's not a wine program
I can't do it by right clicking the program because when I check the bit ON, it automatically goes OFF.
I can't do it through terminal:
sudo chmod +x file
./file
: Permission denied
I think it has to do with the drive not having permission to execute files. Please help

---

### Post by rosencrantz on 2011-07-03
You can't set file-by-file permissions on NTFS or FAT, you can only set them for the whole drive. 
Have you checked the permissions with ls  -l anywhere on the drive?

I could think some things to try:
a) Install ntfs-config and give your external drive read/write permissions. This might also set the executable bit (for everything on the drive, mind you).
b) Quick one-time solution: do a manual mount. E.g.
sudo mkdir /media/mydrive
sudo mount -t ntfs -o umask=000 /dev/sdb1 /media/mydrive
Replace sdb1 with what's appropriate for your drive (e.g., check ls -l /dev/disk/by-id). This should give full rights to everybody, google umask if you want different permissions.
c) I hope this is still applicable: try writing an udev rule if you want a permanent solution. Arch Linux has some templates:
[https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g](https://wiki.archlinux.org/index.php/Udev#Mount_under_.2Fmedia.3B_use_partition_label_if_present.3B_ntfs-3g)

---

### Post by RobikShrestha on 2011-07-04
Thanks the mounting thing worked. Would please explain the parameters -t, -o umask 000?

---

### Post by rosencrantz on 2011-07-04
the -t option specifies the file system, e.g. vfat, ntfs, ext3..
-o is followed by an option list, such as ASCII locale or permission masks.
umask sets user based permissions (so first 0 for user, second for group and third for everybody). 000 gives read, write, execute permissions to everybody, something like 037 would give full access to the user, read to his group and block the drive for everybody else. Check
[http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)
for more details, but note that the octal umask codes are inverted (777 instead of 000 for full access)
For more on mount options try man mount or wikipedia's fstab page:
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

Oh, and I found a typo in my last post:
it should be "mount -t ntfs -o umask**=**000 /dev/sdb1 /media/mydrive" Sorry. Funny you got no complaints about that.

---

### Post by RobikShrestha on 2011-07-06
Thanks for the help.

---

