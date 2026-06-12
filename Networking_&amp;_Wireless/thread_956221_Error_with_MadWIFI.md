---
title: "Error with MadWIFI?"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by jstocky on 2008-10-23
A neighbor and I are over at my house goofing around and we are trying to get my PC to connect to his Wireless network without him telling me the WEP.

We keep getting this error. We are absolute beginners and copied and pasted these commands.

 Any help out there would be greatly appreciated. Thanks, Jim and Nick

stocky@nick:~$ sudo airmon start ath0
-e 
usage: /usr/sbin/airmon <start|stop> <interface> [channel]

-e Interface	Chipset		Driver

-e -n ath0		Atheros		madwifi
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
 (monitor mode enabled)

stocky@nick:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'source=madwifi_ag' in source 'source=madwifi_ag,ath0,madwifi'
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
stocky@nick:~$ sudo airodump ath0 filename channel# 1

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig ath0 up; iwconfig ath0 mode Monitor channel <#>'

stocky@nick:~$

---

