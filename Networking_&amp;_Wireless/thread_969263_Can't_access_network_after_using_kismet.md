---
title: "Can't access network after using kismet"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by oonska on 2008-11-03
Hello, I am running Ubuntu 8.10 and have installed kismet. I believe I have it configured properly, and the program runs just fine. However when I quit the program it doesn't take my card out of monitor mode. I checked iwconfig and it confirmed this.
I tried to get it to switch back to managed mode by using the following commands:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```
After using these commands I check iwconfig again and it said the interface was in managed mode. 
However when I tried to join my network again I was not able to get past the stage where I request an IP address.
So is there anything else I could try to fix this issue?

---

