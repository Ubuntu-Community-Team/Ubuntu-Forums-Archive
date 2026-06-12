---
title: "installing office in Virtual box?"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2011-06-19
Could anyone please let me know how to install Microsoft office on Windows XP in a virtual box please?  When I insert the install CD XP doesn't see it and nothing happens? this is the same with my Blackberry software disc and the Sat Nav software disc!?

---

### Post by YesWeCan on 2011-06-19
Probably, you haven't selected the CD device in the VB Devices menu.

The way it works is that you have to explicitly tell VB to take control of devices from the host. Otherwise you would have the host OS and the guest OS fighting over things.

Once you tick the CD drive in the Devices menu, and the Office CD is inserted, XP should detect it.

---

### Post by crispy_420 on 2011-06-19
You need to let VBox accept the real optical drive as its source. This is usually done outside the virtualized OS.

---

### Post by crispy_420 on 2011-06-19
I should have been more clear looking at my previous post today. Right click the VM in the manager screen (the name they call the main screen) and select settings. Left click to select "Storage" on the left. There is most likely an image of a CD/DVD there, highlight it. On the right you can then select the physical drive or an ISO image.

---

### Post by wildmanne39 on 2011-06-19
Hi, also you can find all the information you need at virtualbox website.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

