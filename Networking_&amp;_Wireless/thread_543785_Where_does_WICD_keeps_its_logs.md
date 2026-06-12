---
title: "Where does WICD keeps its logs??"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-09-05
Switch networks to remote network.  WPA worked for a while (I mean about 2 hours) and now for some reason I cant connect despite rebooting.  Just trying to figure out where WICD logs to.  Ive tried connecting manually also (WPA connection) and cant get that up and running either.  Just trying to compare output of wpa_supplicant -dd run with wicd.

---

### Post by notoriousdbp on 2007-09-05
/opt/wicd/data/wicd.log

---

### Post by kevdog on 2007-09-05
Thanks you were right on with the log location. Thanks.  This is what I found in the logs, the essid of the router is Dorchester:

2007/09/05 11:23:19 :: no wired connection present, wired autoconnect failed
2007/09/05 11:23:19 :: attempting to autoconnect to wireless network
2007/09/05 11:23:19 :: returning wireless interface to client
2007/09/05 11:23:19 :: Dorchester has profile
2007/09/05 11:23:19 :: unable to autoconnect, you'll have to manually connect

Nothing more I can do to debug the last statement??

---

### Post by imdano on 2007-09-06
Right now wicd doesn't pipe the output of any of the external commands run into wicd.log, so the only way to do it is to run the daemon without redirecting stdout and stderr.  If you have the version of the experimental branch of the svn, you should be able to run ```
sudo /opt/wicd/daemon.py -foe
```Which will let you see the output of wpa_supplicant.

---

