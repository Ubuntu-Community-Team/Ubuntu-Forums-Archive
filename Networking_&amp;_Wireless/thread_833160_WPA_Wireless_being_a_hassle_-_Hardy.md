---
title: "WPA Wireless being a hassle - Hardy"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by crazy_vyper on 2008-06-18
Hey guys, i am looking into getting my WPA network to work with linux, however everything ive treid and all the step by steps i've followed have all got me to the same point, one way or another..

My wireless card is a dynamode GI-WL-700S (i believe), and when it connects to an access point the light stays solid.. however, trying to geton a my WPA-TKIP network makes it keep flashing, as if it cant verify the key.. 

I have an error report of when i was debugging with wpa_suppicant :-
Trying to associate with 08:10:73:06:3b:5d (SSID='Wireless Home' freq=2437 MHz)
Associated with 08:10:73:06:3b:5d
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCGIWSCAN]: Operation not supported
Trying to associate with 08:10:73:06:3b:5d (SSID='Wireless Home' freq=2437 MHz)
Associated with 08:10:73:06:3b:5d
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCGIWSCAN]: Operation not supported
Authentication with 00:00:00:00:00:00 timed out.
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
ioctl[SIOCGIWSCAN]: Resource temporarily unavailable
CTRL-EVENT-TERMINATING - signal 2 received

None of that really makes sense to me, especially the remove keys part :|

Any help appreciated

Crazy

---

