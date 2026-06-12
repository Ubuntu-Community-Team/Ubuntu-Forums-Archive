---
title: "Connected external monitor now laptop resolution too low"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by danbaark on 2010-12-27
Hi, I'm using Ubuntu 10.10 with a 1920x1080 (16:9) display. I tried to connect an external monitor (an old CRT one) using the preferences monitor setting. Upon unplugging the external and restarting my laptop though the laptop's screen resolution seems to be stuck at the external monitors. 

Going into preferences, monitors again the highest resolution I get is 1400:1050. Basically I just want to reset my monitor to what I had before (it was working fine) but I have no idea how. 

I've tried sudo dpkg -reconfigure xserver-xorg but it doesn't do anything.

Thanks very much for any suggestions

---

### Post by danbaark on 2010-12-27
Solved by restoring xorg.conf

---

