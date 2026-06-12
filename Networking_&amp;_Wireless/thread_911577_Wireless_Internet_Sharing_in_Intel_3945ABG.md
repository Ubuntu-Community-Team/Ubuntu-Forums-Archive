---
title: "Wireless Internet Sharing in Intel 3945ABG"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by kemadruma on 2008-09-05
hi,
I have 2 laptops in 1st, i have installed windows, it has internet connection which is shared to wireless network without any static ip or security.

**Now the problem:**

In my second laptop,i have just installed ubuntu desktop edition (8.04), i want to connect to wireless internet which is shared as adhoc, i have intel pro/wireless 3945ABG card.

In ubuntu, it shows the access point, but when i connect,it tries to connect saying "Attempting to connect to SAM (access point name)" then it doesnt connect. My Network manager is also set to roaming mode, and drivers of my wireless card are installed automatically by ubuntu but i dnt think their is any issue with drivers.

:confused:


Reply awaited.
Regards,

---

### Post by dvlong on 2008-09-06
You might search this forum on 'ipw3945' for some answers.  I've been able to resolve an identical problem with the same modem (partially) by following some of the thread started by Jason Kirk.  I say partially because by following some of the instructions there I've gotten my wireless working some of the time. 

If you type iwconfig in your console, does it say "Power Management:off"?  If so, this is connected with the problem and may provide a lead as to how to search for a solution.  

Sorry I can't be of more help at the moment.

---

### Post by kemadruma on 2008-09-24
i m using wicd, which solved my prob, but in case of static ip it works fine but when i select automatic ip in adhhoc mode, it doesnt connect, reply.............

---

