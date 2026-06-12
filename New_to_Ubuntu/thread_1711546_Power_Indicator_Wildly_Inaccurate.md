---
title: "Power Indicator Wildly Inaccurate"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-21
I have a Dell Inspiron 1150 running Maverick, and I understand this is a known and commom issue from reading in another thread and seeing all the registered launchpad bug reports.

If I understand correctly for issues with the wireless or display  drivers in past versions the "Ndiswrapper" or something like that was used to use the propritary drivers for Microsoft machines.

My question is this could that "Ndiswrapper" be used to load the original power system drivers to correct these issues, or is that only for wifi or display, what ever it was originally used for?

If not anyone have any other possible solutuons? I mean this thing is crazy bad off it will tell me one second the battery is totally full and not 2 seconds later it says its about to die.

Any help is appreciated.

---

### Post by cariboo on 2011-03-22
Ndiswrapper was designed to allow someone to use windows wireless drivers when there wasn't a suitable Linux module. I didn't work for graphics drivers, and it won't  work for any other drivers.

---

### Post by DGINSD on 2011-03-28
> **cariboo907 said:**
> Ndiswrapper was designed to allow someone to use windows wireless drivers when there wasn't a suitable Linux module. I didn't work for graphics drivers, and it won't  work for any other drivers.

Thank you sir, now I know.

---

