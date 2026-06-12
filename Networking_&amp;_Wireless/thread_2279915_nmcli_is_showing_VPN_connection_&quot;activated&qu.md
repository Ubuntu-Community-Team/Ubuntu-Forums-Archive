---
title: "nmcli is showing VPN connection &quot;activated&quot;, but it is NOT..."
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by jmarcedwards on 2015-05-26
After an upgrade in Vivid (15.04), I was unable to boot my workstation.  I performed several feats to get back to a Gnome desktop and then performed a release-upgrade, which wasn't completely clean, but nonetheless got me back to a stable situation.


When I tried to reconnect my VPN tunnel, I had several command line changes that I seemed to have to change.  After some experimentation and Googling, I was able to get a good nmcli command.  I received:

[COLOR=#0000cd][FONT=courier new]jmarcedwards@jme-Ubuntu:~$ sudo nmcli -p con up SCi-Phi ifname eth0
[sudo] password for jmarcedwards: 
Connection successfully activated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/8)[/FONT][/COLOR]

However, the VPN tunnel is not established.  I reverted back to my "vpnc" application, which established the VPN tunnel with no problem.

Has any seen this situation upon this latest Vivid update?

Regards, Marc

---

