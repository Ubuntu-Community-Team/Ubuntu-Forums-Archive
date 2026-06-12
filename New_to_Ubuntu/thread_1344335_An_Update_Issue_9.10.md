---
title: "An Update Issue 9.10"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Arphitz on 2009-12-02
Good Day to all frenz....
Currently I have a small problem, when I tried to install 3rd party software to my ubuntu (using terminal) come out error issue...
until now I cannot install/update anyway new things to my laptop.

The error code something like this


'E:Type '--2009-11-20' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list, E:The list of sources could not be read.'


before this I tried multiple time to install "playonlinux" on my lappy. But still cannot go....

Someone please help me...

---

### Post by earthpigg on 2009-12-02
hi,

well, let's remove the playonlinux stuff and start over.

```
sudo rm /etc/apt/sources.list.d/playonlinux.list
```

then, go ahead and remove any packages that this playonlinux thing had you install.

that should get you normal ubuntu functionality back. if not, please post back with the output of this command:

```
cat /etc/apt/sources.list
```

---

### Post by Arphitz on 2009-12-03
Many thanks earthpigg

my problem already settled...but I'll try to reinstall again. But the same problem appear. Now still put a hold to install this software.

thanks again...
:p

---

