---
title: "can't remove folders from modprobe.d"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by chkneater on 2015-08-22
this may sound off topic for this forum but it actually is relevant, here is what happened:  i  have a Belkin DB600 that has NEVER worked on this comp since upgrading to 12.04.  First I tried everything I could find or think of to install the rtl8192du driver, which should be the correct NON-Windows driver.  I was never able to get it installed so I started looking at different things and I finally came to figure out that ndiswrapper was missing so I wouldn't be able to use the windows wireless drivers.  I followed the specific instructions and installed ndiswrapper and its components and according to everything I've seen so far the driver is installed,  What I believe is happening is when the installation script gets to the modprobe part it starts to error.   I checked out why it was erroring and the error codes were saying that all modprobe files need to be conf. files.  After looking in modprobe.d there were two New Folders in there. I have no idea how they got there but they're causing any wireless attempts to end in errors.  I can't move them, rename them or anything cuz its owned by root.  So I checked in Users and added myself to the root group and also changed the advanced settings on my account to root also, so I SHOULD be able to move those files, it's two directories that ended up in there just name new folder and new folder 2 and they're both empty but they screw up the script.  Can anyone help me fix modprobe.d and get this wireless working... I believe the two stupid directories are all that's keeping it from working.  Thanx for the help and your time, this is a weird one.

---

### Post by chili555 on 2015-08-22
rtl8192du is easily built. I doubt you need ndiswrapper. Let's be sure what you have. Please run and post:```
lsusb
```I also doubt you need to remove files from modprobe.d. You may need to rename them. Let's see what you have:```
ls  /etc/modprobe.d
```

---

