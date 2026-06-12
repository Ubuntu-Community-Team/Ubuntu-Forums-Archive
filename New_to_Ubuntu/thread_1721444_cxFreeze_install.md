---
title: "cxFreeze install"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by J91321 on 2011-04-04
Hi, I'm trying to install cx_freeze when I run ```
sudo python3 setup.py build
``` I get an error
```
/usr/bin/ld: cannot find -lffi
collect2: ld returned 1 exit status
error: command 'gcc' failed with exit status 1

```
I read somwhere that I need to install libssl-dev, I installed that but I still get that error, is there something else I should install?

---

### Post by Dutch70 on 2011-04-04
Why don't you just use synaptic to install it?

From the cli, I think it would be...
```
sudo apt-get install cx-freeze
```

If I understand your question correctly, you said your trying to install it.

---

### Post by J91321 on 2011-04-04
Yes I know I did that but that installed cx-Freeze for Python 2.6 but I need it for Python 3.1
Edit: Sloved it, I had to install libffi-dev

---

