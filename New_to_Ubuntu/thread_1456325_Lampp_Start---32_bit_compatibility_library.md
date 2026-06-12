---
title: "Lampp Start---32 bit compatibility library"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by marp on 2010-04-17
**Lampp Start---32 bit compatibility library**             
                                                                My Processor is    x86 Family 15 Model 6 Stepping 5 Genuine Intel ~2992 Mhz



 Below is the message I received after trying to do the Lampp start in ubuntu 9.10.



sudo /Downloads/lampp/lampp start
XAMPP is currently only availably as 32 bit application. Please use a 32  bit compatibility library for your system.




If someone could assist me that would be great.

---

### Post by 3rdalbum on 2010-04-17
```
sudo apt-get install ia32-libs
```

ia32-libs is the 32-bit compatibility library.

---

### Post by mran on 2013-03-07
> **3rdalbum said:**
> ```
sudo apt-get install ia32-libs
```

ia32-libs is the 32-bit compatibility library.

Worked for me

---

### Post by QIII on 2013-03-07
Thank you for sharing.

This thread is very old.

*Thread** closed.***

---

