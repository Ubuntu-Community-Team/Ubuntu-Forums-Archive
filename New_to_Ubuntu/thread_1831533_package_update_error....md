---
title: "package update error..."
date: 2011-08-23
forum: New to Ubuntu
---

### Post by ornothaloapq on 2011-08-23
when i try to update packages i get this error message:  Could not initialize the package information  An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'  has anyone else had this problem?

---

### Post by jerrrys on 2011-08-24
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

that should fix it

---

