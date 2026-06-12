---
title: "smcwusb32 wireless usb not detected plea for help"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by homy06 on 2006-08-02
hey my wireless is the last thing i need configured and i'm free from windows. I have a smcwusb32 wireless usb drive. The flashdisk is recognized but the wireless isn't. SMC has no linux drivers, but i've read of people on other forums getting it to work like this guy:

[http://www.linuxquestions.org/questions/showthread.php?p=2180577#post2180577](http://www.linuxquestions.org/questions/showthread.php?p=2180577#post2180577)

but when i put cd /media:/sda1/wlan.exe, it can't go to that directory.

PLease any help or tutorials would be much appreciated.

oh, i'm new to this linux thing.

---

### Post by homy06 on 2006-08-02
oh device manager does pick it up as an wlan device but no driver.  and i tried to ndiswrapper the driver from smc site and the one on the disk, no go, says "invalid driver!".

---

### Post by homy06 on 2006-08-02
solved. during my trial and error process, i somehow managed to get something in the systems->administration menu to pop up a "windows wireless drivers" and viola, the driver from the usb was detected.

---

### Post by Balachmar on 2006-10-01
You don't know how anymore, because I am having the same problem.
Did you need ndiswrapper or not? Although mine is a SMCWUSB-G
OK, I solved the problem quite easily using ndiswrapper and the windows driver.

---

