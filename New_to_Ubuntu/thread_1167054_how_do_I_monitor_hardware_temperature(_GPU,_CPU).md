---
title: "how do I monitor hardware temperature( GPU, CPU)"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by enri2 on 2009-05-22
?

---

### Post by XCan on 2009-05-22
Heh, very descriptive post. Anyway, personally I use lmsensor and sensors applet for this purpose. 

sudo apt-get install lm-sensors
sudo sensors-detect (Answer some questions, most should be YES)
sudo apt-get install sensors-applet

Done! Now you can add some temperature icons into your upper panel.

---

### Post by Nicodemus144 on 2009-05-22
i use gkrellm for my system monitoring needs.  you can find it in Add/Remove Progs.

---

### Post by khelben1979 on 2009-05-22
```
sudo apt-get install ksensors
```
if you prefer [KDE]("http://en.wikipedia.org/wiki/Kde").

---

