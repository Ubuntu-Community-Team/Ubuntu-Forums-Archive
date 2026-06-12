---
title: "Where does the l2tp network manager plugin store its IPSec settings?"
date: 2017-08-09
forum: Networking &amp; Wireless
---

### Post by bvz on 2017-08-09
I am trying to debug an l2tp connection issue.  I have installed network-manager-l2tp and am using it to set up my connection.

But I would really like to dig down and see what the actual settings are that it is using/storing.  Normally IPsec settings are stored in a file /etc/ipsec.conf, but this file is all boilerplate with none of my custom settings stored in it.  So where does the plugin store the settings that it is using when it tries to establish a VPN connection?

---

