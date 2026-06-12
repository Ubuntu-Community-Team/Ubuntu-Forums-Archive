---
title: "whats wrong with this script?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by cosmoshell on 2009-08-04
gksudo ifconfig eth0 down & sudo macchanger -r eth0 & sudo ifconfig eth0 up

i want to run this buy clicking on its icon.

---

### Post by credobyte on 2009-08-04
[COLOR=DimGray]&[/COLOR] should be replaced with [COLOR=DimGray]&&[/COLOR] and [COLOR=DimGray]gksudo[/COLOR] with[COLOR=DimGray] sudo[/COLOR]:
```
sudo ifconfig eth0 down && sudo macchanger -r eth0 && sudo ifconfig eth0 up     
```

---

### Post by wizard10000 on 2009-08-04
Also, test each command separately in the same terminal window.  

'&&' is conditional - it'll only move on to the next command in the string if the previous command returned an exit status of 0.

---

### Post by cosmoshell on 2009-08-04
> **credobyte said:**
> [COLOR=DimGray]&[/COLOR] should be replaced with [COLOR=DimGray]&&[/COLOR] and [COLOR=DimGray]gksudo[/COLOR] with[COLOR=DimGray] sudo[/COLOR]:
```
sudo ifconfig eth0 down && sudo macchanger -r eth0 && sudo ifconfig eth0 up     
```
strange did it like that before and it dident work. does now tho. thank you

---

### Post by credobyte on 2009-08-04
> **wizard10000 said:**
> Also, test each command separately in the same terminal window.  

'&&' is conditional - it'll only move on to the next command in the string if the previous command returned an exit status of 0.

Which is pretty much exactly what most of these scripts need. If turning network off fails, changing mac is useless ( not to mention that trying to turn on already running service is impossible ).

---

### Post by achase79 on 2009-08-04
using sudo in a script is a bad precident.  Executing the script with sudo or gksu is more appropriate.

---

