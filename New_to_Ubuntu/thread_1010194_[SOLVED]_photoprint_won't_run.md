---
title: "[SOLVED] photoprint won't run"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by glendavee on 2008-12-13
Strange problem. I'm running 8.10 and am trying to use photoprint. It shows under  Applications > Graphics, but when I click it doesn't open. I've tried uninstalling and reinstalling several times using both Synaptic and apt-get install, but nothing seems to make any difference

---

### Post by Michael.Godawski on 2008-12-13
Can you run in via the terminal? so we see some nice error messages.

---

### Post by glendavee on 2008-12-13
Here's what I get in the terminal - do I need to find libgutenprint.so.2 and if so why didn't Symantic get it for me?


david@david-desktop:~$ photoprint
photoprint: error while loading shared libraries: libgutenprint.so.2: cannot open shared object file: No such file or directory
david@david-desktop:~$

---

### Post by glendavee on 2008-12-13
After some digging, I've discovered that this is a known bug. The fix is to install a newer version. Follow this link, and install the deb package
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1150417.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1150417.html)

and install the deb package
[http://launchpadlibrarian.net/19642102/photoprint_0.3.9-0ubuntu1_i386.deb](http://launchpadlibrarian.net/19642102/photoprint_0.3.9-0ubuntu1_i386.deb)

Worked for me.

---

### Post by Michael.Godawski on 2008-12-13
Teach a man to fish...:p

---

### Post by fenario on 2009-01-14
Thanks for your efforts glendavee, it solved my problem.

---

### Post by jvnn on 2009-01-31
Wow!  count me among those who saved some effort due to someone else's hard work.

Thanks!:D

---

### Post by iheartubuntu on 2009-02-05
Thank You So Much!!!!

---

### Post by vbonafe on 2012-07-18
Photoprint can't find this file again in 12.04, same message:

photoprint: error while loading shared libraries: libgutenprint.so.2: cannot open shared object file: No such file or directory

Is the bug back? Is there any workarround?

Thanks a lot!

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

