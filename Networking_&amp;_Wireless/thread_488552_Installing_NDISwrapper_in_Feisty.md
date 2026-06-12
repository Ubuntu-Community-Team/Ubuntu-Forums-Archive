---
title: "Installing NDISwrapper in Feisty"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by slam5050 on 2007-06-30
I've managed to extract the .tar.gz  file to my desktop. I'm stuck as what to do next?

---

### Post by bigken on 2007-06-30
why dont you just use add remove programs ?

---

### Post by slam5050 on 2007-06-30
I would but I have no connection to the internet (other than my wireless)

---

### Post by bigken on 2007-06-30
so you dont have a nic on your pc ?

take a look[ here ]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9358-howto-install-software-readme.html")

---

### Post by kevdog on 2007-06-30
This should get you started.  When you actually have to insert your wireless driver inside of ndiswrapper -- your driver will most likely be different.  For the actual installation of the ndiswrapper program, the methodology is the same:

[http://ubuntuforums.org/showthread.php?t=487404](http://ubuntuforums.org/showthread.php?t=487404)

---

### Post by bigken on 2007-06-30
what make and model is your wireless dongle/card

---

### Post by bigken on 2007-06-30
in the ndiswrapper folder look for a file called read me or install this will tell you how to install the package its usually something like 

go into a terminal

cd <directory>


./configure
make 

make install

---

