---
title: "Problem with ubuntu 9.10 boot resolution"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-11-09
I installed ubuntu 9.10 and restarted but after booting it said" cannot boot in *some high resolution i am not sure of the size* trying to boot in 1024*768" and the screen keep fluctuating and it asks for my user name and password , but when i type in my password i am unable to type it correctly as the keys are not entered correctly due to the fluctuation of screen.

---

### Post by synicalx on 2009-11-09
> **ravi_buz said:**
> I installed ubuntu 9.10 and restarted but after booting it said" cannot boot in *some high resolution i am not sure of the size* trying to boot in 1024*768" and the screen keep fluctuating and it asks for my user name and password , but when i type in my password i am unable to type it correctly as the keys are not entered correctly due to the fluctuation of screen.


What sort of hardware are you running? I've seen a few people with this problem (mainly using ATI graphics cards from memory). Also what type of install is this - wubi, clean, LiveCD etc?

Oh and what do you mean the screen fluctuations are preventing you from entering your password? I wouldn't have thought that could effect your keyboard unless your using and on-screen one?

---

### Post by ravi_buz on 2009-11-09
I did a clean install and have a intel p4 with nvidia gforce video card. My resolution is 1440*900 but the boot sceen is set in a high resolution .The screen flickes and when it does i am unable to keyin anything and thus unable to loginto system in command mode.

---

### Post by mbzn on 2009-11-09
try pressing Ctrl+Alt+F1 this will take you to a terminal. If this works fine you could just change xorg.conf to another res. that'll work for you.

(/etc/X11/xorg.conf)

---

### Post by ravi_buz on 2009-11-09
yes f1 took me to a normal one, can u tell me the command to type in that, i tried dpkg-reconfigure xserver.org and it said that xserver is not installed.

---

### Post by ravi_buz on 2009-11-10
i tried to install xserver.xorg but it says i have the latest version.

---

