---
title: "Having troubles with internet connection"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by madebysociety on 2006-12-25
Hey I tried to connect the computer that i recently put ubuntu on and the lights on the bag were glowing saying that it was connected but i can not get it to connect to the internet or anything what can i do? please help

---

### Post by dbott67 on 2006-12-25
Can you post the output of the following commands:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
route -n
```

Also, can you describe your network layout & connection to the internet?

Thanks,
Dave

---

### Post by madebysociety on 2006-12-25
where do i put those codes in. and my network layout is a cabel modem going into a dlink router and i use lan cables to connect to the computer

---

### Post by dbott67 on 2006-12-26
The commands would be entered in the terminal (click **APPLICATIONS > ACCESSORIES > TERMINAL**).

The Cable Modem / D-Link router is a good setup... we should be able to get you going pretty easily.

-Dave

---

