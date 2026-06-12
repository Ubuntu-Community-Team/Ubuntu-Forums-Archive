---
title: "IPW2200 native WEP and wpa_supplicant concflicts"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by InuY4sha on 2008-08-09
Hi All guys,
I'm having troubles with ipw2200 driver WEP;
I installed everything correctly, I can connect to networks and all, BUT when I want to use WEP encryption [with network manager applet] apparently I have troubles: it keeps asking for the password and then I keep staying unassociated... the thing I'm wondering is: the latest firmware (3.0) which I have installed with the latest drivers (1.2.2) should natively support on-chip WEP encryption... but I see that when I write the asked WEP password on the network manager popup, wpa_supplicant starts running in background.

Is there the possibility that 2 WEP encryption algorithms are working and conflicting together at the same time ??? 
If you are wondering how am I writing here, I just created a file "ipw2200"
in /etc/modprobe.d/ and added the line "options ipw2200 hwcrypto=0"
Could this be helping??? I wonder what will happen the next time I disconnect... 
WPA works like a charm btw and Monitor mode as well (nice feature!) :)

---

### Post by chili555 on 2008-08-09
If I am reading correctly, according to *modinfo ipw2200* this:```
options ipw2200 hwcrypto=0
```is the default. I don't think you have changed anything.

I suggest trying:```
sudo rmmod ipw2200
sudo modprobe ipw2200 hwcrypto=1
```See if this changes your ability to connect with WEP.

---

### Post by InuY4sha on 2008-08-09
Makes sense (I've checked that and you are right), but the point is that checking around the forums I've seen many people writing this option into that file, AND MOST OF ALL .. I'm now able to connect easily... (I mean.. I just got disconnected 10 secs. ago and I easily reconnected).. maybe it's just luck ... maybe not!
I'll post about my experience while looking forward to yours :)

Oh another thing that I've noticed right now is that now with that option (hwcrypto=0) I don't see anymore the Encryption activated when calling iwconfig...
This would appoint my solution as being not wrong...

---

### Post by chili555 on 2008-08-09
> checking around the forums I've seen many people writing this option into that fileI've seen a lot of funky stuff recommended on these forums, too. Some advice I read and mutter to myself, "If that works, I'll drop dead in my chair!" I may have given some questionable recommendations myself!

My guiding principal is 'does it work?' If hwcrypto=0 makes your card sing, then that's what you should use. If you try hwcrypto=1 and it works even better, then that's what you should use. > I'll post about my experience while looking forward to yoursI don't have a 2200; but I have laptops with 2915ABG and 3945ABG, which are similar. Also, I like to read *modinfo.*

---

