---
title: "Two Desktop Enviornments?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by walruspanzer on 2009-07-27
I am running Ubuntu 9.04 on my Dell Inspiron (dual boot Ubuntu/XP). Was wondering if it were possible to install Kubuntu 9.04 on the same root partition as my Ubuntu and be able to select which environment I want to use in the GRUB menu that pops up asking me if i want to use windows or ubuntu. If so, how do I go about doing this? Also, I have two monitors - will this be a problem? Appreciate  any feedback thanks!

---

### Post by halitech on 2009-07-27
very easy to do

```
sudo apt-get install kubuntu-desktop
```then log out and you can change the DE to KDE

```
sudo apt-get install xubuntu-desktop
``` and you can select it if you want.

Not sure on the dual monitors

---

