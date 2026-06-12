---
title: "downloaded chrome package not found"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by BigDope on 2010-09-20
hi, i downloaded and installed chrome {not chromium} from google's site a few days back and then removed it via the package manager typing "remove completely"

today i downloaded chrome again, when the installer came up, i closed firefox and clicked install package. i then got the error as "package not found"

any idea on what might have happened ?

---

### Post by frup on 2010-09-20
I'd start by opening synaptic or software centre and seeing if chrome is in fact installed, if not try again. If it is try removing again and re-installing.

---

### Post by BigDope on 2010-09-20
> **frup said:**
> I'd start by opening synaptic or software centre and seeing if chrome is in fact installed, if not try again. If it is try removing again and re-installing.

chrome aint installed. i checked in synaptic

---

### Post by arubislander on 2010-09-20
> **BigDope said:**
> today i downloaded chrome again, when the installer came up, i closed firefox and clicked install package. i then got the error as "package not found"

any idea on what might have happened ?

What happened is that you closed firefox and it cleaned up it's  temporary files, including the package you just downloaded. Try installing the package without closing firefox next time around.

---

### Post by TonKi on 2010-09-20
Firefox deleted the downloaded file, keep firefox open or save it.

Chrome installs (if I remember right) a Package Archive, so you should be able to install it by searching synaptic and install it again.

---

### Post by BigDope on 2010-09-20
> **arubislander said:**
> What happened is that you closed firefox and it cleaned up it's  temporary files, including the package you just downloaded. Try installing the package without closing firefox next time around.

> **TonKi said:**
> Firefox deleted the downloaded file, keep firefox open or save it.

Chrome installs (if I remember right) a Package Archive, so you should be able to install it by searching synaptic and install it again.


thank you guys, that was the problem and its solved now !

---

