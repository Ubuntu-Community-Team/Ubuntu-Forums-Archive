---
title: "SD cards and USB flash drives not mounting"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by calebhopper on 2010-06-16
When I plug in removable drives, such as my 2 GB flash drive, a popup says 
Unable to mount 2 GB Volume
Error creating moint point: No such file or directory

Note the word moint is misspelled in the popup. This seems to have happened after I tryed using some nautilus shell scripts called mount.sh and unmount.sh which are supposed to mount .iso files easily, but never really worked anyways. I removed the shell scripts from their hidden folder; I forget exactly where nautilus stores its custom scripts, but it still doesn't work.

I've tried repeatedly to reformat the device, but it still has the same message. It will, however, mount if I plug it in while the liveusb is running, so I think I messed something up myself. 
Any thoughts?

---

### Post by viralmeme on 2010-06-16
> **calebhopper said:**
> Error creating moint point: No such file or directory
Check for file permissions on where it is trying to mount.

---

### Post by calebhopper on 2010-07-14
I'm not exactly sure where it is trying to mount during the auto-mount action, but I can manually mount it in the terminal, but that doesn't really help me when I'm trying to make a new live-usb drive.

---

