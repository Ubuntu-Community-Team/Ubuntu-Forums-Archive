---
title: "32bit version, does it use pae?"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by ELD on 2010-06-13
Just a quick one, does the 32bit kernel by default use PAE to access 4GB+ RAM?

---

### Post by howefield on 2010-06-13
On a clean install, 10.04 32 should install the pae kernel if it detects more than 3 gig of RAM.

> Ubuntu 10.04 LTS (Lucid Lynx)
Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

