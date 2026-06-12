---
title: "KNetworkManager Hangs on first use"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by sb73542 on 2007-04-24
Hi,

I have Kubuntu 7.04 on a Dell Inspiron B130 (1300) laptop with a bcm43xx WiMi (Wireless Misery) card.  It works OK with Ndiswrapper, but KNetworkManager is giving me trouble.  Every time I boot up my system, KNetworkManager tries to connect, but then it hangs at 

> 
28% Configuring Device


I have to power-cycle my WiMi radio to get it to connect.  Any suggestions?  Ideally, I would like my wireless connection to load during bootup, so that it is immediately enabled for all apps, including console apps if I choose not to login to KDE.

Thanks for your help!

---

### Post by sb73542 on 2007-04-26
I think this has something to do with the fact that my wlan0 connection is configured to load at boot.  Thus, it is always up when Knetworkmanager tries to connect.  Any suggestions?  I want it to load at boot at possible.

---

### Post by schmandr on 2007-04-30
I guess this is rather a general problem of KNetworkManager: [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/96097](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/96097) 
I got the same problem, at 28% (Activation stage: Configuring device) KNetworkManager hangs when trying to establish a connection through my Atheros wireless adapter (using WPA Personal 2 encryption) since I updated on Kubuntu 7.04. However on Edgy I never had such problems with KNetworkManager.

What can we do then? Just wait until the bug gets fixed? :( 

Andreas

---

