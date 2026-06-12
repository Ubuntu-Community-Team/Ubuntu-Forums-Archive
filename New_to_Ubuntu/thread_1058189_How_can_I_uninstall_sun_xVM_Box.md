---
title: "How can I uninstall sun xVM Box ?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by asel_ on 2009-02-02
Hi, How can I uninstall sun xVM Box ? using apt or anything else using text mode . Thank you in advance

---

### Post by jbrown96 on 2009-02-02
If you installed it from synaptic or downloaded a .deb to install it, then yes you can remove it in Synaptic. Just search for it and choose to completely remove it.

---

### Post by asel_ on 2009-02-02
> **jbrown96 said:**
> If you installed it from synaptic or downloaded a .deb to install it, then yes you can remove it in Synaptic. Just search for it and choose to completely remove it.

I'm asking for text mode NOT graphical

---

### Post by jbrown96 on 2009-02-02
It depends on how you installed it, but if you try ```
sudo apt-get remove virtualbox
``` and then hit tab a couple of times it will show all matching packages.

---

### Post by asel_ on 2009-02-02
> **jbrown96 said:**
> It depends on how you installed it, but if you try ```
sudo apt-get remove virtualbox
``` and then hit tab a couple of times it will show all matching packages.


Hi, I just downloaded the sun xVM Box from sun's site with .deb extention and I double clicked on it ,that is all . But Now I cannot boot my ubuntu , and I want to remove it using recovery mode .

---

### Post by jerome1232 on 2009-02-02
I believe that should figure out the name of the installed package

```
dpkg --get-selections | grep install | grep virtualbox
```

```
sudo apt-get autoremove *packagename*
```

---

