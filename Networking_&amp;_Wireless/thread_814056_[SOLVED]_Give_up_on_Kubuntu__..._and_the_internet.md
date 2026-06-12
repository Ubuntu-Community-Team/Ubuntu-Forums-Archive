---
title: "[SOLVED] Give up on Kubuntu  ... and the internet"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by savsav on 2008-05-31
I am connected to the internet thru a 56K external serial modem.


I Telnet and it says I am connected.

But I cannot load any pages on browser. I have 
Kubuntu 8.04 with KDE 3.5

I may be having a "defaultroute" problem, which is rather common, judging from what I've read online.

I need HELP solving this issue!

---

### Post by superprash2003 on 2008-05-31
type ping google.com in your terminal and post output here

---

### Post by savsav on 2008-05-31
PING google.com (64.233.167.99) 56(84) bytes of data.


and here's telnet


```
telnet google.it 80
Trying 216.239.59.104...
Connected to google.it.
Escape character is '^]'.
```

---

### Post by savsav on 2008-05-31
Here's more info, in case it's useful.

I went to terminal and typed ROUTE


This is the result:


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
mia4-dial1.pops *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0
```

---

### Post by savsav on 2008-05-31
A little help, people!

---

### Post by savsav on 2008-05-31
PROBLEM SOLVED!


I installed Firefox on my Kubuntu computer, and I can now surf the web perfectly!

I still cannot surf using Konqueror. Konqueror is crap.


Thank God for firefox.

---

