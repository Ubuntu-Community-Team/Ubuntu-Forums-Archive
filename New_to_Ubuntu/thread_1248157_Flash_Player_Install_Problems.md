---
title: "Flash Player Install Problems"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by airjp73 on 2009-08-23
So, I just got Ubuntu and tried to install flash player 10.

I've looked up a bunch of tutorials and looked at the instructions on the adobe website and none of them seem to work.

I download the .tar.gz file and extract it.
Every tutorial says it should've created the directory install_flash_player_10_linux but it doesn't. Instead, I get a single file called libflashplayer.so.

No matter where I go to find another method, I always get the same problem.

I figure I'm doing something wrong. Can anyone help?

---

### Post by sandyd on 2009-08-23
i know what your doing wrong
you should simply type in 
```

sudo apt-get install flashplayer-nonfree

```
or download the DEB version from adobe's site.

---

### Post by hansdown on 2009-08-23
Hi airjp73.

The easiest way, is to click system> administration> synaptic package manager.

Enter your password.

Search for flash.

Click on flashplugin-installer.

Click install.

---

### Post by airjp73 on 2009-08-23
Thanks!

Problem solved.

---

