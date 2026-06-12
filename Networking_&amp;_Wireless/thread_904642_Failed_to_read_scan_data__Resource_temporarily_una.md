---
title: "Failed to read scan data : Resource temporarily unavailable"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by Leo Simon on 2008-08-29
I'm running Hardy on a D630 latitude.   Most of the time, wireless works fine, but after a while of happy connectivity, I lose my connection, and get the dread message when I try to scan:
"Failed to read scan data : Resource temporarily unavailable."   In order to get my wireless back, I then have to reboot.   Then everything is fine until the next time it happens.    

Can anybody advise please?

---

### Post by itsjareds on 2008-08-29
Happens to me too. I'm using a NETGEAR WPN111 USB Adapter. What wireless card are you using?

Also, I've noticed that each time I restart when this happens, I have to unplug/replug the adapter after it starts the reboot, and before Ubuntu loads. Otherwise, my device stays blinking even after I restart (normal restart).

---

### Post by itsjareds on 2008-08-30
Bump :-\"

Edit: Also, my device does scan and show all connections when I do```
iwlist scan
```

---

### Post by johnvarenda on 2009-11-30
Hi there..
Is there anybody to give a solution for this..
What does this mean.  Won't scan memory or files.  My computer keeps shutting down.
................

[data entry india]("http://www.e-datapro.net")

---

### Post by Minty Pine on 2010-11-21
While this thread is fairly old, I've found a sort of work-around for this problem short of giving in to buying a new wireless adapter.  

If you've connected to your wireless before:
the connection information should be saved.  Click on 'Network Manger', and click on 'Connect to Hidden Wireless Network'.  Select your network from the drop-down menu, and connect.

If you haven't connected to your wireless before:
if know your wireless network name and passcodes, click on 'Network Manger', click on 'Connect to Hidden Wireless Network', and enter your wireless information.  Click on 'Connect', and hopefully it will connect.    

Other information regarding my adapter:
I used this adapter (a really old MN-510) with WinXP and had to unplug/plug repeatedly every time I rebooted after buying a new router.  So, for me, the problem is most likely my wireless adapter is outdated or degrading.  
The default 'prism2_usb' driver "worked" with my adapter to find networks and connect, but the speed was worse than dial-up.  So, I installed the mn510.inf driver using 'ndisgtk', completely wiped the default linux drivers, and had the same difficulty connecting as I did with XP.  

Anyways, my connection is back to "normal" speed (meaning fast- yay!), but with most every boot, I have to connect via hidden network, which isn't nearly as bad as spending five minutes scrunched over plugging and unplugging a USB cable.  

If any one has a better solution (other than buying a new wireless adapter), I'd be glad to hear it.

---

