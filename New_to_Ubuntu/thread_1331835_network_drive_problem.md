---
title: "network drive problem"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by satipera on 2009-11-19
I have an addonics  mini nas set up and working quite well apart from one thing. I can read and write to the drive via ftp connect to network in nautilus. I can also delete the content of the folders, but I can't delete the folders themselves even when they are empty. I am assuming this is not a permissions problem as I can delete the contents of the folder but not the folder itself. Could someone please tell me what the problem is.

---

### Post by satipera on 2009-11-21
All this is taking place over a LAN to a NAS. When I mount the NAS as a windows share I have full read write privileges including the ability to delete anything. 

When I mount the NAS via ftp in nautilus everything is the same except I can't delete any folders even if I have deleted its individual files whilst on ftp.

Is this normal? If not does anyone have an explanation?

---

### Post by byStanderone on 2009-11-21
...perhaps u should evoke root privelege to delete that particular folder, or perhaps it is'nt a folder at all, but a directory.

---

### Post by satipera on 2009-11-21
Thanks standerone.  Whether they are directories or not why can I delete them in a windows share and not over FTP?

---

### Post by byStanderone on 2009-11-22
...i see, perhaps window share waives some of the features of nautilus, specially when it comes to security, and nautilus is strict bout that.

---

