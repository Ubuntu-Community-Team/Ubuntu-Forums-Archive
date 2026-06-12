---
title: "Have I lost all my data?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Psumi on 2009-11-29
My fat32 USB Flash Drive is giving me this error:

```
wrong fs type, bad option, bad superblock on /dev/sdb1
```

dmesg | tail says this:

```
[   38.052716] FAT: IO charset ANSI_X3.4-1968 not found
[   38.059915] FAT: IO charset ANSI_X3.4-1968 not found
```

Searching google says I have to upgrade udev from karmic-proposed, however... udev isn't in karmic-proposed, so I cannot upgrade it!

---

### Post by markjensen on 2009-11-29
If it seems to be unable to mount because of a superblock issue, you might be able to do a fsck/chkdisk(windows) on it.

There are also utilities that can grab your files off while ignoring reported filesystem information.  I am thinking the app **photorec** here.

If your usb stick seems to be unreadable and unfixable, try **sudo apt-get install photorec** then running it and pointing it to your usb stick and see what it can do.

It is a text based app, just so you are warned. ;)

---

### Post by Psumi on 2009-11-29
Seems Parole Media Player was able to mount it, so... I guess this is solved.

---

### Post by markjensen on 2009-11-29
Hey, one "solved" is as good as any other! :cool:

---

