---
title: "how do I repair a program installation?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by hougy on 2010-10-11
my problem is this: I attempted to install adobe flash plug-in on ubuntu 10.04. during installation my laptop battery died. after rebooting with an ac adapter, i tried to reinstall the flash plug-in but was told the last installation was incomplete and must be repaired.  there was no instruction on how to repair the installation.  HOW do I repair the installation?????  or remove the installation so I can reinstall?????  remove installation gives the same "must be repaired"

Hougy

---

### Post by slakkie on 2010-10-11
Try removing it and installing it again:

```

sudo aptitude purge adobe-flashplugin
# If this doesn't work try this:
sudo dpkg -r --force-all adobe-flashplugin

# install it again
sudo aptitude install adobe-flashplugin

```

Hope this helps.

---

### Post by beew on 2010-10-11
If you use Synaptic or the cli to install there is instruction for how to repair. In  the terminal run```


sudo dpkg --configure -a
```

and then install again.

Maybe there is no instruction if you use the Software Center.

---

### Post by hougy on 2010-10-11
BeeW,
I tried to use synaptic but could not load because of errors.  I did use the software center during the install.

Slakkie,
I will try the sudo commands and let you know what happened.

Thanks for you quick reply!!
Hougy

---

