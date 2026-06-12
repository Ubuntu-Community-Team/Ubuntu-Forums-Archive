---
title: "I can't aces update menager"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by shpira on 2011-07-27
What is happening? I can't aces update menager.
Sorry for bad English.

---

### Post by drs305 on 2011-07-27
shpira,

Welcome to the Ubuntu forums.

Try starting Update Manager from a terminal with the following command. If it doesn't open, paste the error messages you get.

If you haven't used 'gksu' or 'sudo' in a terminal before - you will be asked for your password. Type it and press ENTER but you won't see any of the characters as you type them.
```

gksu update-manager
```

---

### Post by shpira on 2011-07-27
Thank you, but doesn't work. It's show me some kind of error mesage, like this: Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/rs.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Rubi1200 on 2011-07-28
Hi and welcome to the forums shpira :)

Open a terminal with Ctrl+Alt+T and copy and paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second updates them.

---

