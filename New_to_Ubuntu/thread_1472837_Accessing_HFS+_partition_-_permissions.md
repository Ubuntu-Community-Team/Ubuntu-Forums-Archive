---
title: "Accessing HFS+ partition - permissions"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by kasyl on 2010-05-04
I've installed Ubuntu 10.04 on my MacBook Pro, dual-booting with Snow Leopard, and have thus far encountered only one problem that I just can't seem to be able to find any solution to.

I'm trying to access my files (music, documents, etc.) on the Mac side of the hard drive, but Ubuntu keeps telling me that I don't have the permissions necessary to view the contents of the folder. In Snow Leopard, I've changed the sharing options for all the folders I want to be available to "everyone" as some other posts have suggested, but to no avail. I've also installed "hfsplus" and "hfsutils" on the Linux side of things, but it made no difference.

---

### Post by hashbaz12 on 2010-05-26
On another thread [http://ubuntuforums.org/showthread.php?t=1031842](http://ubuntuforums.org/showthread.php?t=1031842) it suggested this command (and it worked for me):
gksudo nautilus

---

### Post by srs5694 on 2010-05-26
The gksudo command launches a program as root (the system administrator). This activity will break through many types of permissions problems, but it's a poor solution to this sort of everyday problem, for several reasons. Two of the biggest reasons are the inherent risk of running programs as root and the fact that any files created by the called program (Nautilus in this case) will usually be owned by root, which can lead to further permissions problems down the line.

Better solutions are to learn about Unix-style ownership and permissions (used by both Linux and OS X) to set appropriate ownership and permissions on the files and directories in question; and synchronizing the user ID (UID) numbers on the two OSes. I don't have any references to online resources handy, but I'm sure you can turn up appropriate Web pages by Googling terms such as "Linux ownership permissions" or "synchronizing dual-boot ownership".

---

