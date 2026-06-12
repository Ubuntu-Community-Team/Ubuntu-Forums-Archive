---
title: "which os for mac g4"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by awannabeee on 2010-04-17
need help have g4 with no os. which linux has enough drivers to load up and run my 
 
machine.
 
please advise!:confused:

---

### Post by readycarpenter on 2010-04-17
your going to have to use 6.06

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/)

For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines.
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/ubuntu-6.06.2-server-powerpc.iso](http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs/6.06/ubuntu-6.06.2-server-powerpc.iso)

---

### Post by 3rdalbum on 2010-04-17
There is a community build of Ubuntu 9.10 and soon to be one of 10.04. You should use one of those, just make sure you download the PowerPC edition, not the regular x86 edition.

---

### Post by awannabeee on 2010-04-18
ok thanks;
 
only problem is i tryed the 9 you mentioned and it froze the machine up.
 
as far as loading six, 8 didnt have any drivers with it so i seriously doubt 6 will work.
 
8 wanted a cdrom driver.
 
any thoughts on why they wont work?

---

### Post by 3rdalbum on 2010-04-18
> **awannabeee said:**
> ok thanks;
 
only problem is i tryed the 9 you mentioned and it froze the machine up.
 
as far as loading six, 8 didnt have any drivers with it so i seriously doubt 6 will work.
 
8 wanted a cdrom driver.
 
any thoughts on why they wont work?

It's not "Ubuntu 9" and "Ubuntu 8". It's 9.10, 9.04, 8.10 and 8.04; there's six months between those releases.

If 9.10 didn't work, then you could try 9.04.

On Ubuntu you don't need to worry about drivers for most things. Ubuntus 8.04 and 8.10 are no exception. What didn't work? Your CD drive should have worked.

---

### Post by doctorbighands on 2010-04-18
I struggled mightily trying to find a distro that would work on an iBook G4. Man, it was really frustrating for awhile. The solution I finally found was to install 9.04 using the text-based installer. Don't even try the Live CD installer - it'll just make you mad.

I'll see if I can find a link for you to the version I used.

EDIT:

Well, I can't find the exact solution I used for the G4, but I did find something that worked for me on an old, clunky iBook G3 clamshell. I installed the SERVER version of Ubuntu, and then, once that was finished, installed the ubuntu-desktop package (sudo apt-get install ubuntu-desktop) on top of it. For some reason, that worked beautifully for me.

Hope it helps!

---

