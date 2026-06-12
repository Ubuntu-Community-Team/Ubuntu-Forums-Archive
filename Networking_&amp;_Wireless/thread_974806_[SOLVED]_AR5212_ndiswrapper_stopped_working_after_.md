---
title: "[SOLVED] AR5212 ndiswrapper stopped working after 8.10 upgrade"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by heluani on 2008-11-07
Hi there, I just did the software upgrade from Hardy to 8.10, the upgrade installed the madwifi drivers ath_pci for my atheros card (on a Lenovo X61T) and my previous working wireless (with ndiswrapper) stopped working.

Now if I'm more than 3 meters away from my wireless router I don't have any wireless (something also happened with ath_pci in Hardy)

But the biggest problem I have is that ndiswrapper doesn't work either, I can't get to see any wlan0 interface!, everything else seems to work fine, namely, modprobe ndiswrapper doesn't give any issues!

Any thoughts?
h

EDIT, looking at /var/log/syslog I find tons of these messages:

```
 ndiswrapper (load_wrap_driver:108): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
```

---

### Post by MewRS on 2008-11-07
Probably the same issue that we are trying to solve here: [http://ubuntuforums.org/showthread.php?t=973420](http://ubuntuforums.org/showthread.php?t=973420)

---

### Post by heluani on 2008-11-07
Not really sure if in that thread there a single problem :) or there are plenty of related ones... now in  my case I'm even worse cause I'm not sure why, but now I can't even see the ath0 and wifi0 ifaces (got rid of ndiswrapper and now I can't even see the restricted modules showing up!)

R.

Well, ath5k seems to be working better for me. It was enough to try ```
athenable ath5k
``` it has been working fine with WPA2 for the last 5 minutes without dropping too much signal

---

