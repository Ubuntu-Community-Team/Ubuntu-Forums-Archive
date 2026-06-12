---
title: "WEP issue..."
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by ephman on 2005-09-04
hi,

i set a 64bit ascii wep with an open authentication.  i tried entering the key into "network monitor 2.10", and i can't connect to the network.  however on my wife's winxp machine the encryption works fine.  has anybody had this problem before and know where can start to fix it?

thanks for the bandwidth,
ephman

---

### Post by davidbb on 2005-09-04
have you tried entering it manually? 

```
sudo iwconfig int essid *essid-name*
sudo iwconfig int key *64-bit-key*
sudo iwconfig int channel *number*
sudo ifup int

``` 

replacing "int" with your wireless interface name and "64-bit-key" with your key. i have a home network with wep set up so it should work..

---

### Post by ephman on 2005-09-04
it's a pain for me to switch between networks like that.  does anybody have maybe a "network monitor" subsitute that would work?

thanks,
ephman

---

