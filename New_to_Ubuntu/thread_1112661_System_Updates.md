---
title: "System Updates"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by KevinGallo on 2009-03-31
When trying to run the Synaptic Package Manager, I keep getting this error message...

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I am new, but it appears it wants to read from some CD ROM in order to update. I don't know why it would do that. 

Any advice?

Kevin

---

### Post by lostbuthappy on 2009-03-31
Hey Kevin,

you are right, Ubuntu wants the cdrom.
To change that go to [COLOR="DarkSlateBlue"]System>Administration>Software Sources[/COLOR] and make sure that the checkbox next to "Cdrom with Ubuntu 8.xx" is blank, hit close, reload package information and the problem should be solved.

Dominik

---

### Post by KevinGallo on 2009-03-31
Brilliant. Worked.

Thanks Dominik

---

