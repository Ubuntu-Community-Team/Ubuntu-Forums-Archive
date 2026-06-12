---
title: "Jahshaka"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Zopiac on 2009-12-20
Is there a working .deb for the Jahshaka video editing programme? I tried to add the repo with it in it, but installing it gives me package errors:

```
The following packages have unmet dependencies:
  jahshaka: Depends: openlibraries but it is not going to be installed
            Depends: libboost-filesystem1.33.1 but it is not installable
            Depends: libglew1 (>= 1.3.1) but it is not installable
            Depends: libopenal0a but it is not installable
            Depends: openlibraries but it is not going to be installed
E: Broken packages

```

---

### Post by k3lt01 on 2009-12-20
> **Zopiac said:**
> Is there a working .deb for the Jahshaka video editing programme? I tried to add the repo with it in it, but installing it gives me package errors:

```
The following packages have unmet dependencies:
  jahshaka: Depends: openlibraries but it is not going to be installed
            Depends: libboost-filesystem1.33.1 but it is not installable
            Depends: libglew1 (>= 1.3.1) but it is not installable
            Depends: libopenal0a but it is not installable
            Depends: openlibraries but it is not going to be installed
E: Broken packages

``` You have a broken package/packages. Nothing will install until you fix it. Go into Synaptic, at the bottom left hand corner click on Custom Filters, and then click on Broken. This should tell you what packages are causing you problems. Fix them and then try to install your debs.

---

### Post by Zopiac on 2009-12-20
> **k3lt01 said:**
> You have a broken package/packages. Nothing will install until you fix it. Go into Synaptic, at the bottom left hand corner click on Custom Filters, and then click on Broken. This should tell you what packages are causing you problems. Fix them and then try to install your debs.

Well I've installed a great many packages by the time I read your post...Also no broken packages are being displayed. Error prevails.

---

