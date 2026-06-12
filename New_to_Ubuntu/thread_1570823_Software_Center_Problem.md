---
title: "Software Center Problem"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Jolicoeur on 2010-09-08
Tried to install software using the Software Center, computer crashed before the install could complete.  When computer came back on again and I tried to install the program and then any other program this popped up: 

"Previous installation hasn't been completed.  The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

Anybody know how to "repair" this?  I cannot load any software due to this.  Thanks.

---

### Post by NightwishFan on 2010-09-08
Open a terminal and run:
```
sudo apt-get -f install
```

---

### Post by andrewthomas on 2010-09-08
try to 
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sandyd on 2010-09-08
> **NightwishFan said:**
> Open a terminal and run:
```
sudo apt-get -f install
```
[offtopic]
hey, you got only 181 posts until you get your custom username tag :D [/code]

---

### Post by NightwishFan on 2010-09-08
Yeah. Since the fire I took a break from posting a lot in the help forums, now that I am situated I am working on it again. :)

---

