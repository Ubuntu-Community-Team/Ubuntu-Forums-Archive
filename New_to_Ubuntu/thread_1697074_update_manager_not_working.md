---
title: "update manager not working"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by rishabh.monga on 2011-02-28
hi
I'm kind of new to linux I installed ubuntu 10.10 a few days back. I've been updating it regularly for but now all of a sudden the update manager is unable to resolve package information. it is presenting the following errors:

"An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, 
E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages, 
E:The package lists or status file could not be parsed or opened."

please advice the necessary steps required.

thanks

---

### Post by vivek.pandey on 2011-02-28
can you post the contents of /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_binary-i386_Packages,

---

### Post by rishabh.monga on 2011-02-28
there is a file named security.ubuntu inside this bzip archive file. when i try to open or extract it. it show this error..

An error occurred while extracting files

---

### Post by vivek.pandey on 2011-02-28
no you should have normal text file there not a zip.just check it out once more.
there will be an exact file by that name right click and open with text editor

---

### Post by rishabh.monga on 2011-03-01
i accidentally solved the problem. this archive file had got corrupt so i tried removing security updates from the list of updates to be downloaded and the later re-enabled it. The update manager automatically downloaded the file again and is now working smoothly.
Thank you so much for your assistance.

---

