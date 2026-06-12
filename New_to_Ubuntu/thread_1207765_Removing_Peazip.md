---
title: "Removing Peazip?"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Sexraider on 2009-07-08
Well, I downloaded this .deb thinking it would open .7z files then I realized There was already a package in Ubuntu I had to install.
I installed that and now, I'm not sure on how to uninstall Peazip.

---

### Post by frunns on 2009-07-08
First off, installed packages in Ubuntu won't clutter the computer as much as in Windows, as long as they're not huge. And uninstalling it should be fairly easy...
Try
```
sudo apt-get purge peazip
```
(Tab for automatic completion if the package isn't exactly named 'peazip').

---

