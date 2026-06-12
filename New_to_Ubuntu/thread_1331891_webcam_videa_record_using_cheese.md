---
title: "webcam videa record using cheese"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by workshop1702 on 2009-11-19
hi i have just installed cheese and tried to take a video , it sort of works but very jerky frame rate seems to be about one per second how can i speed up the frame rate please dont have a clue how to do this. also how long a video can i record using cheese.

---

### Post by workshop1702 on 2009-12-01
still need help with this problem have updated to latest version and its even worse video frame rate is one about every 6 seconds has anyone any ideas how to fix this .
has anyone actually got the video feature on cheese working

---

### Post by spiderbatdad on 2009-12-01
cheese is completely  inadequate for movie making. You will need cinelerra
[http://cinelerra.org/getting_cinelerra.php#karmic](http://cinelerra.org/getting_cinelerra.php#karmic)
or possibly kino.

---

### Post by workshop1702 on 2009-12-02
tried to install it as you described didnt work know even cheese cannot find my webcam says no camera found .
need more help pleaSE 
i think cheese would be good enogh for what i want if it worked as it should

---

### Post by spiderbatdad on 2009-12-02
So your webcam was working in cheese and isn't since installing cinelerra?
The instructions were to install it from repos. Have you opened synaptic and removed cinelerra? To get your cam working again may require loading a different camera module. You may need to provide camera type.```
lsusb
``` Cinelerra doent record the videos. It is for editing and movie making.

Back in Gutsy or earlier, I could run cheese without recording and it displayed myself in real time. I could run gtk-recordmydesktop simultaneously and it captured perfectly. Now neither programs works very well independently much less in conjunction with one another.

---

### Post by spiderbatdad on 2009-12-02
Have to take it back I just ran gtk-recordmydesktop recording just the cheese window, with cheese Not recording, and it worked excellently. Far superior to any recording I can do with cheese.

---

