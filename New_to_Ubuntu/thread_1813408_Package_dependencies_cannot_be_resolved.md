---
title: "Package dependencies cannot be resolved"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by salehahmed985 on 2011-07-27
HI there, i'm new user of natty. the problem is when i'm trying to setup chrome, the message appear on my screen is "Package dependencies cannot be resolved". how can i solve it? another problem is when i want to install empathy instant messenger same thing happens and it shows 

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

empathy: Depends: libunity3 (>= 3.4.2) but 3.4.2-0ubuntu5 is to be installed
         Depends: empathy-common (= 2.33.1-0ubuntu3) but 2.34.0-0ubuntu3 is to be installed

bt both of this are installed. if i uninstall one of them another program gone uninstalled. why? pls help me. thnx.

---

### Post by jtarin on 2011-07-27
Are you installing from an Ubuntu repository or some website.If repository what are you using....Software Center, Synaptic or commandline (apt-get)?

---

### Post by sirgogo on 2011-07-27
Like jtarin^ said, verify how you are attempting to install these things.

Sometimes the debian package manager cannot resolve dependencies for utilities that are currently being used. This shouldn't be the case for the packages you say you're trying to install, but its possible there is a idle, lame process hanging around on your system. I'd say, try a restart first. If that doesn't work, remove the packages in question completely (System-->Administration-->Synaptic Package Manager), hit apply, then mark for installation again.

Let us know how it goes.

---

### Post by salehahmed985 on 2011-07-28
i used ubuntu software center, terminal n synaptic.. bt the result is same..

---

### Post by salehahmed985 on 2011-07-28
when i removed the conflict files, other software gone removed. like i said, libunity3 is installed in my pc. bt i can't install empathy-common because of other depends. bt if i remived that depends, some other software gone removed for it.

---

### Post by lkjoel on 2011-07-28
Try this:
```
sudo aptitude install *PACKAGE*
```
And replace PACKAGE by the package you want to install.

---

### Post by sirgogo on 2011-07-28
> **salehahmed985 said:**
> when i removed the conflict files, other software gone removed. like i said, libunity3 is installed in my pc. bt i can't install empathy-common because of other depends. bt if i remived that depends, some other software gone removed for it.

^Try what lkjoel said. If not, note all the packages that its going to remove and simply re-install them manually afterwards. These packages shouldn't be tied to system functionality, so it should be OK.

---

