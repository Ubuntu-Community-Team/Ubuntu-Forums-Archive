---
title: "How to install PyQT to access the hp toolbox?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by kramer65 on 2008-12-05
Hello,

I've got an HP printer for which I want to read out how much ink I have left. Appearently you can do that using the hp toolbox which you can access by running 
```
hp-toolbox
```

It then gives me this error:
```
error: PyQt not installed. GUI not available. Exiting.
warning: Qt/PyQt initialization failed.
error: hp-toolbox requires GUI support. Exiting.
```

How do I install this PyQt thing? Could anybody help with that?  :roll:

---

### Post by ajgreeny on 2008-12-05
```
sudo apt-get install hplip-gui
``` should help out.  The toolbox is a part of that package.

---

### Post by kramer65 on 2008-12-05
That is great! Works like a charm!

Also, I didn't know that hp had such a good toolbox for their printers for linux.

Thanks again!

---

### Post by raelga on 2011-01-26
Only needs to install python-qt4:

```
#sudo aptitude install python-qt4
```

---

