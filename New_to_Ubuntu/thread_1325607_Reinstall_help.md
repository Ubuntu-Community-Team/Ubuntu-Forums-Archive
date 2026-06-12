---
title: "Reinstall help"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by fixerman on 2009-11-13
I recently upgraded from 9.04 to 9.10. My nephew has messed up my files and my computer will not boot up now. If I download the files to create a DVD and carry out a reinstall will my files and documents be preserved or will I lose everything.:)

---

### Post by wojox on 2009-11-13
No it'll overwrite, you could boot a live cd and mount that partition and recover those files.

---

### Post by kansasnoob on 2009-11-13
> **fixerman said:**
> I recently upgraded from 9.04 to 9.10. My nephew has messed up my files and my computer will not boot up now. If I download the files to create a DVD and carry out a reinstall will my files and documents be preserved or will I lose everything.:)

Do you have any Ubuntu Live CD that you can run?

If so boot the Live CD and post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by fixerman on 2009-11-13
Thanks for your advice!

Is the normal CD that is used for to install Ubuntu a "Live CD"? If so, I am in the process of creating one with a view to installing 9.10. Do I take it from what you say that I can boot up a usable version of Ubuntu from the CD without any files being installed?

---

### Post by kansasnoob on 2009-11-13
> **fixerman said:**
> Thanks for your advice!

Is the normal CD that is used for to install Ubuntu a "Live CD"? If so, I am in the process of creating one with a view to installing 9.10. Do I take it from what you say that I can boot up a usable version of Ubuntu from the CD without any files being installed?

You can use any Ubuntu Live CD, it doesn't need to be the newest!

But, yes, boot the Live CD and choose to Try without changes. Then you'll be running in what we call the Live Desktop.

In fact, I'm not a fan of 9.10 (aka: Karmic), I'd use either 9.04 or 8.04 for a fresh install.

---

