---
title: "rsync errors"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by echo314 on 2009-03-29
I'm trying to backup my KeePassX database. One way is I've set up a schedule task to have rsync backup a folder on my HD to a usb drive. However, I get this error, 

rsync: chgrp "/media/DATA/rsynctest" failed: Operation not permitted (1)
rsync: chgrp "/media/DATA/rsynctest/Bookmarks 2009-03-23.json" failed: Operation not permitted (1)

I'm open to suggestions on fixing this, and to any other methods of backing up this db. I'm wary of using those online storage services, such as OakTree, even though they insist the entire process is encrypted and they could not access the data if they wanted to. Using a scheduled task to rsync to a usb drive is the only thing I can think of..what are your solutions to backing up small amounts of data?

---

### Post by llamabr on 2009-03-29
Operation not permitted sounds like a permission error.  Do you have write access to that?  In the end, you could allow root to make these backups.

---

### Post by asmoore82 on 2009-03-29
The USB drive is probably not Linux formatted so rsync cannot properly preserve permissions.

the ``-a'' "archive" switch to rsync turns on preserving times/ownership/permissions

I highly recommend "grsync" to get a quick look at available rsync options.
```
sudo apt-get install grsync
```
you can run a "simulation" to see exactly what switches is passes to rsync.

---

### Post by echo314 on 2009-03-29
I've used grsync, and am now executing ```
rsync -r -t -v --progress --modify-window=1 /home/echo/rsynctest/ /media/DATA/
```

Seems to work fine now, so I have at least a rudimentary backup solution going. Any other solutions that have worked for you users?

---

### Post by HermanAB on 2009-03-30
As a previous poster noted, if you want a decent backup, then you need to format the storage device with a proper file system.

You can format a USB device with something like:
$ mkfs.ext3 /dev/sdx
where x is the ID of the device

Use ls /dev/sd* to figure out what the device name is - don't get it wrong!

---

