---
title: "Can I use an alias for a mounted filesystem?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Donny Bahama on 2010-03-10
OK, so I'm used to C:\ etc. in Windows. Now when I mount (for example) a USB drive, I have to access it via /mnt/mountpoint (or /media/mountpoint). I'd much rather be able to access my music using '/m/subdirs' or my video using '/v/subdirs', etc.

Can I do this somehow?

---

### Post by J V on 2010-03-10
You shoulden't put ANY data under /...

All the stuff you have on your computer should be kept in your home folder, all the rest in /

If you want to save videos to your Videos folder the shorthand way to write it is ~/Videos (Not very long at all)

You can't mount specific folders on your USB to specific folders in the linux filesystem, thats not how it works, however, you can create "symlinks" (read: shotcuts) to those folders and they will behave like actual folders (~/v/file will return /media/mountpoint/v/file)

---

### Post by sisco311 on 2010-03-10
> **J V said:**
> You shoulden't put ANY data under /...

All the stuff you have on your computer should be kept in your home folder, all the rest in /

If you want to save videos to your Videos folder the shorthand way to write it is ~/Videos (Not very long at all)

You can't mount specific folders on your USB to specific folders in the linux filesystem, thats not how it works, however, you can create "symlinks" (read: shotcuts) to those folders and they will behave like actual folders (~/v/file will return /media/mountpoint/v/file)

Actually, since Linux 2.4.0 it is possible to remount  part  of  the  file hierarchy somewhere else. The call is:
```
mount --bind olddir newdir
```
;)


But +1 for the symbolic link(s).

---

### Post by J V on 2010-03-10
Ah yes but you still have to mount the device first, so you might as well have a symlink that works straight away :)

---

### Post by Donny Bahama on 2010-03-10
> **J V said:**
> You shoulden't put ANY data under /...

All the stuff you have on your computer should be kept in your home folder, all the rest in /

If you want to save videos to your Videos folder the shorthand way to write it is ~/Videos (Not very long at all)

You can't mount specific folders on your USB to specific folders in the linux filesystem, thats not how it works, however, you can create "symlinks" (read: shotcuts) to those folders and they will behave like actual folders (~/v/file will return /media/mountpoint/v/file)Very informative. Thanks very much! :)

---

