---
title: "help! changing back to wireless usb adapter"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by fibo112358 on 2009-01-08
Hi!

To make a long story short, I have been trying to get an unsupported pci wireless adapter to work using Wicd with WPA encryption. I had it connected today, but lost it and cannot get it re-connected using Wicd. Lesson learned: buy Linux supported cards ahhhhhg!

Just to experiment, I booted from the live cd and plugged in an old Dynex usb wireless adapter I thought had given up the ghost a while ago. Lo and behold it connected with WPA enabled...no problems. However, the live cd (or more precisely, the native Linux drivers) does not recognize my troublesome pci wireless card. This is the original problem of course.

I can conclude that the native Linux drivers will run this usb device, so I'd like to use it on my Ubuntu install on my hard drive. The problem is that I have done so much configuring that I don't know how to reenable the correct native driver that is running this usb adapter in live mode, and have Wicd connect using this usb device. Here is what I've done to my system:

1. Installed ndiswrapper and am using it to run the driver for my pci card.

2. I blacklisted some stuff (I can't remember...oh wait, it's in a file somewhere), that I assume is what I'm trying to reenable now. 

3. Installed Wicd (which uninstalled network-manager in the process).

Could someone help me get the correct driver reenabled to run this usb device?

---

### Post by fibo112358 on 2009-01-08
Just got it working.

---

