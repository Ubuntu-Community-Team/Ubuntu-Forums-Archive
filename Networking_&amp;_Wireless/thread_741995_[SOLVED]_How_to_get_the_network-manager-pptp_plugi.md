---
title: "[SOLVED] How to get the network-manager-pptp plugin to show pppd commandline?"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by rrwo on 2008-04-01
From this thread [http://ubuntuforums.org/showthread.php?t=740744](http://ubuntuforums.org/showthread.php?t=740744) I've found that NetworkManager connects to the VPN server with the correct routing.

But using the command line to launch pppd, I get a circular route to the VPN server that I am unable to fix by changing the routing.

Looking at the source code for the PPTP plugin, there's an option to get it to show the command line that it uses to launch pppd.  But I can't get it to work when setting the debug" ppp options-- either it's logged to somewhere other than /var/log/messages or syslog, or it's not being logged at all.

Does anyone know how to enable this?

---

### Post by rrwo on 2008-04-01
I was able to use 
```
ps -AF |grep pppd
```
to see the process that NetworkManager launched.

---

