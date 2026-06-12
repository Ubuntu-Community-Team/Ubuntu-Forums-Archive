---
title: "[SOLVED] Need some help... My mic wont turn off"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by tarheelblue on 2008-12-26
i just upgraded to 8.10 on my thosihba satilite X205 and internal Mic wont turn off i mute it and it turns write back on? any one got any sugestions on how to fix it

---

### Post by MarblePanther on 2008-12-26
Try turning the slider all the way down then go into the mixer's settings and make sure the restore volume on login is checked.

---

### Post by nlz on 2008-12-26
open ALSA controls by double clicking the speaker icon in the right upper corner of your screen and put the volume to zero.

---

### Post by tarheelblue on 2008-12-26
i did and its still on

---

### Post by Sand Lee on 2008-12-26
1. open a terminal and open up alsamixer with > alsamixer2. press tab to swich to capture mode
3. go to the capture switches and press spacebar on the switches which have the text  "L-R-Capture" to disable them

---

### Post by bo01 on 2011-04-04
ok, I have the same problem and if I disable R-L from alsamixer I just didn't hear anything when I try to reproduce my recording. I use debian btw, but if you are thinkink of a solution please let me know.

thx!

---

