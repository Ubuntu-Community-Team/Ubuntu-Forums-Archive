---
title: "How do I change the sound theme in 9.10?"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Monrizzy on 2010-01-17
Hi folks,
I downloaded a .tar.gz sound theme from [www.gnome-look.org](www.gnome-look.org) and I'm trying to figure out how to apply it.  So far I've had no luck.  Does anyone know how that's done?

---

### Post by warfacegod on 2010-01-17
System> Preferences> Sound

---

### Post by Monrizzy on 2010-01-17
> **warfacegod said:**
> System> Preferences> Sound

I'm not seeing a place to install a new theme in there though.

---

### Post by nick_goodfate on 2010-01-17
copy the file you downloaded in > /usr/share/sounds
if it doesnt work , you may need to extract the file you downloaded and put it in sound folder ...
then change the theme : System> Preferences> Sound

---

### Post by warfacegod on 2010-01-17
I'm some what guessing here but this won't break your system if it doesn't work, it simply won't work. Open a terminal and:

```
cd/place/where/your/theme/is
```

It's probably in downloads so an exapmle is:

```
cd /home/yourusername/downloads
```

Hit enter. Then.

```
sudo apt-get install exactnameofyourfile
```

---

