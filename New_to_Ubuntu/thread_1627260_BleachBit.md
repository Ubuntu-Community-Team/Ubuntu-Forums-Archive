---
title: "BleachBit"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by olddai on 2010-11-21
I have just come across a program called BleachBit that's supposed to clean up Ubuntu. Would like to know if any forum members have used it and their opinon of the program please.

You can find BleachBit [http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

---

### Post by TeoBigusGeekus on 2010-11-21
I'm using it for a long time and I can highly recommend it.

---

### Post by rburkartjo on 2010-11-21
old, i also have been using for sometime. just make sure what you click to use or you can wipe out all your bookmarks. i use it at least once a week.

---

### Post by olddai on 2010-11-21
I have used it just the once and it threw up a lot of errors. Is it best to use it as root?

---

### Post by TeoBigusGeekus on 2010-11-21
> **olddai said:**
> I have used it just the once and it threw up a lot of errors. Is it best to use it as root?
Both ways: as user and root.
What kind of errors did you have?

---

### Post by olddai on 2010-11-21
They were errors generated because Bleachbit didn't have access to certain files

---

### Post by Frogs Hair on 2010-11-21
I use BeachBit as administator and have no problems  ,   just be sure you know what your cleaning . The  latest version can be found at the website in the forum of .deb package.[U]
[/U]

---

### Post by TeoBigusGeekus on 2010-11-21
> **olddai said:**
> They were errors generated because Bleachbit didn't have access to certain files

Don't worry about it.
Run
```
gksu bleachbit 
```
in order to give it access to these files.

---

### Post by olddai on 2010-11-22
Cheers!

---

### Post by Andrew.Z on 2010-11-23
> **olddai said:**
> I have used it just the once and it threw up a lot of errors. Is it best to use it as root?

Running as root is needed only for certain options, most of which are under the System category.  On the other hand, clean your web browser, trash, etc using non-root privileges.

---

