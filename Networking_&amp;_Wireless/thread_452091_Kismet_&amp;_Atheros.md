---
title: "Kismet &amp; Atheros"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Darkfoxx on 2007-05-22
So I'm trying to get Kismet working on my Atheros based Belkin pcmcia card. I already installed the madwifi drivers and everything works great. 

However, when I go to run Kismet I get some fatal errors:
```
 jm@LAPTOP:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to jm (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (belkin): Enabling monitor mode for madwifi_ag source interface ath0 channel 6...
WARNING:  Could not get mode of vap ath0::wifi0, skipping
FATAL:  Unable to create VAP: Operation not supported
FATAL:  Unable to create monitor-mode VAP
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

```

Any ideas? Looks like it can't set the mode to Monitor.

---

### Post by tturrisi on 2007-05-23
source=madwifi_ag,wifi0,madwifi

---

### Post by Darkfoxx on 2007-05-23
Alright that got it working, but my wireless card is on ath0, not wifi0.

I'm thinking I should change ath0 to wifi0 by doing this:
```
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
```

---

