---
title: "Quick Question About Upgrading Software Though Terminal"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-04-09
How come when you update software through Terminal with sudo apt-get upgrade it sometimes holds software back and you have to upgrade it through Synaptic? I don't really mind, but it's more convenient since I'm usually in Terminal anyway adding a PPA.

---

### Post by taseedorf on 2011-04-09
It holds back certain updates because they CAN make huge changes to systems. (Such as kernel updates).....

use this to get all the changes

sudo apt-get dist-upgrade

Normally, some people don't want to upgrade their kernel all the time because on certain FINELY TUNED systems it can break things... for example, on my system if I upgrade a kernel I need to recompile my NVidia drivers...

---

### Post by Rex Bouwense on 2011-04-09
I thought sudo apt-get dist-upgrade  updates the entire system, i.e. 10.10 to 11.04 or one version to the next.  Is that wrong?

---

### Post by oldos2er on 2011-04-09
> **Rex Bouwense said:**
> I thought sudo apt-get dist-upgrade  updates the entire system, i.e. 10.10 to 11.04 or one version to the next.  Is that wrong?

That's wrong. apt-get dist-upgrade =  dist-upgrade in addition to performing the function of
           upgrade, also intelligently handles changing dependencies
           with new versions of packages; apt-get has a "smart"
           conflict resolution system, and it will attempt to
           upgrade the most important packages at the expense of
           less important ones if necessary. So, dist-upgrade
           command may remove some packages. The
           /etc/apt/sources.list file contains a list of locations
           from which to retrieve desired package files. See also
           apt_preferences(5) for a mechanism for overriding the
           general settings for individual packages.

---

