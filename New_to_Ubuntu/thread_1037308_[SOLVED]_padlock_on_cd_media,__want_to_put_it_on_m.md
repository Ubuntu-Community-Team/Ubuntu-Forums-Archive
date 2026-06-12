---
title: "[SOLVED] padlock on cd media,  want to put it on memory stick"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by adamogardner on 2009-01-11
but I can't seem to drag and click.  the disk is meant for windows.  Will this work?

---

### Post by drs305 on 2009-01-11
Open a file browser with sudo (or its equivalent) and you will be able to move the files. It's a probably a permission issue.  The padlock means you don't own/have full access to the device.
```

gksudo nautilus

```

---

### Post by adamogardner on 2009-01-11
ok did that, and now the pad lock is gone.  But If I click to drag it just opens.  It won't drag.  I'm sure it's something obvious so please excuse me if I do not know. 

edit=  Ok i opened the cd selected all and then dragged that to the memory stick.  It's copying.  Thanks

---

### Post by earthpigg on 2009-01-11
please be very very very careful when running a file manager as root.

---

### Post by adamogardner on 2009-01-12
> **earthpigg said:**
> please be very very very careful when running a file manager as root.

I should have listened!  I knocked my glass of milk all over the floor when I was rooting through my file system.   I got the files transfered to my memory stick though.

---

### Post by drs305 on 2009-01-12
> **adamogardner said:**
> I should have listened!  I knocked my glass of milk all over the floor when I was rooting through my file system.   I got the files transfered to my memory stick though.

Now THAT'S funny. A little humor goes a long way, especially since a lot of users seeking answers here are pretty stressed out. :P

---

