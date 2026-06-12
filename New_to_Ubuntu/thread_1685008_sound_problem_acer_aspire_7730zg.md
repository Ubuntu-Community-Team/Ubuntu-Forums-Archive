---
title: "sound problem acer aspire 7730zg"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by psudodragon on 2011-02-10
help, lol i compiled and installed alsa-driver-1.0.24, alsa-lib1.0.24.1, alsa-utils1.0.24.2, and installed realtek-linux-audiopack-5.16... using $ ./configure $ sudo make $ sudo make install for the alsa-files and just $ ./install for the realtek pack 

now i have no sound something to me to post this; 
[http://www.alsa-project.org/db/?f=9ab4ad85f82cdddb79a2ee2411bec663ba36bf2f](http://www.alsa-project.org/db/?f=9ab4ad85f82cdddb79a2ee2411bec663ba36bf2f) 
for the person helping me out, thanks

---

### Post by psudodragon on 2011-02-10
I solved it ha ha ha, I manually compiled realtek-linux-audiopack-5.16 with $ ./configure --with-cards=hda-intel $ sudo make, $ sudo make install restarted and laptop speaker sound with built in sub working on 5.1 and sound through headphone jack

---

### Post by zone88 on 2011-03-15
Hi, i run into same problem as you.

I had install ubuntu 10.10 on acer aspire 6935g
the sound on the notebook speakers was working. only the headphone wasnt working..

i downloaded realtek-linux-audiopack-5.16 and installed it, now no sound device in hardware :s

Any idea of how i can troubleshoot this or uninstall the realtek-linux-audiopack-5.16 and have the ubuntu alsa back to normal?

thanks

---

