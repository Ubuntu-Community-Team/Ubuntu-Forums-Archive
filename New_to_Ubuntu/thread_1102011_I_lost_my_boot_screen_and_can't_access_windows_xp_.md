---
title: "I lost my boot screen and can't access windows xp or ubuntu"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by racermike1967 on 2009-03-21
Hi everyone,

I don't know what happened but when I recently turned on my laptop, I didn't get my usual boot options asking which OS to boot into.  Rather, it goes directly into the windows OS but after it boots up, I am unable to do anything.  The entire taskbar is missing and so are all my desktop icons.  The mouse doesn't even move.  Is there anyway to get back my ubuntu without having to re-install it?

---

### Post by blueridgedog on 2009-03-21
I sounds as if something has gone wrong with your drive.

Can you boot on a live CD and mount the partitions to verify that they are still there and still intact?  If you can boot a live cd, post the output of 

```
sudo fdisk -l
```

You might consider re-installing grub via the instructions here:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

