---
title: "DVD not mounting"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-09-05
I burnt a remastersys iso on a DVD-RW. It didn't work (I found out why - so that's not the issue) but when I inserted it again to erase the DVD, its not showing up on the screen. I can't mount it through the terminal either. What am I doing wrong?

Thanks

---

### Post by HermanAB on 2010-09-05
Well, if there is no recognizable file system on it, then you cannot mount it.  To erase/burn it, use K3B or any other CD/DVD burner program.

---

### Post by Fifthmarch on 2010-09-05
I have Brasero installed, but it does not detect a dvd in the drive at all. :(

---

### Post by perspectoff on 2010-09-05
> **Fifthmarch said:**
> I have Brasero installed, but it does not detect a dvd in the drive at all. :(

That happens to me whenever a DVD of any type becomes a coffeecup "coaster" (i.e. has had bad data written to it). 

Does the problem persist when you try a new DVD?

Also, some of my D VD drives have a balky sensor head that gets stuck. When I manually move the laser head to a different position, it is able to read the DVD once again. 

This happens on two of my laptops DVD drives and is purely a hardware problem.

---

### Post by Fifthmarch on 2010-09-06
Yes, I'm able to mount other DVDS and CDs. Can you tell me how to solve this problem?

---

### Post by Fifthmarch on 2010-09-15
I managed to delete it using the terminal using 

cdrecord dev=/dev/cdrom blank=fast

After that, I could mount the DVD. 

Thanks!

---

