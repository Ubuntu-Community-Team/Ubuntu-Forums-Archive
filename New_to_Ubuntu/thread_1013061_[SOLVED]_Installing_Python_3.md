---
title: "[SOLVED] Installing Python 3????"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Soriano on 2008-12-16
Hi all this is most likely a simple question.

I want to install python 3 on my system since I am working on learning python on windows and am using python 3.  Now I know that on 8.10 we are still on Python 2.6xx (I think).  

My question is if I go and install Python 3 through synaptic is the older version of python going to still be there?  I am concerned since programs like Exaile are python programs and it would be my guess that they still require the older python 2.xx interpreter.

I may be way off here but any help or literature would be great!

Thanks in advanced!

---

### Post by Locke_99GS on 2008-12-16
Installing python3.0 from the repo's will not override your existing python install. I have both.

Note that when building scripts with python3, you should point to *python3.0*, rather than *python*, with the first line's shebang.

---

### Post by Locke_99GS on 2008-12-16
edit: double post

---

### Post by mbsullivan on 2008-12-16
If it works the same way it used to, then you can have multiple versions installed simultaneously.

Python2.x will put its libraries in /usr/lib/python2.x. Likewise, Python 3 (I'm assuming) will be in /usr/lib/python3.0 (or something similar).

There will be separate binaries for every version of Python under /usr/bin, such as python2.4, python2.5, etc.

The binary that you generally call for the Python interpreter (/usr/bin/python) is a symlink that points to the newest version of python. You can manually change it to point to whichever version you want, or explicitly call the version of Python that you need.

To see where your /usr/bin/python currently points, run:

```
ls -al /usr/bin/python
```

Mike

---

### Post by snova on 2008-12-16
Just install the 'python3' package. It won't break anything.

Also perhaps consider the 'python3-doc' package.

---

### Post by Soriano on 2008-12-16
Ok great thanks everyone for the replies!

---

