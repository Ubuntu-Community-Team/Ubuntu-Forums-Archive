---
title: "unable to mount ext3 usb drive via fstab"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by naja74 on 2009-05-07
I've got an external USB drive that is formatted ext3. I can't get it to mount at boot via fstab.

Here's my fstab entry for the drive:

# Mount My Book
/dev/sdc1 	/media/MyBook 	type 	ext3 (rw)


I get the following error when trying to open the partition after logging in:

[mntent]: line 14 in /etc/fstab is bad
mount: can't find /media/MyBook in /etc/fstab or /etc/mtab

Of course line 14 is my entry above...

Here's the output of ls -la /media:
total 16
drwxr-xr-x  4 root root 4096 2009-05-07 21:23 .
drwxr-xr-x 20 root root 4096 2009-05-05 21:52 ..
lrwxrwxrwx  1 root root    6 2009-05-05 18:02 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-05-05 18:02 cdrom0
-rw-r--r--  1 root root    0 2009-05-07 21:23 .hal-mtab
drwxrw-rw-  2 root root 4096 2009-05-07 19:17 MyBook

I've tried changing the chmod of /media/MyBook with sudo chmod -R 766 /media/MyBook, however the permissions don't seem to change. Even after rebooting I end up with the permission listed above for the MyBook folder.

But here's the kicker.... if I mount it manually with "sudo mount /dev/sdc1 /media/MyBook" it mounts fine. I have rw access to it under my userID, and it mounts as "/dev/sdc1 on /media/MyBook type ext3 (rw)"
But ls -la /media still shows root as having ownership of the /media/MyBook folder which it is mounted under.

I'm missing something here, but I can't figure out what it is.

Any ideas?

---

### Post by starcannon on 2009-05-07
I think what you want is something along the lines of 

/dev/sdc1 	/media/MyBook 	type 	ext3 user

Look here here:[http://wiki.linuxquestions.org/wiki/Fstab](http://wiki.linuxquestions.org/wiki/Fstab)

and here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

for a bit more depth, and of course be sure to 
```
man mount
```
and if your curious
```
man fstab
```

GL

---

### Post by naja74 on 2009-05-08
Got it to work. The fstab entry now looks like this:


# Mount My Book
/dev/sdc1 	/media/backups 	ext3 	relatime 	0 	2

I created another folder in /media to mount it to and it worked. I tried the same line in fstab with a mount point of /media/MyBook with no success.

---

