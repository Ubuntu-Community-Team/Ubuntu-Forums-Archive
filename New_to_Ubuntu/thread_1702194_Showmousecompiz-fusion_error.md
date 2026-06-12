---
title: "Showmouse/compiz-fusion error"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Jane202 on 2011-03-07
Hello! I am trying to install "showmouse" on my Ubuntu/Gnome. I typed in source code:

sudo apt-get source compiz-fusion-plugins-extra

But my terminal came up with:

Check if the 'dpkg-dev' package is installed.
E: Child process failed

Does anyone know how to resolve this? 

Thanks!

---

### Post by Verbeck on 2011-03-07
try installing dpkg-dev as it suggested

btw, is there any special reason why you are trying to get the source?
just install compiz-fusion-plugins-extra as it is from the repos and 'Show mouse' should be in system>preferences>ccsm/compiz-config-settings-manager

---

### Post by Jane202 on 2011-03-07
Thanks Verbeck!  I'm pretty new at this (eek!), so how do I install the compiz-fusion?  Do I just copy and paste the line you wrote?

---

### Post by Verbeck on 2011-03-07
you could search the software-center and install it. or, run from a terminal;
```

sudo apt-get *install* compiz-fusion-plugins-extra
```and if you haven't already installed ccsm yet;
```

sudo apt-get install compizconfig-settings-manager
```after that, you could enable the plugins you want from system>preferences>compiz-config-settings-manager

(make sure you've got desktop effects enabled from system>preferences>appearance)

---

### Post by Jane202 on 2011-03-07
Thanks! That definitely worked. I can't wait to play around with it!

---

