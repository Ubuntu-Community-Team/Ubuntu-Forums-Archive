---
title: "hp photosmart c410a"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by davecec on 2011-01-26
I am an absolute novice to Linux. I have a new HP c410a all-in-one  printer scanner. I can make the printer work, but not the scanner. Can  anyone help?

---

### Post by joshthechamp14 on 2011-01-26
[http://www.sane-project.org/](http://www.sane-project.org/)

Try this

---

### Post by rosswmcgee on 2011-01-26
The HP photosmart c410a is not listed there, what other options are there?? Just trying to help.

---

### Post by sandyd on 2011-01-26
> **davecec said:**
> I am an absolute novice to Linux. I have a new HP c410a all-in-one  printer scanner. I can make the printer work, but not the scanner. Can  anyone help?
one word: hplip.

---

### Post by rosswmcgee on 2011-01-26
It is installed in synapatic package manager, already.

---

### Post by sandyd on 2011-01-27
run
```

hp-scan
```

---

### Post by Sef on 2011-01-28
Read this on [Launchpad]("https://bugs.launchpad.net/hplip/+bug/631028").

In short, it is a new printer and the hplip driver used does not have it in. It will be in the next ubuntu. If you want to use it now, you can download the latest hplip driver.

---

### Post by sandyd on 2011-01-28
> **Sef said:**
> Read this on [Launchpad]("https://bugs.launchpad.net/hplip/+bug/631028").

In short, it is a new printer and the hplip driver used does not have it in. It will be in the next ubuntu. If you want to use it now, you can download the latest hplip driver.
ah.
that explains why I already have it... (I use gentoo....)

---

### Post by rosswmcgee on 2011-01-30
The person involved lasted about a week with Ubuntu, new to it, decided to buy a win7 machine. 

You can't win them all.

---

