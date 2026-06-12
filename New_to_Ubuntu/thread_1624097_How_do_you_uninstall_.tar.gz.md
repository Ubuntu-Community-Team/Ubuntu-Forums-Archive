---
title: "How do you uninstall .tar.gz"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by ubunt12 on 2010-11-17
Hi, I recently installed Python-3.1.2.tar.gz from the official python website and was wondering
if anyone could tell me the command for uninstalling it.
I already tried going into the python-3.1.2 directory and typing:

make uninstall

but output:

make: *** No rule to make target `uninstall'.  Stop.

I installed it by typing:
./configure
make
make test
make install

please can someone help me??
Thanks in advance.

---

### Post by TeoBigusGeekus on 2010-11-17
There should be an uninstall script in the folder.
If you don't have it anymore, download it again.

---

### Post by asmoore82 on 2010-11-17
This is amusing that all the good advice says
```
sudo make uninstall
```
and [COLOR="Red"]**Python really doesn't have one!**[/COLOR]

Assuming you didn't change any options when you config'd and make'd,
you could get away with this:
```
sudo rm -rf /usr/local/bin/python3* /usr/local/bin/pydoc3 /usr/local/lib/python3.1 /usr/local/include/python3.1 /usr/local/lib/pkgconfig/python3.pc /usr/local/lib/libpython3.1.a
```
^Proceed with extreme caution around `sudo rm -rf ...` !!!

---

### Post by ubunt12 on 2010-11-17
thanks, i know i ive just read that malicious commands post : )

---

