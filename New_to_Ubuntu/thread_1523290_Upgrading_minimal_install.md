---
title: "Upgrading minimal install"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by rascal+1/2 on 2010-07-03
I run Ubuntu 8.04 minimal install on a Pentium III with 128 Mb ram. (Works pretty good for some basic tasks including internet). I uploaded synaptic and update manager because I want to upgrade the minimal install to 10.04. Question is, will using the update manager recognize that I'm running openbox & xfe & the minimal install customs? Or wipe out all the customizations and try to install the whole 10.04 package? -That I definitely don't want.  Please and thank you,

Josh

---

### Post by lkjoel on 2010-07-03
It will probably try to install the whole 10.04.
How much disk space do you have?
Because if you can squeak by the full install, it is not hard to remove a lot of applications, and "downgrading" some others.
What I mean by "downgrading" is for example, instead of gnome-terminal, you would have xfce4-terminal, which is less space from a few hundred KB.

---

### Post by mbsullivan on 2010-07-03
Hi Josh!

As far as I know, you're in the clear... Upgrading your distro will only apply updates to the packages you have installed.

For future reference, you can do this from the command line, too. See "Network Upgrade for Ubuntu Servers (Recommended)" [here]("https://help.ubuntu.com/community/LucidUpgrades").

Mike

---

### Post by lkjoel on 2010-07-05
Use the Update Manager to upgrade it.

---

### Post by mbsullivan on 2010-07-09
> Use the Update Manager to upgrade it. 

Users with the minimal install might not necessary *have* or *want* synaptic and update manager. They are not strictly needed for the upgrade.

Right now, the only package that's needed is update-manager-core:

```
sudo aptitude install update-manager-core
``` 

And then to run a do-release upgrade:

```
sudo do-release-upgrade
```

... Of course, you can use the update manager as well, if you have a graphical installation. It's up to you.

Mike

---

