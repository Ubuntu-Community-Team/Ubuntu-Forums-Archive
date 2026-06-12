---
title: "Program installation problem"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by ishmael2k on 2009-07-17
Hi,

I want to install [this]("http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773") screensaver. 

The instructions seem simple but my /usr/share/gnome-screensaver/. file is owned by root and I can't access it. 

I really don't need this screensaver but I do need to know how to install programs of this style. (or at least feel that I do..)

I have looked for the answer to this here and online elsewhere. I am sure it has a simple answer but no luck so far for me.

If someone could point me to the place to read up on this I'd really appreciate it.:D

---

### Post by Sidewinder1 on 2009-07-17
You may make those changes by opening a terminal and typing:
```
gksudo nautilus
```
input your password, then follow the destructions in the link that you gave.
Caution: you can do serious damage to your system using these "root privileges", so make sure you have a good back up of your important data files.
HTH,
Side

---

### Post by ishmael2k on 2009-07-17
Sweet...

Worked like a charm. I will be very careful with root privileges.

Thank-you!:popcorn:

---

### Post by Sidewinder1 on 2009-07-18
You're more than welcome. 
:-)

---

