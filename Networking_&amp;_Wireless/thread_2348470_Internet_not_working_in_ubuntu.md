---
title: "Internet not working in ubuntu"
date: 2017-01-04
forum: Networking &amp; Wireless
---

### Post by raadyhere on 2017-01-04
I have a dual boot windiws 10 and ubuntu 14.0.4. Internet is working fine in windows but not able to access in ubuntu. Any suggestions please. Its a wired connection and i have ipv4 setting >method:manual> enetered details as i did in windows. It shows connection is established but when open browser says no connection. 
I tried pinging an ip address and it responds. "64 bytes from x.x.x.x: icmp_seq=45 ttl=64 time = 0.667 ms

---

### Post by raadyhere on 2017-01-04
gedit /etc/resolv.conf modifying the nameserver 8.8.8.8 resolved my issue.

---

### Post by raadyhere on 2017-01-04
the above solution that i posted resolved my issue but I have to do repeat that every time i start my system , please help me with the issue.

---

### Post by ajgreeny on 2017-01-04
Open dash with the top icon in the launchbar and type "network connection".
In the window that appears highlight the connection you have and click on Edit.  Now in the ipv4 tab set the network as shown in my screenshot and see if that helps.

---

