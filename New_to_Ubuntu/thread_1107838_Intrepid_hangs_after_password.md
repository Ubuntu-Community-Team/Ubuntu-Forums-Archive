---
title: "Intrepid hangs after password"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by tedw on 2009-03-27
Hi All,

Okay I am still struggling with Intrepid Ibex 8.10.

A fresh load on the Dell GX260 proceeds well. 

Boot up and all looks fine.  Splash works.  Xserver must be running because I get the normal login/password blocks. 

Entering username and password gives me a plain light brown 
screen from which there is no escape. 

This same hardware supports Hardy Heron without problems. 

Any ideas ?   Some help would be appreciated. 

thanks,

tedw

---

### Post by LowSky on 2009-03-27
bad install I think might be the culprit, did you do a upgrade or a new install?

try booting into recovery mode, choose go to prompt, the run ```
sudo apt-get update & sudo apt-get upgrade
```

that might fix things

---

### Post by tedw on 2009-03-27
Thanks for the reply.
It was a fresh load from a CD so not an upgrade. 
BTW the CD checked out OK.

Looking at the syslog.

```
 cat syslog | grep gnome 
```
gives me...
x-session-manager: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
followed by
...Application 'gnome-wm.desktop' failed to register before timeout

Is that significant or just a red herring ?

Currently I am not on line so your suggestion to use apt-get may not work ?  Am I right ?   I have not yet got passed the password stage.

Any further suggestions would be appreciated

tedw

---

### Post by spiderbatdad on 2009-04-03
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

