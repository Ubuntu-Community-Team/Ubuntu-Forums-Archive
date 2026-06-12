---
title: "What is a PPA file and how do you install it?"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by TAspr on 2011-06-04
[SIZE=2]**Popper 0.28 Readme ================================================ Beginning with this release, the Popper team will deploy this software as a package in a**** PPA instead of a DEB file. Popper 0.28 is available for Ubuntu 10.10 and Ubuntu 11.04.  How to install? ================================================ 1. uninstall any older version of Popper 2. add a new PPA to your package sources in    Software-Center. The name of the PPA is:        ppa:ralf.hersel/rhersel-ppa     3. install Popper 0.28 in Software-Center**[/SIZE]

---

### Post by nothingspecial on 2011-06-04
Open a terminal and type
```

sudo add-apt-repository ppa:ralf.hersel
```

---

### Post by wolfen69 on 2011-06-04
> **nothingspecial said:**
> Open a terminal and type
```

sudo add-apt-repository ppa:ralf.hersel
```

Then you can search for Popper in the software center or synaptic.

---

### Post by Frogs Hair on 2011-06-04
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

[http://www.omgubuntu.co.uk/2011/05/the-evolution-of-the-personal-package-archive-system/](http://www.omgubuntu.co.uk/2011/05/the-evolution-of-the-personal-package-archive-system/)

---

### Post by nothingspecial on 2011-06-04
Wolfen is right, it is much better to install stuff through the 'official ubuntu repositories'.

A PPA is another repository, a source of software.

.....I'm finding it difficult to think how to explain this......

Ubuntu comes with a big box of applications that you can install, that have been reviewed and tested. You can be absolutely sure the stuff in that box is legitimate software.

PPAs are other people's boxes of software. The software may be more up to date, but it has not been tested. Therefore, installing stuff from those boxes (PPAs) may break your system.

You have to judge weather or not the benefits of using a third party/latest package is worth the risk.

I didn't explain that very well but I hope you get the point.

---

### Post by TAspr on 2011-06-04
> **nothingspecial said:**
> Wolfen is right, it is much better to install stuff through the 'official ubuntu repositories'.
 
A PPA is another repository, a source of software.
 
.....I'm finding it difficult to think how to explain this......
 
Ubuntu comes with a big box of applications that you can install, that have been reviewed and tested. You can be absolutely sure the stuff in that box is legitimate software.
 
PPAs are other people's boxes of software. The software may be more up to date, but it has not been tested. Therefore, installing stuff from those boxes (PPAs) may break your system.
 
You have to judge weather or not the benefits of using a third party/latest package is worth the risk.
 
I didn't explain that very well but I hope you get the point.
 
I do for sure, and thank you.

---

