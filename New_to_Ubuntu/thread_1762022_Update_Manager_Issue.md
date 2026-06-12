---
title: "Update Manager Issue"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Bunnies on 2011-05-18
> Failed to fetch cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


Does anybody know what this problem is or how to fix it?

---

### Post by wojox on 2011-05-18
Go into Update Manager > Settings > Ubuntu Software > uncheck Installable from CD-Rom/DVD

---

### Post by scottstensland on 2011-05-18
are you needing to read your CD/DVD for an update ?
If not then uncheck the entry using Update Manager
in its tab(s) :

Ubuntu Software
Other Software

Getting updates directly from the net is better if U can get online.

---

### Post by Rex Bouwense on 2011-05-18
As I was patiently typing this with my trusty two fingers, one of your questions has been answered not once but twice, I have eradicated that part of my response.  With regard to some packages failing to load.  That happens sometimes.  It generally corrects itself the next time. You can always use the terminal:
sudo apt-get update
sudo apt-get upgrade
That also updates the OS.

---

