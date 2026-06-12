---
title: "Network manager does not show broadband connection icon"
date: 2016-04-26
forum: Networking &amp; Wireless
---

### Post by Gabor_Botzheim on 2016-04-26
Hi all, I haven found an answer for this, maybe you could help:

Since I switched to 16.04(clean install), the nm-applet does not show me the tray icon for the broadband connection. This way I do not have a quick peek for the signal quality or the status of the connection. It would not be nice to forget the connection open. The screenshot of the tray would tell me that I am not connected at all now..

I attached a screenshot and syslog = 
```
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2026] device (cdc-wdm0): Activation: starting connection 'T-Mobile(Telekom)' (81b8e1ff-a7e6-4127-bb27-85d11b737ea2)
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2031] audit: op="connection-activate" uuid="81b8e1ff-a7e6-4127-bb27-85d11b737ea2" name="T-Mobile(Telekom)" pid=2940 uid=1000 result="success"
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2035] device (cdc-wdm0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2038] manager: NetworkManager state is now CONNECTING
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2049] device (cdc-wdm0): state change: prepare -> need-auth (reason 'none') [40 60 0]
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.3445] device (cdc-wdm0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect started...
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (4/8): Wait to get fully enabled
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (5/8): Register
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (6/8): Bearer
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (7/8): Connect
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (registered -> connecting)
Apr 26 23:28:22 GaborNB ModemManager[724]: <info>  error: couldn't start network: QMI protocol error (79): 'PolicyMismatch'
Apr 26 23:28:22 GaborNB ModemManager[724]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connecting -> connected)
Apr 26 23:28:22 GaborNB ModemManager[724]: <info>  Simple connect state (8/8): All done
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2519] device (cdc-wdm0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2531] device (cdc-wdm0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2546] dhcp4 (wwx2edcef14c3f1): activation: beginning transaction (timeout in 15 seconds)
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2578] dhcp4 (wwx2edcef14c3f1): dhclient started with pid 3125
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2580] (cdc-wdm0): IPv6 configuration disabled
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPREQUEST of 10.207.225.238 on wwx2edcef14c3f1 to 255.255.255.255 port 67 (xid=0x76c5a0f3)
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPNAK from 10.30.8.246 (xid=0xf3a0c576)
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3042] dhcp4 (wwx2edcef14c3f1): state changed unknown -> expire
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3084] dhcp4 (wwx2edcef14c3f1): state changed expire -> unknown
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPDISCOVER on wwx2edcef14c3f1 to 255.255.255.255 port 67 interval 3 (xid=0x69896e1c)
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPREQUEST of 10.30.8.245 on wwx2edcef14c3f1 to 255.255.255.255 port 67 (xid=0x1c6e8969)
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPOFFER of 10.30.8.245 from 10.30.8.246
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPACK of 10.30.8.245 from 10.30.8.246
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3284]   address 10.30.8.245
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3285]   plen 30 (255.255.255.252)
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3285]   gateway 10.30.8.246
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3285]   server identifier 10.30.8.246
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3286]   lease time 7200
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3286]   hostname 'GaborNB'
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3286]   nameserver '10.74.210.210'
Apr 26 23:28:22 GaborNB avahi-daemon[686]: Joining mDNS multicast group on interface wwx2edcef14c3f1.IPv4 with address 10.30.8.245.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3287]   nameserver '10.74.210.211'
Apr 26 23:28:22 GaborNB avahi-daemon[686]: New relevant interface wwx2edcef14c3f1.IPv4 for mDNS.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3287] dhcp4 (wwx2edcef14c3f1): state changed unknown -> bound
Apr 26 23:28:22 GaborNB avahi-daemon[686]: Registering new address record for 10.30.8.245 on wwx2edcef14c3f1.IPv4.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3324] device (cdc-wdm0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr 26 23:28:22 GaborNB dhclient[3125]: bound to 10.30.8.245 -- renewal in 3392 seconds.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3340] device (cdc-wdm0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3346] device (cdc-wdm0): state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3349] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 26 23:28:22 GaborNB whoopsie[725]: [23:28:22] Cannot reach: https://daisy.ubuntu.com
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3366] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3368] policy: set 'T-Mobile(Telekom)' (wwx2edcef14c3f1) as default for IPv4 routing and DNS
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3370] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr 26 23:28:22 GaborNB dnsmasq[2032]: setting upstream servers from DBus
Apr 26 23:28:22 GaborNB dnsmasq[2032]: using nameserver 10.74.210.210#53
Apr 26 23:28:22 GaborNB dnsmasq[2032]: using nameserver 10.74.210.211#53
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3503] device (cdc-wdm0): Activation: successful, device activated.
Apr 26 23:28:22 GaborNB dbus[731]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Apr 26 23:28:22 GaborNB whoopsie[725]: [23:28:22] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/4
Apr 26 23:28:22 GaborNB whoopsie[725]: [23:28:22] Network connection may be a paid data plan: /org/freedesktop/NetworkManager/Devices/3
Apr 26 23:28:22 GaborNB systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr 26 23:28:22 GaborNB dbus[731]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 26 23:28:22 GaborNB systemd[1]: Started Network Manager Script Dispatcher Service.
Apr 26 23:28:22 GaborNB nm-dispatcher: req:1 'up' [wwx2edcef14c3f1]: new request (1 scripts)
Apr 26 23:28:22 GaborNB nm-dispatcher: req:1 'up' [wwx2edcef14c3f1]: start running ordered scripts...
Apr 26 23:28:22 GaborNB gnome-session[1701]: (deja-dup-monitor:2869): GLib-CRITICAL **: Source ID 54 was not found when attempting to remove it
Apr 26 23:29:42 GaborNB NetworkManager[844]: <info>  [1461706182.3661] device (cdc-wdm0): state change: activated -> deactivating (reason 'user-requested') [100 110 39]
```

