---
title: "cant intsall or uninstall software"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by ricohott on 2010-08-06
every time I try and install or uninstall a piece of software I get
"The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software"

---

### Post by Darkness Des on 2010-08-06
On the top of the screen, click Applications. Under Accessories, open the Terminal. Post the output of this command.
```
sudo apt-get install -f
```
It will ask for your password, but won't show any characters (such as dots or stars) when you enter it.

---

### Post by uylug on 2010-08-06
See if this works?

```
sudo apt-get install -f
```

---

### Post by ricohott on 2010-08-06
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by 3rdalbum on 2010-08-07
So   what   happens   when   you   do   that?   Put   it   in   the   terminal.

---

