---
title: "iwl4965 RX deauthentication from (reason=7)"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by aldeby on 2008-07-04
Every time I resume from standby or hibernation NetworkManager does not reconnect to my previously connected wireless network.

Network is protected with WPA2.

when this happens syslog logs several lines like this one:
"wlan0: RX deauthentication from [AP MAC ADDRESS] (reason=7)"

When this happens I still can see other networks but mine with NetworkManager and can connect to them. Mine is even not listed in the available networks list.

To get back functionality I have to remove the driver with modprobe -r iwl4965 and then load it again.

uname is: 2.6.24-19-generic #1 SMP
wpasupplicant: 0.6.0+0.5.8-0ubuntu2
NetworkManager: 0.6.6-0ubuntu5

This is a regression since with Hardy vanilla this bug did not exist. It has been introduced by some update after May 22.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/240340](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/240340)

---

