---
title: "IPW2200 Problems"
date: 2005-04-08
forum: Networking &amp; Wireless
---

### Post by wcbaker on 2005-04-08
I have an Acer Travlemate 8000 series and it has a ipw2200. Ubuntu had it in the Networking options as eth1, but in my attempt to get WPA working there is no more eth1 there. How would I go about getting that back?

Wes

---

### Post by blueplazma on 2005-04-08
In your /etc/network/interfaces file you might find that there is no entry for eth1, or it is commented out.  Try uncommenting it, if you can.  If not, try executing ```
sudo ifconfig eth1 up
``` and see if Ubuntu at least can see eth1.  If it can, then try adding an entry like this to /etc/network/interfaces
```
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        name Ethernet LAN card

auth eth1

```

---

