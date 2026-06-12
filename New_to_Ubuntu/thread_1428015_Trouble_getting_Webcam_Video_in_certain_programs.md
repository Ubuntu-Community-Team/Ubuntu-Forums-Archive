---
title: "Trouble getting Webcam Video in certain programs"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by SumthingWicked5 on 2010-03-12
My girlfriend is out of the country for a while, so we got Skype. I installed, and after dealing with a weird language issue, I have my web-cam (Logitech quickcam) connected up. With a bit of messing around, I got the audio to work, but I have no video. Hitting the "test" button makes the light on my camera light up briefly, but then it goes back off. Nothing. I got Camorama, and get errors (unable to capture image). I installed Cheese, and it works just fine... I'm assuming I've configured something wrong. Please help?

---

### Post by no2498 on 2010-03-12
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

try that in a terminal
you may need to run that every time you start skype
so copy an save it
hope it helps

---

