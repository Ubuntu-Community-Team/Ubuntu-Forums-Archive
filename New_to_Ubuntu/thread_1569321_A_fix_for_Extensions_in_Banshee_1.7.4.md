---
title: "A fix for Extensions in Banshee 1.7.4"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by Sonybuntu on 2010-09-06
Hi everyone. This is a guide on how to get the community extensions for Banshee 1.7.4. There are no extension packages for Banshee 1.7.4, so here is a quick and dirty fix.

**BEFORE YOU BEGIN:**

**1)** Add the Banshee unstable repository *(sudo apt-add-repository ppa:banshee-team/banshee-unstable)*

**2)** In a terminal, paste *sudo apt-get update* and then *sudo apt-get install banshee*

**3)** *sudo apt-get build-dep banshee-community-extensions*

**========================================================================**

**1)** Download [this]("http://download.banshee.fm/banshee-community-extensions/1.7.4/banshee-community-extensions-1.7.4.tar.gz") tarball. It is the community extensions tarball for 1.7.4.

**2)** Extract the tarball and cd to the extracted directory.

**3)** In a terminal, type in *./configure* then *make* and then ***sudo make install***. **No using checkinstall!**

**4)** Now copy the files in ***/usr/local/lib/banshee-1/Extensions*** to ***/usr/lib/banshee-1/Extensions***

**5)** Open up Banshee. If there is no App Indicator, go to Edit -> Preferences -> Extensions tab and click on the extensions you want.

Need any help? Just post a reply!

---

### Post by Dportner on 2010-09-06
the only thing i have in usr/local/lib is a python2.6 folder :S

no banshee

---

### Post by Sonybuntu on 2010-09-06
> **Dportner said:**
> the only thing i have in usr/local/lib is a python2.6 folder :S

no banshee

oops, try adding sudo to make install. You don't have to do ./configure again, just cd to the same folder and type in make and then sudo make install.

---

### Post by Dportner on 2010-09-06
AHA! that was it :)

good work!
the community extensions are now back, thanks you very much

---

