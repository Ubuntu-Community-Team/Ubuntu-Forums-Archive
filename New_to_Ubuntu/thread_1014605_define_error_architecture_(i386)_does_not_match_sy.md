---
title: "define error_architecture (i386) does not match system"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mfayaz on 2008-12-18
i just received this error while trying to install w32codecs... does this mean that my current version of ubuntu is amd64??... kinda lost here.. i'have ubuntu installed on my lenovo 3000 N100 (intel) so i guess i'll have to reinstall ubuntu??? any guidelines??

> dpkg: error processing w32codecs_20071007-0medibuntu1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)

---

### Post by perlluver on 2008-12-18
It appears you have Ubuntu 64 bit installed, just to be sure, could you please open a terminal, Applications>Accessories>Terminal and post the output of ```
uname -r
``` if you do have it installed, then you will want to install w64codecs.

---

### Post by jerome1232 on 2008-12-18
From that error message I think it's safe to say that yes you do have a 64 bit install, and you don't have to re-install ubuntu just do as perlluver suggests and install w64codecs.

---

### Post by mfayaz on 2008-12-18
thnxs guy... problem solved :)

---

### Post by perlluver on 2008-12-18
> **mfayaz said:**
> thnxs guy... problem solved :)

Could you please mark as solved.. :)

---

