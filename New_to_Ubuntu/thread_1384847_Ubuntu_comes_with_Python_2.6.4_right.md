---
title: "Ubuntu comes with Python 2.6.4 right?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-01-18
If I'm a developer, should I install Python 3.x? I'm not sure if it's advisable to install both of them together.

---

### Post by Temposs on 2010-01-18
Yes, Ubuntu 9.10 comes with  python 2.6.4. Installing python 3.0 will not cause any conflict, especially if you install it from the repositories(let me know if you need help with that).

After installing python 3.0, the python command should still be linked to 2.6.4. To use python 3.0, you would need to explicitly use the command python3.0. To explicitly use python 2.6.4, you would use the python2.6 command.

---

### Post by Bios Element on 2010-01-18
Actually IIRC the command is "python3". But you were otherwise correct. Actually the first thing I do is install python 3 alongside python 2.6.

---

### Post by raydeen on 2010-01-18
There shouldn't be a problem with having both installed. I have 2.6 and 3.0 installed and call them with separate instances of IDLE. Just look for 3.x in the repos and you should be fine. ;)

---

### Post by oldfred on 2010-01-19
Whatever you do do not uninstall 2.6. Many parts of Ubuntu rely on python 2.6 and if you uninstall python 2.6 it will uninstall most of your Ubuntu system and just about required a fresh reinstall of the entire system.

---

