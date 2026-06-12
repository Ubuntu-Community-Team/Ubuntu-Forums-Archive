---
title: "HD Partitions when running WinXP in virtualbox"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Diamond.Dave on 2009-05-24
Hi.  Recent convert to Ubuntu and I love it, but need WinXP for some functions.  Plan to load virtualbox and then WinXP.  If I want/need to access HD files from WinXP, should I partition my HD (I have an 80GB)?  Would running the virtualbox really require me to leave more space on the operating system partition?  Or, since I plan to use Ubuntu for as much as humanly possible, should I just leave the HD as 1 big partition, load 9.04, and if I want any files for the Windows box access them via USB drive?  Any comments or insights are appreciated.  Thank you!!  :p

---

### Post by jimmy the saint on 2009-05-24
The virtual harddrive is stored as a file.  I store them on a second (internal) drive for speed reasons, but it is not neccessary.  

As far as transfering files, it is not difficult to set up a shared folder on the Host system that he guest system has access to.  There is a really good explanation for that in the virtual box user manual that you can access from the help menu.  If you want to use the shared folder feature I think you need to get the .deb file from the virtualbox website instead of installing from the ubuntu repositories though.

---

### Post by cariboo on 2009-05-24
There is no need to create seperate partitions for an os in Virtualbox. You create a virtual hard drive when you install another os, you can make it whatever size you need. I personally  store my vm's on a second nternal hard drive, that is one large partition.

USB and many other bits of hardware are available once you install the guest additions, available once you have your vm running when you click Devices-->Guest Additions.

---

### Post by Diamond.Dave on 2009-05-24
Thanks for the quick replies!  I'll be trying this out this weekend!
 
Dave

---

