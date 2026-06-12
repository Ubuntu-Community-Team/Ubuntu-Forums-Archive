---
title: "how to uninstall a debian package?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by supermooshman on 2009-05-10
A few days ago I installed the demo of World of Goo.

Now I was wondering how to uninstal this?

Since I cannot find it with Synaptics or Applications-Add/Remove...
Is it okay for me to go into my /usr/games folder and delete this or is there more to it?


a guitar solo for the one who can help me
:guitar:

---

### Post by taurus on 2009-05-10
If you used **dpkg -i package_name** to install the package, then you can use **dpkg -r package_name** to remove the package from your machine.

Applications -> Accessories -> Terminal
```
sudo dpkg -r package_name
```

---

