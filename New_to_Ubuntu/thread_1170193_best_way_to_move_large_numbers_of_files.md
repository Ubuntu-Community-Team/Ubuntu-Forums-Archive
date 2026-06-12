---
title: "best way to move large numbers of files?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-05-26
whats the best way to move large volumes of files from one hard disk to another?

i'm about to reformat my /home to ext4 and don't want to worry about corruption

---

### Post by nandemonai on 2009-05-26
> **Sonic Reducer said:**
> whats the best way to move large volumes of files from one hard disk to another?

i'm about to reformat my /home to ext4 and don't want to worry about corruption

If you're worried about corruption, I'd leave converting to ext4 for a while yet.

As for moving large files, 'cp' will manage fine.

---

### Post by antmenj on 2009-05-26
Install the second drive inside your machine and copy from one to the other.

---

### Post by Sonic Reducer on 2009-05-26
> **nandemonai said:**
> If you're worried about corruption, I'd leave converting to ext4 for a while yet.

really? whats wrong with ext4?

---

### Post by cariboo on 2009-05-26
There is always the chance of data corruption with ext4, if you value your data use somethng else. Personally I use xfs on my server, it's almost as fast as ext4.

Until the devs set it as the default file system when installing, I would wait a while.

---

### Post by WakkiTabakki on 2009-05-26
Maybe you want to take a look at this before you go ahead: [http://ubuntuforums.org/showthread.php?t=1170123](http://ubuntuforums.org/showthread.php?t=1170123)

ext4 is still in development, so stuff like this *may* happen. Then again, it *may* also work just fine...


/N

---

### Post by Greenwidth on 2009-05-26
> **antmenj said:**
> Install the second drive inside your machine and copy from one to the other.

Yes, use COPY rather than cut/paste or mv, and then delete the original if needs be afterwards.
If there is a problem during transfer, the originals are preserved.

---

### Post by Bios Element on 2009-05-26
> **Sonic Reducer said:**
> really? whats wrong with ext4?

Nothing anymore. There used to be a semi-major problem with the system when it'd wait 30 seconds or more before writing a file. Gnome uses tons of tiny config.txt files and thus it caused some problems if your system was shutdown before it was written.

Myself, I've been using it for 2 months now and have yet to have even a tiny problem with it. And file transfers are actually about 20% faster.

---

