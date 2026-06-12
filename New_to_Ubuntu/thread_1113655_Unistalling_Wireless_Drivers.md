---
title: "Unistalling Wireless Drivers"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by alanfang on 2009-04-01
I want to uninstall my wireless driver. I know the name of the .deb file I used to install it. How would I uninstall it?

---

### Post by llamabr on 2009-04-01
sudo apt-get remove thedriver

This might not do what you want it to, though.  That is, whatever package might do other things besides what you think it does.  What was the package name?

Why do you need to remove them?

---

### Post by alanfang on 2009-04-01
I don't know the exact name of the driver, is there a way to find that out? I just installed the wireless driver manually, it was the the incorrect one and now it's screwing up my system.

---

### Post by 3rdalbum on 2009-04-01
The first part of the name of the .deb file (before the _ symbol) is the name of the package. For instance, if the .deb file is called "blacklight3-gui_0.1-1_all.deb", then it will be called "blacklight3-gui" in Synaptic. You can then remove it from there.

---

