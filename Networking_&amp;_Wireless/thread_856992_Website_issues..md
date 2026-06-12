---
title: "Website issues."
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by nightwolf2k5 on 2008-07-12
Hi guys,
i have a similar problem that is posted on the below link
```
http://ubuntuforums.org/showthread.php?t=662572
```.

I followed all the instruction including the part where it said that it was a bug and to edit the sysctrl.conf

I did everything and then when i typed sudo sysctrl -p, i get the below message,
```
sudo: sysctrl: command not found
```

What seems to be the problem?

Thanks

---

### Post by pjcvdpol on 2008-07-12
try sysctl instead of sysctrl (skip the "r")

sysctl.conf is located in /etc 

by the way: the midnight commander (mc) may be of help while browing the system. (sudo apt-get install mc)

---

### Post by nightwolf2k5 on 2008-07-12
Thanks for the help, but still does not work.

Websites like adobe, macromedia still does not open

---

### Post by superprash2003 on 2008-07-12
try changing MTU values. it helps sometimes [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by nightwolf2k5 on 2008-07-12
Tried this too. No luck :(

By the way, when i do a telnet [www.adobe.com](www.adobe.com) 80, i get,

Trying 216.104.208.201...
telnet: Unable to connect to remote host: Connection refused

Could this be the problem? I am not behind any firewall though.

---

### Post by superprash2003 on 2008-07-12
hmm..thats weird.. does adobe open through anonymouse [http://anonymouse.org/anonwww.html](http://anonymouse.org/anonwww.html)

---

### Post by nightwolf2k5 on 2008-07-12
Lmao!! You know what? Anonymouse aint opening either.

I donno, i'm thinking there is a problem with flash. Uninstalled and reinstalled, flash, nothing happened. 
I even uninstalled and reinstalled firefox, still nothing happens.

Hey, i am using Firefox 3, u think that might be the prob?

Edit: Tried uninstalling firefox 3 and installed firefox 2, still no luck. Reinstalled firefox 3.

---

