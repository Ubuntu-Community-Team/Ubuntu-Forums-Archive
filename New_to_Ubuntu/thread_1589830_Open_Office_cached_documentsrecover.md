---
title: "Open Office cached documents/recover?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Jadesocket on 2010-10-07
I am posting this in desperation right now. I recently just finished a paper which i spent hours upon hours on and just like that i accidently replaced the main file with an empty one as i thought that was the one i wrote it in. I know there are ways people recover documents and i was wondering if there is a way i can recover mine. I dont care how early the document is i just want a part of it back...
Any help is REALLY appreciated. I am about to breakdown right now...

---

### Post by jtarin on 2010-10-07
If the document is still open try "Undo" as many times as you can......This is no guarantee...only a long shot...Open Nautilus and go to your home folder....press keys Ctrl + h to view hidden files. Find your Open Office directory and look inside...maybe in your profile folder [COLOR="Red"](/home/<user name>/.openoffice.org/3/user)[/COLOR]. If the document is valuable I would not write to the disk at all. Shutdown immediately and call someone that is good at computer forensics and tell them what has happened. There are programs to do this, but I wouldn't advise doing any more disk writes to your disk unless you have the necessary software and have the disk mounted as a secondary in your computer so you can use another OS for recovery.
**Backup important files often and preferably off-disk.**

---

### Post by jtarin on 2010-10-07
If you've activated the feature in Tools>Options>Load/Save>General, Always create a backup copy. Each time you save manually a file, the previous version is saved here (overwriting the former one).

[http://user.services.openoffice.org/en/forum/index.php](http://user.services.openoffice.org/en/forum/index.php)

---

### Post by mikechant on 2010-10-08
You might want to look into this:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I believe testdisk is in the Ubuntu repositories.

One of its functions is 'undelete' which may or may not help - it all depends exactly what low-level file operations openoffice does and in what sequence as to what data might be left untouched. If you're lucky, when saving a file openoffice might do some sort of create/rename/delete sequence which would leave a 'deleted' copy of the old file still lying around on the disc.

I haven't used testdisk myself but it is widely recommended.

You should boot from a live CD (e.g. using the 'try ubuntu without installing' option on the install disk), then install/run testdisk from the liveCD, this will make sure there are no further writes to the hard drive while you are attempting recovery.

---

