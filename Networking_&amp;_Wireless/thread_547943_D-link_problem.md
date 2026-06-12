---
title: "D-link problem"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Onay on 2007-09-10
I installed my DWL G132 using ndiswrapper, then I saved my settings using the -m switch. Unfortunately for me, it does not automatically start up this way. For some reason, the two lights that say Act and Link on the adapter do not light up after I restart the computer. The only way they do light up is when I boot into windows first, then do a restart.

Is there any way I can integrate networking to boot up BEFORE ubuntu does? I have ubuntu installed via wubi, but I have had this work in the past. Even when I do boot into windows, then reboot, I still have to run the "sudo depmod -a" and "sudo modprobe ndiswrapper" commands to get the wlan0 to activate.

Any ideas?

---

### Post by spd106 on 2007-09-10
Check the /etc/modules file for a line that says ndiswrapper. If it's not there, add it. 

It might also be a good idea to have a read through this wiki help page. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Onay on 2007-09-11
Thank you very much, I didn't have ndiswrapper as one of the startup modules. If any more problems arise I'll post em, but thanks again.

---

