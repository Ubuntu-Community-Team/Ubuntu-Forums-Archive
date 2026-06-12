---
title: "Samsung Laptop"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Eddison on 2010-12-31
Hi- bought a laptop for my wife and proclaimed the virtues of Ubuntu ! Loaded ubuntu on it for her, and she can't play DVD's ??? Errors like - could not read from source- come up. I have done huge research on this prior to posting.
Some DVD's do play, although for the life of me, no one seems to know anything about this problem.

Help of any kind is appreciated...

eddison

---

### Post by sandyd on 2010-12-31
> **Eddison said:**
> Hi- bought a laptop for my wife and proclaimed the virtues of Ubuntu ! Loaded ubuntu on it for her, and she can't play DVD's ??? Errors like - could not read from source- come up. I have done huge research on this prior to posting.
Some DVD's do play, although for the life of me, no one seems to know anything about this problem.

Help of any kind is appreciated...

eddison
tried libdvdcss?

---

### Post by Eddison on 2010-12-31
Yeah... tried that :confused: thanks anyway.

---

### Post by Eddison on 2011-01-01
Hi Guys,
rockerphil solved this problem !! 
The problem was, I had libdvdread2 installed and not libdvdread4, and it wasn't configured properly. The laptop is a Samsung rv510 and the problem was with the optical drive or TS-L633 which is a toshiba dvd drive. 
Here are instructions

> in order to play DVDs on Ubuntu you need the software that decodes the  DVD called libdvdread4. you can install this by running this in a  terminal

 	Code:
 	sudo apt-get install libdvdread4 
then simply run this in a terminal to configure it

 	Code:
 	sudo /usr/share/doc/libdvdread4/install-css.sh 
after rebooting you should be able to play the majority of  proprietary DVDs with any of the major media players, i personally  prefer VLC. hope this helps,



eddison

---

