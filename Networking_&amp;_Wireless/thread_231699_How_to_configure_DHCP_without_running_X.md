---
title: "How to configure DHCP without running X?"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by Kaidelong on 2006-08-07
I don't know if this is the right place to put this; it has absolutely nothing to do with hardware.

I need to know what the commandline tool is to make ubuntu configure DHCP (I am famaliar with the dhcpc daemon in slackware, apparently Ubuntu does not use this? "which dhcpcd" and "man dhcpcd" - from sudo root - both seem to indicate this.) 

I cannot always run the x.org or xfree86 servers stably/at all on my computers (and do not always wish to) and I need to connect to my wireless network, which for me meant just passing iwconfig and dhcpcd, but now dhcpcd isn't there anymore? I am very happy with Ubuntu's hardware support and the fact that a lot more compiles on it than on Slackware, so I would be really greatful to know how I can get along without network-admin.

---

### Post by MrHorus on 2006-08-08
> **Kaidelong said:**
> I need to know what the commandline tool is to make ubuntu configure DHCP 


```
dhclient
``` Should do the trick.

---

