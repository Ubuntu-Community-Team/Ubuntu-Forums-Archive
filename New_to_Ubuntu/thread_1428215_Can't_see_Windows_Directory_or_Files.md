---
title: "Can't see Windows Directory or Files"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by ubu newb on 2010-03-12
Windows 7 pro 64 bit and Ubuntu 9.10 installed using wubi.

How do I view and even gain access to my windows files?  I know it's possible as it even states it in the Ubuntu Pocket Guide and Reference.  It says: "13.8GB Media: This is a shortcut to the Windows file system".  

However on one computer I see 750GB Media but only shows the restore portion of disk not the actual windows directory.   On my laptop I don't even see what should be 300GB Media for my windows directory.

Windows files are viewable as I had no problem with files on an external HD.  

What am I missing?  Could I have made a mistake in the installation of Ubuntu?

Thanks

---

### Post by Elfy on 2010-03-13
When using wubi the windows drive should be available in /host in nautilus

```
nautilus /host
```

---

### Post by ubu newb on 2010-03-13
Thanks, files found.

---

