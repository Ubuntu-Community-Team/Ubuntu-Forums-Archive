---
title: "compizconfig-settings-manager"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Dmck23 on 2009-07-03
Hi everyone,

I've just switched over to ubuntu 9.04 and am trying to install the compiz settings manager but am getting the following error

:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compizconfig-settings-manager: Depends: python-compizconfig (>= 0.8.2) but it is not installable
E: Broken packages

i looked in the synaptic Package manager and there is no python-compizconfig file.. any help that anyone could give to me would be greatly appreciated

Thanks
Dmckd23

---

### Post by Garyhans on 2009-07-03
I believe it's install ccsm    to correctly install it.

---

### Post by snakeman21 on 2009-07-03
Don't bother using the command line for Compiz.  For some reason, is doesn't seem to work correctly.  Use the Add/Remove Programs utility.  That worked for me.

---

### Post by Dmck23 on 2009-07-04
Hi all thanks for the advice, I've tried to install it with Synaptic but am still getting the following error..

[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

compizconfig-settings-manager:
 Depends: python-compizconfig (>=0.8.2) but it is not installable

again any heip would be great

---

### Post by The Jinx on 2009-07-04
hmm, maybe you need to update the pkg list?

apt-get update

---

### Post by CatKiller on 2009-07-04
python-compizconfig is in the Universe repository. Enable it from System -> Administration -> Software Sources or by editing sources.list.

---

