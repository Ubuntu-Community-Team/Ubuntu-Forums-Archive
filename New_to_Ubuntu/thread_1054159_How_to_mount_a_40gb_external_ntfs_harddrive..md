---
title: "How to mount a 40gb external ntfs harddrive."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-29
I have a 40gb external harddrive from back in my windows days which I'm trying to pull my music off of. When I try to mount the drive It keeps giving me an error. Is there a way that I can get into the drive to get the music off of it? Here's a screen shot of the error.


file:///home/alex/Desktop/Screenshot.png

---

### Post by Jynxx on 2009-01-29
Crap, screenshot didn't past the way I thought it would. Is there a way to past this screenshot here so that everyone can see the error I'm getting?

---

### Post by jkid on 2009-01-29
upload it to ur page and then....post......it.....

---

### Post by Jynxx on 2009-01-29
[attach]101419[/attach] No clue what I'm doing.  lol

---

### Post by Mark Phelps on 2009-01-29
When you remove an external device from MS Windows, you need to do a "safe" removal, that is, click the icon in the notification area for that drive, and wait until Windows tells you it's OK to remove it.  If you don't do that, MS Windows will turn on the "dirty bit" and Linux utilities will then routinely refuse to automatically mount the drive.

If you have a Windows box, you need to plug in this drive, run a chkdksk on this drive, and then do a safe removal.  That will reset the "dirty bit".

You can also manually mount the drive, using the "mount" command, with the "-force" option, but you run the risk of corrupting the filesystem when you do that.

---

