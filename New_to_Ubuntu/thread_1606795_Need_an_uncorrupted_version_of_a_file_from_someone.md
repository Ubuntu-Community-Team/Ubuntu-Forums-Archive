---
title: "Need an uncorrupted version of a file from someone. Any helpers?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2010-10-26
I need someone's modules.dep from a 10.10 64 bit installation. Any chance of that happening?

Thanks in advance!

---

### Post by Quackers on 2010-10-26
Where is it? I tried a search but came up with nothing.

---

### Post by NightwishFan on 2010-10-26
It should be in this package somewhere. You can open .deb files with file-roller or just right click in Nautilus open with archive manager.
[http://packages.ubuntu.com/maverick/user-mode-linux](http://packages.ubuntu.com/maverick/user-mode-linux)

Edit: Directory is: /usr/lib/uml/modules/2.6.35.1/modules.dep

---

### Post by pHreaksYcle on 2010-10-26
/lib/modules/2.6.35-22-generic/

---

### Post by Quackers on 2010-10-26
If you still want it, if you pm me an email address I can send a copy.

---

### Post by srs5694 on 2010-10-27
Type the following command to generate a fresh modules.dep file for your system:

```

sudo depmod -a

```There should be no need to obtain one from somebody else.

---

