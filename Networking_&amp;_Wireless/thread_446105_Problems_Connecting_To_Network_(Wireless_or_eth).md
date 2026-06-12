---
title: "Problems Connecting To Network (Wireless or eth)"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by OzzMosiz on 2007-05-16
Ok, just installed Ubuntu 7 Desktop and been playing around trying to get either wireless or wired networking running - so far no joy. tried running: iwconfig

lo       no wireless extensions.

eth0   no wireless extensions.

eth1   unassociated   ESSID: off/any
          mode:Managed  Channel:0  Access Point: Not-Associated
          Bit rate: 0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Encryption key: off
          Link Quality:0   Signal level:0   Noise level:0



I'm guessing this isn't looking good??

can anyone suggest what I need to do to resolve this issue?

Edit: ok I've used sudo iwconfig and now ESSID shows my SID and Encryption Key shows my WEP key,  I ran a dhclient eth1 and still cannot connect (though it worked once!!!!)

I'm baffled

---

### Post by OzzMosiz on 2007-05-16
Wierd alert!! Its working now and I did nothing differently.

---

