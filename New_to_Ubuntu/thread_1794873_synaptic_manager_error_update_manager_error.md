---
title: "synaptic manager error /update manager error"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by amchornet on 2011-07-01
I can not run update manager or synaptic manager either i get error  message about not being able to open or read a package with no header. anyone with any Ideas?


Could not initialize the package information


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by TeoBigusGeekus on 2011-07-01
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_old
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
Try again and post back with the outcome.

---

### Post by AaronDaycentChild on 2011-07-01
> **TeoBigusGeekus said:**
> ```
sudo mv /var/lib/apt/lists /var/lib/apt/lists_old
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
Try again and post back with the outcome.

This worked for me. :grin:

---

### Post by amchornet on 2011-07-04
It worked for me!! I cant thank you enough!!!

---

