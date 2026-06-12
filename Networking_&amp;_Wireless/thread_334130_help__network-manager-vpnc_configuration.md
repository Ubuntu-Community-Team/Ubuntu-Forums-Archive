---
title: "help : network-manager-vpnc configuration"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by bernstein on 2007-01-08
hi folks

i daily use network manager (with networkmanager-vpnc) to connect my laptop to my vpn university network. this works flawlessly but after network manager has connected to the network, i have to manually connect to vpn, which is kinda annoying.

Can't this be automated???

thanks,
bernstein

------- Older question now solved : How to configure network-manager-vpnc ?

You need the following : IPSec gateway , IPSec ID , IPSec secret , Xauth username , Xauth password

Where "Xauth username" is "override user". And "IPSec secret" and "Xauth password" will be prompted for on connection.

One more thing : after installing the [.deb]("http://ubuntuforums.org/showthread.php?t=235655&page=6") package i needed restart network-manager to show the VPN-Menuentry and after adding my config i needed to restart Linux (possibliy X is enough though)

---

### Post by pacodani on 2007-03-06
Thank you very much. Your solution worked for me.

---

