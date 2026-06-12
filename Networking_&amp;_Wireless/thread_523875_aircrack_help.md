---
title: "aircrack help"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by Abss1185 on 2007-08-12
Hello, when i run aircrack and start to gather packets from a bssid/AP or w/e it is, my wireless card just stops halfway or so before i have enough IVs, anyone know how i can keep my wifi on till i get enough IVs? Thx in advance.

---

### Post by ankorie on 2007-08-26
hello I had a problem very close to that one. I wrote a simple script to keep my card in monitor mode and on the right channel (or scan) it looked like this:

```
while true
        do
        sudo iwconfig ethx channel x 
        sudo iwconfig ethx mode monitor
        sleep 60      
        done
```

remember it is unmoral to crack other peoples wifi networks

---

