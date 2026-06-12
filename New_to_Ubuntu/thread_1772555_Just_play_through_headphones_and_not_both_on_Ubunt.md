---
title: "Just play through headphones and not both on Ubuntu"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by ICEhockeyGOALTENDER on 2011-05-31
Anyone know why the System(Ubuntu v11.04) wont just play through headphones and not both

UBUNTU PLAYS THRU INTEGRATED SPEAKERS**_ AND_** EAR BUDS(PLUGGED IN), does anyone know how to play only thru ear buds and not both?    i started playin a song that is not the best for my mom to hear so it would be much appresiated if you could help me out here.

Thanks, 
Sam

---

### Post by mishathegoat on 2011-05-31
A temporary fix is to open the Terminal.

Run the command:

```
alsamixer
```

Press the left and right buttons to navigate to each sound source. (Master, Headphones, Etc)

Pree the "m" key to mute a source you do not want to use or simple press the up/down key tow raise/lower the volume for that source.

When you're finished run the command:
```

alsactl store 

```
to save these settings until you change them again.

---

