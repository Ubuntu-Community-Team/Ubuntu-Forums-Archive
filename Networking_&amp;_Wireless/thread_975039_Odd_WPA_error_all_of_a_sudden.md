---
title: "Odd WPA error all of a sudden"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by svguy on 2008-11-08
So I stayed up a little later than normal tonight to work on a bash script that changes my MAC address and my hostname.  Then after I got that all ironed out I played with conky a little bit.
I was just hanging out and all of a sudden my shell printed out the following:
** (nm-applet:312): CRITICAL **: nmu_security_serialize_wpa_psk: assertion `(key_mgt == IW_AUTH_KEY_MGMT_802_1X) || (key_mgt == IW_AUTH_KEY_MGMT_PSK)' failed

I tried restarting the nm-applet multiple times. I tried erasing the key for my WPA network and readding it, but every time I finally associate and get an IP address it immediately loses its association.

Can anyone make sense of that error I'm getting above?

---

