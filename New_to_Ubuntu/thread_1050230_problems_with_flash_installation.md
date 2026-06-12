---
title: "problems with flash installation"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by yobird42 on 2009-01-25
For some reason Flash won't work for me. This is what happens, but firefox won't load the plugin. 

```
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox-3.0.5/

WARNING: A newer version of the Adobe Flash Player has been detected in
         /usr/lib/firefox-3.0.5//plugins.
         The installer will overwrite this existing binary.



----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox-3.0.5/

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): 

```

---

### Post by taurus on 2009-01-25
Look in there to see if there is a flash plugin.

```
ls -la /usr/lib/firefox-3.0.5/plugins
```
And don't forget to restart firefox.

---

### Post by yobird42 on 2009-01-25
It's in the folder and I copied the plugin to pretty much every folder with the name mozilla or firefox. I'll try restarting my computer since I haven't done that since I installed it.

---

### Post by taurus on 2009-01-25
Copy it to /usr/lib/mozilla/plugins if you want since I believe all the web browsers will look in there for plugins.

---

### Post by yobird42 on 2009-01-25
libflashplayer.so is in that folder but it still doesn't work.

---

