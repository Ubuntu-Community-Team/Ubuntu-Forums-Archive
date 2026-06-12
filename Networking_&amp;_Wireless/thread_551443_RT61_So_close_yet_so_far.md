---
title: "RT61 So close yet so far"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Captaincrash on 2007-09-15
Hello Folks a I am a newbie to Linux let alone Ubuntu. After major problems with my BCM4318 I swapped with my old mand for his RT61 now I have managed to Ping the route using the commands from the Ubuntu documentation site but have thus far been unable to get to the outside world. When I try and do the command
sudo echo "nameserver 192.168.2.1" >> /ect/resolv.conf
I get the error
Directory /ect/resolv.conf unknown
I checked the directory to find it was called resolvconf, I tried this instead of resolv.conf to no avail.

I have got this far on both Kubuntu and Ubuntu.  Any help you can offer would be most appreciated.

---

### Post by unisol on 2007-09-15
try sudo gedit /etc/resolv.conf and enter : nameserver 192.168.2.1, save it and see what happens. also what driver are you using for the rt61? is it a stock driver or did you compile it yourself?

---

### Post by Captaincrash on 2007-09-15
Will do.

I am using the inculded stock driver.

---

