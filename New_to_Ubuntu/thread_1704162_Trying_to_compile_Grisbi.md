---
title: "Trying to compile Grisbi"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by lesliek on 2011-03-10
I was using Grisbi, a finance program, but the version available via the software center has problems, according to the Grisbi website. It's recommended to upgrade, but there's no Ubuntu package available, so I'm trying to compile the latest version. When I run "./configure", I get stopped with the following message:

"checking for GRISBI... configure: error: Package requirements (gtk+-2.0 >= 2.12.0 glib-2.0 >= 2.18.0 gmodule-2.0 >= 2.18.0) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gmodule-2.0' found"

If I search the Synaptic package manager for "gtk+", "glib" or "gmodule", I get no results for those precise names. I suspect that I have the relevant packages installed, but that Ubuntu uses different names for them. Is that right? If so, how do I overcome the problem?

Leslie

---

### Post by Nickjpost on 2011-03-10
Did you download directly from the site? If so, did you go to the Ubuntu download option from the top of the page? Check out this link to make sure:
[http://www.grisbi.org/download.en.html#ubuntu](http://www.grisbi.org/download.en.html#ubuntu)

---

### Post by lesliek on 2011-03-10
Thanks for replying, Nickjpost.

The package you mention is for the same version one can get from the repositories. Unfortunately, it's no longer supported because there's said to be an "incompatibility between Grisbi 0.5.9 and the latest version of the GTK libraries (2.18.x)". That's what's led me to try to compile version 0.8.3.

Thanks again,

Leslie

---

### Post by Paul820 on 2011-03-10
Copy and paste:
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev 
```
The last one i don't know, someone else may know that one. Although searching synaptic comes up with **gir1.0-glib-2.0** when searching for gmodule, so you might try that one.

---

### Post by cipherboy_loc on 2011-03-10
Duplicate of above post:


```

   /\
  /||\
 / || \
   ||
   ||

```

---

### Post by Nickjpost on 2011-03-10
> **lesliek said:**
> Thanks for replying, Nickjpost.
 
The package you mention is for the same version one can get from the repositories. Unfortunately, it's no longer supported because there's said to be an "incompatibility between Grisbi 0.5.9 and the latest version of the GTK libraries (2.18.x)". That's what's led me to try to compile version 0.8.3.
 
Thanks again,
 
Leslie
Oh, my bad.....sorry.
Found this for that last package though; maybe I can redeem myself, haha
[http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

---

### Post by lesliek on 2011-04-05
Well, in case anyone else is interested in using Grisbi and wants at least version 6, you can get it by using the program as compiled for Debian. It's working for me.

---

