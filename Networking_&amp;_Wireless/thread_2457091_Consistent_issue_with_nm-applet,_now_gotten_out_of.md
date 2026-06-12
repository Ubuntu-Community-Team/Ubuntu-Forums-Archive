---
title: "Consistent issue with nm-applet, now gotten out of control"
date: 2021-01-25
forum: Networking &amp; Wireless
---

### Post by gde061-www on 2021-01-25
I'm running ubuntu 16.04, and since the original install I have suffered the problems with wifi connections where the wifi manager / applet would disappear sometimes, sometimes stop showing the connection correctly (e.g., show ethernet connect when on wifi).  I've got a few "go to" ways that I've picked up from various other posts where others have had that same problem.  And where it's claimed that the problem was fixed in updates and they close the bug.  Anyway, I kinda accepted this crummy state of the world until today, when I was trying to configure and test a new wifi router, and in the process something REALLY broke on the applet to the point where it is not letting me log in to this new wifi network (which yesterday, prior to renaming that network on the router and changing the wifi PW, I was able to log in to.)

What I mean by "not letting me log in" is that when I click the applet to show the list of available networks, there I find the network I want.  I click it.  The dialogue to enter password shows up.  But as soon as I start to type something in the dialogue, it closes on it's own, and I lose all connection until I go to the terminal and kill nm-applet and then restart the network-manager.  

Here is the relevant entries in /var/log/syslog:

