---
title: "WUSB54Gv2 help?"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by Night on 2005-11-16
So Im currently trying to get ndiswrapper set up for my wirless usb adapter. I downloaded all the drivers that Linksys has listed for WUSB54Gv2. I then loaded them using:
```
sudo ndiswrapper -i
``` then when is used ```
ndiswrapper -l
``` it always listed them as invalid. So am I forgetting something, could it be because im using the preinstalled version of ndiswrapper rather then compling my own. I did install ndiswrapper-uttils (or what ever its called) throught syanptic (again not sure of exact name). So can anyone help?

---

### Post by taurus on 2005-11-16
It should be 

sudo ndiswrapper -i /path-to-where-the-driver-is-located/<filename>.inf

---

### Post by Night on 2005-11-16
I use all the command while in the directory where the drivers are located. Also 
```
sudo ndiswrapper -l
```
This loads the driver affiliates fine it just says its an invalid driver (or something to this affect) making me believe that it is having trouble detecting my usb device (hmm will need to check gnome device manager when I get home) or that Im just getting the wrong driver.

Well hope someone can help me with my difficulties.

---

