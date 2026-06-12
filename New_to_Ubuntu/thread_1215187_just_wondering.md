---
title: "just wondering"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by the great 32 on 2009-07-16
does Ubuntu come with a C++ IDE or IED whatever it is called

---

### Post by starcraft.man on 2009-07-16
[http://linuxappfinder.com/development/integrateddevelopmentenvironments](http://linuxappfinder.com/development/integrateddevelopmentenvironments)

There's no shortage. Pick your poison and install by your preferred means. See sig for install help. Most of the popular ones should be in the repositories.

Edit: None of these are installed with a vanilla desktop install, just to be clear.

---

### Post by y-lee on 2009-07-16
not in a default install as far as i know. You can install one latter tho if you need one.

---

### Post by alphacrucis2 on 2009-07-16
> **the great 32 said:**
> does Ubuntu come with a C++ IDE or IED whatever it is called

```
sudo apt-get install build-essential
```

gets you a C++ compiler and some other stuff as the bare minmum for development. There's a bunch of optional stuff in the standard repos.

---

### Post by allenbradley on 2009-07-16
Just to offer an opinion : IDE's are really bulky and really come to the fore only when you are handling huge projects. Personally, I've stopped using IDE's since the original Borland C++ v3. Its much easier to use a text editor like vim/emacs/gedit/nano/... and compile using g++, the GNU implementation of C++. gdb is another amazing tool that can be used for debugging. Just download the frontend to gdb, called ddd as well and you're all set!

---

