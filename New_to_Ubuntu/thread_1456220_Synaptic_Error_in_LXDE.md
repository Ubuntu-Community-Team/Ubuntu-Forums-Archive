---
title: "Synaptic Error in LXDE"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Fred the Penguin on 2010-04-16
Hello. I just did a command line install of Ubuntu Karmic and installed LXDE-common. It has very few things automatically installed. I installed Synaptic, but when I go into it, as soon as I type a few letters into the search box it closes. When I start it from the terminal, I get this error:
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 683, in <module>
    (dbkind, dbpath) = open(index).readline().split()
ValueError: need more than 0 values to unpack
Segmentation fault

Could someone please tell me how to fix this? I want to be able to install some things, and I don't know specific names, so I can't use apt-get or aptitude.
Thanks in advance.

---

### Post by -humanaut- on 2010-04-16
When you go to synaptic make sure your packages are "checked" off

---

### Post by Fred the Penguin on 2010-04-16
> **-humanaut- said:**
> When you go to synaptic make sure your packages are "checked" off
What exactly do you mean by that. 
I just realized that I can still use Synaptic, I just can't use the search box. It's annoying to have to scroll through all the packages to find what I want.

---

### Post by The Thunder Chimp on 2010-04-16
I think what humanaut means is that he wants you to unmark everything from installation.

---

### Post by Fred the Penguin on 2010-04-26
I just switched to Arch Linux out of curiosity and I like it. I am marking this thread as solved because I no longer need a gui package manager.

---

