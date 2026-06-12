---
title: "Change Chromium's icon globally"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by faviouz on 2011-01-27
Hi,

I recently installed Ubuntu 10.10 and I have something I'd like to change. How do you change Chromium's icon globally? That is, on the desktop, the applications menu and the window bar.

I right-clicked the Chromium shortcut, went to Properties and tried changing it but it only took effect on the desktop! Everything else remained the same. Any ideas?

Thank you.

---

### Post by mharrison on 2011-01-27
This might help...can't test it right now but it is worth a shot:

[http://simplistictechnologies.com/blog/2009/06/ubuntu-change-menu-icon/](http://simplistictechnologies.com/blog/2009/06/ubuntu-change-menu-icon/)

---

### Post by faviouz on 2011-01-28
Hey, thanks for the response, but I'm not sure how I can edit a program's icon with that.

Is there another way to do this?

---

### Post by mharrison on 2011-01-29
My mistake....I thought it worked for global icons as well.  Unfortunately I have not found a way to do this yet.  I can change it on the Menu, and then change it on the desktop, but that is it.  If I change it on the menu and add a launcher on the desktop, the original icon is used. 

I did read somewhere that the default icon might be embedded in the source code of the app so that might be something as well.

---

### Post by hakermania on 2011-01-29
replace /usr/share/app-install/icons/chromium-browser.png (you had better keep a backup first)  to whatever you want, restart and ready.

---

### Post by faviouz on 2011-01-30
That doesn't seem to work either. Did it step by step.

Does it matter if the icon I got is 256x256 while the default icon was 48x48?

---

### Post by speedwell68 on 2011-01-30
Easy, change it on the menu, then drop that shortcut from the menu to the desktop and then drop it on the window bar.

---

