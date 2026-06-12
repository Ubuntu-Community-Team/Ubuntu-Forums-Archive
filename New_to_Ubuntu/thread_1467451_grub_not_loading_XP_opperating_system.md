---
title: "grub not loading XP opperating system"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by nash black on 2010-04-30
Hi

I just upgraded to ubuntu 10.04 on a dual boot machine. I have windows XP Pro on one hard drive and a second hard drive with an ubuntu partition and a shared partition. This was working fine before the upgrade, both operating systems could boot.

Since the upgrade, however, XP will not load. Grub recognizes and displays XP as an option, but when I select it, all I get is a blank command prompt. It doesn't do anything and I can't type anything...

I tried reinstalling "grub-pc" in the package manager and selecting different or both drives for installation, but none of that seemed to work. I still get the blank command prompt when I select XP


Any idea what is going on?

---

### Post by nash black on 2010-04-30
Btw

I can mount the windows partition in ubuntu, so it is still there...

---

### Post by lockalidiot on 2010-04-30
I saw a similar thread but with windows 7.. Wait a sec and I'll search it for you.

EDIT: [http://ubuntuforums.org/showthread.php?t=1466038&highlight=boot](http://ubuntuforums.org/showthread.php?t=1466038&highlight=boot)

That should be it. read it through and see if you find something that works.

---

### Post by bcbc on 2010-04-30
It is possible you installed grub2 over your windows bootsector. See this link for a fix [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by nash black on 2010-04-30
[http://ubuntuforums.org/showthread.php?t=1466824](http://ubuntuforums.org/showthread.php?t=1466824)

That soln worked!

I think its the same one from the sourceforge link you posted.

Thanks guys!

---

