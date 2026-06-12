---
title: "Wi-fi randomly disconnects"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by Grigoriy on 2017-07-23
[h=1][SIZE=3]Hello!
                                
                          
                          Ubuntu 14.04 Desktop I usually connect to  Internet via PPPoE over Wi-Fi signal from my router. The router gets the  Internet from Ethernet cable which comes from my ISP into my apartment.  So it's not a regular Wi-Fi Internet, WLAN just connects my computer to  WIRED PPPoE I get from the ISP. Sometimes what happens is that Internet  stops working and wireless signal in Ubuntu keeps disconnecting and  then reconnecting by itself. And pppoeconf command can't finf PPPoE over  wlan0. Then I have to connect the cable directly to my computer's RJ-45  and re-do pppoeconf and then it finds PPPoE over eth0 and then I get  Internet. The problem is that for some strange reason, it works better  when I use the former option, i.e. connect the cable to the router and  use the wireless signal to connect to the PC. I just don't know how to  fix this issue with my Wi-Fi.[/SIZE][/h]

---

### Post by praseodym on 2017-07-24
Does it work with
```

sudo pppoeconf wlan0
```
What about adding Login/PW directly into the router? Do you have access to its interface?

---

### Post by Grigoriy on 2017-07-24
You might have found the right spot. I did get a router Wi-Fi login screen, though I hadn't changed a thing in that regard. I'll try to check my router. Maybe it needs to be restarted... I'll look into that. Thanks!

---

### Post by Grigoriy on 2017-07-24
SOLVED: Now Wi-Fi is back in order again. Maybe it was a temporary issue  with a signal as someone suggested (meaning that maybe it's neighbors'  Wi-Fi interfered). Who knows. It happens once in awhile and I don't know  why...

---