```
Jan 25 18:48:04 ThinkPad-L560 avahi-daemon[1201]: Withdrawing address record for fe80::d994:34a4:8d1d:3243 on wlp2s0.Jan 25 18:48:04 ThinkPad-L560 avahi-daemon[1201]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::d994:34a4:8d1d:3243.
Jan 25 18:48:04 ThinkPad-L560 avahi-daemon[1201]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8472] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 1898
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8472] dhcp4 (wlp2s0): state changed bound -> done
Jan 25 18:48:04 ThinkPad-L560 kernel: [  454.791581] wlp2s0: deauthenticating from e4:c3:2a:74:f9:b3 by local choice (Reason: 3=DEAUTH_LEAVING)
Jan 25 18:48:04 ThinkPad-L560 wpa_supplicant[1379]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=e4:c3:2a:74:f9:b3 reason=3 locally_generated=1
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8752] dns-mgr: Writing DNS information to /sbin/resolvconf
Jan 25 18:48:04 ThinkPad-L560 avahi-daemon[1201]: Withdrawing address record for 192.168.0.115 on wlp2s0.
Jan 25 18:48:04 ThinkPad-L560 avahi-daemon[1201]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.0.115.
Jan 25 18:48:04 ThinkPad-L560 avahi-daemon[1201]: Interface wlp2s0.IPv4 no longer relevant for mDNS.
Jan 25 18:48:04 ThinkPad-L560 dnsmasq[1908]: setting upstream servers from DBus
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8839] manager: NetworkManager state is now DISCONNECTED
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8842] device (wlp2s0): Activation: starting connection 'TD_24_guest' (3c227712-5930-495f-beb0-f8b122843a98)
Jan 25 18:48:04 ThinkPad-L560 dbus[1162]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <warn>  [1611618484.8862] sup-iface[0x17ceb60,wlp2s0]: connection disconnected (reason -3)
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8867] device (wlp2s0): supplicant interface state: completed -> disconnected
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8899] device (wlp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8900] manager: NetworkManager state is now CONNECTING
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8956] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8959] device (wlp2s0): Activation: (wifi) access point 'TD_24_guest' has security, but secrets are required.
Jan 25 18:48:04 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618484.8960] device (wlp2s0): state change: config -> need-auth (reason 'none') [50 60 0]
Jan 25 18:48:04 ThinkPad-L560 systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan 25 18:48:04 ThinkPad-L560 dbus[1162]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 25 18:48:04 ThinkPad-L560 systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 25 18:48:04 ThinkPad-L560 nm-dispatcher: req:1 'down' [wlp2s0]: new request (2 scripts)
Jan 25 18:48:04 ThinkPad-L560 nm-dispatcher: req:1 'down' [wlp2s0]: start running ordered scripts...
Jan 25 18:48:05 ThinkPad-L560 gnome-session[2258]: nm-applet-Message: No keyring secrets found for TD_24_guest/802-11-wireless-security; asking user.
Jan 25 18:48:06 ThinkPad-L560 gnome-session[2258]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jan 25 18:48:06 ThinkPad-L560 dbus[1162]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jan 25 18:48:06 ThinkPad-L560 systemd[1]: Starting Hostname Service...
Jan 25 18:48:06 ThinkPad-L560 dbus[1162]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 25 18:48:06 ThinkPad-L560 systemd[1]: Started Hostname Service.
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4991): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4971): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4976): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:5016): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:5020): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:5005): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:5012): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4982): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: message repeated 3 times: [ ** (gvfsd:2189): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused]
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4969): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4985): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:5001): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:06 ThinkPad-L560 org.gtk.vfs.Daemon[2110]: ** (process:4996): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: Internet Systems Consortium DHCP Client 4.3.3
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: Copyright 2004-2015 Internet Systems Consortium.
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: All rights reserved.
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: For info, please visit https://www.isc.org/software/dhcp/
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: 
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: Listening on LPF/wlp2s0/a4:34:d9:eb:c0:17
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: Sending on   LPF/wlp2s0/a4:34:d9:eb:c0:17
Jan 25 18:48:07 ThinkPad-L560 dhclient[5150]: Sending on   Socket/fallback
Jan 25 18:48:07 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618487.2683] device (wlp2s0): supplicant interface state: disconnected -> disabled
Jan 25 18:48:07 ThinkPad-L560 kernel: [  457.224341] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Jan 25 18:48:07 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618487.3056] device (wlp2s0): supplicant interface state: disabled -> disconnected
Jan 25 18:48:07 ThinkPad-L560 wpa_supplicant[1379]: nl80211: deinit ifname=p2p-dev-wlp2s0 disabled_11b_rates=0
Jan 25 18:48:07 ThinkPad-L560 wpa_supplicant[1379]: p2p-dev-wlp2s0: CTRL-EVENT-TERMINATING
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: Internet Systems Consortium DHCP Client 4.3.3
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: Copyright 2004-2015 Internet Systems Consortium.
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: All rights reserved.
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: For info, please visit https://www.isc.org/software/dhcp/
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: 
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: Listening on LPF/enp0s31f6/1c:39:47:13:b0:97
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: Sending on   LPF/enp0s31f6/1c:39:47:13:b0:97
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: Sending on   Socket/fallback
Jan 25 18:48:07 ThinkPad-L560 wpa_supplicant[1379]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0
Jan 25 18:48:07 ThinkPad-L560 wpa_supplicant[1379]: wlp2s0: CTRL-EVENT-TERMINATING
Jan 25 18:48:07 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618487.4285] supplicant: wpa_supplicant stopped
Jan 25 18:48:07 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618487.4285] device (wlp2s0): supplicant interface state: disconnected -> down
Jan 25 18:48:07 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618487.4288] device (wlp2s0): state change: need-auth -> unavailable (reason 'supplicant-failed') [60 20 10]
Jan 25 18:48:07 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618487.4299] manager: NetworkManager state is now DISCONNECTED
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: DHCPRELEASE on enp0s31f6 to 192.168.0.1 port 67 (xid=0x7898f28)
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: send_packet: Network is unreachable
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: send_packet: please consult README file regarding broadcast address.
Jan 25 18:48:07 ThinkPad-L560 dhclient[5178]: dhclient.c:2474: Failed to send 300 byte long packet over fallback interface.
Jan 25 18:48:07 ThinkPad-L560 root: /etc/dhcp/dhclient-enter-hooks.d/avahi-autoipd returned non-zero exit status 1
Jan 25 18:48:07 ThinkPad-L560 root: /etc/dhcp/dhclient-enter-hooks.d/samba returned non-zero exit status 1
Jan 25 18:48:07 ThinkPad-L560 kernel: [  457.691267] e1000e: enp0s31f6 NIC Link is Down
Jan 25 18:48:07 ThinkPad-L560 kernel: [  457.899117] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: Deleting interface #4 wlp2s0, 192.168.0.115#123, interface stats: received=200, sent=201, dropped=1, active_time=398 secs
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 91.189.91.157 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 91.189.89.198 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 91.189.89.199 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 144.172.118.20 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 198.255.68.106 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 72.30.35.88 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 47.190.36.235 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 50.205.244.39 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 108.59.2.24 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 65.182.224.39 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 149.20.176.27 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 73.239.136.185 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 66.220.10.2 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 207.192.69.118 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 99.104.170.138 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: 172.98.193.44 local addr 192.168.0.115 -> <null>
Jan 25 18:48:09 ThinkPad-L560 ntpd[1516]: Deleting interface #5 wlp2s0, fe80::d994:34a4:8d1d:3243%3#123, interface stats: received=0, sent=0, dropped=0, active_time=398 secs
Jan 25 18:48:09 ThinkPad-L560 whoopsie[1474]: [18:48:09] Cannot reach: https://daisy.ubuntu.com
Jan 25 18:48:09 ThinkPad-L560 whoopsie[1474]: [18:48:09] Cannot reach: https://daisy.ubuntu.com
Jan 25 18:48:18 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618498.0043] supplicant: wpa_supplicant die count reset
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Stopped Network Manager Wait Online.
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Stopping Network Manager Wait Online...
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618541.4268] caught SIGTERM, shutting down normally.
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Stopping Network Manager...
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[1172]: <info>  [1611618541.4335] exiting (success)
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Stopped Network Manager.
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Starting Network Manager...
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Started Network Manager.
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Starting Network Manager Wait Online...
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4702] NetworkManager (version 1.2.6) is starting...
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4703] Read config: /etc/NetworkManager/NetworkManager.conf (etc: default-wifi-powersave-on.conf)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4742] manager[0x21d71c0]: monitoring kernel firmware directory '/lib/firmware'.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4742] monitoring ifupdown state file '/run/network/ifstate'.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4761] dns-mgr[0x21b6960]: init: dns=dnsmasq, rc-manager=resolvconf, plugin=dnsmasq
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4772] rfkill2: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/ieee80211/phy0/rfkill2) (driver iwlwifi)
Jan 25 18:49:01 ThinkPad-L560 dbus[1162]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan 25 18:49:01 ThinkPad-L560 dbus[1162]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4912] init!
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4915] management mode: unmanaged
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4921] devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0, iface: wlp2s0)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4921] device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0, iface: wlp2s0): no ifupdown configuration found.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4921] devices added (path: /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6, iface: enp0s31f6)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4921] device added (path: /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6, iface: enp0s31f6): no ifupdown configuration found.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4921] devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4921] device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4922] end _init.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4922] settings: loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4923] settings: loaded plugin keyfile: (c) 2007 - 2015 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4925] SettingsPlugin-Ofono: init!
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <warn>  [1611618541.4925] SettingsPlugin-Ofono: file doesn't exist: /var/lib/ofono
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4925] SettingsPlugin-Ofono: end _init.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4925] settings: loaded plugin ofono: (C) 2013-2016 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4926] (35687328) ... get_connections.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.4926] (35687328) ... get_connections (managed=false): return empty list.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.5071] keyfile: new connection /etc/NetworkManager/system-connections/TD_24_guest (3c227712-5930-495f-beb0-f8b122843a98,"TD_24_guest")
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.5204] keyfile: new connection /etc/NetworkManager/system-connections/TD_24 (885f5fb2-6eb7-42cd-b828-4753b7d999f1,"TD_24")
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.5339] keyfile: new connection /etc/NetworkManager/system-connections/TP_5 (68c272cf-b154-4f0a-b3c7-cc96b70faf0c,"TP_5")
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.5480] keyfile: new connection /etc/NetworkManager/system-connections/TP_24 (839c69a7-704d-46fc-a6c9-4ab07bde08b8,"TP_24")
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.5620] keyfile: new connection /etc/NetworkManager/system-connections/Wired connection 1 (2c337bf7-acb1-3c2d-bcdf-b69b03bbd941,"Wired connection 1")
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.6426] keyfile: new connection /etc/NetworkManager/system-connections/NETGEAR94 (3025dd16-25e1-4126-a0c0-51cc5ca3fabe,"NETGEAR94")
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.7391] SettingsPlugin-Ofono: (35687552) ... get_connections.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.7392] SettingsPlugin-Ofono: (35687552) connections count: 0
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.7393] get unmanaged devices count: 0
Jan 25 18:49:01 ThinkPad-L560 dbus[1162]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Starting Hostname Service...
Jan 25 18:49:01 ThinkPad-L560 dbus[1162]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Started Hostname Service.
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8219] settings: hostname: using hostnamed
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8220] settings: hostname changed from (none) to "ThinkPad-L560"
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8226] Using DHCP client 'dhclient'
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8226] manager: WiFi enabled by radio killswitch; enabled by state file
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8227] manager: WWAN enabled by radio killswitch; enabled by state file
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8228] manager: Networking is enabled by state file
Jan 25 18:49:01 ThinkPad-L560 nm-dispatcher: req:1 'hostname': new request (2 scripts)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8231] Loaded device plugin: NMVxlanFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 nm-dispatcher: req:1 'hostname': start running ordered scripts...
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8232] Loaded device plugin: NMVlanFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8233] Loaded device plugin: NMVethFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8234] Loaded device plugin: NMTunFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8235] Loaded device plugin: NMMacvlanFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8235] Loaded device plugin: NMIPTunnelFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8236] Loaded device plugin: NMInfinibandFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8237] Loaded device plugin: NMEthernetFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8238] Loaded device plugin: NMBridgeFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8239] Loaded device plugin: NMBondFactory (internal)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8253] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8266] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8299] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8316] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8324] (wlp2s0): using nl80211 for WiFi device control
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8338] device (wlp2s0): driver supports Access Point (AP) mode
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8363] manager: (wlp2s0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/0)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8404] device (wlp2s0): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 25 18:49:01 ThinkPad-L560 kernel: [  511.779309] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8432] manager: (enp0s31f6): new Ethernet device (/org/freedesktop/NetworkManager/Devices/1)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8451] device (enp0s31f6): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8464] device (lo): link connected
Jan 25 18:49:01 ThinkPad-L560 kernel: [  511.783906] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8471] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/2)
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8596] urfkill disappeared from the bus
Jan 25 18:49:01 ThinkPad-L560 dbus[1162]: [system] Activating via systemd: service name='fi.w1.wpa_supplicant1' unit='wpa_supplicant.service'
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8768] ofono is now available
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.8777] bluez: use BlueZ version 5
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Starting WPA supplicant...
Jan 25 18:49:01 ThinkPad-L560 dbus[1162]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan 25 18:49:01 ThinkPad-L560 systemd[1]: Started WPA supplicant.
Jan 25 18:49:01 ThinkPad-L560 wpa_supplicant[5341]: Successfully initialized wpa_supplicant
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <warn>  [1611618541.8921] failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.9307] ModemManager available in the bus
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.9339] supplicant: wpa_supplicant running
Jan 25 18:49:01 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618541.9339] device (wlp2s0): supplicant interface state: init -> starting
Jan 25 18:49:01 ThinkPad-L560 wpa_supplicant[5341]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jan 25 18:49:01 ThinkPad-L560 wpa_supplicant[5341]: dbus: Failed to construct signal
Jan 25 18:49:01 ThinkPad-L560 wpa_supplicant[5341]: Could not read interface p2p-dev-wlp2s0 flags: No such device
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.0307] device (wlp2s0): supplicant interface state: starting -> ready
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.0308] device (wlp2s0): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 25 18:49:02 ThinkPad-L560 kernel: [  511.969573] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9148] device (wlp2s0): supplicant interface state: ready -> inactive
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9364] policy: auto-activating connection 'TP_24'
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9374] device (wlp2s0): Activation: starting connection 'TP_24' (839c69a7-704d-46fc-a6c9-4ab07bde08b8)
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9375] device (wlp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9376] manager: NetworkManager state is now CONNECTING
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9380] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9382] device (wlp2s0): Activation: (wifi) access point 'TP_24' has security, but secrets are required.
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9382] device (wlp2s0): state change: config -> need-auth (reason 'none') [50 60 0]
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9415] device (wlp2s0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9418] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9419] device (wlp2s0): Activation: (wifi) connection 'TP_24' has security, and secrets exist.  No new secrets needed.
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9420] Config: added 'ssid' value 'TP_24'
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9420] Config: added 'scan_ssid' value '1'
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9420] Config: added 'key_mgmt' value 'WPA-PSK'
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9420] Config: added 'auth_alg' value 'OPEN'
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9421] Config: added 'psk' value '<omitted>'
Jan 25 18:49:02 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618542.9528] sup-iface[0x22438c0,wlp2s0]: config: set interface ap_scan to 1
Jan 25 18:49:03 ThinkPad-L560 gnome-session[2258]: (nm-applet:2390): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Jan 25 18:49:03 ThinkPad-L560 gnome-session[2258]: message repeated 18 times: [ (nm-applet:2390): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed]
Jan 25 18:49:03 ThinkPad-L560 wpa_supplicant[5341]: wlp2s0: SME: Trying to authenticate with e4:c3:2a:74:f9:b3 (SSID='TP_24' freq=2417 MHz)
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.730773] wlp2s0: authenticate with e4:c3:2a:74:f9:b3
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.741327] wlp2s0: send auth to e4:c3:2a:74:f9:b3 (try 1/3)
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.745031] wlp2s0: authenticated
Jan 25 18:49:03 ThinkPad-L560 wpa_supplicant[5341]: wlp2s0: Trying to associate with e4:c3:2a:74:f9:b3 (SSID='TP_24' freq=2417 MHz)
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.749624] wlp2s0: associate with e4:c3:2a:74:f9:b3 (try 1/3)
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.754653] wlp2s0: RX AssocResp from e4:c3:2a:74:f9:b3 (capab=0x1431 status=0 aid=130)
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.757681] wlp2s0: associated
Jan 25 18:49:03 ThinkPad-L560 kernel: [  513.757825] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
Jan 25 18:49:03 ThinkPad-L560 wpa_supplicant[5341]: wlp2s0: Associated with e4:c3:2a:74:f9:b3
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8246] device (wlp2s0): supplicant interface state: inactive -> authenticating
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8318] device (wlp2s0): supplicant interface state: authenticating -> associating
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8320] device (wlp2s0): supplicant interface state: associating -> associated
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8369] device (wlp2s0): supplicant interface state: associated -> 4-way handshake
Jan 25 18:49:03 ThinkPad-L560 wpa_supplicant[5341]: wlp2s0: WPA: Key negotiation completed with e4:c3:2a:74:f9:b3 [PTK=CCMP GTK=TKIP]
Jan 25 18:49:03 ThinkPad-L560 wpa_supplicant[5341]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to e4:c3:2a:74:f9:b3 completed [id=0 id_str=]
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8532] device (wlp2s0): supplicant interface state: 4-way handshake -> completed
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8532] device (wlp2s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TP_24'.
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8534] device (wlp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8542] dhcp4 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8557] dhcp4 (wlp2s0): dhclient started with pid 5358
Jan 25 18:49:03 ThinkPad-L560 gnome-session[2258]: (nm-applet:2390): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Jan 25 18:49:03 ThinkPad-L560 gnome-session[2258]: (nm-applet:2390): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Jan 25 18:49:03 ThinkPad-L560 dhclient[5358]: DHCPREQUEST of 192.168.0.115 on wlp2s0 to 255.255.255.255 port 67 (xid=0x125f2f06)
Jan 25 18:49:03 ThinkPad-L560 dhclient[5358]: DHCPACK of 192.168.0.115 from 192.168.0.1
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8910]   address 192.168.0.115
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8910]   plen 25 (255.255.255.128)
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8910]   gateway 192.168.0.1
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8911]   server identifier 192.168.0.1
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8911]   lease time 7200
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8911]   hostname 'ThinkPad-L560'
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8911]   nameserver '192.168.0.1'
Jan 25 18:49:03 ThinkPad-L560 avahi-daemon[1201]: Joining mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.0.115.
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8911]   nameserver '192.168.0.1'
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8911] dhcp4 (wlp2s0): state changed unknown -> bound
Jan 25 18:49:03 ThinkPad-L560 avahi-daemon[1201]: New relevant interface wlp2s0.IPv4 for mDNS.
Jan 25 18:49:03 ThinkPad-L560 avahi-daemon[1201]: Registering new address record for 192.168.0.115 on wlp2s0.IPv4.
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8944] device (wlp2s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jan 25 18:49:03 ThinkPad-L560 whoopsie[1474]: [18:49:03] Cannot reach: https://daisy.ubuntu.com
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8961] device (wlp2s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8965] device (wlp2s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.8966] manager: NetworkManager state is now CONNECTED_LOCAL
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.9414] manager: NetworkManager state is now CONNECTED_GLOBAL
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.9417] policy: set 'TP_24' (wlp2s0) as default for IPv4 routing and DNS
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.9584] dns-plugin[0x21e5d00]: starting dnsmasq...
Jan 25 18:49:03 ThinkPad-L560 NetworkManager[5314]: <info>  [1611618543.9608] dns-mgr: Writing DNS information to /sbin/resolvconf
Jan 25 18:49:03 ThinkPad-L560 dhclient[5358]: bound to 192.168.0.115 -- renewal in 3483 seconds.



```

