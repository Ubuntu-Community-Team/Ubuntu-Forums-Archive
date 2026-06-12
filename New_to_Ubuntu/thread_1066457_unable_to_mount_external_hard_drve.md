---
title: "unable to mount external hard drve"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Dfnoboy on 2009-02-10
okay, I have seen some other posts about this, but haven't been able to solve it by them (but I've tried ;__; )

When I click on Dfnoboy 230, I get this error message:
You are not privileged to mount the volume 'Dfnoboy 230'

My fstab is as follows:

```
# /dev/hdb1
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sdc1 /media/disk ntfs-3g default 0 0
UUID=9125c9ac-da02-44b2-b79e-e3bd8b619cf1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c0acb0f-e049-ad8e-b7b8-b37acf6d213a none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I manually added the line 
```
/dev/sdc1 /media/disk ntfs-3g default 0 0
```
at the recommendation of someone else for a similar problems. I also commented out the last line based on another recommendation. 

Also, I installed Ubuntu  via a flashdrive (the asus 900 has no CD drive)


Thanks for  any help!
-Dfnoboy

---

### Post by KuroYoma on 2009-02-10
I have a 500 gig external HD and have had some problems too.  I need more information.  Going by your fstab I take it your external is ntfs.  Also gives the impression that you use your external with windows as well.  If so do you "Safely remove hardware".  If not do you recieve any errors when you first plug the external in.  If so what does the error say?  Just to make sure this is a USB external.

---

### Post by Dfnoboy on 2009-02-10
yeah, I also use Windows with this drive. When I plugged it into Windows XP, there were no errors.

Also, sometimes the drive just does work. But most of the time it tells me I am not privileged.

---

### Post by egalvan on 2009-02-10
> **Dfnoboy said:**
> 
**When I click on Dfnoboy 230**, I get this error message:
You are not privileged to mount the volume 'Dfnoboy 230'

My fstab is as follows:

```
# /dev/hdb1
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sdc1 /media/disk ntfs-3g default 0 0
UUID=9125c9ac-da02-44b2-b79e-e3bd8b619cf1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c0acb0f-e049-ad8e-b7b8-b37acf6d213a none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I manually added the line 
```
/dev/sdc1 /media/disk ntfs-3g default 0 0
```
at the recommendation of someone else for a similar problems.
 I also commented out the last line based on another recommendation. 

Dfnoboy


Curious, I have two external hard drives hooked via USB, neither shows up in fstab, and they are both accessible.


Question... where do you "**click on Dfnoboy 230**"?
Desktop? File browser window?

Observation... to avoid problems in the future, you should change/remove the blank space from the drive label (drive name).
either use an 'underscore' (Dfnoboy_230), or remove it (Dfnoboy230).

Following some helpful advice, I changed ownership of my external drives, and made sure ntfs-3g was installed.
(I also removed/changed spaces, and used only lower-case letters)

[CODE]sudo chown -R username: /path/to/drive[CODE]

---

### Post by KuroYoma on 2009-02-10
is it saying that you are privileged to mount it or that you are not priviliged to read/write on it?  Also I was asking that when you plug in into linux after plugging it into windowz do you get any error messages on your ubuntu linux?  If it mounts to /media/disk everytime then just change the privileges on that folder.  

First
```

sudo chown [COLOR="Red"]username[/COLOR] /media/disk
[br]
sudo chmod a+rwx /media/disk

```

I can't guarentee this will work but it should.  If not go to you Synapsis Package Manager and look for an application designed for mounting ntfs external/thumbdrives and see if that works.

---

### Post by Dfnoboy on 2009-02-11
i renamed it to Ein.

Also, the drive shows up in Places, but not the desktop.
It says I am not privledged to mount it.

I plugged it into Windows and copied some files. When I plugged it back into Linux, it was the same error message: "You are not privileged to mount the volume 'Ein'."


edit: okay, I tried to mount it through the terminal using
```
 sudo mount /dev/sdc1 /media/disk
```

and this was the output:
```
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use
```

Then it told me to go to windows and safely shut it down, so I did. Then I retired the mount command and got this:
```
fuse: failed to access mountpoint /media/disk: No such file or directory
```

so...

---

### Post by KuroYoma on 2009-02-11
Ok gotcha,  the best way to take care of this problem is to log into windows and hook up the external.  Once it loads, go to the bottom right corner and look for the safely remove icon.  This will cause it to shutdown clean.  or you can do this in the terminal.

```
 
sudo mount -o ntfs-3g /dev/sdc1 /media/disk -t force

```

this will clean the shutdown record and mark the external as not in use and then mount it to /media/disk.  Obviously if you get an error saying /media/disk then do
```

sudo mkdir /media/disk

```

then run the code up above.  Once again you can just log into windoeze and fix it that way.

---

### Post by Deldo on 2009-02-11
I also have these problems with one of my external harddrives. The problem is that I don't close the harddrive proberly in Windows. 
When it is connected in WinXP, I just shut it down by cutting the power to my harddrive. I need to disable the harddrive from the "Safely Remove Hardware" or what it is called. Try that.

---

### Post by detroit/zero on 2009-02-11
You only need to include the drive in fstab if you want it to automount at boot. Otherwise, just erase the entry for the external HDD altogether, and the drive will mount itself when you connect it.

Not that this has anything to do with your problem, really, but there's no need for an external device to be in fstab unless you always have it connected and always want it mounted.

---

