---
title: "Updates crashed system"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by sirius1 on 2009-04-17
Inspirion 910
Ubuntu8.04.1
Bios: A04

Out of the box, two days ago, everything worked great! Started downloads and got error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem E: _cache->()failed, please report...

Popup error messager: The configuration defaultsn for Gnome Power Manager have not been installed correctly.

It ruined my network connections to.  I need help restoring my netwrok connections, then help with the 'dpkg problem.

Code: 
:~$ ifconfig
 lo Link encap:Local Loopback
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:16436 Metric:1
 RX packets:1830 errors:0 dropped:0 overruns:0 frame:0
 TX packets:1830 errors:0 dropped:0 overruns:0 frame:0
 collisions:0 txqueuelen:0
 RX bytes:91500 (89.3 KB) TX bytes:91500 (89.3 KB)

:~$ iwconfig
 no wireless extensions
 eth0 no wireless extensions

:~$ lspci
(card can be seen)

:~$ tail -f /var/log/messages
(curser goes to next line and blinks for an eternity)

Again, I need to get my working network connections back, then address the dpkg issue.

Thank you for your time on my problem...

---

### Post by zvacet on 2009-04-17
Just type in terminal 

```
sudo dpkg --configure -a
```

---

### Post by sirius1 on 2009-04-18
Thanks Zvacet, I ran the code and the terminal displayed a good 10 minutes of rebuilding, then faded slowly to black.

After 20 minutes, I held my breath and rebooted. Everything is back the way it was!

Thank you so much for making my week!

---

