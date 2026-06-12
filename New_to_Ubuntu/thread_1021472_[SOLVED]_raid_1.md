---
title: "[SOLVED] raid 1"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by anewguy on 2008-12-25
Helping some friends set up a server for their small business which is becoming quite a learning experience!  I would like to use raid 1 across the 2 sata drives so I have a hot backup for them.  The server is built from an old PC which doesn't have built-in raid support, so I've been looking at sata raid controllers (I wanted the sata so the drives could be hot-swapped).  Can anyone point me to a link that has information on what hardware add-on raid controllers work with Ubuntu?

Thanks in advance!

Dave :)

---

### Post by nhasian on 2008-12-25
i found this page that had a list of sata raid controllers and their driver support in linux.  scroll down to *Driver Support for Each Known SATA Chipset*


[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by cariboo on 2008-12-25
You can also use software raid to accomplish what you want. Have a look [here]("http://ubuntuforums.org/showthread.php?t=408461").

Jim

---

### Post by anewguy on 2008-12-25
> **nhasian said:**
> i found this page that had a list of sata raid controllers and their driver support in linux.  scroll down to *Driver Support for Each Known SATA Chipset*


[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

Thanks - the list I was looking for!  Now I need to decide though - perhaps software RAID as mentioned on the next post is the way to go, especially for RAID 1 where I just want to mirror the disk.

Dave :)

---

### Post by anewguy on 2008-12-25
> **cariboo907 said:**
> You can also use software raid to accomplish what you want. Have a look [here]("http://ubuntuforums.org/showthread.php?t=408461").

Jim

Very interesting - I wasn't aware of this.  This sounds like the type of raid we used on some DEC equipment in the 1990's.  Sounds like it could be a good choice for this!

Dave :)

---

