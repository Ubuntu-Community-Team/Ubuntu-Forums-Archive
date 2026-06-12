---
title: "Connecting an External Hardrive"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by minigmgoit on 2009-01-31
Hello all

Another quick question

I have a 500gb external hardrive (Moontec GigaSave 3.5) that I have all my media files on from Windows.

I just attempted to plug it in and it said that Ubuntu is unable to mount volume. 

Before installing Ubuntu I reset windows back to factory. Would I still need to go in to windows and "safely remove hardware"?
Or is there something else I need to do.
Obviously I am being a little carefull here as theres a rather large amount of Media on it.

Any Ideas?

---

### Post by HotShotDJ on 2009-02-01
> **minigmgoit said:**
> I have a 500gb external hardrive (Moontec GigaSave 3.5) that I have all my media files on from Windows.

I just attempted to plug it in and it said that Ubuntu is unable to mount volume.Since this is probably an NTFS formated drive, it is very likely that it was not "Safely Removed" in Windows.  There does exist a "work around" to get it to mount in Linux, but that involves forcing the thing to mount (ignoring the error).  Better to boot into a Windows machine, connect the USB drive, then Safely remove.  After that, it should mount properly when you plug it into your Ubuntu box.

---

### Post by Pappy1911 on 2009-02-02
I agree, use the 'safely remove device' in Windoze.

Worked for me using a LaCie 1Tb external drive....

---

