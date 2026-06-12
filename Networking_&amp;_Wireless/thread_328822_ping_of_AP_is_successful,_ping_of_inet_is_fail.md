---
title: "ping of AP is successful, ping of inet is fail"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by aDOT on 2006-12-31
DEAR frieds,
](*,) ](*,) ](*,) ](*,) 
i have next problem :
I use ndiswrapper for wlan0, WEP and static IP
wifi AP 192.168.1.1

ping 192.168.1.1 returs expected 
ping 209.85.135.104 returns network is unreachable
ping [www.google.com](www.google.com) returns host is unknown (as i remember, but i am not sure)

what does work wrong?????:( :( :( 
HELPPP

---

### Post by aDOT on 2006-12-31
Hello, again
I faced next strange symptoms:

1. route returns
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0         *                   255.255.0.0     U     0      0        0 wlan0

2. my wlan0 has static 192.168.1.123
but;  ping 192.168.1.123 returns  **network is unreachable **

What does it mean???

---

### Post by PilotJLR on 2006-12-31
Sounds like you have no default route. Try this:
```

sudo route add default gw 192.168.1.1

```

Then... ping an external IP address (like you tried previously). If that works, then ping google.com or something similar (to test DNS).

---

### Post by aDOT on 2007-01-01
Thank you for help,

I tried do next > sudo route add default gw 192.168.1.1

but resut is: **SIOADDRT: No such device**

this is very strange, because i can ping 192.168.1.1, and iwconfig wlan0 returs about access point is OK.
what do you think about above?

---

### Post by aDOT on 2007-01-01
:KS 
sorry,
now inet woks,it looks that i made mistake and wrote 
route add default 192.168.1.1
instead 
 route add default gw 192.168.1.1

a lot of thanks

---

