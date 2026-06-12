---
title: "Update Manager Problem"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by munna.cheyur on 2011-05-26
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.mitra.net.np_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

(the window containing above error report coming at each time when i'm opening upd mgr and it is not opening too thnks for ur help)

---

### Post by jre6 on 2011-05-26
Run the following in a terminal:
```

sudo rm /var/lib/apt/lists/*
sudo apt-get upgrade

```

That should fix the problem.

---

### Post by dg4345 on 2011-05-26
I have the same problem. The solution fixes the problem until I reboot the system. Is there a permanent solution to this issue?

---

### Post by spillage on 2011-05-26
have you tried going into synaptic package manager and using the "fix all broken packages"..think this might help..

Spill.

---

### Post by Rubi1200 on 2011-05-26
Try doing it like this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

