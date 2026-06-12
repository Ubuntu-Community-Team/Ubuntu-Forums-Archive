---
title: "lost internet available networks after update"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by shawnberlin on 2010-01-10
my box has no internet after updates installed! running latest version of Ubuntu. the 'available networks' thingy disappeared from the top bar. no idea how to get this working again, do i need to reinstall from CD or what?

---

### Post by 3rdalbum on 2010-01-10
Either you've removed the "Notification Area" applet from the top panel, or the system is not running the Network Manager Applet program.

Try right-clicking the top panel and choosing "Add to Panel" and then go to Notification Area and click Add.

If that doesn't work, then maybe nm-applet is not running - hit Alt-F2 and type:

```
nm-applet
```

If this works, then check that Network Manager is in your Startup Applications.

---

### Post by shawnberlin on 2010-01-10
no network manager from ''add to panel'' list
nothing happens when nm-applet is entered
 
from startup applications preferences a pop up asks for Name:, Command: comment: not sure what to enter
 
thanks from lisbon!

---

### Post by derekmbarnes on 2010-01-10
Open Applications > Accessories > Terminal and run this:

```
lspci -v | less
```

This will give a detailed (but not too detailed) list of your hardware. Scroll down to the bottom, where you will find Internet devices listed as "controllers." If you can't find information for the device driver (the line will be clearly labeled "Driver"), it probably got lost with the kernel update and has to be reinstalled.

---

### Post by shawnberlin on 2010-01-10
> **derekmbarnes said:**
> Open Applications > Accessories > Terminal and run this:
 
```
lspci -v | less
```
 
This will give a detailed (but not too detailed) list of your hardware. Scroll down to the bottom, where you will find Internet devices listed as "controllers." If you can't find information for the device driver (the line will be clearly labeled "Driver"), it probably got lost with the kernel update and has to be reinstalled.
 
No Driver found, do i got to reinstall the entire ubuntu again from a cd?  what about my data?  appreciate a step by step here or a link to a how to:KS

---

### Post by derekmbarnes on 2010-01-12
You don't have to reinstall Ubuntu; you just need the driver for the hardware. Note down the brand name and device number of your card, then do an Internet search for a downloadable version of the driver. help.ubuntu.com is a fairly good resource; there's a page somewhere that lists various card models and provides instructions for proper installation, but I can't quite remember where it is. It is best if you try to find a Linux-native driver, as using anything made for Windows involves mucking about with ndiswrapper (which I've heard is a pain to use).

Good luck!

---

### Post by andrea.ca on 2010-01-12
Why would an update result in losing a driver?
 
I did an update yesterday and also lost internet connection with the same problems mentioned above.

---

