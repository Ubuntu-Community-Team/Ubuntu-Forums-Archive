---
title: "iptables + privoxy intercepting proxy"
date: 2014-01-21
forum: Networking &amp; Wireless
---

### Post by martin38 on 2014-01-21
Hi!

I try to configure my machine as adblocking WiFi-Access Point using privoxy but got stuck.
The access point itself is working, having eth0 connected to the internet and wlan0 serving the clients. 
Privoxy is running on the same machine, configured to ```
accept-intercepted-requests
``` and with rules to manipulate the served html.
When set up the proxy manually in the browser on the client everything is working, but i want it to be a transparent/intercepting proxy on the AP.

I just can't find the right iptables rules to redirect all HTTP client traffic through the AP's privoxy (listening to port 8118).

I tried what i found at [http://ubuntuforums.org/showthread.php?t=1346350&p=8443344#post8443344](http://ubuntuforums.org/showthread.php?t=1346350&p=8443344#post8443344) and [http://wiki.ubuntuusers.de/Squid#Iptables-Regel](http://wiki.ubuntuusers.de/Squid#Iptables-Regel) but without success.

Any help appreciated :)

---

