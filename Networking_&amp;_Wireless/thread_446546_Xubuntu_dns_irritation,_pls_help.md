---
title: "Xubuntu dns irritation, pls help"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Strev_123 on 2007-05-17
Hi I've sorted a problem with Xbuntu not automatically resolving dns settings with my Linksys ADSL2MUE modem. I've followed this post to get it working

[http://ubuntuforums.org/showthread.php?t=279901&highlight=adsl2mue](http://ubuntuforums.org/showthread.php?t=279901&highlight=adsl2mue)

Problem is everything works great once I enter the dns server ip's for my broadband provider but when I restart the system the dns server in the "wired connection" network config reverts to my modems IP, 192.168.1.1, which then means the internet doesn't work so I have to re-enter the dns server ip's which is a real pain.

Is there anyway to have this remembered by Xubuntu?

---

### Post by joft on 2007-05-17
I never had this problem, but I remember that the DHCP client has a configuration option to "supersede" values provided by the DHCP server. Have a look at "man dhclient.conf" for more information.
I think you have to add a line like:
```

supersede domain-name-servers <dns-ip-of-provider>;

```
to your /etc/dhcp3/dhclient.conf file. This file also contains lots of (commented) "example lines". Of course, replace "<dns-ip-of-provider>" with your provider's DNS server ip ...

---

