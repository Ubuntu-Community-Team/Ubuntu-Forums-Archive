---
title: "Hardy - bad line in ndiswrapper?"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by bilekbp on 2008-05-06
Hi, as a part of getting my Broadcom Wireless Network Adapter working, I added the following line to /etc/modprobe.d/ndiswrapper:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

(line one is: alias wlan0 ndiswrapper)

When updating modules to get lm_sensors working, I received this error:
WARNING: /etc/modprobe.d/ndiswrapper line 2: ignoring bad line starting with 'echo'

Can anyone see what the problem is in the line I posted?  Please be gentle on me, I am a real newbie at this.

Thanks!

---

### Post by Ayuthia on 2008-05-06
> **bilekbp said:**
> echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
The line needs to read:
```
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

You are going to have to go into that file and correct it.  You can do this by:
```
gksu gedit /etc/modprobe.d/ndiswrapper
```
You should be able to find your change on line 2.

It looks like this happened when you were trying to get NDISwrapper up and running.

---

