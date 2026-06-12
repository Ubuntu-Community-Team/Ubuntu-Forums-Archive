---
title: "usb ntfs hdd (storage only) command line"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by joshua_james on 2009-02-19
Hi everyone, just want to say that it's great to be "legacy free" once again and thanks for being here!!

I have Ubuntu 8.0.4 on at Toshiba Satellite A100.  I have a Western Digital usb hdd with the ntfs file system.  It mounts in /media under "new volume".

It works via Gnome and Nautilus.  When I try to access it from the command line, it doesn't recognize "new volume" as a directory.  Am I wrong to think I should be able to access this drive by typing the following;

cd /media/new volume


Thanks again

Cheers!

---

### Post by kk0sse54 on 2009-02-19
Linux doesn't recognize folder names with spaces so you need to put quotation marks around it /media/"new volume"

---

### Post by jerome1232 on 2009-02-19
When there's spaces you need to either encase the path in quotes or escape the space with a backslash like this

cd /media/mount\ point
cd "media/mount point"

second thing, unless the file system has a label of "new volume" it's actually going to be mounted at /media/disk, or if it's the second disk it will be at /media/disk1 and etc...

---

### Post by joshua_james on 2009-02-19
Thanks for the prompt replies.  Neither of the two options will work either.  I guess I could rename the drive, though.

---

### Post by egalvan on 2009-02-19
Even better, replace the space with an underscore.

like so:

"new_volume".

cd /media/new_volume

No need for quotes, or escape characters.

Then you will be even further on the path to "legacy free". :)

(unix did not use spaces in file names;
also case counts.
Upper and lower case are different.)

ErnestG

---

### Post by jerome1232 on 2009-02-19
Out of curiosity what does this output (it will list all the files and directories in /media

```
ls -l /media/
```

---

### Post by joshua_james on 2009-02-19
> **jerome1232 said:**
> Out of curiosity what does this output (it will list all the files and directories in /media

```
ls -l /media/
```

jbertrand@bexnet1:~$ ls -l /media/
total 6
lrwxrwxrwx  1 root root    6 2009-02-18 15:38 cdrom -> cdrom0
dr-xr-xr-x 10 root root 2048 2009-01-21 02:24 cdrom0
drwxrwxrwx  1 root root 4096 2009-02-19 01:36 New Volume

---

### Post by jerome1232 on 2009-02-20
It's the caps that are getting you.

So to cd to it you would

```
cd /media/New\ Volume
or 
cd "/media/New Volume"
```

---

### Post by joshua_james on 2009-02-20
> **jerome1232 said:**
> It's the caps that are getting you.

So to cd to it you would

```
cd /media/New\ Volume
or 
cd "/media/New Volume"
```

i tried it with caps...does this make sense to you?

jbertrand@bexnet1:~$ sudo su
root@bexnet1:/home/jbertrand# mv -v "/media/New Volume" /media/storage
mv: cannot move `/media/New Volume' to `/media/storage': Device or resource busy
root@bexnet1:/home/jbertrand#

---

### Post by joshua_james on 2009-02-20
/media/New \Volume just worked


Thanks for your help!!

---

### Post by jerome1232 on 2009-02-20
I think this is happening because your attempting to move the mount point itself. 

If you just want to remount the drive to /media/storage than you would either relabel the file system to "storage" or you would edit fstab to mount this drive to /media/storage, you could also use the gui to change the mount point.

To relabel [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

You can also click Places->Computer, right click your drive, click rename, then relabel the filesystem.
--edit-- I think I spoke to soon on this gui method as it tosses errors for me, have a look at the other methods instead.

to edit fstab [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
To use the gui to change the mount point just click Places-Computer

Right click your partition, click properties, click the "Drive" tab, for mount point type "storage", click close.


If you are wanting to move the files in /media/New Volume to /media/storage I would do this

```
sudo -i
mkdir /media/storage/New\ Volume
mv -v /media/New\ Volume/* /media/storage/New\ Volume/
```

---

### Post by joshua_james on 2009-02-20
x

---

