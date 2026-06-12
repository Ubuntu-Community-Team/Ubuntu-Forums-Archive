---
title: "connect to internet using dsl in unbuntu 6.10"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by zagloba on 2007-09-04
need help with getting on line just install unbuntu 6.10 and try the help
file on how to connect to internet but no luck plz help I do not want to go back to window.l

---

### Post by guardsman85 on 2007-09-04
Is your computer plugged directly into the DSL modem?

---

### Post by zagloba on 2007-09-04
yes ethernet connection not usb

---

### Post by guardsman85 on 2007-09-04
OK, what happens when you execute:
```
ifconfig
```

---

### Post by zagloba on 2007-09-04
not sure how to past the info from linux terminal to window notpad txt
but ther is no errors when i do the command

---

### Post by guardsman85 on 2007-09-04
> **zagloba said:**
> not sure how to past the info from linux terminal to window notpad txt
OK, if you go to Applications  >>  Accessories  >>  Terminal and run the command from there you should be able to select the output with your mouse.  Once you've done this you can right-click and copy to the clipboard and paste to the thread.

To save the output to a file called myifconfig.txt use this command:
```
ifconfig > myifconfig.txt
```
It will be created in whichever folder you are currently in (probably your home folder, but you can type pwd to be sure).

---

### Post by zagloba on 2007-09-04
sorry is not the past im having problem but how do i get the info from linux terminal posted in window os i have to comp one linux one win and i do 
the forums wit the window comp
but once i get internet on linux will be the only os on two comps

---

### Post by guardsman85 on 2007-09-04
Well, if you can't paste it, that's alright.  What are the interfaces listed when you do ifconfig?  The name of the interface is listed on the far left side of the terminal and usually consist of a few letters and often a number.  For example it might say *lo* or *eth0.*

---

