---
title: "Why can't i update through update manager?"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by pocchi on 2011-06-27
my update manager keep prompted me with this message

Could not initialize the package information

an unresolvable problem occured while initializing the package
information.

Please report this bug against the 'update manager'
package and include the following error message;

'E:Encountered a section with no Package: header,
E:Problem with Mergelist/var/lib/apt/list/
us.archive.ubuntu.com_ubuntu_dist_natty_main_binary-
amd64_Packages,E:The package lists or status file could not
be parsde or opened.'


i tried update using the terminal
but still the same.

i also can't enter the ubuntu software center...
btw this is my first time using ubuntu.

anyone please HELP me!!!!

---

### Post by TeoBigusGeekus on 2011-06-27
Try this
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_old
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
Open update manager again and post back with the outcome.

---

### Post by jerrrys on 2011-06-27
check out rubi1200's answer

[http://ubuntuforums.org/showthread.php?p=10985675#post10985675](http://ubuntuforums.org/showthread.php?p=10985675#post10985675)

---

### Post by pocchi on 2011-06-27
thanks!!! to both of you.
i think my update manager is working again.

arigatougozaimas!!!!!!:D

---

