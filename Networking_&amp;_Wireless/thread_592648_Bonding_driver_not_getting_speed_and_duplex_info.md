---
title: "Bonding driver not getting speed and duplex info"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by sricketts on 2007-10-26
I am trying to set up a bond of two wireless NICs with Atheros AR5212 chipsets. I am getting a warning from dmesg:

```
bonding: bond0: Warning: failed to get speed and duplex from ath0, assumed to be 100Mb/sec and Full.
```

I've snooped around the bonding code a bit, and it looks like the warning is generated when a call to ethtool_ops->get_settings fails. This function I think gets defined by the device driver. I am using Madwifi.

Anyway, my bond setup works fine when I use wired NICs, but fails when I swap in the wireless NICs. The only help from dmesg is the warning in question. So my thinking is that if I can get rid of the warning, I might be able to get my wireless bonding setup working.

So this is where my lack of understanding of ethtool, madwifi, etc becomes apparent. Could someone please help me understand what is going on here?

Thanks,
S.

---

### Post by sricketts on 2007-10-26
I have a few more pieces of information to add.

1) A grep of the madwifi code shows no definition of the ethtool_ops struct
2) Greps of wired NIC drivers e100, e1000, and b44 show ethtool_ops being defined

So in light of 1 and 2, the way to fix the warning seems like it would be to define an ethtool_ops->get_settings in madwifi. My question is then, what should this function look like? What should the speed and duplex be for a wireless NIC? Does this even make sense?

---

