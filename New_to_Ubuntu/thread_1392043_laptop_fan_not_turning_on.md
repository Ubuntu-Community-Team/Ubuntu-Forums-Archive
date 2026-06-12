---
title: "laptop fan not turning on"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by DestructionsRightHand on 2010-01-27
in ubuntu 9.10 my laptop fan never turns on and my temps are hitting around 45* and is bumping into the red.  How can i turn these fans on or set them manual if it cant be done automatically.

---

### Post by Paqman on 2010-01-27
45 isn't really that hot for a laptop, are you really sure they aren't running? I'd expect your machine to be a lot hotter than that if they weren't. Have you had any random shutdowns?

---

### Post by DestructionsRightHand on 2010-02-07
that temp was in cel,  the temp are hot even for a laptop around 111 - 115 f*.  It is not to hot to the touch but i know the cpu and north-bridge are well shielded on my model of laptop

---

### Post by DestructionsRightHand on 2010-02-08
bump

---

### Post by duruttye on 2010-02-08
What does the sensors command tell you?

---

### Post by saif_held on 2010-02-08
A faulty fan maybe?

---

### Post by DestructionsRightHand on 2010-02-14
it has 6 temps. With a temp number and a (crit = +108.0°C) 

***
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +16.0°C  (crit = +108.0°C)                  
temp2:       +24.0°C  (crit = +105.0°C)                  
temp3:       +42.0°C  (crit = +108.0°C)                  
temp4:       +46.0°C  (crit = +105.0°C)                  
temp5:       +30.0°C  (crit = +108.0°C)                  
temp6:       +35.0°C  (crit = +110.0°C)

---

### Post by kio_http on 2010-02-14
Could you state what laptop you have and if possible motherboard and chipset model?

---

### Post by akashiraffee on 2010-02-14
I don't know why you'd expect the fan to be on at that point.  These are more like ideal temperatures.  It is not good to run too cold, either.

If the room temp. is <16°C, then it's probably never going over 50° internally, esp if you are not doing anything too stressful.  

Anyway, I would not worry -- the BIOS will override and turn the fan on when it wants to (it will also turn the whole thing off if it has to).  The OS *can *operate the fans, but it doesn't matter that much whether it does or doesn't (meaning even if the software malfunctions nothing bad will happen).

---

