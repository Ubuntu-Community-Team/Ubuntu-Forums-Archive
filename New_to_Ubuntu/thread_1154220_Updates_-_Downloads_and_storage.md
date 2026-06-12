---
title: "Updates - Downloads and storage?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-05-09
Hi all.

I've just done a nice fresh re-install of Ubuntu 8.10 & Ive downloaded
575? odd updates @ around 500+ MB.

I was wondering If I could store all the updates that I've downloaded
so far, burn them to CD/DVD and then re-install them from disc, rather
than having to re-download them again?

Where would I find them within the file system?

Thanks in advance for any help.

---

### Post by logos34 on 2009-05-09
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

hope that works for you

---

### Post by ugm6hr on 2009-05-09
> **GeordieJedi said:**
> Where would I find them within the file system?

/var/cache/apt/archives

Everything in there except the lock file.  After reinstalling, just copy back to same location and update normally.

AptOnCD does something similar automatically.

---

### Post by logos34 on 2009-05-09
GeorgieJedi:

ugm6hr's method may be better (+simpler), if you're only wanting to get the updates for a fresh install (in which case the package mgr update function will automatically select the .debs for install). vs. a backup of an existing installation

If later on you also decide to back up whatever else you downloaded and installed, you can copy /var/cache/apt/archives, but you'd also want to run

dpkg --get-selections > installedpkgs

dpkg --set-selections < installedpkgs

to automatically mark the pkgs for installation, otherwise you'd have to go through it manually (time-consuming)

Or use AptOnCD.  

Just some thoughts...

---

### Post by GeordieJedi on 2009-05-10
Excellent!

Thank you both very much. logos34, and ugm6hr.


Appreciate the help. Take it easy. :D

---

