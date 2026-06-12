---
title: "broken dependencies???!!!"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by sstewart207 on 2009-05-04
hello. i was trying to install the drivers for my dial up modem and i was manually installing the packages from windows cuz i dont have internet access on my ubuntu partition...and now theres a red thing that says broken depedencies and if i remove those it says 26 essential packages will be removed and i dont want to f. up my system. :/ idk what to doo

---

### Post by sstewart207 on 2009-05-04
**bump**

---

### Post by NESFreak on 2009-05-04
try find someone with a wired network and run:
```
sudo apt-get check
```

that would be the easiest way to fix it

---

### Post by sstewart207 on 2009-05-04
> **NESFreak said:**
> try find someone with a wired network and run:
```
sudo apt-get check
```

that would be the easiest way to fix it

no can do. there is no ethernet connection where i live.

---

### Post by unutbu on 2009-05-04
Keryx can help you download the needed packages (for Ubuntu) while in Windows. 

See  [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/) for information on how to use Keryx.

See [http://ubuntuforums.org/showthread.php?p=6790061#post6790061](http://ubuntuforums.org/showthread.php?p=6790061#post6790061) for an example use case,

and to download: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by sstewart207 on 2009-05-04
> **unutbu said:**
> Keryx can help you download the needed packages (for Ubuntu) while in Windows. 

See  [http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/) for information on how to use Keryx.

See [http://ubuntuforums.org/showthread.php?p=6790061#post6790061](http://ubuntuforums.org/showthread.php?p=6790061#post6790061) for an example use case,

and to download: [http://keryxproject.org/](http://keryxproject.org/)

does this also download all the dependencies as well??

&& so i have broken dependencies but how do i go about fixing them is what i am asking. :)

---

### Post by unutbu on 2009-05-04
When you use Keryx to download a deb package, it is smart enough to also download all dependent packages that you need.

---

### Post by sstewart207 on 2009-05-04
> **unutbu said:**
> When you use Keryx to download a deb package, it is smart enough to also download all dependent packages that you need.

this is exactly what I need. thank you ^_^

---

### Post by sstewart207 on 2009-05-04
so wouldn't i just reinstall the broken packages with that program? :guitar:

---

### Post by unutbu on 2009-05-04
Yes, that is what I would do.

---

### Post by sstewart207 on 2009-05-04
thanks, unutbu! :)

---

