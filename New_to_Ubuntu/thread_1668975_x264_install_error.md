---
title: "x264 install error"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by vogskis on 2011-01-17
i'm following [this tutorial]("http://ubuntuforums.org/showpost.php?p=9114176&postcount=967") to eventually install ffmpeg on my server, but i'm having issues installing x264, Step 3.

after running...

sudo checkinstall --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`+`git rev-list HEAD -n 1 | head -c 7`" --backup=no --default --deldoc=yes

here is the error message i am receiving...



Installing with make...Installing with install...



========================= Installation results ===========================

/usr/bin/installwatch: /var/tmp/tmp.SSV747Q8Dz/installscript.sh: /bin/sh: bad interpreter: Permission denied



****  Installation failed. Aborting package creation.



Cleaning up...OK



Bye. 


i think it may have something to do with some permissions modifications i made to the /var/tmp/ directory.  

anybody got an idea on what's happening here?

---

### Post by fabricator4 on 2011-01-17
Forgive me for being dense, but doesn't your distro (you didn't specify which one) have a package manager? Those instructions are 18 months old, and possibly for a beta or candidate release.  It seems to be harder than it needs to be.

Chris

---

### Post by FakeOutdoorsman on 2011-01-17
Those instructions are not 18 months old. If you scroll to the bottom of the page you can see that the last time it was updated was *September 17, 2010*. They also have nothing to do with a beta or candidate release.

---

