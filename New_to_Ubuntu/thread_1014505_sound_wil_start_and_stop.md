---
title: "sound wil start and stop"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Kedster on 2008-12-17
ok Every once in a while my sound will stop working, then most of the time if I log out I think it starts to work but then sometimes I even have to shutdown. it seem more frequent if I listen to lots of music or watch movies and then stop for an hour or more but sometime is just doesn't work when I got to start listening to music, form what i can tell it has never stopped while Iwas listening to music

---

### Post by zeronothing on 2008-12-17
try doing this when you loose sound. try closing the programs that are using sound like media players, web browser, etc. then open up terminal and use this command:

sudo alsa force-reload

this will cause the sound to reload. this works for me whenever I loose sound on my PC. this can help until you can find the root of the problem..

---

### Post by Kedster on 2008-12-17
thanks man ill try that maybe ill make a launcher on my panal but i hope i can fine a cure to

---

