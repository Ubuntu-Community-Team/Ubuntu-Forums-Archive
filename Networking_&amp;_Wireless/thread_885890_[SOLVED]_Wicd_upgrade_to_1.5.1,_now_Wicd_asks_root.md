---
title: "[SOLVED] Wicd upgrade to 1.5.1, now Wicd asks root's password every boot"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by gerben1 on 2008-08-10
I upgraded from Wicd 1.4.1, using Wicd_1.5.1_all.deb. (from: [https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)) 
I did nothing special, just double clicked it and let it install it installed without errors or warnings.

When I boot my computer I am asked for the root password after I have logged in.
A dialog pops up with this text:
"Wicd needs to access your computer's network cards"
underneath is a box where I can enter the password, after I give it the root password, the internet connection is working, but there is no tray icon even though wicd-client has automatically been added to session startup. If I then run wicd-client from the Terminal I get the tray icon.


When I try to reinstall the package I get this:
[http://img170.imageshack.us/img170/1936/screenshotwicdreinstallvm4.png](http://img170.imageshack.us/img170/1936/screenshotwicdreinstallvm4.png)
I can also not reinstall network-manager I get a similar error message.

here is /var/log/wicd/wicd.log
```

2008/08/10 19:43:05 :: ---------------------------
2008/08/10 19:43:05 :: wicd initializing...
2008/08/10 19:43:05 :: ---------------------------
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: automatically detected wireless interface wlan0
2008/08/10 19:43:05 :: found wireless_interface in configuration wlan0
2008/08/10 19:43:05 :: setting wireless interface wlan0
2008/08/10 19:43:05 :: found wired_interface in configuration eth0
2008/08/10 19:43:05 :: setting wired interface eth0
2008/08/10 19:43:05 :: found wpa_driver in configuration wext
2008/08/10 19:43:05 :: setting wpa driver wext
2008/08/10 19:43:05 :: found always_show_wired_interface in configuration True
2008/08/10 19:43:05 :: found use_global_dns in configuration False
2008/08/10 19:43:05 :: setting use global dns to False
2008/08/10 19:43:05 :: setting use global dns to boolean False
2008/08/10 19:43:05 :: found global_dns_1 in configuration None
2008/08/10 19:43:05 :: found global_dns_2 in configuration None
2008/08/10 19:43:05 :: found global_dns_3 in configuration None
2008/08/10 19:43:05 :: setting global dns
2008/08/10 19:43:05 :: global dns servers are None None None
2008/08/10 19:43:05 :: found auto_reconnect in configuration True
2008/08/10 19:43:05 :: setting automatically reconnect when connection drops
2008/08/10 19:43:05 :: found debug_mode in configuration 0
2008/08/10 19:43:05 :: found wired_connect_mode in configuration 1
2008/08/10 19:43:05 :: found signal_display_type in configuration 0
2008/08/10 19:43:05 :: found dhcp_client in configuration 0
2008/08/10 19:43:05 :: Setting dhcp client to 0
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: checking dhcp...
2008/08/10 19:43:05 :: found link_detect_tool in configuration 0
2008/08/10 19:43:05 :: found flush_tool in configuration 0
2008/08/10 19:43:05 :: Wireless configuration file found...
2008/08/10 19:43:05 :: Wired configuration file found...
2008/08/10 19:43:05 :: chmoding configuration files 0600...
2008/08/10 19:43:05 :: chowning configuration files root:root...
2008/08/10 19:43:05 :: Using wireless interface...wlan0
2008/08/10 19:43:05 :: autoconnecting... wlan0
2008/08/10 19:43:06 :: No wired connection present, attempting to autoconnectto wireless network
2008/08/10 19:43:06 :: trying to automatically connect to...Gerben
2008/08/10 19:43:06 :: Connecting to wireless network Gerben
2008/08/10 19:43:06 :: Putting interface down
2008/08/10 19:43:07 :: Releasing DHCP leases...
2008/08/10 19:43:08 :: Setting false IP...
2008/08/10 19:43:10 :: Stopping wpa_supplicant and any DHCP clients
2008/08/10 19:43:10 :: Flushing the routing table...
2008/08/10 19:43:10 :: Generating psk...
2008/08/10 19:43:10 :: Attempting to authenticate...
2008/08/10 19:43:11 :: Putting interface up...
2008/08/10 19:43:12 :: exiting connection thread
2008/08/10 19:43:08 :: Connecting to wireless network Gerben
2008/08/10 19:43:08 :: Putting interface down
2008/08/10 19:43:08 :: Releasing DHCP leases...
2008/08/10 19:43:10 :: Setting false IP...
2008/08/10 19:43:11 :: Stopping wpa_supplicant and any DHCP clients
2008/08/10 19:43:12 :: Flushing the routing table...
2008/08/10 19:43:12 :: Generating psk...
2008/08/10 19:43:12 :: Attempting to authenticate...
2008/08/10 19:43:12 :: Putting interface up...
2008/08/10 19:43:13 :: Running DHCP
2008/08/10 19:43:13 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2008/08/10 19:43:13 :: Internet Systems Consortium DHCP Client V3.0.6
2008/08/10 19:43:13 :: Copyright 2004-2007 Internet Systems Consortium.
2008/08/10 19:43:13 :: All rights reserved.
2008/08/10 19:43:13 :: For info, please visit http://www.isc.org/sw/dhcp/
2008/08/10 19:43:13 :: 
2008/08/10 19:43:13 :: wmaster0: unknown hardware address type 801
2008/08/10 19:43:14 :: wmaster0: unknown hardware address type 801
2008/08/10 19:43:14 :: Listening on LPF/wlan0/00:14:a4:6a:b1:ae
2008/08/10 19:43:14 :: Sending on   LPF/wlan0/00:14:a4:6a:b1:ae
2008/08/10 19:43:14 :: Sending on   Socket/fallback
2008/08/10 19:43:14 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2008/08/10 19:43:15 :: DHCPOFFER of 192.168.1.101 from 192.168.1.1
2008/08/10 19:43:15 :: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
2008/08/10 19:43:15 :: DHCPACK of 192.168.1.101 from 192.168.1.1
2008/08/10 19:43:15 :: bound to 192.168.1.101 -- renewal in 42026 seconds.
2008/08/10 19:43:15 :: DHCP connection successful
2008/08/10 19:43:15 :: Connecting thread exiting.
2008/08/10 20:02:31 :: GetWiredProperty: WiredNetwork does not exist

```

---

### Post by gerben1 on 2008-08-10
The cause of the problem was that I still had the old /etc/int.d/wicd script, as in the one from the previous version 1.4.2

The problem seems to be solved by opening the wicd_1.5.1_all.deb file in archive manager, then open the etc/init.d/wicd script that is in the .deb file and copy its contents over the contents of the /etc/init.d/wicd script that is on the hard drive.

No clue why it did not install that file properly when installing wicd_1.5.1_all.deb

---

### Post by Joeb454 on 2008-08-10
Please do not create duplicate threads

[http://ubuntuforums.org/showthread.php?t=885761](http://ubuntuforums.org/showthread.php?t=885761)

---

