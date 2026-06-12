---
title: "Permissions for usb stick"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by OllieGab on 2009-10-30
For some reason one of my usb memory sticks will not let me add any files. Permission status read-only, it says. I can only think that when I changed some permissions for some files some time ago this also caused any usb stick connected to the machine to change as well.
So, how do I go about to give myself permission again? I tried with right clicking on the usb icon (when inserted), going to permissions and change there. It didn't protest to my action but neither did it actually carry out "my wishes".
I assume the best way is via the command line, but how?

Cheers Ollie

---

### Post by Buuntu on 2009-10-30
You can do it a couple of ways:

1) Right click on the icon, select properties, and go to the Permissions tab

2) From the command line run the command:
(Make sure to replace /media/usb_disk to the actual name of your usb stick)
```
sudo chmod +w /media/usb_disk
```

That command will make /media/usb_disk writable.  It basically adds write (+w) permissions to the file - you can use that for anything.

---

### Post by falconindy on 2009-10-30
You need to make sure the USB stick is being mounted with ntfs-3g, and not ntfs (as the basic ntfs driver doesn't have write support). If it's mounted correctly, it may show up as type 'fuseblk' in the output of the `mount` command, rather than ntfs-3g.

---

### Post by OllieGab on 2009-10-30
I don't seem to find the name of my usb stick.
Tried fdisk and lsusb but didn't really get any the wiser.
fdisk shows my four partitions of my hard drive, nothing of the usb stick (though I can access the contents of the stick)

---

### Post by Buuntu on 2009-10-30
Navigate over to /media and search around until you find the folder that is your usb.

---

### Post by OllieGab on 2009-10-30
I found the name of the usb stick and I did the 'chmod.....' and the system seemed to accept that.
I did 'ls -l /media/ to check and it said I had both read and write permissions.
Still, when I try to drag a folder across from my desktop to the memory stick I get an error message: "Access denied. The destination is read only'

??

---

### Post by OllieGab on 2009-10-30
This is the output of the 'mount' command:

/dev/sdf1 on /media/2CA9-652C type vfat (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

---

### Post by falconindy on 2009-10-30
> **OllieGab said:**
> This is the output of the 'mount' command:

/dev/sdf1 on /media/2CA9-652C type vfat (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

FAT partition... You'll need to mount it manually I suppose. Notice the 'ro' and the 0077 dmask? That's what's preventing you from writing.

```
sudo umount /dev/sdf1
mkdir $HOME/usb
sudo mount -t vfat /dev/sdf1 $HOME/usb -o rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,umask=0000,dmask=0000
```
And then you'll be able to write.

---

