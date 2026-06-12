---
title: "error while installing any software through terminal..."
date: 2010-07-09
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-09
hi!
every time when i go to install anything through terminal, it ends with the following results.......



"Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-23-genericE: Sub-process /usr/bin/dpkg returned an error code (1)"





though everytime the installation get completed easily....

please tell me how to get rid of this problem?
thanks!!!!!

---

### Post by mcduck on 2010-07-09
Try running the following commands in a terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
```
(The first command updates information abut available packages, the second one downloads and installs possible updates, and the third one tries to fix any broken packages.)

---

