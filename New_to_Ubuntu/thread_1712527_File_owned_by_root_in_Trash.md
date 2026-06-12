---
title: "File owned by root in Trash"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by CVGH on 2011-03-22
I've got a file in trash owned by root but can't figure out where the .Trash directory is. I can chmod it if I can find it......

---

### Post by sisco311 on 2011-03-22
Your user's "home trash" directory is ~/.local/share/Trash. You may also have trash directories in &#8220;top directories&#8221; of some or all mounted resources (/media/partition/.Trash or /media/partition/.Trash-*UID*).

For details check out [The FreeDesktop.org Trash specification]("http://www.ramendik.ru/docs/trashspec.html")

---

### Post by CVGH on 2011-03-23
I probably should have said this is a USB install, so probably the file structure is a bit different.....

---

### Post by sisco311 on 2011-03-23
> **CVGH said:**
> I probably should have said this is a USB install, so probably the file structure is a bit different.....

I doubt, as far as know, Ubuntu follows the FreeDesktop.org specification.

---

### Post by CVGH on 2011-03-23
/local/share/Trash/files is empty....
Yet the trash can still has the root owned file.

---

### Post by alphacrucis2 on 2011-03-23
> **CVGH said:**
> /local/share/Trash/files is empty....
Yet the trash can still has the root owned file.

Try 

```
gksudo nautilus
``` 

This runs nautilus as root

Try and delete the offending file from /home/<user>/.local/Trash/files

That will probably move the file to root's trash:

and navigate to:

/root/.local/share/Trash/files

See if you can see the offending file 

Not sure if you can delete them from there in nautilus though. You may have to do it from the terminal via sudo rm

---

### Post by CVGH on 2011-03-24
Every trash folder I can find is empty.
I made the USB install using gtk-creator-usb.
The persistent "file" was casper-rw, 128MB.
Deleted it and then ran gparted to make a 14GB, ext2 partition
named casper-rw. This was so I could have more space to install
programs. Shut down, removed CD and have booted from the USB ever since.
So somehow that file is stuck in a trash folder somewhere.......

If I click on the trash ican and look at properties I see:
Location:  trash:///
Volume:   unknown

If I try Open With I see:
"Select an application to open \cdrom\.Trash-999\files\casper-rw"

Fired up GnomeCommander and there it is!!!!!!!

Thanks to you all for helping me figure this out!!

B.

---

### Post by sisco311 on 2011-03-24
Try to find the file:
```
sudo find / -iname "casper-rw" 2> /dev/null
```

---

