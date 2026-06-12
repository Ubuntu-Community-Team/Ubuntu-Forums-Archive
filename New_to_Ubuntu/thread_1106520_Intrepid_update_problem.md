---
title: "Intrepid update problem"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by lee292 on 2009-03-25
I get an orange triangle in the upper right of my screen.  When I click on it it tells me that my system is out of date and I need to run Update Manager manually.  When I do, I get a message that says "Could not download all repository indexes" and it lists the following:

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I don't have these CD-ROMs.  What should I do?

Thanks for your help.

---

### Post by Gramps on 2009-03-25
go to System/Administration/Software Sources and on the Ubuntu Software tab. At the bottom of the page there is a box marked Installable from CD-ROM/DVD, uncheck everything in the box below.

Close and answer yes to reload. You sould now be ab[e to update using the Update Manager

---

### Post by lee292 on 2009-04-02
Thanks, Gramps!  Your suggestion did the trick!

---

