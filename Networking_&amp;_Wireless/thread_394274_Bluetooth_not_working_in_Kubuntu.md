---
title: "Bluetooth not working in Kubuntu"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by theschwa on 2007-03-26
I'm running kubuntu and I'm trying to use a bluetooth dongle. Using hcitool inq I can find my phone, but I can't find it under bluetooth:/ or the Bluetooth OBEX client.  Here's my hcid.conf.
```

options {
	autoinit yes;
	security user;
	pairing multi;
        pin_helper /usr/lib/kdebluetooth/kbluepin;
}
device {
	name "%h-%d";
	class 0xff0100;
	iscan enable; pscan enable;
	discovto 0;
	lm accept;
	lp hold,sniff,park;
}
```
I've been trying to find a solution for the past several hours, so any tips or suggestions of any kind will be greatly appreciated.

---

