---
title: "Could not initialize the package information"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by arunb24 on 2011-05-31
i am using ubuntu 11.04 and always get an error notification on taskbar which on clicking just opens the Synaptic Package Manager with the following message:

Could not initialize the package information
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en, E: The package lists or status file could not be parsed or opened.'

how to get rid of this?

---

### Post by LowSky on 2011-05-31
open a terminal copy and paste this command.

```
sudo apt-get update && sudo apt-get update
```

---

### Post by jerrrys on 2011-05-31
something is going on with updates right now.

[http://ubuntuforums.org/showthread.php?p=10885118#post10885118](http://ubuntuforums.org/showthread.php?p=10885118#post10885118)

---

### Post by arunb24 on 2011-05-31
> **LowSky said:**
> open a terminal copy and paste this command.

```
sudo apt-get update && sudo apt-get update
```


d above command updated many things. but i got error at the end:

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

got the above error

---

### Post by wildmanne39 on 2011-05-31
> **arunb24 said:**
> d above command updated many things. but i got error at the end:

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

got the above error
Hi, try this
```
sudo rm -r /var/lib/apt/lists
sudo apt-get update
```

---

### Post by arunb24 on 2011-05-31
> **wildmanne39 said:**
> Hi, try this
```
sudo rm -r /var/lib/apt/lists
sudo apt-get update
```

oh thanks a lot man!!!
well can you tell me actually what had happened, and by removing 'lists' will it work as it used to?

---

### Post by wildmanne39 on 2011-05-31
> **arunb24 said:**
> oh thanks a lot man!!!
well can you tell me actually what had happened, and by removing 'lists' will it work as it used to?Hi, a lot of people have been having the same problem the ppa list are getting corrupted or are the wrong ones. That should fix your problem it has a lot of peoples but some find that it takes more commands.

---

