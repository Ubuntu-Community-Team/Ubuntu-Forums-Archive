---
title: "not all installed packages removed by autoremove and --purge...method?"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-11-26
So I am using Ubuntu minimal,
I went to install mintmenu, and gnome system menu. Realizing that it bloated my system, I did a full --purge and auto-remove. However some programs installed with these packages remain: ex. synaptic and software sources (not sure why these would have been installed). 

  Is there a more complete way to see what was installed alongside these two (now removed) panels? So that i can be sure to delete everything installed with them? 


Thanks! 

ideally id like to use aptitude, apt-get, or command line utility, but not adverse to using synaptic to uninstall synaptic :)  Any method welcome

---

### Post by cariboo on 2010-11-26
I know this doesn't solve your problem, but if you use:

```
apt-get install --no-install-recommends <packagename>
```

You won't have the problem of needing to remove other packages installed when you install a package. I personally don't see a problem with leaving packages on the hard drive, unless space is an issue, as they don't take up any other resources.

---

### Post by rbhkamal on 2010-11-26
Think before you uninstall everything this command gives you:
```
sudo deborphan --guess-all --all-packages
```

again, use your brain before uninstalling orphan packages.

---

