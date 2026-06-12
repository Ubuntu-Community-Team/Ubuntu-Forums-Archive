---
title: "moving files from hard drive to external drive"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by 007casper on 2009-08-25
If I do copy and paste the external drive unmounts.
 
In the terminal I tried sudo mv /home/cat/main /dev/sdc1
 
 I got...
 mv: cannot overwrite non-directory 'dev/sdc1' with drivectory 'home/cat/main'
 
 I created a directory in the external drive
 I got... 
 mv: accssing 'dev/sdc1/directory': Not a directory
 
 what is the proper way of moving files through the terminal?
 
 Thank you.

---

### Post by nhasian on 2009-08-25
your not trying to move your home directory while your logged in are you?  You should boot off the liveCD, then move the home directory while its not in use.

---

### Post by 007casper on 2009-08-25
I am trying to move one of the folders that is in the home directory.  Is there any other way to do this?

I was always able to copy files to external drive / flash drive without a problem.  However, the current folder I am trying is a bit large in size.

---

### Post by 007casper on 2009-08-25
if I tried to copy and paste to the external drive it works.  However, if the name of the file has space, then the external drive unmounts.

I got into habit of not putting dash, or underscore for files in windows.  It seems as linux doesnt like this.  If the file is called "first folder", then it fails.  However, if the file is called "first-folder", it works.

is there a way to to insert dash or underscore to these files in order for me to unload it? 

I cant boot from cd at the moment, because I am using testdisk to rescue files from a failed hard drive.  It is still copying files from failed hard drive to the main hard drive.  In the mean time I am trying to unload some of rescued data from main hard drive to the external hard drive.

Thank you.

---

### Post by 3rdalbum on 2009-08-26
Well, your main problem is that you are trying to move files to the device file name. You should be copying or moving files to the mount point (the place where you can actually see the contents of the destination disk).

On Ubuntu, the first disk mounted in Gnome tends to be mounted into /media/disk - try that.

For the second question, if you are specifying a file path with spaces in it, you either need to "wrap the whole file path in quotation marks" or\ put\ a\ backslash\ before\ every\ space.

---

### Post by 007casper on 2009-08-26
i tried sudo mv /home/cat/main /media/backup

then the hard drive umounted... again, I think due to the space issue... is there anyway to insert dash, underscore, or slash in batch?

The hard drive is 1TB... 800gb full

It is a bit difficult to go through them one by one...

thanks

---

### Post by unutbu on 2009-08-26
007casper, perhaps the easiest way to copy files from the (internal) hard drive to the external drive, is to use rsync. For example,
```

sudo rsync -a /home/cat/main/ /media/backup/
```

Will copy everything in /home/cat/main/ and place it in /media/backup/main/

This will preserve, ownership, permissions, and timestamps, as long as the target filesystem supports such things. (FAT, for example, does not support ownership and individual file permissions. I'm not sure about NTFS. ext3, ext4, jfs, xfs filesystems should all work fine.)

If you use rsync, you do not have to worry about the spaces in directory and filenames.


On the other hand, if you really want to rename all your files and directories to get rid of spaces, then you could run this command:```


sudo find . -depth -exec sudo rename 's/ /_/g' "{}" + 
```

Please test this command on a small directory first. Be careful with it, since it could change the name of an awful lot of files, and there is no way to revert the change without backups. All in all, I think it is safer to try the rsync command first.

---

### Post by LewRockwell on 2009-08-26
> **007casper said:**
> i tried sudo mv /home/cat/main /media/backup

then the hard drive umounted... again, I think due to the space issue... is there anyway to insert dash, underscore, or slash in batch?

The hard drive is 1TB... 800gb full

It is a bit difficult to go through them one by one...

thanks

you do realize what your command attempted, do you not?

perhaps you desired to use "cp" and not "mv"?

.

---

### Post by cmcanulty on 2009-09-27
Grsync is a graphical interface that makes it a bit easier for me

---

