---
title: "Switching from Ubuntu to Kubuntu"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by jotremba on 2009-01-24
What is the best way to do this???
Thank you,
James

---

### Post by SOULRiDER on 2009-01-24
IMHO reinstall. But you can also install the kubuntu-desktop package.
```
sudo aptitude install kubuntu-desktop
```
Then when you are goign to log in, in the session menu you can select KDE. Remember you KDE and GNOME applications with show up on both enviroments.

---

### Post by purplepaint on 2009-01-24
I can't see any reason to reinstall.  I switched for a while using apt-get and it was fine, but if you want to switch completely you can just follow this guide rather than reinstall: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

EDIT: Make sure you install kubuntu-desktop before removing the Ubuntu packages.

---

### Post by yeats on 2009-01-24
Yes - the easiest way is definitely to just install the kubuntu-desktop metapackage.  The only side effect is the need to edit your menus in each environment (for cleanliness' sake), as all programs appear in menus by default.

---

