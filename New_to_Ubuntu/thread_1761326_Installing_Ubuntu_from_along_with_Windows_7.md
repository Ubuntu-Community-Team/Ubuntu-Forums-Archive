---
title: "Installing Ubuntu from along with Windows 7"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by rawbertb on 2011-05-18
I currently have Ubuntu installed along with Windows 7.  I want to keep Ubuntu as my sole OS and get rid of Windows, but have absolutely no idea how to do this.

---

### Post by NormanFLinux on 2011-05-18
There is Gparted. You can try to delete the Windows partition but I think you should back up all your data and then do a fresh install of Ubuntu in place of Windows 7.

---

### Post by apollothethird on 2011-05-18
> **rawbertb said:**
> I currently have Ubuntu installed along with Windows 7.  I want to keep Ubuntu as my sole OS and get rid of Windows, but have absolutely no idea how to do this.

Make sure you didn't install Ubuntu as a Windows app (wubi).  If you booted to the installation disk and installed it from there this wouldn't be a problem.  But if you ran the Ubuntu installer from Windows 7, this could be a problem and would take some important and special steps.

Again, if you ran the installation from Windows 7, removing Windows 7 might remove Ubuntu.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Rubi1200 on 2011-05-18
As apollothethird correctly points out, we need to know whether this is a regular or Wubi install. 

And just to clarify something; if this is a Wubi install, removing Windows _will definitely_ remove Wubi.

Further advice depends on this piece of information.

It would also be useful if you could post a screenshot of the disk setup either from Disk Management in Windows or GParted from a LiveCD/USB.

Thanks.

---

