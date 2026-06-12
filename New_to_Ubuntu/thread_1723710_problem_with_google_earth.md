---
title: "problem with google earth"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-07
i have installed google earth , and i think i installed it okay , bcoz there is an icon in Application > internet > google earth  but when i click on it nothing happens

as suggested in an older thread i already tried this 


zaafar@mirza:~$ sudo apt-get install lsb-core
[sudo] password for zaafar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zaafar@mirza:~$ 


????

---

### Post by squaregoldfish on 2011-04-07
Run it from a terminal to see if there's any errors (the command is google-earth, I think).

Steve.

---

### Post by rosencrantz on 2011-04-07
Hi zaafar.
a) Where did you get Google Earth from, the main/medibuntu repositories (e.g., with Synaptics) or did you use the .deb from Google's homepage?
b) Can you get some more info on what happens when you try to run it? For that, open a terminal and type google-earth. See whether it starts or not and copy and paste the terminal output here.
c) You mentioned another forums thread. Please add a link.

Ack, steve beat me to it....
Cheers,
rosencrantz

---

### Post by sleepingdragon on 2011-04-07
+1 for the Google Earth download. They've now released their own .deb file which seems to install just fine. Previous attempts at the googleearth-package was nothing more than a bucket of pain. You should be able to [find it here]("http://www.google.com/earth/download/ge/agree.html").

---

