---
title: "How do i install aircrack"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by RedSamurai on 2007-06-19
How would i go about doing this? I want to use it but i dont know how to install it. Thank you for helping me  i am new to linux

---

### Post by diatribe on 2007-06-19
...

---

### Post by dashnak on 2007-06-19
I would say something like:
```
sudo apt-get install aircrack-ng
```

---

### Post by RedSamurai on 2007-06-19
It says it couldent find the package

---

### Post by LEDominator on 2007-06-19
did you try getting it from the libraries?  I think it was system->Administration->Package manager.  If not there then in the programs

---

### Post by RedSamurai on 2007-06-19
i looked for it but couldent find it :(

---

### Post by LEDominator on 2007-06-19
look in here

---

### Post by RedSamurai on 2007-06-19
i only have the networking option on mine not universal or anything so no i do not have it

---

### Post by LEDominator on 2007-06-19
try

> sudo apt-get install aircrack

---

### Post by tturrisi on 2007-06-19
You don't want aircrack, you want aircrack-ng:
[http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=ec0bedf467b1fc1ff91b6366608b8d6b](http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=ec0bedf467b1fc1ff91b6366608b8d6b)

---

### Post by RedSamurai on 2007-06-20
it says it couldent find packages.

---

### Post by dashnak on 2007-06-20
You should enable multiverse and universe

---

### Post by RedSamurai on 2007-06-20
how?

---

### Post by tturrisi on 2007-06-20
Don't install aircrack from gthe Ubuntu repos, it's a old version.  Aircrack is way way old.  Aircrack-ng is the newer utility based on the Aircrack code.  It has less bugs, more features, security holes patched, faster, better & the newest version also now includes aircrack-ptw which will crack a 64 bit wep key in about 3 minutes.  Follow the instructions in the link I posted above.

---

### Post by Long_Live_Linux on 2008-01-01
I have installed Aircrack-ng, but how do I RUN it??? Why is there no shortcut like in Windows? This Linux stuff is about to drive me insane!!!!:confused::confused::confused:

---

### Post by Demon in the Rough on 2008-01-01
I'm having a similar problem where i have installed Aircrack through the Package manager but on the website it says to just run the program through it's basic commands and these do not work...  I just get a bash error saying that those commands don't exist...

---

