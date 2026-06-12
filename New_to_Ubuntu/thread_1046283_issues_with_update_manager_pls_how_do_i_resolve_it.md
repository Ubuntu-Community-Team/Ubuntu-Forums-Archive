---
title: "issues with update manager pls how do i resolve it"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by nnamdi on 2009-01-21
i have an issue i cannot update my ubuntu hardy is gives me an error message

```

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.

```

please thank you for your replies

---

### Post by taurus on 2009-01-21
What happens if you run it from a terminal?  Make sure you close update-manager first though.

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Michael.Godawski on 2009-01-21
hi

can you please post your sources.list?

```
cat /etc/apt/sources.list
```

There are some other bugs on launchpad with this error message.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/306515](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/306515)

Have you upgraded your Ubuntu at some time?
And do you have the CD as an installation sources enabled?

---

### Post by handydan918 on 2009-01-21
> **nnamdi said:**
> i have an issue i cannot update my ubuntu hardy is gives me an error message

```

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.

```

please thank you for your replies

You might want to [look at this unresolved bug report.]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/237013")

I would also try ```
sudo apt-get update && apt-get upgrade
``` Post any errors you get....

If the universe repo keeps erroring and keeping you from updating, you might simply "un-check"it in Synaptic, at least temporarily.

---

### Post by nnamdi on 2009-01-21
thank you everyone for your help it working well now i actually used taurus advise which is

```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


```

---

