---
title: "the irritating thing bout ubuntu"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by NfF on 2007-06-14
- build-essentials
- kernel headers

These are the things which i think is missing.
HOW DO I INSTALL THEM VIA TERMINAL, and using the live cd.

and.if it fails.  what should i do? ive tried this guides-http://ubuntuforums.org/showthread.php?t=192588
and failed

tried all guides on installin ndiswrapper,but still no light.

however. i do get a same error msg everytime which is:

E:couldn't find or locate ndiswrapper

which is weird,becuz when i performed the command

locate ndiswrapper
it appears.and is sitting on my file system, and moreover on my desktop.

im appearing as root when typing these commands

I GOT NO INTERNET-SO IM USING XP NOW.

---

### Post by kevdog on 2007-06-14
Although it is irritating that there is no specific internet site that addresses your questions, the irritating thing about you is that this question has been answered (I know at least 4 times by me to 4 different users).  Please search forums because a lot of information that is given is repetitive:

Here is what you want if you need to build ndiswrapper.  I believe the header files for you should be installed already.

You can get the build-essentials package from the ubuntu cd (if you choose). Place CD in drive.
At command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

---

