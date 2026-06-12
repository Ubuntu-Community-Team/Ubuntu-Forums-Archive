---
title: "Laptop Won't Boot unless wired first"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by jmblakey on 2007-06-27
So, I have a little bit of a weird issue.  I installed my wireless driver without any issue and it connects fine once the laptop is booted. The hitch is that it freezes during bootup at configuring network interfaces if I do not have a wired connection plugged in. My wireless if configured for my home network in the interfaces file.

Not sure if it's related but I also tend to get "Failed to access /dev/sbd1: no such file or directory"
Now I think I heard this was a flash drive or removable device of some kind, why would it still be looking for it?

Any help would be wonderful!

Oh, yeah...I'm using a dell truemobile 1350 wireless

---

### Post by sargeras on 2007-06-27
I think you may have the sdb1 automounting on bootup.  This causes your computer to try to load it everytime it is turned on.  Not sure how to fix this.

I had a problem with Dapper when the eth0 was unplugged.  For me, hitting Ctrl+C during the stall allowed the computer to continue booting.  I think it was a problem with the timeout.  It would boot eventually, in like 2 minutes, if I didn't do this.  Does yours actually boot if you wait long enough?  Try going into the network settings and uncheck the "start at boot" option for your eth0.

hope this helps some

---

### Post by jmblakey on 2007-06-27
The automount makes sense, I'm not sure where it would be either.  The stall started happening after the wireless, but the sdb1 MIGHT have started after installing Automatix's .....ah ha.....
Ok, so I talked myself to a solution :KS.  I apparently had a usb drive plugged in while installing Automatix Switcher

Alright, so now we just need a solution for the configuring network interfaces hangup.

---

