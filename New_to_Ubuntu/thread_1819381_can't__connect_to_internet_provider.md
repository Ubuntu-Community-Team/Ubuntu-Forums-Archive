---
title: "can't  connect to internet provider"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by scorpious on 2011-08-06
I was playing around on my computer today and installed network-manager. The computer asked me to restart and afterwards I couldn't browse the internet or download and install anything. 
I connect through pppoe.
I've tried to fix it by using
```
 
sudo pppoeconf

```
but no sucess.
 
It may be important to note that I can bowse to my providers webpage and check my account. I also tried uninstalling network-manager but it didn't make any difference.
 
cheers
Tom

---

### Post by bayvista on 2011-08-06
Are you connected via Ethernet or WiFi?

---

### Post by scorpious on 2011-08-06
Ethernet

---

### Post by scorpious on 2011-08-06
I tried pinging google but it didn't work

---

### Post by Wim Sturkenboom on 2011-08-06
Can you ping 74.125.233.18 or access google with [http://74.125.233.18?](http://74.125.233.18?) If so, you have a DNS issue.

Not behind an Ubuntu machine so not sure where to check.

---

### Post by scorpious on 2011-08-09
Well I found a solution that fixed my problem but I don't know why. Anyway here is what to try for anyone else with this problem;


delete all network connections >> shut down the pc >> Unplug everything from the wall including the network cable >> start the machine back up again without the network cable plugged in >> plug the network cable back in and reconnect using the terminal
```
sudo pppoeconf
```

cheers

---

