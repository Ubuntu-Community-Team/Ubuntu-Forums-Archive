---
title: "Chrome Dev PPA"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-01-06
Hi all,

I try to keep up to date with Google Chrome's Dev releases, but it appears that with the recent upgrade of Linux's version of Chrome, I was put on the Beta list.

How do I get back on to the Dev Channel? Ive already tried uninstalling Chrome completely and installing the 'dev' package, and even editing the PPA to 'testing'.

Does anyone have a current Dev release? The most recent release was from today- Version 4.0.288.1.

My version is 4.0.266.0.


I would really appreciate it if anyone could help me get 'back' on the dev releases!

---

### Post by Merk42 on 2010-01-06
Check in synaptic and search for Chrome
you may have google-chrome-beta installed when you want google-chrome-unstable.

If so, just uninstall google-chrome-beta and then install google-chrome-unstable

---

### Post by tom.swartz07 on 2010-01-06
> **Merk42 said:**
> Check in synaptic and search for Chrome
you may have google-chrome-beta installed when you want google-chrome-unstable.

If so, just uninstall google-chrome-beta and then install google-chrome-unstable

Nope, only available choice is google chrome unstable, version 4.0.266.0

Can anyone verify the correct ppa in the sources list?
Mine is [http://dl.google.com/linux/deb](http://dl.google.com/linux/deb) testing main

I think the only difference is the ppa....

---

### Post by tom.swartz07 on 2010-01-06
Bump.

---

### Post by Merk42 on 2010-01-06
The file /etc/apt/sources.list.d/google-chrome.list contains the following:
```
deb http://dl.google.com/linux/deb/ stable main
```
and yet I have 4.288 available under unstable (though I currently have beta installed)

---

