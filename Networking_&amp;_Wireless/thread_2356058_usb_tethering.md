---
title: "usb tethering"
date: 2017-03-19
forum: Networking &amp; Wireless
---

### Post by ajithabraham.m on 2017-03-19
I need to connect internet via usb tethering, if I connect after a fresh start of the OS it works fine but if I reconnect it'll connect but wouldn't get internet but if I restart the system again it gone back to normal 

I think this problem occurce after the last update.

syslog
```

Mar 19 17:28:40 user_name-Inspiron-15-3567 gnome-session[2111]: (tracker-miner-fs:2282): Tracker-CRITICAL **: Could not set mount point in database 'urn:nepomuk:datasource:f0bad42107e5a5bcb9a4e1b32b8a03d4', GDBus.Error:org.freedesktop.Tracker1.SparqlError.Internal: UNIQUE constraint failed: nie:DataObject.nie:url (strerror of errno (not necessarily related): No such file or directory)
Mar 19 17:28:40 user_name-Inspiron-15-3567 org.gtk.vfs.MTPVolumeMonitor[1937]: (process:2241): GVFS-MTP-WARNING **: device (null) has no BUSNUM property, ignoring
Mar 19 17:28:41 user_name-Inspiron-15-3567 org.gtk.vfs.Daemon[1937]: ** (process:4045): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/27 (g-dbus-error-quark, 19)
Mar 19 17:28:41 user_name-Inspiron-15-3567 org.gtk.vfs.Daemon[1937]: ** (process:4045): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/27 (g-dbus-error-quark, 19)
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.061375] usb 1-1: USB disconnect, device number 7
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.485858] usb 1-1: new high-speed USB device number 8 using xhci_hcd
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.671062] usb 1-1: New USB device found, idVendor=1782, idProduct=5d20
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.671075] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.671082] usb 1-1: Product: era1X
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.671088] usb 1-1: Manufacturer: Xolo
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.671094] usb 1-1: SerialNumber: e1x2j16ka035025
Mar 19 17:28:59 user_name-Inspiron-15-3567 kernel: [ 3010.674228] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, 2a:71:d0:8c:da:98
Mar 19 17:28:59 user_name-Inspiron-15-3567 NetworkManager[1075]: <warn>  [1489924739.6933] device (usb0): failed to find device 5 'usb0' with udev
Mar 19 17:28:59 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924739.6965] manager: (usb0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/5)
Mar 19 17:29:00 user_name-Inspiron-15-3567 kernel: [ 3011.356250] rndis_host 1-1:1.0 enp0s20f0u1: renamed from usb0
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.3843] device (usb0): interface index 5 renamed iface from 'usb0' to 'enp0s20f0u1'
Mar 19 17:29:00 user_name-Inspiron-15-3567 kernel: [ 3011.548305] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u1: link is not ready
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.5639] devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/enp0s20f0u1, iface: enp0s20f0u1)
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.5640] device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/enp0s20f0u1, iface: enp0s20f0u1): no ifupdown configuration found.
Mar 19 17:29:00 user_name-Inspiron-15-3567 org.gtk.vfs.Daemon[1937]: Android device detected, assigning default bug flags
Mar 19 17:29:00 user_name-Inspiron-15-3567 avahi-daemon[1052]: Joining mDNS multicast group on interface enp0s20f0u1.IPv4 with address 192.168.0.204.
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.5648] device (enp0s20f0u1): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 19 17:29:00 user_name-Inspiron-15-3567 avahi-daemon[1052]: New relevant interface enp0s20f0u1.IPv4 for mDNS.
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.5681] device (enp0s20f0u1): link connected
Mar 19 17:29:00 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for 192.168.0.204 on enp0s20f0u1.IPv4.
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.5817] device (enp0s20f0u1): state change: unavailable -> disconnected (reason 'none') [20 30 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.6102] policy: auto-activating connection 'Profile 1'
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.6116] device (enp0s20f0u1): Activation: starting connection 'Profile 1' (2d319f1c-66cc-47a2-ad58-46290f4f1aa0)
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.6119] device (enp0s20f0u1): state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.6120] manager: NetworkManager state is now CONNECTING
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.6125] device (enp0s20f0u1): state change: prepare -> config (reason 'none') [40 50 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.6129] device (enp0s20f0u1): state change: config -> ip-config (reason 'none') [50 70 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.7662] device (enp0s20f0u1): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.7730] device (enp0s20f0u1): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.7740] device (enp0s20f0u1): state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.7745] manager: NetworkManager state is now CONNECTED_LOCAL
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.9580] manager: NetworkManager state is now CONNECTED_GLOBAL
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.9584] policy: set 'Profile 1' (enp0s20f0u1) as default for IPv4 routing and DNS
Mar 19 17:29:00 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924740.9587] device (enp0s20f0u1): Activation: successful, device activated.
Mar 19 17:29:01 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:01] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:01 user_name-Inspiron-15-3567 dbus[1054]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Mar 19 17:29:01 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:01] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Mar 19 17:29:01 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:01] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Mar 19 17:29:01 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:01] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Mar 19 17:29:01 user_name-Inspiron-15-3567 systemd[1]: Starting Network Manager Script Dispatcher Service...
Mar 19 17:29:01 user_name-Inspiron-15-3567 dbus[1054]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 19 17:29:01 user_name-Inspiron-15-3567 systemd[1]: Started Network Manager Script Dispatcher Service.
Mar 19 17:29:01 user_name-Inspiron-15-3567 nm-dispatcher: req:1 'up' [enp0s20f0u1]: new request (2 scripts)
Mar 19 17:29:01 user_name-Inspiron-15-3567 nm-dispatcher: req:1 'up' [enp0s20f0u1]: start running ordered scripts...
Mar 19 17:29:01 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:01] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:01 user_name-Inspiron-15-3567 avahi-daemon[1052]: Joining mDNS multicast group on interface enp0s20f0u1.IPv6 with address fe80::dda7:f675:3485:2de.
Mar 19 17:29:01 user_name-Inspiron-15-3567 avahi-daemon[1052]: New relevant interface enp0s20f0u1.IPv6 for mDNS.
Mar 19 17:29:01 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for fe80::dda7:f675:3485:2de on enp0s20f0u1.*.
Mar 19 17:29:02 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:01] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:02 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:02] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:02 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924742.9655] dhcp6 (enp0s20f0u1): activation: beginning transaction (timeout in 45 seconds)
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.0192] dhcp6 (enp0s20f0u1): dhclient started with pid 4245
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.0205] policy: set 'Profile 1' (enp0s20f0u1) as default for IPv6 routing and DNS
Mar 19 17:29:03 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:03] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:03 user_name-Inspiron-15-3567 dnsmasq[2651]: setting upstream servers from DBus
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.0208] dns-mgr: Writing DNS information to /sbin/resolvconf
Mar 19 17:29:03 user_name-Inspiron-15-3567 dnsmasq[2651]: using nameserver 2402:8100:9:0:8000::1#53(via enp0s20f0u1)
Mar 19 17:29:03 user_name-Inspiron-15-3567 dnsmasq[2651]: using nameserver 2402:8100:d::1#53(via enp0s20f0u1)
Mar 19 17:29:03 user_name-Inspiron-15-3567 ModemManager[1042]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1': not supported by any plugin
Mar 19 17:29:03 user_name-Inspiron-15-3567 dhclient[4245]: XMT: Info-Request on enp0s20f0u1, interval 1090ms.
Mar 19 17:29:03 user_name-Inspiron-15-3567 dhclient[4245]: RCV: Reply message on enp0s20f0u1 from fe80::184b:64ff:fe5b:7545.
Mar 19 17:29:03 user_name-Inspiron-15-3567 nm-dispatcher: req:2 'dhcp6-change' [enp0s20f0u1]: new request (2 scripts)
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.7596]   nameserver '2402:8100:9:0:8000::1'
Mar 19 17:29:03 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:03] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:03 user_name-Inspiron-15-3567 nm-dispatcher: req:2 'dhcp6-change' [enp0s20f0u1]: start running ordered scripts...
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.7597]   nameserver '2402:8100:d::1'
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.7597] dhcp6 (enp0s20f0u1): state changed unknown -> bound
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.8163] dhcp6 (enp0s20f0u1): client pid 4245 exited with status 0
Mar 19 17:29:03 user_name-Inspiron-15-3567 NetworkManager[1075]: <info>  [1489924743.8163] dhcp6 (enp0s20f0u1): state changed bound -> done
Mar 19 17:29:04 user_name-Inspiron-15-3567 avahi-daemon[1052]: Leaving mDNS multicast group on interface enp0s20f0u1.IPv6 with address fe80::dda7:f675:3485:2de.
Mar 19 17:29:04 user_name-Inspiron-15-3567 avahi-daemon[1052]: Joining mDNS multicast group on interface enp0s20f0u1.IPv6 with address 2402:8100:3900:1a84:adb6:548:2a07:9f2d.
Mar 19 17:29:04 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.*.
Mar 19 17:29:04 user_name-Inspiron-15-3567 avahi-daemon[1052]: Withdrawing address record for fe80::dda7:f675:3485:2de on enp0s20f0u1.
Mar 19 17:29:04 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:04] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:04 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for 2402:8100:3900:1a84:b15c:7e85:4388:c2b on enp0s20f0u1.*.
Mar 19 17:29:04 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:04] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:05 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:05] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:08 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:08] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:17 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:17] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:26 user_name-Inspiron-15-3567 avahi-daemon[1052]: Withdrawing address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.
Mar 19 17:29:26 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.*.
Mar 19 17:29:27 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:27] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:35 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:35] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:43 user_name-Inspiron-15-3567 avahi-daemon[1052]: Withdrawing address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.
Mar 19 17:29:43 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.*.
Mar 19 17:29:44 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:44] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:51 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:51] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:29:56 user_name-Inspiron-15-3567 whoopsie[1107]: [17:29:56] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:01 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:01] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:06 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:06] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:11 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:11] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:16 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:16] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:21 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:21] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:30 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:30] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:37 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:37] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:46 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:46] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:30:53 user_name-Inspiron-15-3567 whoopsie[1107]: [17:30:53] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:02 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:02] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:06 user_name-Inspiron-15-3567 org.gnome.Terminal[1937]: (gnome-terminal-server:3847): Gtk-CRITICAL **: gtk_device_grab_add: assertion 'GDK_IS_DEVICE (device)' failed
Mar 19 17:31:10 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:10] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:17 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:17] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:22 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:22] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:26 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:26] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:30 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:30] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:33 user_name-Inspiron-15-3567 /usr/lib/snapd/snapd[1112]: daemon.go:176: DEBUG: uid=1001;@ GET /v2/find?q=tom 2.851698141s 500
Mar 19 17:31:33 user_name-Inspiron-15-3567 gnome-session[2111]: (gnome-software:2275): Gs-WARNING **: failed to call gs_plugin_add_search on snap: snapd returned status code 500: Internal Server Error
Mar 19 17:31:33 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:33.706] Initializing Mono.Addins
Mar 19 17:31:35 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:35] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:38 user_name-Inspiron-15-3567 org.gnome.OnlineMiners.MediaServer[1937]: Gom-Message: Setting scheduler policy to SCHED_IDLE
Mar 19 17:31:38 user_name-Inspiron-15-3567 org.gnome.OnlineMiners.GData[1937]: Gom-Message: Setting scheduler policy to SCHED_IDLE
Mar 19 17:31:38 user_name-Inspiron-15-3567 dleyna-server-service[4467]: dLeyna core version 0.4.0
Mar 19 17:31:38 user_name-Inspiron-15-3567 dleyna-server-service[4467]: dleyna-server-service version 0.4.0
Mar 19 17:31:38 user_name-Inspiron-15-3567 org.gnome.OnlineMiners.Flickr[1937]: Gom-Message: Setting scheduler policy to SCHED_IDLE
Mar 19 17:31:38 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Type[0] Level[0x13] Mask[0x4C] Flags[0x4F]
Mar 19 17:31:38 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Load file [/home/user_name/.config/dleyna-server-service.conf]
Mar 19 17:31:38 user_name-Inspiron-15-3567 dleyna-server-service[4467]: [General settings]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Never Quit: F
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Connector Name: dbus
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: [Logging settings]
Mar 19 17:31:40 user_name-Inspiron-15-3567 org.gnome.OnlineMiners.Facebook[1937]: Gom-Message: Setting scheduler policy to SCHED_IDLE
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Log Type : 0
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Log Level: 0x13
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: [Network filtering settings]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Enabled : F
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-server-service[4467]: Entries: (null)
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: dLeyna core version 0.4.0
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: dleyna-renderer-service version 0.4.0
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Type[0] Level[0x13] Mask[0x4C] Flags[0x4F]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Load file [/home/user_name/.config/dleyna-renderer-service.conf]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: [General settings]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Never Quit: F
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Connector Name: dbus
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: [Logging settings]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Log Type : 0
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Log Level: 0x13
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: [Network filtering settings]
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Enabled : F
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Entries: (null)
Mar 19 17:31:40 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Calling GetRenderers method
Mar 19 17:31:42 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:42] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:47 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [ERROR 17:31:47.989] Error parsing note XML, skipping "/home/user_name/.local/share/tomboy/03b785ad-09cf-49fc-b851-9b4e09aa33f9.note": Root element is missing.
Mar 19 17:31:48 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [ERROR 17:31:48.049] Error parsing note XML, skipping "/home/user_name/.local/share/tomboy/1793c466-49ad-4534-889b-a29987528864.note": Root element is missing.
Mar 19 17:31:48 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [ERROR 17:31:48.419] Error parsing note XML, skipping "/home/user_name/.local/share/tomboy/6fdcae63-19c4-47e4-b54c-480569caa0ae.note": Root element is missing.
Mar 19 17:31:48 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [ERROR 17:31:48.772] Error parsing note XML, skipping "/home/user_name/.local/share/tomboy/cce8e4bf-e72e-45ea-924b-613369b714e3.note": Root element is missing.
Mar 19 17:31:48 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [ERROR 17:31:48.812] Error parsing note XML, skipping "/home/user_name/.local/share/tomboy/dbdf5b33-3351-4a0e-999a-5e8f4ea5797c.note": Root element is missing.
Mar 19 17:31:48 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [ERROR 17:31:48.824] Error parsing note XML, skipping "/home/user_name/.local/share/tomboy/f83d020a-e119-424f-ae03-2e4cc0dcb05d.note": Root element is missing.
Mar 19 17:31:49 user_name-Inspiron-15-3567 gnome-session[2111]: Gjs-Message: JS LOG: Received error from DBus search provider org.gnome.Documents.desktop: Gio.IOErrorEnum: Timeout was reached
Mar 19 17:31:49 user_name-Inspiron-15-3567 gnome-session[2111]: Gjs-Message: JS LOG: Received error from DBus search provider bijiben.desktop: Gio.IOErrorEnum: Timeout was reached
Mar 19 17:31:49 user_name-Inspiron-15-3567 gnome-session[2111]: Gjs-Message: JS LOG: Received error from DBus search provider org.gnome.Photos.desktop: Gio.IOErrorEnum: Timeout was reached
Mar 19 17:31:49 user_name-Inspiron-15-3567 dleyna-server-service[4467]: dLeyna: Exit
Mar 19 17:31:49 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:49] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:31:50 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:50.918] Monitor number returned by GetMonitorAtPoint (actual) is: 0
Mar 19 17:31:50 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:50.918] Saved monitor number is: 0
Mar 19 17:31:50 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:50.918] Saved Search window position is 0 x 27
Mar 19 17:31:50 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:50.918] Saved monitor number does match the actual one...
Mar 19 17:31:50 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:50.918] ...and saved window position is within it - restoring as-is.
Mar 19 17:31:50 user_name-Inspiron-15-3567 tomboy.desktop[4346]: [INFO 17:31:50.918] Restoring Search window to position 0 x 27 at monitor 0
Mar 19 17:31:58 user_name-Inspiron-15-3567 whoopsie[1107]: [17:31:58] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:03 user_name-Inspiron-15-3567 org.gnome.Bijiben.SearchProvider[1937]: Unable to load location /home/user_name/.local/share/bijiben: Error opening directory '/home/user_name/.local/share/bijiben': No such file or directory
Mar 19 17:32:03 user_name-Inspiron-15-3567 org.gnome.Bijiben.SearchProvider[1937]: (bijiben-shell-search-provider:4316): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Mar 19 17:32:03 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: Client :1.103 lost
Mar 19 17:32:04 user_name-Inspiron-15-3567 dleyna-renderer-service[4484]: dLeyna: Exit
Mar 19 17:32:04 user_name-Inspiron-15-3567 org.gnome.Bijiben.SearchProvider[1937]: (bijiben-shell-search-provider:4316): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Mar 19 17:32:04 user_name-Inspiron-15-3567 org.gnome.Bijiben.SearchProvider[1937]: sending the mass change
Mar 19 17:32:05 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:05] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:11 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:11] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:19 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:19] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:23 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:23] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:30 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:30] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:34 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:34] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:42 user_name-Inspiron-15-3567 avahi-daemon[1052]: Withdrawing address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.
Mar 19 17:32:42 user_name-Inspiron-15-3567 avahi-daemon[1052]: Registering new address record for 2402:8100:3900:1a84:adb6:548:2a07:9f2d on enp0s20f0u1.*.
Mar 19 17:32:43 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:43] Cannot reach: https://daisy.ubuntu.com
Mar 19 17:32:50 user_name-Inspiron-15-3567 whoopsie[1107]: [17:32:50] Cannot reach: https://daisy.ubuntu.com


```

Thanks

---

### Post by ajithabraham.m on 2017-03-19
if tries to reconnect from a different usb port it works but the used ports can't use again. if ran out usb ports then restarting the OS is the only option.

---

