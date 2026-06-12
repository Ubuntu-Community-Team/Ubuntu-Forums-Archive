---
title: "firefox fails to connect"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by don-bothell on 2011-01-07
Firefox defaults to offline mode even after changing it in file
Update Manager fails when trying to get [http://security-ubuntu](http://security-ubuntu) ,,,,,,,,,
Tried removing Firefox with package manager, and reinstalling firefox..
  
that did not help
:(

---

### Post by eriktheblu on 2011-01-07
What is your internet connection? Do you have a direct connection to your computer or is it through a network?

---

### Post by Hippytaff on 2011-01-07
Are you able to ping anything? open a terminal and type
```

ping www.google.com

```
also what is the output of
```

ifconfig

```

---

### Post by don-bothell on 2011-01-09
I have been using Ubuntu 10.04 and Firefox for more than a month without problem.  Then it started defaulting to "offline" on startup and even after
using "File" menu to kill "offline" it fails to connect. 

I AM able to use Firefox without problem on the  Ubuntu 8.04 on this computer.

The following is from startup with "offline" checked.

don@don:~$ ping google.com
ping: unknown host [www.google.com](www.google.com)

don@don:~$ ifconfig
    Link encap:Local Loopback
    inet addr:127.0.0.1  Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MYU:16436 Metric:1
    RX packets:20 errors:0 droppe:0 overruns:0 frame:0
    TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB)

----------------------------------------------------------------
The following is after removing the check from "work offline"

don@don:~$ ping google.com
ping: unknown host [www.google.com](www.google.com)

don@don:~$ ifconfig
    Link encap:Local Loopback
    inet addr:127.0.0.1  Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MYU:16436 Metric:1
    RX packets:108 errors:0 droppe:0 overruns:0 frame:0
    TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:8320 (8.3 KB)  TX bytes:8320 (8.3 KB)

---

### Post by don-bothell on 2011-01-09
Solved: At least it is fixed.  Still do not know why problem arose.
The fix was to run recovery mode.  Why I did not know this or get this advise is interesting !!

---

### Post by Hippytaff on 2011-01-10
Are you constantly running in recovery mode? or did you log into recovery mode and this somehow fxed the issue in normal mode?

---

