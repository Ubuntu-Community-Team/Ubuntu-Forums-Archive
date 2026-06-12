---
title: "Repost:  The Update Manager Blues"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by sillyboy on 2009-09-04
I'm getting the orange triangle icon for updates again. The triangle message says:The update info is outdated...etc.  In the Update Manager I click on the "Check button", and I get this message:

[I]Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/I]

I have changed my sources numerous times.  I thought this problem was solved a few weeks ago, but...:rolleyes:

Any help is appreciated. :P

Thanks 


PS  Please remember this is the Absolute Beginner forum #-o

---

### Post by scragar on 2009-09-04
```
sudo su
mv /etc/apt/sources.{list,backup}
cat /etc/apt/sources.backup | sed 's/.*cdrom:.*/#\0/' > /etc/apt/sources.list
exit
```If you run those one after another you shouldn't have any problems.

In short that code will enter root user(so it has perms to edit the sources file). Rename the current sources file so it doesn't get erased, then make a new copy in the origional location and comment out any line with the word cdrom followed by a colon as you don't need those lines, then it will exit the root user, since it's a security risk to remain as root for a long time.

---

### Post by sillyboy on 2009-09-04
Resolved

Thanks  scragar!

---

