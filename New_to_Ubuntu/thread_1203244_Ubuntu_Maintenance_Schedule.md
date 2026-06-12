---
title: "Ubuntu Maintenance Schedule"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by riph72 on 2009-07-03
Hello all,
 
My typical maintenance schedule with WinXP is a monthly disk cleanup, disk check, defrag, virus/spyware check (and then backup).
 
What schedule is advisable with Ubuntu, to keep it in good shape?
 
Regards,
Richard.

---

### Post by Zack McCool on 2009-07-03
> **riph72 said:**
> 
My typical maintenance schedule with WinXP is a monthly disk cleanup, disk check, defrag, virus/spyware check (and then backup).
 
What schedule is advisable with Ubuntu, to keep it in good shape?


Backup your files on a very regular basis.

No other maintenance is necessary.  Use your time in Linux to get things done.

---

### Post by riph72 on 2009-07-03
> **Zack McCool said:**
> Backup your files on a very regular basis.
 
No other maintenance is necessary. Use your time in Linux to get things done.
 I was hoping that would be the answer!
 
Thanks,
Richard.

---

### Post by Zack McCool on 2009-07-03
No problem.

Disk checks are done automatically on boot, every so many boots.  The default is around 30.  If you lose power, or for some reason need to shut down the hard way, the system will check the journal on next boot, and put everything in place.

Defrags are not necessary with the [default] ext3 filesystem.

Viruses?  Blah...   ;)

It is recommended to do updates when they come available, as they will fix any newly found security holes.

Also, a rootkit checker isn't a bad idea, though they do have a habit of giving false positives...

Most importantly, backup backup backup.  And if the files are important, do more than one type.  You can't have too many backups.  I recommend you backup often.  

Am I getting the point across?  :lolflag:

---

### Post by Astarroth on 2009-07-03
Great advice McCool! With Linux there is really nothing to worry about as long as you are backing up your data.

---

