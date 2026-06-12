---
title: "kismet error"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2008-10-01
Hello I get the following error when trying to run kismet, I have followed various guides, and believe I have installed everything correctly.

```

rhys@Apple:~$ sudo kismet
[sudo] password for rhys: 
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```

---

### Post by AmbiguousOutlier on 2008-10-03
Bumping

---

### Post by AmbiguousOutlier on 2008-10-04
On my other laptop i get this error

```

rhys@Orange:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface ath0 channel 6...
ERROR:  Unable to create VAP: Operation not supported
ERROR:  Unable to create monitor-mode VAP
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
Done.

```

---

