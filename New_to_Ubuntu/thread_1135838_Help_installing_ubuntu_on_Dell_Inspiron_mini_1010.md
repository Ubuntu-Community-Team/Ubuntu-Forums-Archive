---
title: "Help installing ubuntu on Dell Inspiron mini 1010"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by thyplo101 on 2009-04-24
I tried to install ubuntu studio but I forgot to select the repositories including the desktop to install. Then, I wiped the computer clean (including windows) to start over. After installing it again (all repositories), it says it couldn't load the GUI and goes straight to a command prompt. What went wrong?

---

### Post by LowSky on 2009-04-24
type **_startx _**at terminal prompt, and try to list the errors

---

### Post by Yvan300 on 2009-04-24
Hmmmm, try again and this time format the disk into different partitions for home, root and swap. ext3 is preferred, i don't suggest you use ext 4 :)

---

### Post by thyplo101 on 2009-04-24
it says a bunch of random stuff and then
(EE) VESA(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by Yvan300 on 2009-04-25
Maybe there isn't a proper driver for your graphics card. WHat card do you have ?

---

### Post by brianchidester on 2009-04-27
Dell Mini 10 has the GMA500 graphics chipset. There are only drivers for this in the Jaunty, the latest Hardy releases and Dell's customized ubuntu versions.

---