If you are able to follow along the log, you can see that the network manager starts up and successfully connects to TP_24, for which it has a stored key.  Then it tries to connect to TD_24, asks for the key, and that's where everything blows up.  Toward the end is where I manually kill it, then restart it, and then it just goes back and connects again to TP_24.   In case it matters, TD_24 is in a different subnet than DP_24.  

Anybody know what is going on and how to fix?  I have done upgrade of network-manager via apt.   Not interested in upgrading to newer version of Ubuntu at this time, thanks.

---

### Post by CelticWarrior on 2021-01-25
> [COLOR=#000000]Not interested in upgrading to newer version of Ubuntu at this time, thanks.[/COLOR]
You'll have to in just a few months, support for 16.04 ends in April. I see no point in troubleshooting a 5 years old release, to be honest.

---

### Post by CelticWarrior on 2021-01-25
I had zero problems with WiFi in 16.04, and older or newer releases. I don't know what you're talking about. Maybe it has nothing to do with the OS but with the networks you're trying to connect to? Start with simple things like making sure the encryption settings at the router are WPA2-AES, update its firmware, if available, and if really old, replace it.

Experts, namely networking and WiFi experts are still around but nobody will help troubleshooting an about to be EoL release. And you never actually asked for help here regarding this issue in those 5 years, did you? If you did you must have deleted your threads/posts, they're nowhere to be found.

Also, there's sticky in the section: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
Having the results of that script is a must for most of the network related questions. I guess that's why it's a sticky thread.

---

### Post by gde061-www on 2021-01-25
Just gonna add another detail from investigation of behavior... trying to switch wifi networks using command prompt with [COLOR=#000000][FONT=courier new]nmcli[/FONT][/COLOR]

returns Error: Connection activation failed: (10) 802.1X supplicant failed.

---

### Post by gde061-www on 2021-01-25
Just gonna comment some indication from a little more research that the error about dup.data.hash might not mean what I thought and, where I find it coming up in other contexts, looks like it had something to do with the Linux kernel.  Anybody have a idea what's up with that?  

I have spent a bit of time mucking around in all the config files to be found in various places, including: 

/etc/NetworkManager/NetworkManager.conf[COLOR=#000000][FONT=cantarell]
[/FONT][/COLOR]/etc/NetworkManager/conf.d/*name*.conf[COLOR=#000000][FONT=cantarell]
[/FONT][/COLOR]/usr/lib/NetworkManager/conf.d/*name*.conf[COLOR=#000000][FONT=cantarell]
[/FONT][/COLOR]/var/lib/NetworkManager/NetworkManager-intern.conf

none appaear to have any blatant corruption, although I apparently did modify one of them back in 2018, probably as part of trying to solve the flakey nm-applet behavior, and looks like that did nothing.  But I rolled it back anyway.  Nothing doing.  So if it's not the config files, but something corrupted in the service handling / handler / whatever by the kernel, then what?   I did not think it germane to the subject, but infrequently I have been getting random "The Ubuntu Kernel had to close unexpectedly" error from time to time, but it always seemed to start back up and be fine... so I just chalked it up to random process overload or some buggy app that happened to be floating around trying to do something it shouldn't.  Maybe that app was nm all along?

---

