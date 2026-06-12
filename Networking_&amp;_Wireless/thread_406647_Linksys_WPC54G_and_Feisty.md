---
title: "Linksys WPC54G and Feisty"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by Gina on 2007-04-11
I have Dapper running wireless sucessfully on 3 PCs using ndiswrapper and the Windows driver but am now trying Feisty as that looks quite an improvement generally.  Edgy gives problems that don't occur with either Dapper or Feisty.  I'm using my laptop as a test machine whilst continuing to run Dapper on my desktop.

I have a Linksys WPC54G wireless card (bcm4306 rev3 chipset) in my laptop.  Having tried various things with ndiswrapper including compiling the latest version, all without success, I found a post using fwcutter to get the firmware from the Windows driver and use that and the built-in kernel driver.   (Though admittedly the post referred to Edgy rather than Feisty.)  Well it gets much further but still won't actually connect.  **iwconfig** shows it recognising the router AP and a sensible signal level etc. **iwlist scan** shows the router too.  However, I cannot access the router (let alone the net) - even **ping** doesn't work.

Also, after rebooting I find it has lost the ESSID setting though still shows the AP MAC address.  I think this may be a separate issue - something I've not set to keep.

Any help would be much appreciated.

---

### Post by adampyre on 2007-04-19
Hey, have you tried this post? [http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3](http://ubuntuforums.org/showthread.php?t=405990&highlight=wpc54g+v3)

This is how I got mine going. Super simple after being so super frustrated....

---