---

### Post by d-a-johnston-hw on 2016-04-28
No answer, but a "me too"....

The broadband connected icon and list of broadband connections  has disappeared from the network manager applet on 3 Lenovo Thinkpads (N5321gw WWAN chips) after upgrading from 15.10. The laptops can still connect to broadband, but nothing is showing in the applet.


> **Gabor_Botzheim said:**
> Hi all, I haven found an answer for this, maybe you could help:

Since I switched to 16.04(clean install), the nm-applet does not show me the tray icon for the broadband connection. This way I do not have a quick peek for the signal quality or the status of the connection. It would not be nice to forget the connection open. The screenshot of the tray would tell me that I am not connected at all now..

I attached a screenshot and syslog = 
```
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2026] device (cdc-wdm0): Activation: starting connection 'T-Mobile(Telekom)' (81b8e1ff-a7e6-4127-bb27-85d11b737ea2)
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2031] audit: op="connection-activate" uuid="81b8e1ff-a7e6-4127-bb27-85d11b737ea2" name="T-Mobile(Telekom)" pid=2940 uid=1000 result="success"
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2035] device (cdc-wdm0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2038] manager: NetworkManager state is now CONNECTING
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.2049] device (cdc-wdm0): state change: prepare -> need-auth (reason 'none') [40 60 0]
Apr 26 23:28:20 GaborNB NetworkManager[844]: <info>  [1461706100.3445] device (cdc-wdm0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect started...
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (4/8): Wait to get fully enabled
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (5/8): Register
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (6/8): Bearer
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Simple connect state (7/8): Connect
Apr 26 23:28:20 GaborNB ModemManager[724]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (registered -> connecting)
Apr 26 23:28:22 GaborNB ModemManager[724]: <info>  error: couldn't start network: QMI protocol error (79): 'PolicyMismatch'
Apr 26 23:28:22 GaborNB ModemManager[724]: <info>  Modem /org/freedesktop/ModemManager1/Modem/0: state changed (connecting -> connected)
Apr 26 23:28:22 GaborNB ModemManager[724]: <info>  Simple connect state (8/8): All done
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2519] device (cdc-wdm0): state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2531] device (cdc-wdm0): state change: config -> ip-config (reason 'none') [50 70 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2546] dhcp4 (wwx2edcef14c3f1): activation: beginning transaction (timeout in 15 seconds)
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2578] dhcp4 (wwx2edcef14c3f1): dhclient started with pid 3125
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.2580] (cdc-wdm0): IPv6 configuration disabled
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPREQUEST of 10.207.225.238 on wwx2edcef14c3f1 to 255.255.255.255 port 67 (xid=0x76c5a0f3)
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPNAK from 10.30.8.246 (xid=0xf3a0c576)
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3042] dhcp4 (wwx2edcef14c3f1): state changed unknown -> expire
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3084] dhcp4 (wwx2edcef14c3f1): state changed expire -> unknown
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPDISCOVER on wwx2edcef14c3f1 to 255.255.255.255 port 67 interval 3 (xid=0x69896e1c)
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPREQUEST of 10.30.8.245 on wwx2edcef14c3f1 to 255.255.255.255 port 67 (xid=0x1c6e8969)
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPOFFER of 10.30.8.245 from 10.30.8.246
Apr 26 23:28:22 GaborNB dhclient[3125]: DHCPACK of 10.30.8.245 from 10.30.8.246
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3284]   address 10.30.8.245
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3285]   plen 30 (255.255.255.252)
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3285]   gateway 10.30.8.246
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3285]   server identifier 10.30.8.246
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3286]   lease time 7200
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3286]   hostname 'GaborNB'
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3286]   nameserver '10.74.210.210'
Apr 26 23:28:22 GaborNB avahi-daemon[686]: Joining mDNS multicast group on interface wwx2edcef14c3f1.IPv4 with address 10.30.8.245.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3287]   nameserver '10.74.210.211'
Apr 26 23:28:22 GaborNB avahi-daemon[686]: New relevant interface wwx2edcef14c3f1.IPv4 for mDNS.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3287] dhcp4 (wwx2edcef14c3f1): state changed unknown -> bound
Apr 26 23:28:22 GaborNB avahi-daemon[686]: Registering new address record for 10.30.8.245 on wwx2edcef14c3f1.IPv4.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3324] device (cdc-wdm0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr 26 23:28:22 GaborNB dhclient[3125]: bound to 10.30.8.245 -- renewal in 3392 seconds.
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3340] device (cdc-wdm0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3346] device (cdc-wdm0): state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3349] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 26 23:28:22 GaborNB whoopsie[725]: [23:28:22] Cannot reach: https://daisy.ubuntu.com
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3366] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3368] policy: set 'T-Mobile(Telekom)' (wwx2edcef14c3f1) as default for IPv4 routing and DNS
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3370] dns-mgr: Writing DNS information to /sbin/resolvconf
Apr 26 23:28:22 GaborNB dnsmasq[2032]: setting upstream servers from DBus
Apr 26 23:28:22 GaborNB dnsmasq[2032]: using nameserver 10.74.210.210#53
Apr 26 23:28:22 GaborNB dnsmasq[2032]: using nameserver 10.74.210.211#53
Apr 26 23:28:22 GaborNB NetworkManager[844]: <info>  [1461706102.3503] device (cdc-wdm0): Activation: successful, device activated.
Apr 26 23:28:22 GaborNB dbus[731]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Apr 26 23:28:22 GaborNB whoopsie[725]: [23:28:22] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/4
Apr 26 23:28:22 GaborNB whoopsie[725]: [23:28:22] Network connection may be a paid data plan: /org/freedesktop/NetworkManager/Devices/3
Apr 26 23:28:22 GaborNB systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr 26 23:28:22 GaborNB dbus[731]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 26 23:28:22 GaborNB systemd[1]: Started Network Manager Script Dispatcher Service.
Apr 26 23:28:22 GaborNB nm-dispatcher: req:1 'up' [wwx2edcef14c3f1]: new request (1 scripts)
Apr 26 23:28:22 GaborNB nm-dispatcher: req:1 'up' [wwx2edcef14c3f1]: start running ordered scripts...
Apr 26 23:28:22 GaborNB gnome-session[1701]: (deja-dup-monitor:2869): GLib-CRITICAL **: Source ID 54 was not found when attempting to remove it
Apr 26 23:29:42 GaborNB NetworkManager[844]: <info>  [1461706182.3661] device (cdc-wdm0): state change: activated -> deactivating (reason 'user-requested') [100 110 39]
```

---

### Post by lauricat on 2016-04-29
Gabor & Johnson.

I have exactly the same problem.

Found this workaround:

see here:

[http://ubuntuforums.org/showthread.php?t=2321873&p=13479201#post13479201](http://ubuntuforums.org/showthread.php?t=2321873&p=13479201#post13479201)

---

