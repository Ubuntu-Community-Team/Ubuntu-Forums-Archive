---
title: "Monitor Network Utilization from Command Line"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by lobo235 on 2008-03-31
Does anyone know of a command-line tool that I can use to see network utilization statistics including throughput in and throughtput out from the command-line?

Any help is appreciated.

---

### Post by nsche on 2008-04-01
Will netstat -i -c do what you want.  It has so many options it probably will have what you want somewhere.

---

### Post by lobo235 on 2008-04-03
After doing more research I found a bunch of terminal applications that monitor network traffic. The two that I liked the best were **bwm-ng** and **iftop**. Both are very useful and powerful. I wanted to post what I found in case anyone else needed a way to monitor bandwidth usage, throughput, or network utilization from the command line.

Both of these programs can be installed via apt-get with the below commands:
```
sudo apt-get install bwm-ng
sudo apt-get install iftop
```

---

### Post by Matt512 on 2008-07-15
Very helpful, thank you.

---

