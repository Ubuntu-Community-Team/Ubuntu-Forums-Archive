---
title: "How to install debug versions"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-05-01
Running Jaunty.  Have a problem with removable media.  Whenever I insert a CD or a DVD into the drive, Nautilus stops working and my Desktop icons vanish.  The objects are still in /Desktop, they just don't appear on the screen.  Have to restart to get everything to work.

I've tracked the problem down in launchpad ([https://bugs.launchpad.net/ubuntu/+source/hal/+bug/315373](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/315373)) and apparently I need to install gvfs-dbgsym and libhal1-dbgsym packages.  Using Synaptics I can see I already have libhal1 and gvfs.  How to I get the gvfs-dbgsym and libhal1-dbgsym packages?  Maybe I have to build them.  If that is so, how to do it?

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by raymondvillain on 2009-05-04
Solved!

All is revealed in this link:

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

