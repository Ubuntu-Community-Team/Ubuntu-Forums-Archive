---
title: "Windows will not read external drive after ubuntu"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by superdoopergenius on 2009-03-19
New here, hello everybody. 

I'm having a bit of trouble. I got a computer from a co-worker and the hard drive was failing. I popped in a liveCD of ubuntu 7.10 and it worked. I could now see the drive ok. I plugged in an external usb hard drive that is ntfs formatted. I didn't have enough space to transfer the files from the failing drive so I moved some to trash. When I went to trash, there was nothing, but there was no additional space on the external drive. So I unmounted it and plugged it into a windows machine. Now the windows machine won't read it. When I boot off the liveCD I can read it, but I need to read it in windows. Any suggestions?

---

### Post by ntrgc89 on 2009-03-19
I'm assuming you didn't reformat the external drive?

You might try cutting out a partition of the external using gparted (or whatever other partition editor you like), formatting it to something like FAT32 and see if windows can see that part of the drive. That might indicate whether the problem is with windows or with the drive.

---

### Post by jlochhead on 2009-03-19
Sound like you didn't unmount it properly. You cannot just simply pull it out. Right click on the gnome panel and add the mount applet. To unmount the usb stick just click on it in the mount applet and click unmount.

If you do not remove usb flash drives safely in Windows or Linux they will not work correctly on the other OS.

---

### Post by superdoopergenius on 2009-03-19
It sounds like you may be right about unmounting it improperly. Is there any way for me to remedy this? I have tried remounting it on ubuntu and then unmounting it and even shutting down before turning the drive off, but this does not seem to solve the problem.

---

### Post by jlochhead on 2009-03-19
> **superdoopergenius said:**
> It sounds like you may be right about unmounting it improperly. Is there any way for me to remedy this? I have tried remounting it on ubuntu and then unmounting it and even shutting down before turning the drive off, but this does not seem to solve the problem.

If mounting was the problem then remounting and unmounting should have solved it. This is obviously not the problem, unfortunately.

---

### Post by superdoopergenius on 2009-03-19
I was thinking that it may have something to do with the fact that I could not completely delete the files on the external drive...is there a way to delete them permanently? Right now, the trashed files do not show up in trash. Is there somewhere I can go to see these files, perhaps even to restore them?

---

### Post by vijushimpi on 2009-03-19
Did you deleted system restore point files etc. ? Is that drive have any OS ? Try with pluging it before boot.

---

### Post by superdoopergenius on 2009-03-20
restarting my windows pc and then plugging in the hard drive worked. yay:)

---

