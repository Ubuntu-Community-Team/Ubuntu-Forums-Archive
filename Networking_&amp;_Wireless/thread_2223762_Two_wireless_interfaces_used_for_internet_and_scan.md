---
title: "Two wireless interfaces used for internet and scanning?"
date: 2014-05-12
forum: Networking &amp; Wireless
---

### Post by parkour86 on 2014-05-12
I plan on writing a bash script that will utilize two wireless adapters. One of the interfaces (wlan0) will scan and connect to a wireless access point that has the best link quality. This interface will be used by the OS. The other one (wlan1) will continue scanning until it finds an access point with a higher link quality and connect to it. If wlan1 finds a higher link quality then it will become the new connection the OS uses and the other one (wlan0) will start scanning. This is repeated between both adapters.

Is it possible to designate one interface (wlan0) for the host OS to use while the other one (wlan1) is scanning?

If the other interface (wlan1) found an access point with a higher link quality, is it possible to tell the OS to use that interface (wlan1)?

---

