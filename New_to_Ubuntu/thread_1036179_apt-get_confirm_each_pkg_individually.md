---
title: "apt-get: confirm each pkg individually?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by minsf on 2009-01-10
when running "sudo apt-get upgrade" (following "sudo apt-get update" of course) i am asked to confirm upgrading/installing a bunch of packages.
If I just want to upgrade/install some of them, how do i confirm the desired packages individually?

I can't seem to find the right option in the apt-get manual. 

I guess what I am trying to do is to not install the nvidia update, as i am satisfied with my installation. For this, it seems that "sudo apt-get upgrade --no-install-recommends" will help, but not completely solve the problem; since, in the future i may want to install one of the recommended packages.

---

### Post by Norm24 on 2009-01-10
Uncheck the box next to the undesirable upgrades?

Not to sound condescending but why are you asking?The update manager very clearly gives you the option of upgrading individual updates.

---

### Post by minsf on 2009-01-10
thanks, i am familiar with the gui but i like updating/upgrading from the command line, and then i cannot uncheck a box. i hope i dont need a gui tool just because i dont want to upgrade one of the packages...

---

### Post by JoshuaRL on 2009-01-10
You could always upgrade a specific package.  I think it goes:
```

sudo apt-get upgrade the-package-I-want

```
But to be honest, I haven't tried that in a long while.

---

### Post by handydan918 on 2009-01-10
If you are just trying to avoid one or two specific upgrade, try [pinning the package version]("https://help.ubuntu.com/community/PinningHowto").

---

