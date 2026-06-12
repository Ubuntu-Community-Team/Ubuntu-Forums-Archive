---
title: "Looked but can't find an answer to this wireless issue"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by drakeskywing on 2008-01-31
Well here is my problem, I am currently using Ubuntu 7.10 Gutsy Gibbon, using the Intel(R) PRO/Wireless 3945ABG Network Connection driver, and i am trying to connect to my DSL-G604T. Every time i select my nm-applet, and select my ESSID, i have tried with WEP and with no security, but it turns to the signal thing and shows me as having a signal of ~90% but i cannot access the net, or even the router. I have made sure i have the latest drivers, i have made sure i don't have MAC Filtering on, it doesn't give me an IP, Subnet mask, or anything.

I have used ndiswrapper -l and it doesn't have any drivers installed and i have no clue where to get the appropriate drivers since i can't even find what wireless card i am using, and all i know is i am using a Dell Inspiron 640m.

I have been struggling with this issue for a while and have looked through this forum, but can't find anything that has warranted any results.

---

### Post by jan quark on 2008-01-31
open the terminal

and type 
```
lspci 
```

its a long list of all hardware devices, wireless should be somewhere at the bottom

---

### Post by jan quark on 2008-01-31
please post also the results of the following terminal commands
```

ifconfig
```
```
iwconfig
```
```
sudo iwlist scan
```

---

