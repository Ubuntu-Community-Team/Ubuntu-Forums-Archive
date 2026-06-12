---
title: "Is necessary to remove these packages."
date: 2009-04-05
forum: New to Ubuntu
---

### Post by herbertg on 2009-04-05
Is it necessary to remove these packages? If I need to how should I do this.


The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 libarts1c2a kdelibs4c2a libartsc0 liblualib50 libqt3-mt
  kdelibs-data liblua50 libaudio2
Use 'apt-get autoremove' to remove them.

Thanks

---

### Post by freak42 on 2009-04-05
these are libraries.. you probably once installed an application that needed them, and then uninstalled it again, so now they are on your system but nothing uses them.

You don't 'need' to remove them.. however they use up space on your hd for nothing.

How you remove them? The solution is already in your post.

---

### Post by |Mitch| on 2009-04-05
> **herbertg said:**
> If I need to how should I do this.


sudo apt-get autoremove

---

### Post by CLomax on 2009-04-05
I'd remove them otherwise you'd have unneeded files floating around.

[PHP]sudo apt-get autoremove[/PHP]

---

