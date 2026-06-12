---
title: "WPA and hermes driver"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by thorheimdall on 2005-09-05
I have a laptop with a Hermes/Orinoco wireless card (which is working perfectly with WEP).  Now I want to use WPA so I have installed wpasupplicant package using "apt-get install wpasupplicant" but this package was not compiled with the hermes driver.  I downloaded the source code of wpa_supplicant and as described in the REAME, I have activated the compilation of the hermes driver and I have downloaded the files needed from Agere web site (Linux LKM Wireless Driver Source Code, Version 7.22).  After finding all .h files it needs to compile properly, I have got some compilation errors.  It seems that the API has changed or something like that because some functions don't have the right number of parameters :
```
driver_hermes.c: In function `wpa_driver_hermes_associate':
driver_hermes.c:450: warning: passing arg 1 of `wpa_driver_wext_set_freq' discards qualifiers from pointer target type
driver_hermes.c:452: warning: passing arg 1 of `wpa_driver_wext_set_ssid' discards qualifiers from pointer target type
driver_hermes.c:454: warning: passing arg 1 of `wpa_driver_wext_set_bssid' discards qualifiers from pointer target type
driver_hermes.c: In function `wpa_driver_hermes_scan':
driver_hermes.c:471: warning: passing arg 1 of `wpa_driver_wext_scan' discards qualifiers from pointer target type
driver_hermes.c:471: warning: passing arg 3 of `wpa_driver_wext_scan' makes integer from pointer without a cast
driver_hermes.c:471: error: too many arguments to function `wpa_driver_wext_scan'
driver_hermes.c: At top level:
driver_hermes.c:481: warning: initialization from incompatible pointer type
driver_hermes.c:482: warning: initialization from incompatible pointer type
driver_hermes.c:483: error: unknown field `events_init' specified in initializer
driver_hermes.c:483: error: `wpa_driver_wext_events_init' undeclared here (not in a function)
driver_hermes.c:483: error: initializer element is not constant
driver_hermes.c:483: error: (near initialization for `wpa_driver_hermes_ops.init')
driver_hermes.c:484: error: unknown field `events_deinit' specified in initializer
driver_hermes.c:484: error: `wpa_driver_wext_events_deinit' undeclared here (not in a function)
driver_hermes.c:484: error: initializer element is not constant
driver_hermes.c:484: error: (near initialization for `wpa_driver_hermes_ops.deinit')
driver_hermes.c:485: warning: initialization from incompatible pointer type
driver_hermes.c:486: warning: initialization from incompatible pointer type
driver_hermes.c:487: warning: initialization from incompatible pointer type
driver_hermes.c:489: warning: initialization from incompatible pointer type
driver_hermes.c:490: warning: initialization from incompatible pointer type
driver_hermes.c:491: warning: initialization from incompatible pointer type
make: *** [driver_hermes.o] Error 1
```
Someone has make that wireless card working with WPA?  Someone has an idea of what is wrong?

---

