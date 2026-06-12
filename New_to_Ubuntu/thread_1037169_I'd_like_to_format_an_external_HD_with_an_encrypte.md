---
title: "I'd like to format an external HD with an encrypted volume..."
date: 2009-01-11
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-11
I have an external USB hard drive and I'd like to wipe it completely clean and start with a fresh encrypted partition that will be accessed by Ubuntu more than one PC that is running Ubuntu.  How do I do this?

---

### Post by oldrocker99 on 2009-01-11
> **diablo75 said:**
> I have an external USB hard drive and I'd like to wipe it completely clean and start with a fresh encrypted partition that will be accessed by Ubuntu more than one PC that is running Ubuntu.  How do I do this?

My own experience with external drives (ALL of which are formatted FAT32) is to LEAVE THE FORMATTING ALONE. I tried another format and met with nothing but grief. You can always encrypt a directory.

:guitar:

---

### Post by diablo75 on 2009-01-11
I'm currently using NTFS with my external...and would never use FAT32 (because of it's maximum filesize limitations).  I used to have an ext3 partition on there and had no issues with it as long as I attached it to a linux system.  NTFS is on there now because "everything" can read it.

Anyway I found a tutorial [here]("http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/") that looks like it's worth trying out.

---

### Post by nhasian on 2009-01-11
i recommend you look into Truecrypt:

[http://www.truecrypt.org/](http://www.truecrypt.org/)

I have a 1TB external usb hard disk that i've formatted as NTFS and encrypted the volume with truecrypt.  I can easily move the external drive from any windows or linux pc.  If you're only going to be using your drive on linux computers you should use EXT3 instead.

---

