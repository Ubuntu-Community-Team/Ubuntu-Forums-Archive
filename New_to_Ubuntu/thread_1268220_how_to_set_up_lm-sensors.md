---
title: "how to set up lm-sensors"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-09-16
I had lm-sensors set up before i did a clean install of jaunty, i remember it was relatively easy but i can't find the how to. any help

---

### Post by bodhi.zazen on 2009-09-16
Install and then run sudo sensors

```
sudo apt-get install lm-sensors

sudo sensors
```

---

### Post by halitech on 2009-09-16
I think you need to run sudo sensors-detect after installing it and then run sensors to get the output

---

### Post by DarinB on 2009-09-16
I did the sensors detect i did add an hdd sensor as well but last time i it on my panel, no idea what i did though

---

### Post by Bachstelze on 2009-09-16
> **bodhi.zazen said:**
> Install and then run sudo sensors

No need to run it with sudo.

---

### Post by halitech on 2009-09-16
if you want it in your panel, I believe there is gkrellem that can be added. there could be others as well but I use the output in conky.

---

### Post by AClark on 2009-09-16
Right click on the panel - Choose "+ Add to Panel"

Then find "Hardware Sensors" - Highlight and click on "Add to Panel"

Right click on the panel icons to configure.

---

### Post by DarinB on 2009-09-16
sheesh so easy i was looking for lm-sensors. 
thanks do you know what the maximum values are for hdd's i know that 75C is upper for cores?

---

### Post by QIII on 2009-09-16
Actually, core max is a bit different depending on which OEM you talk to (of course they will tell you a higher max, so you'll melt it and buy a new one).

The trick is whether your sensor is detecting the temperature at the board or in the air stream across the fan...

---

### Post by DarinB on 2009-09-16
damn can't trust anyone any more. never thought of the being dishonest so you fry your pc. I have no idea where the sensors are, i didn't even know it was possible until about four weeks ago but i do know that my hdd fan was off and my /home hdd was really hot to the touch, finally got the fan working and did a full clean install or re install of jaunty.... i think my hdd was corrupting data i lost my grub and before that all sorts of stuff was messing up. 
freezes etc now even the memory seems to be better, although another 20 hour memtest i won't bother with, i am sick of working on this thing for today....thanks again

---

