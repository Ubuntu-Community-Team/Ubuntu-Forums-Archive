---
title: "murrine config"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-27
I've installed this murrineconfigurator 0.5.I'm trying to figure this out.I have some murrine themes installed yet the configurator doesn't "see"any of them.Does version 0.5 actually work in 9.10?

---

### Post by dzon65 on 2009-11-28
Been trying to get this configurator to work,no use.Now,how do I uninstall it?Tried this but file isn't recognized (yet it's there)john@ubuntu:~$ cd ~/usr/bin/murrine-configurator
                           sudo ./uninstall.sh

---

### Post by Virtual Liberty on 2009-11-28
The easiest way to remove it is to open Synaptic or Ubuntu Software Center and mark it for removal, tough, I prefer command line.

```
sudo apt-get remove <package>

```

---

### Post by dzon65 on 2009-11-28
Virtual L.I's not in synaptics,can't execute that command.

---

### Post by Virtual Liberty on 2009-11-28
> **dzon65 said:**
> Virtual L.I's not in synaptics,can't execute that command.

How did you installed it ?

---

### Post by dzon65 on 2009-11-28
By downloading it from their website:[http://cimi.netsons.org/media/downlo...or-0.5.tar.bz2]("http://cimi.netsons.org/media/download_gallery/murrine/murrine-configurator-0.5.tar.bz2")
Crazy thing though,when ....uninstall it cannot be found.I'm looking at it right now!

---

### Post by Virtual Liberty on 2009-11-28
Extract the package and instead of *make install*, try *make uninstall* ( don't forget the *sudo* prefix ).

---

### Post by dzon65 on 2009-11-28
I did.Will not recognize it."File/folder doesn't exist"

---

### Post by Virtual Liberty on 2009-11-28
> **dzon65 said:**
> I did.Will not recognize it."File/folder doesn't exist"

Will not recognize .. what ? Can you show us what you are doing there ( copy / paste ) and the corresponding output ?

---

### Post by dzon65 on 2009-11-28
When trying to locate the file (it's in a bin file usr/bin/murrine-configurator),according to the terminal,the file doesn't exist.

---

### Post by dzon65 on 2009-11-28
According to the author this should uninstall it,but how do you do that?
UNINSTALL:
Just run as root:
./install.sh --uninstall

---

### Post by dzon65 on 2009-11-28
john@ubuntu:~$ find/murrine-configurator
bash: find/murrine-configurator: Bestand of map bestaat niet (...doesn't exist)
john@ubuntu:~$

---

