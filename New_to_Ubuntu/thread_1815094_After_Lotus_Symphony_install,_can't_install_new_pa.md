---
title: "After Lotus Symphony install, can't install new packages"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Catfish Dubois on 2011-07-30
I installed Lotus Symphony 1.3 today and ever since then I have been unable to install packages in synaptic or the ubuntu software center.  When I try, I get the following:

Preconfiguring packages ... dpkg: error: parsing file '/var/lib/dpkg/available' near line 0:  field name `/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.launcher.linux.x86_1.5.0.20090908-0900/IBM' must be followed by colon E: Sub-process /usr/bin/dpkg returned an error code (2) A package failed to install.  Trying to recover:

I uninstalled Symphony to no avail.  I also cannot find the supposed file /opt/ibm/Symphony/framework/shared/eclipse/plugins

Does anyone have any suggestions?

---

### Post by trozamon on 2011-07-30
I don't know. Try this:

```
sudo apt-get install -f
```That may or may not fix it.

---

### Post by bodhi.zazen on 2011-07-30
Well two things.

First that package is broken, and as it is not in the Ubuntu repositories, you will have to contact IBM for support

To fix it you will have to remove it.

```
sudo dpkg --remove --force-all name_of_your_Lotus_package
```

or 

```
sudo dpkg --remove --force-remove-reinstreq name_of_your_Lotus_package
```

If that fails see:

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/) 

and post any error messages.

---

