---
title: "Problem Upgrading Ubuntu 10.04 lucid lynx to 10.10"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by BJones007 on 2010-10-16
I tried updating my netbook to 10.10 and i kept getting this error message >  Error during commit
'E:Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.'
Restoring original system state 

does anybody know how I can fix this?

---

### Post by matsuzine on 2010-10-17
I think this might be the problem you are seeing:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/659610](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/659610)

There seem to be some suggestions here:

[http://wwww.ubuntuforums.org/showthread.php?t=1571449](http://wwww.ubuntuforums.org/showthread.php?t=1571449)

---

### Post by BJones007 on 2010-10-17
> **matsuzine said:**
> I think this might be the problem you are seeing:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/659610](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/659610)

There seem to be some suggestions here:

[http://wwww.ubuntuforums.org/showthread.php?t=1571449](http://wwww.ubuntuforums.org/showthread.php?t=1571449)
Yeah thas the bug alright, but the help page the link directed me to was about Kubuntu, will it work with Ubuntu Lucid Lynx as well? Plus I'm not using the beta version either.

---

### Post by matsuzine on 2010-10-17
I'm not familiar enough with these packages to be certain, but I think the packages and their dependencies are all related to the xorg server, which should be consistent regardless of the desktop environment.  

As alternate advice, it might be easier to avoid the upgrade issues and back up your data for a clean install.  Mostly I've always had good luck with upgrades, but I think the communal wisdom points to when in doubt, clean install.

---

