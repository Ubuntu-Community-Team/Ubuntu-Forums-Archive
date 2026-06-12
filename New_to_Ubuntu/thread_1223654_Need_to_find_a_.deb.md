---
title: "Need to find a .deb"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by StupendousMan on 2009-07-26
I have installed Jaunty and everything went well until I came to getting my modem set up. I have installed and used scanModem, slmodemd, wvdial, wvstreams, etc. In reading through the scanModem DOCs I find that I need to compile drivers and headers[?], but in order to do this I need to download and install **kernel-header-2.6.28-11-generic.deb**. Where do I get this? I can't use the repos 'cuz I don't have an internet connection through ubuntu. 

I really want to get this up and running, because I am so over Windows. The antivirus caught some infected files in iTunes on Friday--and this is NOT the first time. Yup, Mr. Gates can keep his virus magnet; I prefer to be less of a target. :)

---

### Post by wojox on 2009-07-26
In the terminal:

```
uname -a
```

You should already have a higher version installed.

---

### Post by mike555 on 2009-07-26
If your trying to use dialup you should just get an external serial modem that works with Ubuntu , check the hardware forums.

---

### Post by Liolikas on 2009-07-26
It is somewhere it this site:
[http://archive.ubuntu.com/](http://archive.ubuntu.com/)

---

### Post by scorp123 on 2009-07-26
> **StupendousMan said:**
> but in order to do this I need to download and install **kernel-header-2.6.28-11-generic.deb**. Where do I get this?  ```
sudo apt-get install build-essential
```

... that should download compiler packages, header files and what not ... all the stuff you'd need to build programs, drivers and so on.

---

### Post by markharding557 on 2009-07-26
suggest you post separarate thread to get your internet working this is essential on an o/s which uses internet repositories

---

