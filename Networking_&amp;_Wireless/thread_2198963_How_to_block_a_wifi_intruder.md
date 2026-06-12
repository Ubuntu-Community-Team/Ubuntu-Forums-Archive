---
title: "How to block a wifi intruder?"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by artatore on 2014-01-11
Hello to all,

I use Ubuntu 12.04 LTS and I am connected to my wireless router. My router does not have the MAC address filter. I detected an intruder. I see the IP address and MAC address. How do I block it permanently? Is there a MAC address filter/software or similar?

Thank You in advance.

---

### Post by TheFu on 2014-01-11
* Use WPA2
* Change the PSK - to something non-trivial - 30+ random characters
* Don't tell anyone else the PSK.
* Don't use WPS.

[http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security) explains more.
MAC filtering is NOT going to help. Spoofing a MAC address is trivial on every OS.

---

### Post by artatore on 2014-01-11
> **TheFu said:**
> * Use WPA2
* Change the PSK - to something non-trivial - 30+ random characters
* Don't tell anyone else the PSK.
* Don't use WPS.

[http://blog.jdpfu.com/pages/wifi-security](http://blog.jdpfu.com/pages/wifi-security) explains more.
MAC filtering is NOT going to help. Spoofing a MAC address is trivial on every OS.


Thank you for your response. I set all these security settings. Now, how do I remove the intruder? I am aware of the MAC spoofing. My concern is to remove the person "x".

---

### Post by TheFu on 2014-01-11
If you changed the WPA2 key, then when the router is rebooted, their connection will be gone.

---

