---
title: "Error for wireless request"
date: 2021-01-29
forum: Networking &amp; Wireless
---

### Post by moto1860 on 2021-01-29
Hi all, tonight I got disconnected from the network while using the laptop, it sometimes happens so I didn't bother reconnecting right after, now I just can't re-connect to it, cell phone and Fire Stick are connected and working.

 ```
avo@avo-Latitude-E5430-non-vPro:~$ iw dev
phy#0
    Interface wlp2s0
        ifindex 3
        wdev 0x1
        addr a4:17:31:a4:e1:84
        ssid PARCO TIRRENO GUEST
        type managed

avo@avo-Latitude-E5430-non-vPro:~$ iwconfig wlp2s0 essid PARCO TIRRENO GUEST ********
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlp2s0 ; Operation not permitted.




```

Edit: it was an issue with the provided, it's been solved.

---

### Post by praseodym on 2021-02-07
Please run the wireless script from the sticky thread and show the output

---

