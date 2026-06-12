---
title: "dell studio 15, no sound problem, need help implementing the solution"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by Falc7 on 2009-07-04
I have a dell studio 15, and the no-sound problem, i am following the guide 
[http://www.uluga.ubuntuforums.org/showthread.php?t=1139700](http://www.uluga.ubuntuforums.org/showthread.php?t=1139700)

It tells me to edit the /etc/modprobe.d/alsa-base file, but when i try and do this, i can't because of insufficient permissions.

---

### Post by Falc7 on 2009-07-05
Can anyone tell me how to edit this file?

---

### Post by ivanvajar on 2009-07-05
Open Terminal and:

> sudo gedit /etc/modprobe.d/alsa-base.conf

Add:

> options snd-hda-intel model=dell-m6

at the end of file

---

### Post by Falc7 on 2009-07-05
great that worked, thanks very much

---

### Post by LewRockwell on 2009-07-05
please mark thread solved

.

---

### Post by amaresh_83 on 2009-08-12
No .. I am facing same problem here .. i did all modification still same problem 

:popcorn:

---

