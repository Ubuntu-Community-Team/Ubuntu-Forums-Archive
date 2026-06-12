---
title: "Sony DVD-R issue"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by Rolfmeister on 2010-04-01
I have a Sony DRUV200A/BR burner and Ubuntu 9.10 will not recognize any DVD-R video or data discs.  The same DVD video on a DVD+R reads fine.  Any help would be most appreciated.

---

### Post by Chesamo on 2010-04-01
Define "not recognize". Will the discs show up, but not be read? Is the disc not being mounted?

Try force-mounting the DVD. It may be different for you, but it *should* be ```
sudo mount /dev/cdrom0 /media/cdrom0
```

---

### Post by Rolfmeister on 2010-04-01
DVD-R will not mount.  I will try to force it to mount and let you know.

Also, I'm not sure if this matters, but when no discs are in the drive, under properties the drive is not recognized and is shown only as /dev/cdrom0.  With Ubuntu, is the drive not recognized as a Sony, etc.

---

### Post by Chesamo on 2010-04-01
Yes, because that information is largely irrelevant. /dev/cdrom0 isn't a directory in the normal sense; rather, it's a block device (ie. hardware).

---

