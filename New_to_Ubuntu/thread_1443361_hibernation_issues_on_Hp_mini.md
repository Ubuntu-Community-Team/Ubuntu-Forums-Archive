---
title: "hibernation issues on Hp mini"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by shosean on 2010-03-31
Hi!  My first post!

I'm very new to ubuntu and linux and just downloaded Ubuntu 9.10 Netbook remix on my Hp mini 110.  It had some hibernation issues, it shut down after closing the laptop instead of hibernate, so after some research I found out to do this:

type in the terminal:  gedit /usr/sbin/pm-suspend

and then to type in on the first line after comments:  umount /media/mySD

And it fixed it, kinda.  Now when I close my computer, it appears to shut down.  But when I open it up again, the screen is off, and in addition any window that is open and not maximized has resizing issues.  The wifi also starts having issues.

To be more specific, when I try to maximize a window, it thinks it is already maximized.  Often windows are partially off screen and therefore impossible to utilize until I restart the computer.

This has really been bugging me and I don't know what to do.  Any help would greatly be appreciated!

---

### Post by cariboo on 2010-03-31
I have a Compaq Mini 110, for me suspend works intermittently, but hibernate works the way it should. Right-click on the battery icon and select preferences you can set what happens when you close the lid as well as other settings. I'm currently running Lucid UNR, but things worked exactly the same as running Karmic(9.10).

---

### Post by Echtesatir on 2010-10-31
Hi, Suspend and Hibernate wont work on lid close.. but do from the top right menu..!

UNR 10.10 
HP mini 5101

- Does ubuntu see the lid close event?
Seems so as "blank screen" option in pm preferences does work.. 

Ill search further but after grub changing options and reading threads and trying advise no solution yet..

Any help is welcome..

---

