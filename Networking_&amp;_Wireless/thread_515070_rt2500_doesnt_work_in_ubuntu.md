---
title: "rt2500 doesnt work in ubuntu"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by dan171717 on 2007-08-01
i have an ralink rt2500 chipset in my wireless card (a belkin laptop card) it works fine in windows,but in ubuntu it cannot connect to anything and can in some cases doing anything to do with it can crash it. ive heard theese cards work out of the box in ubuntu but thats probbly a load of crap. help?

---

### Post by kevdog on 2007-08-01
You are correct.  rt2500 works out of the box in Edgy and versions before, but not in Feisty.  To use your card you are going to have to install the serial monkey rt2500 drivers.  Here is a tutorial to start with that references the rt73 chipset.  The instructions for you are basically the same except except everywhere rt73 is mentioned substitute rt2500.  Write back if you have questions.  Read the instructions about 3 times before you start.

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by dan171717 on 2007-08-18
i used to have dapper but it didnt work i that either:( ive tried the serial monkey drivers but i can't compile even for my life! i dont know the dependecys ive also tried the synaptic drivers but they dont do anything i can open the network windo click on my wireless and can see networks to connect to but cant connect to them even with the right wep keys

---

