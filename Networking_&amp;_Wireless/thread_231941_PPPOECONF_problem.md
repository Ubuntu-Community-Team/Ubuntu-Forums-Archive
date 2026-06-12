---
title: "PPPOECONF problem"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by anabelle on 2006-08-08
Hi, im very new to Linux, and i just got a kubuntu 6.06 

I had no trouble setting it up but i can't get the internet working.

I wrote 

```
sudo pppoeconf
mypassword
```

it seemed to be working fine but after a while it returned an error telling me "Sorry, I scanned 1 interface(s), but the Access Concentrator of your provider did not erspond. Please check the network card and modem cables. Another reason for the scan failure may be another running pppoe process which controls the modem"

iv also tried 
```
sudo pppoeconf modconf
```

this way it doesn't tell me an error and it keeps through the process normally, but when its done my internet connection desn't work.

i don't now what else to do.

i was trying to kill  pppd and pdflush because that seemed to work for somebody else, but i don't know how to do that.

what can i do to get my internet (ADSL) working?

---

### Post by anabelle on 2006-08-08
i've tried 
```
pppd call dsl-provider
``` 
But it returns me a " Unrecognized option nic-modconf "


im scared

---

### Post by anabelle on 2006-08-08
this showed up when i was trying to start networking services from the system prefeences 

```
* Configuring network interfaces...
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
Plugin rp-pppoe.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-modconf'
Failed to bring up dsl-provider.
modconf: ERROR while getting interface flags: No such device
Failed to bring up modconf.
   ...done. 

```

does this help?

---

