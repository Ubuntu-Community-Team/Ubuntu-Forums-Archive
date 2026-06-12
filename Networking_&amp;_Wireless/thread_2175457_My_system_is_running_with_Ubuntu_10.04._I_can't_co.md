---
title: "My system is running with Ubuntu 10.04. I can't connect idea alcatel netsetter with t"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by manoj_nath_vs on 2013-09-19
My system is running with Ubuntu 10.04. I can't connect idea alcatel netsetter with this OS. In windows 7 it is working. I can't see the modem in network manager. please give me a solution.

---

### Post by TheFu on 2013-09-19
I googled for "alcatel netsetter ubuntu" and didn't find any answers. Looks like Alcatel is not working with Linux at all to make this device supported.  The exact device model might lead to more favorable results.

Ubuntu 10.04 desktop has been non-supported since May 9th this year.  [http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)  However, I noticed that application updates stopped from the upstream providers in late 2011.  Upgrading to Ubuntu 12.04 LTS will provide 5 yrs of support (2017), but probably will not make Alcatel support Linux. Sorry.

If you are willing, it may be possible to discover the specific chips used inside the modem and find similar drivers for Linux. It might work, but it will not be a point-n-click solution if going to that level to make it work.  OTOH, if you can find the exact model number and post it, we might get lucky.  Cross your fingers!

BTW, did this modem ever work under any Linux OS?

---

### Post by manoj_nath_vs on 2013-09-23
Thanks for the reply. 
My system is running with Ubuntu 10.04. I can't connect idea alcatel netsetter with this OS. In windows 7 it is working. I can't see the modem in network manager. please give me a solution. The model No, is ALCATEL ONETOUCH X230E-2BIJIN4

---

### Post by varunendra on 2013-09-23
Hello Manoj, and Welcome to the forums ! :)

Like TheFu mentioned, 10.04 desktop is no more supported and the latest kernel drivers in the currently supported versions *may* make your device work out-of-box.

As such, I'd recommend you upgrade to 12.04.3 (see this [post=12796734]post[/post])

To let us see the device ID of your netwetter device, please post the output of -
```
lsusb
``` while it is plugged in.

Is it a 3g modem?

---

