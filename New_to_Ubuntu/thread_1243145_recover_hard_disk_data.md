---
title: "recover hard disk data"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by gkraju on 2009-08-18
hi i had ubuntu 9.04 
yesterday instead of formatting a pen drive in Gparted  i selected hard disc and selected create partition table 
so my entire hard disk partition is lost 
so i cant boot  
i want to recover my hard disk 
please help

---

### Post by Lars Emil Gutt on 2009-08-18
You could make a a usb bootable, and recover the data.
But from what it sounds like, you deleted everything that was on the harddisk.

---

### Post by jerrrys on 2009-08-18
i have not used this, but sounds like what your looking for

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by gkraju on 2009-08-18
> **Lars Emil Gutt said:**
> You could make a a usb bootable, and recover the data.
But from what it sounds like, you deleted everything that was on the harddisk.
yes i clicked create partition table so my hard disk looks like new one with no partitions 
any ideas what to do?
thanks

---

### Post by gkraju on 2009-08-18
> **jerrrys said:**
> i have not used this, but sounds like what your looking for

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


is it possible with this software to recover the entire partition in the hard disk 
i hasnt even formated my system just partition table is lost

---

### Post by lkraemer on 2009-08-18
First, HOW important is your Data?  Is it worth ~$50.00?  If so,
I'd suggest getting a new Hard Drive, use Clonezilla to copy
your existing (messed up) drive before it gets any thing else
done to it.  Install the copy and attempt the repair.  Keep the
Original (messed up) drive safe for a second attempt, if needed.

That way you can try different things if the first attempt doesn't 
work correctly.  Just copy the Original to the new drive again and
try the second time.  Otherwise your data will get more corrupt.

So, Try testdisk first, then Photorec as last resort.

You could always take a Memory stick or camera card, erase all the files,
then plug that card into a reader attached to Linux, and use testdisk
from a LiveCD to try and recover the files.  That will give you an idea
of how Testdisk & Photorec work before you attempt repairing your
messed up Hard Drive.  It will take a bit of playing to see what you
need to do to recover your files and you don't want to do any more damage
than possible before the actual attempt is finished.

lkraemer

---

