---
title: "R40 laptop"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by manners2345 on 2011-04-03
Here I am again, Have an old IBM R40 laptop. Cannot use USB or Cd to try and format and reload OS. Have Ubuntu 10.04.1 on both, flash drive and CD, apparently no drivers loaded.:confused::confused: Have an Internet connection, 

Problem is: laptop quites responding, the screen turns gray, and stays that way for varying periods if time. Have absolutely no idea as to cause, seems to have started when I upgraded my Internet Speed to 3MB and wireless. When I had a 2MB and no wireless seemed to work good

Example: if trying to use Firefox, open office or any other app

Is there away using command line get rid of current 10.10 version an load 10.04

---

### Post by mörgæs on 2011-04-04
What do you mean by 'no drivers loaded'?

My guess is that the machine is too old for booting from USB, but what exactly happens if you boot from CD?

Go for 10.04.2 rather than 10.04.1. There are some important bug fixes in the new release.

---

### Post by wep940 on 2011-04-04
Normally when the screen grays and quits responding for various times it means that the CPU is being topped out - extremely busy.  We can try to look into that, but first, as mörgæs pointed out, your laptop may be too old to boot from USB.  Check the BIOS setup screens, look for boot order, and see if it allows you to specify USB.  Also, if by no drivers loaded you mean the drivers that normally come on a CD for a PC, be it chipset drivers or device drivers, remember that in Linux you don't install those drivers - those drivers are for Windows only.  Linux will normally have most if not all of the drivers you need already built in.  Some devices require additional work to get a driver.
 
I would open the system monitor and be sure to have the view so that you can see CPU usage, swap usage and memory usage.  Then try what ever it is you've been doing when the screen grays.  Check the system monitor screen and see if the CPU is pegged or if swap usage is up.
 
As far as going back to 10.04 from 10.10, I've always been under the impression (I could be very wrong) that you don't just fall back.  You actually have to re-install to remove the new version and install the older version.  It's possible that a kernel update in 10.10 may be part of your problem - get to the grub menu at boot and try selecting an older kernel if 1 is available.
 
Check the system log (dmesg) to see if there are any big errors or warnings showing in the log.

---

### Post by davidmohammed on 2011-04-04
> **manners2345 said:**
> Here I am again, Have an old IBM R40 laptop. Cannot use USB or Cd to try and format and reload OS. Have Ubuntu 10.04.1 on both, flash drive and CD, apparently no drivers loaded.:confused::confused: Have an Internet connection, 

Problem is: laptop quites responding, the screen turns gray, and stays that way for varying periods if time. Have absolutely no idea as to cause, seems to have started when I upgraded my Internet Speed to 3MB and wireless. When I had a 2MB and no wireless seemed to work good

Example: if trying to use Firefox, open office or any other app

Is there away using command line get rid of current 10.10 version an load 10.04

This laptop came originally with 256Mb RAM - how much have you got?  I suspect the key issue may be the RAM - you should look to have at least 1GB.

---

### Post by mörgæs on 2011-04-04
If there is less than 512 MB, Lubuntu is worth trying. Remember to have Flashblock on all browsers.

---

