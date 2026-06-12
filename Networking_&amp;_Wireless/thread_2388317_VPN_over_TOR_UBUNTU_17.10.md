---
title: "VPN over TOR UBUNTU 17.10"
date: 2018-03-31
forum: Networking &amp; Wireless
---

### Post by gorgeee on 2018-03-31
How configure VPN over TOR on Ubuntu 17.10 ?
OpenVPN version 2.4.5
I try this tutorial but it doesn't work.

***.ovpn **
socks-proxy localhost 9150 
socks-proxy-retry
route-up up.sh

**torcfile**:   /etc/tor/torrc SOCKSPort 9150 PreferSOCKSNoAuth

Script up.sh: 

#!/bin/bash
/sbin/ip route delete 128.0.0.0/1 via $ifconfig_remote

---

