---
title: "OpenSSH-server always starts at bootup!"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Mb0742 on 2008-07-18
How do I stop that so I can only start it up when I physically start it myself with sudo /etc/init.d/ssh start  ?

---

### Post by dmizer on 2008-07-18
system > administration > services

uncheck "remote shell server (ssh)"

---

### Post by ilrudie on 2008-07-18
If you don't have a gui going you should be able to find it in /etc/rc2.d/.  It will have a name like S##openssh.  Something like that.  Anyways just change the capital letter S to a lower case s and it shouldn't run at boot.  This of course is if you boot to runlevel 2.  If you boot to a different run level then change that rc#.d/.  If you are not sure use ```
runlevel
``` to find out but if you aren't sure its probably 2.

---

