---
title: "How to open google earth"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by gotanothergrot on 2009-04-05
I have downloaded Google earth how do i install.
what should i do??

---

### Post by taurus on 2009-04-05
Try installing it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by spudpucker on 2009-04-05
ok i'm a newbie but I sometimes get this for files I downloaded.  I right click and click properties, then I have to click on permissions tab and click the box at the bottom next to " allow executing file as program "

then the proper program comes up at double click or right click.

hope this helps

---

### Post by gotanothergrot on 2009-04-05
Installed smoothly,Thanks,  however when i open it i get a few seconds of earth opening, some flickers and then shuts down!

---

### Post by The_R on 2009-04-05
> **gotanothergrot said:**
> Installed smoothly,Thanks,  however when i open it i get a few seconds of earth opening, some flickers and then shuts down!

Rename libcrypto.so.0.9.8 to something else in the google-earth directory. This usually fixes it for most people.

mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

Also, make sure your graphics drivers are up to date.

---

### Post by keypox on 2009-04-05
> **The_R said:**
> Rename libcrypto.so.0.9.8 to something else in the google-earth directory. This usually fixes it for most people.

mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

Also, make sure your graphics drivers are up to date.

hmm fixed my closing issue now the issue is that some much graphical problems.  Bet it works perfect in vista :(

---

### Post by alphacrucis2 on 2009-04-05
> **keypox said:**
> hmm fixed my closing issue now the issue is that some much graphical problems.  Bet it works perfect in vista :(


Try turning off your desktop effects. Problems with OpenGL apps vs compiz.

---

### Post by gotanothergrot on 2009-04-06
Thanks for the help, done the rename but some issues remain.


so what do i punch in the terminal to do a complete removal of the google earth download as i can live without it for now.

---

