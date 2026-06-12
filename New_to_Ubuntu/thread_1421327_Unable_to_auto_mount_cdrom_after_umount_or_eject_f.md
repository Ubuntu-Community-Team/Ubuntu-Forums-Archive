---
title: "Unable to auto mount cdrom after umount or eject from the 1st cd"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by sokam on 2010-03-04
I am using karmic.

Here is the problem.  After a reboot, My computer is able to automatically mount my 1st disk I put into my dvd drive.  I can fully interact with the contents of the disk.  However, when I either umount or eject the 1st disk and put a second disk (or even put the same disk back) into the dvd drive, the computer won't detect the disk anymore.

I know the drive work and connected correctly b/c the 1st disk after a reboot will do just fine.  The problem is when I need to work with more than one disk.  

Anyone have this problem or any quick solution.

I found this bug report from last year but hoping that there is a solution came out during last 3 months.
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1915907.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1915907.html")

---

### Post by Kulgan on 2010-03-05
I believe I have experienced this before. Now, however, it will mount the CD/DVD but not open it in Nautilus/File browser. 

You can mount the disk using
```
mount /dev/cdrom
``` 
(as a normal user). GNOME will treat the disk as if it had been mounted all along. If, like me, you don't have a hardware tray opener button, you can eject the disk using, well...
```
eject
```

This has always worked for me.

---

