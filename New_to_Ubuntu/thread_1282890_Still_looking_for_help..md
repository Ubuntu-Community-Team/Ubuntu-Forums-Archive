---
title: "Still looking for help."
date: 2009-10-04
forum: New to Ubuntu
---

### Post by iamjfarrell on 2009-10-04
```
fusion-icon
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon.interface import choose_interface
  File "/usr/lib/python2.6/dist-packages/FusionIcon/interface.py", line 21, in <module>
    from util import env
  File "/usr/lib/python2.6/dist-packages/FusionIcon/util.py", line 21, in <module>
    import os, compizconfig, ConfigParser, time
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions


justin@justin-laptop:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.6/dist-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

```

That is what I get when I try to run Fusion-icon and ccsm in terminal. I don't know what those errors are but when I try to run them nothing happens.

---

### Post by nhasian on 2009-10-05
instead of that fusion-icon all you need is compizconfig-settings-manager.

```
sudo apt-get install compizconfig-settings-manager
```

then you can modify your compiz settings from System->Preferences->Compiz Config Settings Manager.

---

### Post by iamjfarrell on 2009-10-05
> **nhasian said:**
> instead of that fusion-icon all you need is compizconfig-settings-manager.

```
sudo apt-get install compizconfig-settings-manager
```

then you can modify your compiz settings from System->Preferences->Compiz Config Settings Manager.

I have CCSM. It doesn't open when I try to start it. Neither does fusion-icon. When I tried to re-install CCSM this is what I got.

```
sudo apt-get install compizconfig-settings-manager
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11-generic dkms linux-headers-2.6.28-11
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  compizconfig-settings-manager
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/638kB of archives.
After this operation, 4166kB of additional disk space will be used.
Selecting previously deselected package compizconfig-settings-manager.
(Reading database ... 233780 files and directories currently installed.)
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb) ...
Setting up compizconfig-settings-manager (0.8.2-0ubuntu1) ...
**INFO: using unknown version '/usr/bin/python3.0' (debian_defaults not up-to-date?)**


```

Does anyone know what the bold means?

---

### Post by achase79 on 2009-10-05
did you install python3 and uninstall python2.6?  That could be your error.

---

### Post by iamjfarrell on 2009-10-06
Not that I know of. I doubt it. I could I ensure that both are installed?

---

### Post by bruno9779 on 2009-10-06
Go to synaptic, ctrl+f python and see which versions you have installed.

You may have more than one.

for example I have 2.5 and 2.6 installed but not 3.0

if you run in terminal

```
python --version
```

you should get something like this:

```
Python 2.6.2
```

---

### Post by oldos2er on 2009-10-06
> **iamjfarrell said:**
> Does anyone know what the bold means?
 Which version of Ubuntu are you running?

---

### Post by iamjfarrell on 2009-10-09
> **oldos2er said:**
> Which version of Ubuntu are you running?

Jaunty 9.04
Kernel 2.6.28-15
Gnome 2.26.1

---

### Post by iamjfarrell on 2009-10-09
> **bruno9779 said:**
> Go to synaptic, ctrl+f python and see which versions you have installed.

You may have more than one.

for example I have 2.5 and 2.6 installed but not 3.0

if you run in terminal

```
python --version
```

you should get something like this:

```
Python 2.6.2
```


I have versions: 2.4, 2.5, 2.6 and 3.0

When I put in 

```
python --version
```

I got

```
Python 2.6.2
```

---

### Post by iamjfarrell on 2009-10-13
Bump for some help!

---

### Post by iamjfarrell on 2009-10-15
Bump

---

### Post by LewRockwell on 2009-10-15
> **iamjfarrell said:**
> Bump for some help!

[http://pic.phyrefile.com/a/an/anonymous/2008/12/08/bump.gif](http://pic.phyrefile.com/a/an/anonymous/2008/12/08/bump.gif)

image=fail

imageX2=fail

.

---

