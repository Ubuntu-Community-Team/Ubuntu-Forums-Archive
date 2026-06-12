---
title: "slow wireless and fast wired connection"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by stlcoptony on 2007-10-09
I know this has been covered before, but I have tried some of the solutions suggested (like installing wifi radar) and others I didn't quite understand. I get normal download rates (@500kb/s) when I have a wired connection but only 20 or less kb/s when using the wireless. Does anyone know what is causing this or how to fix it? Is this something that will be fixed in 7.10?

thanks,
tony

---

### Post by scrooge_74 on 2007-10-09
I have read about this somewhere and is probably a driver issue, what wireless card do you have? How did you configure it, those are the main points you should post.

---

### Post by stlcoptony on 2007-10-09
where can I find this info on my computer (wireless card model)? I haven't really confiigured anything except what ubuntu does itself, I just selected my wireless network

thanks

---

### Post by scrooge_74 on 2007-10-09
from a command line you can type lspci and start reading until you find it.

Also which model you have? is a laptop right? you can search the net for it you fill find the specs right away

---

### Post by stlcoptony on 2007-10-09
Here is the wireless card model from lspci:
   05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
 The laptop is a fujitsu lifebook t4210. I experience good rates when connected to ethernet (when downloading the initial updates after installation I saw 500+ kbps) but when on the wireless I rarely saw over 20 kbps. This is the only thing keeping me from using ubuntu all the time (already on the desktop)

thanks,
tony

---

### Post by stlcoptony on 2007-10-09
bump

---

### Post by scrooge_74 on 2007-10-09
Do a google search for that model, Intel is usually good in providing open source drivers

---

### Post by stlcoptony on 2007-10-10
when I installed, ubuntu correctly recognized the card model # and everything. Doesn't that mean the driver is already being used?

thanks

---

### Post by scrooge_74 on 2007-10-10
It would appear to be running, but nevertheless check for more info, it could need some tweaking

---

### Post by stlcoptony on 2007-10-18
If I can find a driver from intel for the wireless card, how do I use it? Does anyone know if this has been solved in 7.10?

thanks

---

### Post by scrooge_74 on 2007-10-18
Check ndiswrapper (for using the windows driver) Can't find the thread with the Howto for ndiswrapper, but you should loo into it.

Also check here [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

