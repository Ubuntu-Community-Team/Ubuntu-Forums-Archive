---
title: "Bluetooth Problem"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by rj7 on 2011-09-06
Hi, 
   I have both blueman and default bluetooth application installed... Recently i am facing this problem.. I cant turn on the bluetooth... If i turn on the bluetooth in default application it  shows its turned on... But the bluetooth icon is still grey not white... If i right click it (after i turned on) it shows me an option to turn off.... I cant turn it on using Blueman too!!!

---

### Post by pierreyy on 2011-09-06
what if you reinstall the drivers... 

  was the problem always there? how did it come about?

---

### Post by nipunshakya on 2011-09-06
There is a software called "Additional drivers"(in ubuntu 11.04 and hope your version 10.04 has that too)...if not, find it from Software Centre and then run it...it will search for available hardwares in your machine and then show u with a list of drivers...you might get your bt driver enlisted there somewhere....

I have suggested this to some other friends having bluetooth problem...(in and out of the forum)..worked with some...hope works for you too....goodluck.

Regards, NeptuneTech

---

### Post by gandaran on 2011-09-07
try removing and installing bluez, maybe it can fix the problem
```
sudo apt-get remove --purge bluez
```
```
sudo apt-get install bluez
```

---

