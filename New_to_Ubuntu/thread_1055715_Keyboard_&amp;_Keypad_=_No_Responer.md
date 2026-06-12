---
title: "Keyboard &amp; Keypad = No Responer?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by Izmmm on 2009-01-31
Hello everyone.  I had what I thought was a successfull install of Ubuntu 8.10.  However when I booted up and got to the login screen I found my keyboard and keypad were not responding.  This of course leaves me unable to login.  Anyone know how I can fix this?

Thanxz Izmmm

---

### Post by Izmmm on 2009-01-31
orry I meant = No Response? not No Responser?

---

### Post by Izmmm on 2009-01-31
Anyone got any tips?  If not does anyone know how to move a thread.  In retrospect I think this would be better suited for another forum such as Hardware.

---

### Post by putonghua73 on 2009-01-31
Check out [_this_]("http://ubuntuforums.org/showthread.php?t=891544") thread where a number of people including myself, experienced the same issue of keyboard and mouse / keypad disabled on DE [desktop environment] first loading.

Hope that helps!

---

### Post by linux_tech on 2009-01-31
What are we working with? If it is a laptop, what are the system specs; if a desktop, then ps2 or usb?

---

### Post by Izmmm on 2009-01-31
Yes I am working with a Dell Latitude C600 and everything responds prior to login screen.

---

### Post by Doktor Sleepless on 2009-02-12
It's something wrong with HAL. If you open up your Xorg config file, you'll find your entries for the keyboard and mouse are commented out automatically. Remove the # and save. This is what worked for me.

---

