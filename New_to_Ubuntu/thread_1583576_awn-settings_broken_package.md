---
title: "awn-settings broken package"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by stonejug on 2010-09-28
Hey there,

I just upgraded to Ubuntu 10.04, and awn disappeared.  I tried to reinstall, but am getting a broken package error.  It seems that the package awn-settings is broken, and I have been having a hell of a time trying to repair it and reinstall awn.  I have tried (without success) fixing the package through the synaptic package manager, and using sudo apt-get -f install.  When I try to install via Update Manager I get this error:

E: /var/cache/apt/archives/avant-window-navigator_0.4.0-0ubuntu1_i386.deb: trying to overwrite '/usr/lib/awn/applets/separator/separator.so', which is also in package awn-core-applets-bzr 0
E: /var/cache/apt/archives/awn-applets-c-core_0.4.0-0ubuntu1_i386.deb: trying to overwrite '/usr/lib/awn/applets/awnterm/awnterm.so', which is also in package awn-core-applets-bzr 0
E: /var/cache/apt/archives/awn-applets-python-core_0.4.0-0ubuntu1_all.deb: trying to overwrite '/usr/share/avant-window-navigator/applets/animal-farm/animal-farm.py', which is also in package awn-core-applets-bzr 0

Anyone have any ideas? I need a dock back asap!

---

### Post by andrewthomas on 2010-09-28
Post the output of :
```

sudo aptitude update && sudo aptitude reinstall awn-settings
```

---

### Post by stonejug on 2010-09-28
Sweet!, it worked...thanks so much...

---

### Post by andrewthomas on 2010-09-28
mark the thread as [SOLVED] using the thread tools menu

---

