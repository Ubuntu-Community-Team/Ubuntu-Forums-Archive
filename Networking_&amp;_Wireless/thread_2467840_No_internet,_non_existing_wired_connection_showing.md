---
title: "No internet, non existing wired connection showing instead of wifi"
date: 2021-10-09
forum: Networking &amp; Wireless
---

### Post by redline22 on 2021-10-09
Hi! 
I've been googling for the past 2 hours and could not find a solution. 
It all started when my computer froze, so i looked up online and rebooted it 

 holding alt and prtSc snd typing r e i s u b 

After the reboot, there was no internet, the wifi logo was gone and instead I see the wired connection logo instead. Even though the computer is still connected to a working wifi. 
In settings there are no wired connections to cancel either. I would post pictures but I can't find how on mobile.

Im using ubuntu 20.04. 

Ty!

---

### Post by VMC on 2021-10-09
On "Settings" , does it show "Wi-Fi"

From a Terminal type this and show output ```
ls /sys/class/net
```

---

