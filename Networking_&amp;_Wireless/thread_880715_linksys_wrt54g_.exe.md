---
title: "linksys wrt54g .exe?"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by ample on 2008-08-05
in windows, in order to connect to my wireless wrt54g v8 router, i had to plug a wired connection in and run a .exe from here: [http://linksysfix.com/ela/](http://linksysfix.com/ela/)    and my wireless would work.  before running the .exe, i would get a "unable to find a certificate to log you onto the network" error.
im using WPA-PSK with TKIP authentication
heres a look at dmesg:
```
[  913.562069] wlan0: authenticated
[  913.562073] wlan0: associate with AP 00:1d:7e:1c:c3:7c
[  913.565168] wlan0: RX ReassocResp from 00:1d:7e:1c:c3:7c (capab=0x11 status=0 aid=2)
[  913.565174] wlan0: associated
[  914.107086] wlan0: no IPv6 routers present
[  917.559685] wlan0: RX deauthentication from 00:1d:7e:1c:c3:7c (reason=15)
[  917.559690] wlan0: deauthenticated
[  918.555301] wlan0: authenticate with AP 00:1d:7e:1c:c3:7c
[  918.556797] wlan0: RX authentication from 00:1d:7e:1c:c3:7c (alg=0 transaction=2 status=0)
[  918.556801] wlan0: authenticated
[  918.556805] wlan0: associate with AP 00:1d:7e:1c:c3:7c
[  918.559574] wlan0: RX ReassocResp from 00:1d:7e:1c:c3:7c (capab=0x11 status=0 aid=2)
[  918.559578] wlan0: associated
[  922.554249] wlan0: RX deauthentication from 00:1d:7e:1c:c3:7c (reason=15)
[  922.554255] wlan0: deauthenticated
[  923.550081] wlan0: authenticate with AP 00:1d:7e:1c:c3:7c
[  923.567574] wlan0: RX authentication from 00:1d:7e:1c:c3:7c (alg=0 transaction=2 status=0)
[  923.567582] wlan0: authenticated
[  923.567587] wlan0: associate with AP 00:1d:7e:1c:c3:7c
[  923.555623] wlan0: RX ReassocResp from 00:1d:7e:1c:c3:7c (capab=0x11 status=0 aid=2)
[  923.555629] wlan0: associated
[  927.550015] wlan0: RX deauthentication from 00:1d:7e:1c:c3:7c (reason=15)
[  927.550021] wlan0: deauthenticated
```
any suggestions? do i just need to download a certificate for linux to log in as well?

Edit:I went back and read the webpage finally and realized it says it offers a tutorial for connecting non-windows machines, but no luck finding it yet. ****ing linksys

---

