---
title: "Forcing ppp interface name"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by vvinoth on 2014-01-13
Hi 

I am running Saucy 32bit on my machine. I use wvdial 1.61 for dialling ppp dongles. Basically, when I dial three dongle, one after the other, i get interface name in order, 

dongle1 - ppp0
dongle2 - ppp1
dongle3 - ppp2

But if dongle2 takes more time than the other dongles to dial, then i see

dongle1 - ppp0
dongle2 - ppp2

dongle3 - ppp1, sometimes.

Is there any way to force interface through wvdial or any another way?

Thanks, 
Vinoth Kumar

---

### Post by ian-weisser on 2014-01-14
Map interfaces to hardware addresses using udev rules.
See /etc/udev/rules.d/ for several examples.

---

### Post by vvinoth on 2014-01-15
I have connected 7 ppp in a usb hub and these devices get changed at times. I need to literally map like, usb0 has ppp0 .... and usb6 has ppp6 and not with the hardware addressses.

---

### Post by ian-weisser on 2014-01-15
usb0 and usb6 may be different at each boot, too. Or may be the same 90% of the time...until they unexpectedly (to you) change. That's why the recommended way is hardware address.

---

### Post by vvinoth on 2014-02-13
I added my new pppd in the wvdial.conf, 

[wvdial.conf]
....
PPD Path=/home/vinoth/mypppd9
....

where the mypppd9 has the same permission as /usr/sbin/pppd. In mypppd9 sctipt, I am passing the unit X(desired pppX) to the pppd

$ll mypppd9
-rwsr-xr-- 1 root dip 96 Feb 10 17:36 mypppd9*

[mypppd9]

/usr/sbin/pppd $@ unit 9

In this method, I can force the ppp interface name and its working fine :-D

---

