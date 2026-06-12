---
title: "Installing python"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by sagmate on 2010-08-15
I'm need some assistance on installing python 2.7 from the command line. I think apt-get is used but I'm not sure how to write the command.

---

### Post by themusicalduck on 2010-08-15
I can't find python 2.7 in synaptic.. only 2.6 or 3.0.

By the way, you can search for packages from the command line by using ```
sudo apt-cache search <searchterm>
```then use ```
sudo apt-get install <packagename>
``` to install a package.

---

### Post by fatality_uk on 2010-08-15
[http://packages.ubuntu.com/lucid/python/](http://packages.ubuntu.com/lucid/python/)

BIG +1 for apt-cache search (You don't need to do this as root/sudo by the way) a simple **apt-cache search <searchterm>** will suffice. Then you need sudo to install.

---

