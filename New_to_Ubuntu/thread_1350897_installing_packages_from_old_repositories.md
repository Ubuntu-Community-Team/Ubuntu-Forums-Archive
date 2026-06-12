---
title: "installing packages from old repositories"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by rgb on 2009-12-09
Hi,

I have a fresh installation of Karmic Koala on a desktop and I need libstdc++5 for some applications (mathematica). libstdc++5 is not installed, nor in the karmic repository. 

Of course, I can download libstdc++5 from packages and manually install it. Alternatively, I suppose I could install it from the Jaunty repositories by adding 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
to my sources.list file, in which case it would probably update it regularly. But would that also try to update other common packages from the Jaunty repository rather than Karmic repositories? 

Is it possible to set up software sources so that it updates all other packages from karmic repositories, and this particular package from an older repository?

Thanks

---

### Post by Chesamo on 2009-12-09
Karmic will not try to update from the Jaunty repos, simply because the deb files in the Karmic repos are newer (higher version number).

---

### Post by rgb on 2009-12-09
> **Chesamo said:**
> Karmic will not try to update from the Jaunty repos, simply because the deb files in the Karmic repos are newer (higher version number).

Cool. So, this means my problem will be solved my adding this line to my repositories.

---

### Post by Chesamo on 2009-12-09
I'm not going to commit and outright say "yes", but in theory it should work.

---

