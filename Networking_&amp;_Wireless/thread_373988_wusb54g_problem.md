---
title: "wusb54g problem"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by Oldstyl3 on 2007-03-01
sorry I'm sure that many of you have heard this same complaint many times before, but I've been working on this problem for a few days now, I'm currently in the process of switching to Linux permanently.It would be nice to get some feedback on the steps necessary to enabling a wireless connection through my usb adapter.  I have a usb54g and am stuck at this output:

Installed drivers:
load    invalid driver!
wusb54gv2               driver installed, hardware present 

at one point the device was being recognized by the computer but couldn't communicate to the network, now I'm just lost because I can no longer communicate to the device.  

Any explanations of why this behavior occurs or even what is going on would be much appreciated.

---

### Post by Floppyjoe on 2007-03-01
Try this command to get rid of the invalid driver you have listed there called "load"
```
sudo ndiswrapper -e load
```
Then to see if that got rid of the invalid driver:
```
ndiswrapper -l
```

---

### Post by Oldstyl3 on 2007-03-02
Alirght I followed your instructions Floppyjoe, thanks for that.  What is the next step now?  the output now reads as follows:

Installed drivers:
wusb54gv2               driver installed, hardware present 

I think I'm close but don't want to jump to any conclusions and make sure that I am doing things correctly.

---

### Post by Oldstyl3 on 2007-03-02
nvm I think I solved my problem.

---

