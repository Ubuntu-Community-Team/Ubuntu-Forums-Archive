---
title: "can't play dvd (freezes or crashes)"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Konbuntu on 2009-11-19
i seem to have a problem with my os when ever i play a REAL, not pirated, dvd... mplayer crashes or freezes... i still haven't got vlc to play my dvd..
this problem is not only occurring with every dvd i play.. and no, its not my laptop =)

thanks in advance guys!!!
i appreciate all the help i've had so far from this community =)

---

### Post by werecatomega on 2009-11-19
do you have the "restricted" codecs?

---

### Post by Konbuntu on 2009-11-19
yes, i do!

---

### Post by herbertportillo on 2009-11-19
After you downloaded ubuntu-restricted-extras, did you run the following command?

"sudo /usr/share/doc/libdvdread4/install-css.sh"

---

### Post by Konbuntu on 2009-11-19
yes, still doesn't work =/ that sucks...

---

### Post by emigrant on 2009-11-19
what about totem?

---

### Post by Konbuntu on 2009-11-19
movie playe or movie player totem... i have the first one installed and it doesn't work either... the program freezes

---

### Post by kelvin spratt on 2009-11-19
Most freezing problems are down to Graphic cards and driver problems. Do a simple test type glxgears in your terminal and see what you get and post here. although its not a ultimate test it gives some idea.
By the way VLC should play straight from the box as its dependencies are sel contained.

---

### Post by Konbuntu on 2009-11-19
ok guys.. i think i got this figure it out =)
its working, now, with VLC

:popcorn:

---

### Post by ilil on 2009-11-19
The best DVD player is xine, IMHO. Try it too.
Totem can use xine for playing, just run totem-xine.

---

