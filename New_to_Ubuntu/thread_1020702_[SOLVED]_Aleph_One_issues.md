---
title: "[SOLVED] Aleph One issues"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by atngplusultra on 2008-12-24
this is on 8.10, Intrepid

I just want to play Marathon, you know, so, I try to install AlephOne to do this, and I install everything that their install file says to, except what's not available or what have you, but, the one thing that constantly comes up on the configure step is:
```
checking boost/bind.hpp usability... no
checking boost/bind.hpp presence... no
checking for boost/bind.hpp... no
You need boost/bind.hpp from the boost library to run Aleph One
```

I've installed the library, so, why does it not "find" bind.hpp? I don't know the path it wants for it, because it doesn't state it, it just says it isn't there, when I'm fairly certain it is.
Do I need to manually install the header file? and if so, where?

---

### Post by atngplusultra on 2008-12-24
shoot, I simply hadn't found libboost.
you think I would've learned by now.

---

### Post by siriusfox on 2009-05-05
So how did you solve this? I'm having a similar error on another distro. Yet /usr/local/include/boost-1_38/ contains boost/bind.hpp

---

### Post by atngplusultra on 2009-05-05
> **siriusfox said:**
> So how did you solve this? I'm having a similar error on another distro. Yet /usr/local/include/boost-1_38/ contains boost/bind.hpp

well the:
```
sudo apt-get install libboost
```
as i recall, was the last of my problems, or, the last major one at least. It was so many months ago that now i forget, sadly. just thoroughly check the log of all your ./configure and make commands and see if any other errors are present

---

