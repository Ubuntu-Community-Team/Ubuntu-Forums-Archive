---
title: "Ubuntu server - sharing printers"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-11-30
Setting up an Ubuntu file/print server at home. Have this issue with seeing the networked printers. I need to run these commands before they are visible to other computers:
```
family@svlamserver:~$ sudo service smbd restart
smbd start/running, process 1531
family@svlamserver:~$ sudo service cups restart
cups start/running, process 1544
```
Any idea why? Once I've done that, it all works fine.

Also, I have hooked up the printer without difficulty to Windows clients (after installing drivers).. but how do I link it up to Mac OS X? I have installed the drivers there but it's being an ***. Printer is a Canon LBP3100B, Mac is a Macbook Pro 15 2010, running 10.6.4.

---

### Post by Pas_sa on 2010-11-30
OK.. got the Mac printing.. adding a raw printer on OS X is ridiculously difficult.. but I still need to restart those two services to have the printers shared on reboot.

Any ideas?

---

