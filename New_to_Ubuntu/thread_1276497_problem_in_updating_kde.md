---
title: "problem in updating kde"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by gkraju on 2009-09-27
hi i have installed ubuntu 9.04 and installed kde through synaptic package manager so kde 4.2.2 is installed. i updated it to 4.3.but now in kde i cant close any application since the title bar is missing and desktop has changed so please help me thanks.

---

### Post by yeats on 2009-09-27
there is a hidden directory in your /home/[*your username* directory called .kde.  You can rename that, then log out and log back in.  You will lose your settings from the previous .kde folder, but at least things will work as they should.

---

### Post by gkraju on 2009-09-27
> **chrissharp123 said:**
> there is a hidden directory in your /home/[*your username* directory called .kde.  You can rename that, then log out and log back in.  You will lose your settings from the previous .kde folder, but at least things will work as they should.

thanks for your reply 
but it doesnt work.
**after update KDE version is changed to  4.3.1. i forgot to mention that in my post  **

---

### Post by ~sHyLoCk~ on 2009-09-27
Type ```
kwin --replace&
```

---

### Post by sandyd on 2009-09-27
turn off compositing?

---

### Post by gkraju on 2009-09-27
> **~sHyLoCk~ said:**
> Type ```
kwin --replace&
```

keyboard is not working in terminal alone i dont know why .
but keyboard is working on other applications

---

### Post by sandyd on 2009-09-27
press alt-f2 and type kwin --replace into the box that appears in the middle of the screen

---

