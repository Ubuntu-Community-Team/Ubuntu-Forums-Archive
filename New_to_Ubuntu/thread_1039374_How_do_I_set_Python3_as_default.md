---
title: "How do I set Python3 as default?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by MockY on 2009-01-14
I installed python 3.0 and can do some magic interactively in the interpreter. But the system still uses 2.5.2 as default, and therefore Geany is still using 2.5.2.
How do I set Python 3 as default?

---

### Post by ken22 on 2009-01-15
Hi,

Python3 as default may introduce incompatibilities. To install```
sudo apt-get install python3
```

Then type ```
python3
``` as your interpreter

---

### Post by MockY on 2009-01-19
I did not install python via the repository since it only has the RC version. I downloaded and installed it from the official site, so I don't know if I want to venture into executing your commands, in fear of breaking it.
I have gotten it to work in Geany now, and if I want to use the terminal instead, I simply type python3.0. 
Thanks for your help though.

---

### Post by Paul Miller on 2009-01-19
I actually do not recommend setting Python 3 as the default.  Python 3 introduces some incompatibilities with Python 2.x code which may cause parts of your system to fail or behave in a way you do not want.

---

### Post by ken22 on 2009-01-20
> **Paul Miller said:**
> I actually do not recommend setting Python 3 as the default.  Python 3 introduces some incompatibilities with Python 2.x code which may cause parts of your system to fail or behave in a way you do not want.

I agree for the reason you outline. I've edited my post.

---

### Post by MockY on 2009-01-23
Well, I don't need Python 3 to be default. As long as I can program with it in Geany, I'm fine. And since I now can, problem solved.

---

### Post by tripwire45 on 2009-01-25
> **ken22 said:**
> Python3 as default may introduce incompatibilities. To install```
sudo apt-get install python3
```
May I ask which repository you're using? I've tried Googling this and searching both this forum and Python.org, and I can't see what repository I should add to /etc/apt/sources.list for Hardy Heron.

---

### Post by ken22 on 2009-01-26
It's in the Intrepid repo. I don't know of a backport to Hardy.

---

### Post by tripwire45 on 2009-01-26
Thanks for the reply. Probably why I can't find anything about it for Hardy. ;-)

Cheers.

---

### Post by kindofabuzz on 2009-02-10
> **tripwire45 said:**
> Thanks for the reply. Probably why I can't find anything about it for Hardy. ;-)

Cheers.

Only RC1 is in Intrepid repos. Just get the source from python.org and compile it yourself if you want the final version.

---

