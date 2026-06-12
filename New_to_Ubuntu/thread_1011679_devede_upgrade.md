---
title: "devede upgrade"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by lizandeen on 2008-12-15
How can I upgrade my current version of Devede? Every time I try I'm told I need Mplayer but cannot load that either because it's conflicting with some other software ( I cannot find what this is ) or am told " Depends: libdirectfb-0.9-25  but it is not installable ", what is the solution to this as it's driving me insane! Thanks in advance:confused:

---

### Post by nandemonai on 2008-12-15
Need more info..

What release of ubuntu? What version of devede? How are you trying to upgrade? Error outputs etc etc

---

### Post by nhasian on 2008-12-15
the DeVeDe in the Multiverse Repository is Version 3.11, its already the newest version.  I saw on rastersoft's website there is a minor revision b but it only fixes some language issues in EL, PL, SK and SV locales.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by lizandeen on 2008-12-15
> **nandemonai said:**
> Need more info..

What release of ubuntu? What version of devede? How are you trying to upgrade? Error outputs etc etc
I'm running Ubuntu 8.04 and trying to upgrade Devede 3.06 to version 3.11. The problem is that every time I try to load the 3.11 DEB package I,m told " Error:Cannot Install 'Mplayer'" and if I try to load Mplayer by itself I'm told it conflicts with other software. Any ideas? I'm also told I can't install Mplayer because it depends on libdirectfb-0.9-25 but this is not installable. Aaargh!

---

### Post by nhasian on 2008-12-16
what if you enabled the backports repository?

System->Administration-Software Sources click the *updates* tab, then *Unsupported Updated* backports

---

### Post by nandemonai on 2008-12-16
> **nhasian said:**
> what if you enabled the backports repository?

System->Administration-Software Sources click the *updates* tab, then *Unsupported Updated* backports

^ Try that ^ :)

---

### Post by lizandeen on 2008-12-18
I've tried out your suggestion but to no avail, still getting the same annoying error messages! Any other ideas? Thanks, lizandeen

---

