---
title: "Ubuntu server cannot see network card"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by erosion on 2008-01-21
1. installed ubuntu server.
2. installed lamp
3. installed a network card 
4 .edited config file with i.p. numbers
Then concluded that ubuntu server cannot see the network card. How can i make ubuntu server see my network card? any clues anyone

---

### Post by burbankmarc on 2008-01-21
open a terminal and type 

```
ifconfig
```

if you get an eth0 then it is detecting your card.

if not type 

```
lspci
```

and paste the output

---

### Post by erosion on 2008-01-22
i did all that sort of thing :-)
As a last resort i just started again and install in all again, The effect was that everything now work and the network card is visable the the system. I supose that the thing i learned from this is : make sure you have a network card in first.:lolflag:

---

