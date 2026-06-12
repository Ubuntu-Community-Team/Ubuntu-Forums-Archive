---
title: "Error using update manager"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Peterfc on 2009-01-07
HI all

Using Update manager i get two error messages the first is after i installed wine. Wine has not shown up in the application section it has on another machine.


W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263



The second error is a list of Openoffice programs

All start 

openoffice.org-base-core
openoffice.org-calc
openoffice.org-core
openoffice.org-draw
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-math


Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.


[http://ubuntuforums.org/attachment.php?attachmentid=99051&stc=1&d=1231343789](http://ubuntuforums.org/attachment.php?attachmentid=99051&stc=1&d=1231343789)

Thanks for reading this thread

---

### Post by namdung on 2009-01-07
In a terminal (applications -> accessories -> terminal)
```
sudo apt-get update
```

and try updating ur system again.

It is safe to upgrade as long as you trust your source of packages.

---

