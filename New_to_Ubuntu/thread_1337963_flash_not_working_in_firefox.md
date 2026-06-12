---
title: "flash not working in firefox"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by lems on 2009-11-25
This happened after installing the updates. flash works for opera and chrome however. Anyone know why?

---

### Post by wojox on 2009-11-26
Try reinstalling:

```

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

```

---

