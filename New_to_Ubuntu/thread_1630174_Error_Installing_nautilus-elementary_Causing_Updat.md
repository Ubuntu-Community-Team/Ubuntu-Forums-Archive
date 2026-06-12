---
title: "Error Installing nautilus-elementary Causing Update Manager Error"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by phillo on 2010-11-24
I'm using Ubuntu 10.10 Maverick Meerkat on a HP DV9000 AMD.  I made an unknown mistake while attempting to install nautilus-elementary which has caused the Ubuntu Update Manager to stop functioning with this error message:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list'
 

I found [this thread]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/132153"), followed the instructions but got errors right away:

cannot remove `/etc/apt/sources.list.d/phillip-ppa-maverick.list': No such file or directory

I'm not sure what additional info is needed but if you're able to help and need more info let me know.

---

### Post by jtarin on 2010-11-24
```
"/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list"
```
**and** ```
"/etc/apt/sources.list.d/phillip-ppa-maverick.list"
``` are two different things.
Your error message only referenced the first one. 
Make the corrections to the former as indicated on line 3 or comment it out by placing a # at the beginning of the line and try again. 
You will need to open the file in gedit from the commandline use the command ```
sudo gedit
```the locate your file and edit.

---

### Post by phillo on 2010-11-29
I manually deleted 2 files in sources.list.d that were apparently causing the update error.  Thanks for the help.

---

