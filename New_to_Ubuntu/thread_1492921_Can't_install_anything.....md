---
title: "Can't install anything...."
date: 2010-05-25
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-05-25
Fresh install of 9.10

sudo apt-get install ubuntu-restricted-extras  "package not found"


Downloading it from the Ubuntu website  "Package not found"


There is no install button option in the software center...

---

### Post by Ozymandias_117 on 2010-05-25
Do you have Multiverse and Universe repositories active (System -> Admin -> Software Sources)? Have you run sudo aptitude update?

---

### Post by 3rdalbum on 2010-05-25
Check that the first four checkboxes in System > Administration > Software Sources are ticked. Without them, the system doesn't know of the repositories where it can get software.

If they are already ticked, then you may need to reload the package list, which can be done from System > Administration > Synaptic Package Manager. Hit the Reload button and the contents of the Ubuntu repositories will be scanned. Then you'll be able to install ubuntu-restricted-extras.

---

