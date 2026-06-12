---
title: "How can i update kde software that be installed on ubuntu"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by BamsTia on 2009-06-23
i'm very beginner.....
i'm use Ubuntu Ultime Edition 1.9 
How can i update ( maintenance ) kde software that be installed on ubuntu 8.04 or to add kde sources to ubuntu software sources......
( i'm very sorry if i can't use English well ):confused::confused::confused:

---

### Post by frup on 2009-06-23
KDE should be in the same repositories, it is in vanilla Ubuntu.

You install it by finding the package Kubuntu_Desktop.

Update manager will take care of maintaining updates for you. If you want newer releases than Ubuntu shipped with you should look for a launchpad ppa, but it may be best to wait until you are slightly more familiar with Ubuntu.

---

### Post by tarps87 on 2009-06-23
Just to add the the post above, if you install any programs from the repository (using apt, synaptic, add/remove, or whatever you call it) it will be maintained for you.

---

### Post by BamsTia on 2009-07-03
i'm very sorry Master.... q still cann't update my K3b on Ubuntu 8.04... here are screenshots....

---

### Post by tarps87 on 2009-07-06
It is in the backports section, this is probably as it is only a recent update and there for not currently supported (it needs testing), anyway to update it you will need to go into System -> Administration -> Software Sources go to the update tab and select Unsupported updates (*version*-backports)

---

### Post by BamsTia on 2009-07-06
i have do this at the beginning..... but still cann't be updated........

---

### Post by tarps87 on 2009-07-07
You can try updating and then installing k3b again

```
sudo apt-get update
sudo apt-get install k3b
```

If this does not work it may just be that one of its dependences hasn't been updating in the repository so k3b can not update, if this is the case it will update as soon as all its dependences are updated

---

