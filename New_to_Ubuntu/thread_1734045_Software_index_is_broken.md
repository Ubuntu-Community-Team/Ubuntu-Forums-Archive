---
title: "Software index is broken"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by ni ni on 2011-04-19
hello all.

I can't launch the Ubuntu Software Centre.

I cant use update manager i get the following:
```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ck' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list'
```

Also i get the following when trying to install a package:
```
Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

Please help. What is "/etc/apt/sources.list" and how do i edit it safely?

I'm an absolute beginner :-(

thanks  x x x x x

---

### Post by MooPi on 2011-04-19
Try opening a terminal and use this command
```
sudo apt-get update
```
Post back your results.
Could you also post the contents of ```
gedit /etc/apt/sources.list
```

---

### Post by oldos2er on 2011-04-19
You've got a typo in /etc/apt/sources.list.d/tualatrix-ppa-maverick.list. Run ```
sudo rm /etc/apt/sources.list.d/tualatrix*
``` then ```
sudo apt-get update
``` and hopefully the error will be gone. If you want to try adding the PPA again, see [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

