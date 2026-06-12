---
title: "moving a Linux text file to my Win XP e-mail by USB drive"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by dpeters on 2009-01-06
I see all these long command outputs posted in the forums and am trying to learn how they do it. 
I created a file I.E ifconfig > ifconfig.txt. Copied it to a Fat32 thumb drive, removed the thumb drive from the Linux server (networking is broken) and plugged it into my Windows PC so I can e-mail it to someone helping me troubleshoot a problem.
When I opened the drive it is blank. I tried chmod 0777 ifconfig.txt. It didn't work. Everything is being done at the command line as there is no GUI. What am I missing?

---

### Post by adult swim on 2009-01-06
you might want to look into notepad ++ that can open linux txt documents in windows
[http://notepad-plus.sourceforge.net/uk/site.htm](http://notepad-plus.sourceforge.net/uk/site.htm)

---

### Post by dpeters on 2009-01-10
Thanks for the reply. The problem is, the files are not there.
Mount and umount commands came back with errors. After a bit of poking around I edited the fstab file and added the sdc1 device there (/dev/sdc1/ /mnt/usb1 vfat defaults 0   0), a mount point in /etc/mnt had already been done, rebooted, plugged in the thumb drive, and mounted the /dev/sdc1 to /mnt/usb1 and it worked. So, copied the files to /mnt/usb1 and umount /mnt/usb1. Took it over to the "other" machine and there they were. :) But,
the formatting is all messed up making them difficult to read.
I'll ask a new question about this.

---

### Post by cerealtx on 2009-01-10
are you ejecting the device properly? there should be no problem for windows reading the information, when u chmod, does it give u errors? and have u checked the permissions to make sure that it was acctually modded?

---

### Post by The Cog on 2009-01-10
Agreed with cerealtx - If you unplug the drive without unmounting it, the file may not have been written. It may still just be in the disk cache in memory. Right-click the drive icon on the desktop and unmount it, This is the equivalent of "safely remove" in windows, and for the same reason.

---

### Post by dpeters on 2009-01-10
Apparently, see my previous message, USB operation is not automatic on ubuntu server 8.10. There is no gui. The kernal recognized the deviced being plugged in as the device appeared in the device list as sdc1 whereas before it was not there. Mounting is a different matter. 
Mounting didn't work until the "fstab" entry was created. Chmod did not cause an error and ls -l verified the chmod. Manual mounting and unmounting was where I received an error. 
I had to manually create the mount point and manually mount it before any files were visible on the device or before you could copy anything to the device. I was told "udev" was supposed to take care of this. When I tried to copy to the device the file apparently ended up in a buffer and did not get written to the device in spite of "cache write through" appearing from the kernal when I plugged it in. This may explain why I could list the files on /mnt/usb1 when I had inadvertantly left the thumb drive on the "other machine". All of this works perfectly on my 8.10 desktop with gnome.

---

### Post by The Cog on 2009-01-11
Oops. I missed the bit about being a server version - no desktop. Unmounting with **sudo umount /dev/sdc1** should do the trick.

---

