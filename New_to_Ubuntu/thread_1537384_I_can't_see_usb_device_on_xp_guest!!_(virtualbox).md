---
title: "I can't see usb device on xp guest!! (virtualbox)"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-23
I'm running windo$s xp as a guest OS under Oracle VM Virtualbox 3.2.0, and i attached the usb device before i ran vbox under USB section, also i unmounted the device on ubuntu and then started xp but i couldn't see it listed in my computer devices 

vbox photo : [http://dl.dropbox.com/u/5392244/Screenshot-xp%20-%20Settings.png](http://dl.dropbox.com/u/5392244/Screenshot-xp%20-%20Settings.png)
xp photo : [http://dl.dropbox.com/u/5392244/xp.png](http://dl.dropbox.com/u/5392244/xp.png)

any help?

---

### Post by migs73 on 2010-07-23
Do have the OSE or PUEL version? The OSE version is the one in the repos. The OSE version does NOT support USB.
You would have to download the PUEL version from the website and install the 'guest additions' to be able to have USB connections.

If you have all this (I think you might looking at your screen dumps) try starting Vbox then plug in your USB and then check on the Vbox menus (whilst running XP) under Devices> USB Devices and see if your drive is listed. If so check it and it should then be available. 

After this I am running out of ideas so input from others would be appreciated.

---

