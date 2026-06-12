---
title: "big problem with ubuntu"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by unknown23 on 2010-05-17
first,

i shutdown my pc; which was running xubuntu 9.10, and when i rebooted i could not get past the login screen

the login screen appears, i type in the correct password, screen flickers, back to the login screen.

so, actually when i upgraded to 9.10, my dvd drive failed, so doing a new reinstall via live cd was not possible

i took my laptop apart, and installed a new working dvd drive so thqt i could install 10.04

so, i installed 10.04, only to find that all of my files are not there, but still in the system and encrypted...... so, now i tried to install some of my missing programs with the idea that i just get to the issue of my files later, but then i had memory issues because of how the drives were partitioned, i actually do not know whats going on with that

now when i boot, the screen is distorted, can not see anything but distorted images
anyway, now as i am typing this, can not even get the system to boot from the cd

do i chuck my laptop out the window or what?

---

### Post by Dougie187 on 2010-05-17
From what I understand, your disk space is limited because of your encrypted file system that you are trying to recover.

I don't know how to decrypt the home folder, but here is a link that might be helpful.

[http://ubuntuforums.org/showthread.php?t=1463392](http://ubuntuforums.org/showthread.php?t=1463392)

Next time you upgrade make sure you back up your important documents, especially if you have an encrypted home folder. It's easily the most important step in upgrading, or installing.

When you did the fresh install of 10.04 did you choose to mount the old file system as /home? or did you just leave it alone? Did you have a separate home partition previously or do you have no idea what I'm talking about? Hopefully this will lead someone to help you.

---

### Post by sidzen on 2010-05-17
SystemRescueCD 1.3.4 is my old stand-by, as well as Universal Boot CD, for cases like yours.  

If nothing else works, at the initial prompt (before X is invoked) of sysrescd, type "dban" then at the blue background screen prompt, "quick."  After the wipe, invoke "startx" after rebooting and pressing F2, then "gparted."  You know your way from there.  

Life is a learning experience.  Yes, it is!  Best wishes, friend -- we've been there!

---

