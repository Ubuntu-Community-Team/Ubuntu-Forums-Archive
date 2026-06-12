---
title: "how to undelete files help!"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-03
i've just emptied the trash and have no idea how to bring back some files
any ideas?

---

### Post by megamania on 2009-09-03
> **heyyy said:**
> i've just emptied the trash and have no idea how to bring back some files
any ideas?
Look for Testdisk / Photorec. I can't be more specific because I'm not at home, but they will do the trick.

Try booting from a Live CD, because the more you use your system, the more chances are that the deleted files are overwritten.

---

### Post by theluddite on 2009-09-03
Or install foremost.  Your main problems will be:  a.  As the previous poster mentioned, overwriting the files makes them near impossible to recover so you likely want to shutdown immediately and only boot from a usb or live cd; b.  finding media large enough to accomodate the image you'll need to make.  Commonly, you'd image the whole disk using dd, then use foremost to recover the deleted files.  This means that the media you store your disk image on will need to have enough space to accomodate the entire disk you're imaging.

---

