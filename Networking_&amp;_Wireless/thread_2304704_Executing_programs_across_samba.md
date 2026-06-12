---
title: "Executing programs across samba"
date: 2015-11-29
forum: Networking &amp; Wireless
---

### Post by BrianSwatton on 2015-11-29
Hi,

Is it possible to make programs executable across samba shares?  I was under the impression it was if ownership and group rwx privileges were set appropriately at the server. I've done this to the shared directory and the files contained, but no joy.  I made a special group for the purpose too.

I realise I could run the app remotely via vnc, but don't really want to do it that way for this.  I want to bring the executable over to the logged in machine and execute it there, with its working directory being the shared one on the server it came from.  Perhaps I am asking too much, and/or still not having a good enough overview of linux networking.  Any pointers to good info would be appreciated in any case.

I've been using a bunch of 12.04 machines here for a few years, I'm fairly used to installing OS and setting up new machines, and arranging for samba shares, vnc access, and basic terminal stuff.  I still consider myself a bit of a noob with it really, though I've been into coding on various computers for over 30 years.

Thanks for reading,

Brian

---

### Post by BrianSwatton on 2015-11-29
Found I could make this work using smbmount to mount to a local directory (had to install smbfs first) - this article helped : [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

Still comprehending otherwise, but on the right track.

---

