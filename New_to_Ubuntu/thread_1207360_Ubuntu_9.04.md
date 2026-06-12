---
title: "Ubuntu 9.04"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by GSI on 2009-07-08
I'm having problem playing tracks on the latest ubuntu...Every player refuses to play MP3..I have the codecs..Or the players starts playing it crashes in 5 sec... PLEASE HELP!

---

### Post by masux594 on 2009-07-08
try to open the program with a terminal.. so, u can see why it crashes! Tell us the program that u use for..

Sysc, A

---

### Post by GSI on 2009-07-08
I tried amarok 2 ,VLC,Rhytmbox and Dragon player and nothing different...dosen't want to play or if it does the player crashes 5-10 sec after starting playing..

---

### Post by masux594 on 2009-07-08
Run ```
rhythmbox
``` in a terminal.. what happen when the program crashes?

Sysc, A

---

### Post by GSI on 2009-07-08
I'm soo sorry i didnt said it right...the programs don't crash they just freeze and i have to use force quit to close them

---

### Post by masux594 on 2009-07-08
Well, googling i haven't found some solution, other people wis similar problem but not solutions.. ..Looks like a codec problem, look in this way.. Maybe gstreamer problem.. Have you installed some codecs?

Sysc, A

---

### Post by alexlafreniere on 2009-07-08
Try reinstalling your codecs, sounds like they didn't install properly so any program that tries to use them locks up. Try these commands:

```
sudo apt-get remove gstreamer
sudo apt-get install gstreamer
```

---

### Post by GSI on 2009-07-08
This is what error i get when i try removing codecs....


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer

---

### Post by masux594 on 2009-07-08
Try with[ this link]("http://hivltg.co.uk/?p=8") ..

Sysc, A

---

