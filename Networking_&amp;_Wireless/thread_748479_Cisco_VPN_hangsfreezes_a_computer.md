---
title: "Cisco VPN hangs/freezes a computer?"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by danpre on 2008-04-07
I have successfully installed vpnclient-linux-x86_64-4.8.01.0640-k9 with patch vpnclient-linux-2.6.24-final.diff.

All instructions from: [http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client)

I can connect to my work network and and access windows computer via RDP.

But after 1 or 2 minutes my Linux computer freezes - nothhing works:
mouse
ctrl + alt + F2
ctrl + alt + Backspace
ctrl + alt + Delete :)

Only thing I can do is to shut power down.

What is it?
(I have another computer with Ubuntu 7.10, cisco vpn and I never had a problems like this)

Ubuntu 8.04 Hardy
Kernel 2.6.24-15-generic
Dell XPS m1330

/var/log/messagess
Apr  7 19:57:44 dell-desktop kernel: [  100.244003] cisco_ipsec: module license 'Proprietary' taints kernel.
Apr  7 19:57:44 dell-desktop kernel: [  100.246331] Cisco Systems VPN Client Version 4.8.01 (0640) kernel module loaded

last info - next one is:
Apr  7 20:00:52 dell-desktop syslogd 1.5.0#1ubuntu1: restart.

/var/log/syslog
Apr  7 19:57:04 dell-desktop kernel: [   72.680135] wlan0: no IPv6 routers present
Apr  7 19:57:44 dell-desktop kernel: [  100.244003] cisco_ipsec: module license 'Proprietary' taints kernel.
Apr  7 19:57:44 dell-desktop kernel: [  100.246331] Cisco Systems VPN Client Version 4.8.01 (0640) kernel module loaded
Apr  7 19:58:18 dell-desktop kernel: [  116.845681] cipsec0: no IPv6 routers present
Apr  7 20:00:52 dell-desktop syslogd 1.5.0#1ubuntu1: restart.

/var/log/kern.log
Apr  7 19:57:04 dell-desktop kernel: [   72.680135] wlan0: no IPv6 routers present
Apr  7 19:57:44 dell-desktop kernel: [  100.244003] cisco_ipsec: module license 'Proprietary' taints kernel.
Apr  7 19:57:44 dell-desktop kernel: [  100.246331] Cisco Systems VPN Client Version 4.8.01 (0640) kernel module loaded
Apr  7 19:58:18 dell-desktop kernel: [  116.845681] cipsec0: no IPv6 routers present

---

### Post by lesviva on 2008-04-26
I got the same problem here... system freezes completely...

---

### Post by Jamie Jackson on 2008-04-26
Posted this on another thread a bit ago. Just wanted to be sure you're aware of it: [http://ubuntuforums.org/showpost.php?p=4797354&postcount=8]("http://ubuntuforums.org/showpost.php?p=4797354&postcount=8").

---

### Post by forumache on 2008-04-26
I agree with Jamie Jackson, no need to use the Cisco's VPN client.
Search for vpnc in synaptic, install networkmanager-vpnc (or something like that) and it will nicely work by selecting an encrypted connection in Network Manager.

---

