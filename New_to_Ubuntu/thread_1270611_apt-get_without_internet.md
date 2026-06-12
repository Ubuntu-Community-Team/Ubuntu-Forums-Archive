---
title: "apt-get without internet"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by garyed on 2009-09-19
Is it possible to use apt-get without it getting software from the internet?
I have a fast internet connection now so downloading is not a problem.
What I want to do is download whatever programs & dependencies I want from the repos & copy them to a DVD then install them through apt-get or whatever way would work. This way I could use the CD on another computer Ubuntu to install the software without having to download again. It especially would be good if the version of Ubuntu becomes no longer supported & the dependencies are hard to get.
If so any ideas how to?

---

### Post by aesis05401 on 2009-09-19
```
man apt-cdrom
```

---

### Post by sandyd on 2009-09-19
apt-on-cd

---

### Post by garyed on 2009-09-19
> **aesis05401 said:**
> ```
man apt-cdrom
```

1 -Ok does that mean I would do something like this:

```
apt-cdrom install ubuntustudio-audio
```
to install the program ubuntustudio-audio from a CD?

2 -My other question is how do I download the program & all dependencies needed to my HD so I can put it on a CD?

---

### Post by sandyd on 2009-09-19
get internet access on another ubuntu computer.

make a apt-on-cd there.

---

### Post by wojox on 2009-09-19
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by garyed on 2009-09-19
Thanks,
I'll try the apt-on cd.

---

