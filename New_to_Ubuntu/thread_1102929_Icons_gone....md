---
title: "Icons gone..."
date: 2009-03-22
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-03-22
Hi, I recently updated my OS, and now a few icons are gone...

Looking at the icons directory in /usr/share showed that the icons that are not showing are corrupted...

How can I run fsck to just diagnose the erros?
(drives are mounted)

---

### Post by WitchCraft on 2009-03-22
OH, good:

 Various options for **fsck** exist: 
  **-f**    performs a fast check; files systems with  check = true  entries in **/etc/filesystems** are checked 
 **-p**    fixes minor problems without interaction from user 
 **-y**    gives permission to correct every problem found 
 **-n**    indicates not to correct any problems


For forcing fsck on restart:
```

sudo touch /forcefsck
```

---

### Post by WitchCraft on 2009-03-22
Can I have gnome running while running fsck?
Of course that means I have to unmount the root filesystem...

???

---

### Post by arpanaut on 2009-03-22
If you are using Jaunty, then your question would be better answered in the developement section of this forum...

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=352](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=352)

---

### Post by WitchCraft on 2009-03-22
> **arpanaut said:**
> If you are using Jaunty, then your question would be better answered in the developement section of this forum...

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=352](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=352)

I have done that.

But the problem wasn't even file system corruption.
The problem was that under Debian Squeeze, image files have to fit their file extension... they had the extension .png, but as I checked that with the file utility, they were in fact windows icons...

So I just had to save them once again in the appropriate format, and my icons were back.

---

