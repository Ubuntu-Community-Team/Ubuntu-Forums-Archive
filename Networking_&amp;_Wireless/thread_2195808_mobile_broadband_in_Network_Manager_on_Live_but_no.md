---
title: "mobile broadband in Network Manager on Live but not installed Ubuntu-Genome"
date: 2013-12-26
forum: Networking &amp; Wireless
---

### Post by dlw_insulin on 2013-12-26
Hi,

The live 13.10 Ubuntu-Genome on a USB works great with Huawei mobile broadband and 
mobile broadband appears in Network manager and connection to internet immediate.

Not so if I am install this. No /dev/ttyU* and no choice for mobile broadband in network 
manager. Looks like someone completely deleted support for mobile broadband. Anyone 
know what's going on?

Thanks!

---

### Post by varunendra on 2013-12-30
Some of the working Huawei 3g modems have been reported to be failing to work on latest kernels even though the usb_modeswitch and related packages seem to have support for them. So it may be a bug in the updates that might be causing this.

Please compare the versions of these in your live and installed sessions -
```
uname -r
dpkg -l | grep usb-modeswitch
modinfo option | grep version
```

And in your installed system (after a fresh reboot), plug in the modem > wait for about 20-30 seconds, then post back the outputs of -
```
lsusb
dmesg | tail -40
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

