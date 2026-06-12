---
title: "Partition Rodeo Question"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by oldtug on 2009-06-19
First off, finally took the leap and installed 9.04 in my badly bloated Dell Insperon 600m in its own partition of about 9.5MB.  Things seem to be running fine on the Ubuntu side.  (A bit like stepping off the boat onto an new undiscovered land)  

I now want to wipe the XP partition and do a clean XP install, and at same time divide the total HD capacity between the 2 systems.

What is the best practice to follow?  I don't want to (if I don't have to) reinstall 9.04. 

[B]If I use the XP install disk will that wipe ALL partitions on disk, including 9.04, or just the XP side of things?   Or is there a method that works using the live 9.04 disk.
[/B]
Thanks

Eric in Seattle

PS: I'm starting to enjoy the feeling of removing myself from the M*M*I*C!          (microsoft mac industrial complex)

---

### Post by TeoBigusGeekus on 2009-06-19
Boot up with the live cd and extend your Ubuntu partition.
Also create a new SEPARATE partition on which you will install winxp.
Just remember that windows will destroy grub and you will have to restore it.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

