---
title: "Symbolic Links and the Desktop Directory"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by sharkllama on 2010-09-24
Hi, 
   I was interested in synchronizing my desktop (and several other directories) across several different computers.  I've already accomplished this with other directories, which contain scripts or other office documents, using svn and symbolic links.  
   My system consists of creating an svn respository.  This repo is hosted on my primary workstation and is accessible from every other computer.  There are several directories within this repo: Scripts, Documents, Webpages, etc. each of which are linked to the appropriate path on each machine.  
   I'd like to do the same with my desktop.  Thereby allowing me to synchronize my desktop.  Unfortunately, when I remove the existing ~/Desktop directory and replace it with a symbolic link which points to the svnrepo/Desktop directory none of the files present int he svnrepo/Desktop directory are visible on my desktop?  
   Any ideas why?  Or preferably, how to resolve the issue?
Thanks, 
-Brant

---

### Post by sharkllama on 2010-09-28
Alright, 
   For those of you running into a similar problem I would like to reccomend a restart/log-off.  Problem appears to be fixed now.  I'm not sure how the desktop icons come to be visualized through GNOME, but they appear to be initialized on boot.
-Brant

---

