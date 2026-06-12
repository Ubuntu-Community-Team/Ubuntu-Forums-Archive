---
title: "Application Bandwidth Monitoring"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by rraj.be on 2010-06-23
Is there any application available to monitor bandwidth of each application as we do with kaspersky in windows?

---

### Post by cariboo on 2010-06-23
Have a look at bandwidthd, it is in the repositories, It creates html files, located in /usr/share/bandwidthd.

---

### Post by Deadite81 on 2010-06-23
I like iftop.  It's a terminal app.
```
sudo apt-get install iftop
```
Then in a terminal type:
```
sudo iftop eth0
```
Where "eth0" would be your particular interface.  Mine being "wlan0" on my wireless network.
I don't know if this is like Kaspersky, but it gives bandwidth usage in real-time of everything using an internet connection, detailing the service/ip addresses, etc.

---

