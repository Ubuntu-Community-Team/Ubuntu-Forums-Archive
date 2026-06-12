---
title: "locked out of usb file system:  help"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-12-30
OK, I will come right out at the beginning and admit that I did something stupid, and I knew better.  I was running a script that I created in synaptic to download some packages.  It was taking some time, and the computer was not doing anything.  I wanted to try a different approach.  So, I tried to unmount the usb drive, but it wouldn't let me.  So ... I just pulled it right out, and restarted the computer.  (I'm running off of a live cd and experimenting, so I wanted to start fresh with a restart.)

Now, I have some package files on the usb drive that I want to delete, but it won't let me.  I get two kinds of errors.  One is a read-only error, which is strange because the file owner, which is me (called "ubuntu"), has full permissions.  The other error is an input/output error, and I have no idea what that means.  There are also lock symbols on the folder icons.

How can I fix this?  I want to delete some files and empty the .Trash-999 file.

---

### Post by AndThenWhat on 2009-12-30
Try hitting ALT + F2 and typing in:
```

gksu nautilus /
```

Then navigate to your USB drive (probably in the "media" folder) in the window that pops up and try to delete the files.

If that doesn't work you should try formatting the USB drive, which will erase the files off of it unfortunately.

---

### Post by MichaelBurns on 2009-12-30
UPDATE:
The method
Alt+F2 >> gksu nautilus / >> media/BACKUP/ >> (delete files)
does not work.  I get the same errors.

> **AndThenWhat said:**
> If that doesn't work you should try formatting the USB drive, which will erase the files off of it unfortunately.Is that my punishment for misbehaving and pulling out the drive without permission :Q

---

### Post by corncob on 2009-12-30
Hit ALT F2 and enter
```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```
See if that lets you do anythying.

---

### Post by wilee-nilee on 2009-12-30
Use gparted on the live cd to delete the thumb and install a new partition if you don't need the script.

---

### Post by MichaelBurns on 2009-12-30
Thanks to everyone who responded.  I just copied all the files to a harddrive that I have lying around, reformatted the flash drive (in gparted), and then transferred the files from the harddrive back to the flash drive.  That worked, but only because I happened to have that harddrive lying around.  It would still be nice, for future reference, to know how I could just get access to the flash drive in the first place (i.e. without reformatting), because I have more experimenting to do.

> **wilee-nilee said:**
> Use gparted on the live cd to delete the thumb and install a new partition if you don't need the script.I have no idea what that means.  Are you just suggesting a reformat as AndThenWhat did?  That's what I decided to do (as stated above).

---

### Post by Geoff918 on 2009-12-30
> **MichaelBurns said:**
> Thanks to everyone who responded.  I just copied all the files to a harddrive that I have lying around, reformatted the flash drive (in gparted), and then transferred the files from the harddrive back to the flash drive.  That worked, but only because I happened to have that harddrive lying around.  It would still be nice, for future reference, to know how I could just get access to the flash drive in the first place (i.e. without reformatting), because I have more experimenting to do.

I have no idea what that means.  Are you just suggesting a reformat as AndThenWhat did?  That's what I decided to do (as stated above).

He basically just told you to format the USB drive. Nothing to worry about if your problem is resolved.

---

### Post by MichaelBurns on 2009-12-31
Oh, I just thought that it would be helpful to relay this tidbit of info to any of you who are having a problem to refort a flash drive.  The "Partition Editor" would not let me edit the existing (single) partition.  ***I had to unmount the flash drive***, and then I was able to delete the partition and reformat using the "Partition Editor".  That may be obvious to you, but it was just a matter of fumbling around for me.  In retrospect, it makes sense.

---

