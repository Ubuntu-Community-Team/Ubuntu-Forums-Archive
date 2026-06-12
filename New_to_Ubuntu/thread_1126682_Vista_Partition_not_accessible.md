---
title: "Vista Partition not accessible"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by hrobinson23 on 2009-04-15
After yesterdays, dual boot installation because of a vista virus that broke the OS. I cannot access the NTFS partition because I am unfamiliar with how to run as root, which I think is sudo but I am not sure? Also, I am unfamiliar with the mount command syntax because, what I think I am typing, is not working. I need my data from the old partition? 

These are the errors:

[LIST] DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[/LIST]

[LIST=1]logfile indicates unclean shutdown (0,1) failed to mount dev/sda1, NTFS is marked in use.
[/LIST]

I got it to work briefly but the it disappeared after a reboot. when I was messing around with windows after a reboot.

---

### Post by jimmy the saint on 2009-04-15
The easiest thing to do would be to boot vista and do a proper shutdown.  Windows marks files as "in use" when it is using them, and when they are safely removed or the computer is properly shutdown, it releases them.  Ubuntu has a very difficult time reading disks marked as "in use" by windows.  This happens to USB drives a lot as well.

Like I said, the easiest thing to do is just allow vista to do a proper shutdown, then use nautilus to browse the disk.  You should not need to manually mount the disk, nautilus can take care of that once you have performed a proper shutdown in vista.

---

### Post by hrobinson23 on 2009-04-15
The crcdisk.sys is where the safemode boot process stops, then loops for a reboot. Then ChkDsk starts with a check, then back to the same. My lenovo rescue disk will not allow me to access partition 1 with only 2GB of free space. I was thinking that i could re-install which would repair or copy on the files that were corrupt. That did not work either. I need a way to shut down or trick the computer into thinking that c is no longer in use. Incidentally, I have four usb drive icons that must be the same issue, because I do not use them. I never had a clean shut down of windows.

---

### Post by Monotoko on 2009-04-15
Well, if you are certain that you cannot boot into windows anymore, just use this from the terminal (it will force mount)

Example (you will have to change it to suit your system)

```
mount -t ntfs-3g /dev/sda1 /media/windows -o force
```

---

