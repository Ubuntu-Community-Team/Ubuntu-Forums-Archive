---
title: "How do I recover files from a dd'd image file?"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by luckyal on 2011-07-27
Hi there,

I'm very new to the whole Linux thing.  So far I like what I see.  Ddrescue was able to do what no other program did for me.  However, now that I've recovered an image of a 150 Gb hard disk to another external 500 Gb, I'm out of hard drives to restore the recovered image to.  Which brings me to my next question: how do I recover the files from the image I previously recovered using ddrescue?  Is it possible to recover to another directory that I would create on the same drive the image resides?  

For example: the address where the image file resides currently is: dev/sdb/mnt/recovery (image titled: "yumian4life")

...what commands would I use to create another directory on the "mnt" volume and recover the "yumian4life" into it?

Also, how do you navigate backwards out of a directory into parent directory?  What's the proper syntax?

Any help would be greatly appreciated.  Documents recovered are being used for adoption proceedings and are critically time sensitive.

Thank you!

---

### Post by wolfen69 on 2011-07-27
[This]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html") article explains how to mount the image.

---

### Post by bodhi.zazen on 2011-07-27
You loop mount the image and run your recovery tools on the mounted image.

```
sudo mkdir /mnt/recovery
sudo mount /path/to/your.img /mnt/recovery
```

And yes you will need some space for the recovered files ;)

---

