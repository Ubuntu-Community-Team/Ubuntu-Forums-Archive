---
title: "Cisco Airnet 350 issue with kismet"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by jackmacokc on 2005-10-27
hello,

I've done some extensive reading in the forums regarding aironet 350s and kismet, but I cannot seem to find what my issue is. 

bg: i had everything working fine in breezy, but hard drive failed on this laptop (dell c600) and had to put in a new one. original working configuration had pcmcia ethernet card as eth0 and had aironet as eth1 and wifi0 (which as i've read is necessary). however, when re-installing breezy i now have eth0 for ethernet, and eth1 and ETH2 for the aironet.

in my kismet.conf i put the source line as source=cisco_wifix,eth1:eth2,cisco, but that yields this error:

```
$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (cisco): Enabling monitor mode for cisco_wifix source interface eth1:eth2 channel 6...
Source 0 (cisco): Opening cisco_wifix source interface eth1:eth2...
FATAL: pcap reported netlink type 1 (EN10MB) for eth2.  This probably means you're not in RFMON mode or your drivers are reporting a bad value.  Make sure you have the correct drivers and that entering monitor mode succeeded.

```

Any ideas on how I can get kismet back to scanning with this aironet card?

---

### Post by jackmacokc on 2005-10-27
well, after some extensive searching - i've discovered the answer to my problem. it lied in /etc/networking/interfaces - it was bringing up the interfaces incorrectly. i erased all entries regarding eth1 and eth2, and the system correctly recognized them as eth1 and wifi0. i thought i'd post in case someone runs into the same problem!

---

