---
title: "kismet problems"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by jamiekownacki on 2007-07-15
root@me:/home/me# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wrt54g): Enabling monitor mode for wrt54g source interface eth1 channel 0...
sh: /usr/sbin/wl: not found
Source 0 (wrt54g): Opening wrt54g source interface eth1...
FATAL: pcap reported netlink type 1 (EN10MB) for eth1.  This probably means you're not in RFMON mode or your drivers are reporting a bad value.  Make sure you have the correct drivers and that entering monitor mode succeeded.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

---

### Post by jamiekownacki on 2007-07-15
having problems launching kismet......any info on post would be great. I have a internal broadcom card that is giving me problems so i installed an external linksys and attempted to configure in kismet and here are the results. any  help would be great............thanks

---

