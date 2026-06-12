---
title: "Wubi will not run on Windows 98"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by stickynote427 on 2009-11-08
I'm trying to install Ubuntu 9.10 through Wubi on Windows 98, but whenever I try to run Wubi.exe, nothing happens. What might be happening and how can I fix this?

Thanks!
stickynote427

---

### Post by RealG187 on 2009-11-08
Is Windodws 98 supported? It is old (I am not denying the fact some still use it, I played with it a while ago, but stopped, maybe I will again).

If not just do a normal install...

---

### Post by alzie on 2009-11-08
I did a little searching.  You are probably using fat32 file system with win98,  try setting your virtual drive to only 4GB.  I seem to remember having to do this on an earlier wubi install (I was still using fat32 with XP)

I hope this helps

---

### Post by sandyd on 2009-11-08
> **RealG187 said:**
> Is Windodws 98 supported? It is old (I am not denying the fact some still use it, I played with it a while ago, but stopped, maybe I will again).

If not just do a normal install...
it is supported in win98

[http://wubi-installer.org/](http://wubi-installer.org/)

scroll down a bit, its on the right.

---

### Post by stickynote427 on 2009-11-08
> **alzie said:**
> I did a little searching.  You are probably using fat32 file system with win98,  try setting your virtual drive to only 4GB.  I seem to remember having to do this on an earlier wubi install (I was still using fat32 with XP)

I hope this helps
I just checked; the file system is FAT32.

I have a virtual drive? How do I set it to 4 GB?

---

### Post by Sir Jasper on 2009-11-08
Hi,

As an aside, not only can you have Win 98 and ´buntu but  you can configure Wine to run as XP (for example) by default (or even make different Windows settings to run different programs).

So that you could, for example, run Evernote and/or a-squared Free.

_Most_ programs do not run well, or indeed at all, using Wine but some work superbly. In my limited experience, portable Windows programs (e.g. from PortableApps) tend to run well with Wine.

My regards

---

### Post by stickynote427 on 2009-11-08
Ugh, I'm just about to install it on my primary, Windows Vista computer instead. :-/

Can anyone tell me how I might be able to fix this?

**EDIT:** Yes, that's what I'm doing. If anyone has any ideas as to how to fix the Wubi on Windows98 problem I'm having, please still post replies here, but I *am* going to install Ubuntu on my primary computer using Wubi.

---

### Post by louieb on 2009-11-08
How much memory in the win98 PC. IIRC the minimum requirement for Ubuntu is 384MB.

---

### Post by stickynote427 on 2009-11-09
I'm not certain, but I'm pretty sure it was less than 200 MB.

---

### Post by NotWindowsXPagain50 on 2009-11-09
Best workaround is to install the normal way! (Partitioning, Partition Size. You know it)

---

### Post by ibizatunes on 2009-11-09
If you have less than 200mb RAM then you need to download puppy linux, it doesnt have wubi, but will make the old pc fly like a new box
Backup your data and format the machine, 

[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by alzie on 2009-11-09
I misread your original post.  Setting the virtual drive is one of the first steps after wubi starts to run.

Are you trying to run wubi.exe from the desktop?

Is it the most recent release of wubi?

According to wubiguide  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)  wubi *should* run on win98 but has not been thoroughly tested,  it may not work for you.

There is a list of older wubi installers here: [http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)
If the current version won't work maybe an earlier one?

Sorry I can't be of more help right now.

---

