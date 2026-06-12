---
title: "Ethernet locks.  Syslog full of error messages."
date: 2017-09-07
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2017-09-07
Hi

After a period of inactivity my Ethernet locks up.  My syslog is full of messages that I don't understand.

```

Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 17:28:44 mimir systemd-resolved[1185]: Switching to DNS server 210.55.111.1 for interface enp3s0.
</CODE>

If I try and ping 210.55.111.1 or 122.56.237.1, they are unreachable.
I get connected again by turning the network off/on in the System GUI.
This is what appears in the syslog.  I have substituted some IP addresses with xxx.xxx.xxx.xxx.

<CODE>
Sep  7 18:12:16 mimir hud-service[2229]: #033[31mvoid DBusMenuImporter::slotGetLayoutFinished(QDBusPendingCallWatcher*)#033[0m: "No such interface 'com.canonical.dbusmenu' on object at path /org/ayatana/bamf/window/56623115"
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0131] device (enp3s0): state change: activated -> deactivating (reason 'user-requested') [100 110 39]
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0132] manager: NetworkManager state is now DISCONNECTING
Sep  7 18:12:18 mimir dbus[916]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Sep  7 18:12:18 mimir systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0167] audit: op="device-disconnect" interface="enp3s0" ifindex=2 pid=3797 uid=1000 result="success"
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0171] device (enp3s0): state change: deactivating -> disconnected (reason 'user-requested') [110 30 39]
Sep  7 18:12:18 mimir avahi-daemon[986]: Withdrawing address record for fe80::a573:c4d8:4131:2f24 on enp3s0.
Sep  7 18:12:18 mimir avahi-daemon[986]: Leaving mDNS multicast group on interface enp3s0.IPv6 with address fe80::a573:c4d8:4131:2f24.
Sep  7 18:12:18 mimir avahi-daemon[986]: Interface enp3s0.IPv6 no longer relevant for mDNS.
Sep  7 18:12:18 mimir dbus[916]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep  7 18:12:18 mimir systemd[1]: Started Network Manager Script Dispatcher Service.
Sep  7 18:12:18 mimir nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Sep  7 18:12:18 mimir nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0309] dhcp4 (enp3s0): canceled DHCP transaction, DHCP client pid 1231
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0309] dhcp4 (enp3s0): state changed bound -> done
Sep  7 18:12:18 mimir NetworkManager[961]: <info>  [1504764738.0315] manager: NetworkManager state is now DISCONNECTED
Sep  7 18:12:18 mimir nm-dispatcher: req:2 'down' [enp3s0]: new request (1 scripts)
Sep  7 18:12:18 mimir nm-dispatcher: req:2 'down' [enp3s0]: start running ordered scripts...
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6152] device (enp3s0): Activation: starting connection 'Wired connection 1' (562ad437-d81e-31ed-9db9-418fc19eb921)
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6153] audit: op="connection-activate" uuid="562ad437-d81e-31ed-9db9-418fc19eb921" name="Wired connection 1" pid=3797 uid=1000 result="success"
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6153] device (enp3s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6154] manager: NetworkManager state is now CONNECTING
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6157] device (enp3s0): state change: prepare -> config (reason 'none') [40 50 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6161] device (enp3s0): state change: config -> ip-config (reason 'none') [50 70 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6163] dhcp4 (enp3s0): activation: beginning transaction (timeout in 45 seconds)
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6172] dhcp4 (enp3s0): dhclient started with pid 3826
Sep  7 18:12:21 mimir dhclient[3826]: DHCPREQUEST of xxx.xxx.xxx.xxx on enp3s0 to 255.255.255.255 port 67 (xid=0x16a00b88)
Sep  7 18:12:21 mimir dhclient[3826]: DHCPACK of xxx.xxx.xxx.xxx from xxx.xxx.xxx.xxx
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6621] dhcp4 (enp3s0):   address xxx.xxx.xxx.xxx
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6623] dhcp4 (enp3s0):   plen 24 (255.255.255.0)
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6624] dhcp4 (enp3s0):   gateway xxx.xxx.xxx.xxx
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6625] dhcp4 (enp3s0):   server identifier xxx.xxx.xxx.xxx
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6626] dhcp4 (enp3s0):   lease time 3600
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6627] dhcp4 (enp3s0):   hostname 'mimir'
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6628] dhcp4 (enp3s0):   nameserver '122.56.237.1'
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6629] dhcp4 (enp3s0):   nameserver '210.55.111.1'
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6630] dhcp4 (enp3s0):   domain name 'localdomain'
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6632] dhcp4 (enp3s0): state changed unknown -> bound
Sep  7 18:12:21 mimir avahi-daemon[986]: Joining mDNS multicast group on interface enp3s0.IPv4 with address xxx.xxx.xxx.xxx
Sep  7 18:12:21 mimir avahi-daemon[986]: New relevant interface enp3s0.IPv4 for mDNS.
Sep  7 18:12:21 mimir avahi-daemon[986]: Registering new address record for xxx.xxx.xxx.xxx on enp3s0.IPv4.
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6649] device (enp3s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Sep  7 18:12:21 mimir dhclient[3826]: bound to xxx.xxx.xxx.xxx -- renewal in 1470 seconds.
Sep  7 18:12:21 mimir systemd-resolved[1185]: Switching to fallback DNS server 8.8.8.8.
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6672] device (enp3s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6674] device (enp3s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6675] manager: NetworkManager state is now CONNECTED_LOCAL
Sep  7 18:12:21 mimir nm-dispatcher: req:3 'connectivity-change': new request (1 scripts)
Sep  7 18:12:21 mimir nm-dispatcher: req:3 'connectivity-change': start running ordered scripts...
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6708] manager: NetworkManager state is now CONNECTED_GLOBAL
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6709] policy: set 'Wired connection 1' (enp3s0) as default for IPv4 routing and DNS
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6710] device (enp3s0): Activation: successful, device activated.
Sep  7 18:12:21 mimir nm-dispatcher: req:4 'up' [enp3s0]: new request (1 scripts)
Sep  7 18:12:21 mimir nm-dispatcher: req:4 'up' [enp3s0]: start running ordered scripts...
Sep  7 18:12:21 mimir systemd-resolved[1185]: Switching to DNS server 122.56.237.1 for interface enp3s0.
Sep  7 18:12:21 mimir whoopsie[2390]: [18:12:21] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Sep  7 18:12:21 mimir whoopsie[2390]: [18:12:21] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Sep  7 18:12:21 mimir whoopsie[2390]: [18:12:21] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Sep  7 18:12:21 mimir whoopsie[2390]: [18:12:21] online
Sep  7 18:12:23 mimir colord[1101]: failed to get session [pid 3136]: No such device or address
Sep  7 18:12:23 mimir avahi-daemon[986]: Joining mDNS multicast group on interface enp3s0.IPv6 with address fe80::a573:c4d8:4131:2f24.
Sep  7 18:12:23 mimir avahi-daemon[986]: New relevant interface enp3s0.IPv6 for mDNS.
Sep  7 18:12:23 mimir avahi-daemon[986]: Registering new address record for fe80::a573:c4d8:4131:2f24 on enp3s0.*.

```

After this, the network works again.

Where should I look to try fixing this problem?

---

### Post by BenginM on 2017-09-08
Hiya Dazz,  try setting the DNS servers with opendns or google's , and make sure the Ethernet device has an IP address) different from any other device on the same network!


 we see few of these:
```

NetworkManager[961]: <info>  [1504764741.6153] device (enp3s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
 mimir NetworkManager[961]: <info>  [1504764741.6157] device (enp3s0): state change: prepare -> config (reason 'none') [40 50 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6161] device (enp3s0): state change: config -> ip-config (reason 'none') [50 70 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6163] dhcp4 (enp3s0): activation: beginning transaction (timeout in 45 seconds)
NetworkManager[961]: <info>  [1504764741.6649] device (enp3s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
mimir NetworkManager[961]: <info>  [1504764741.6672] device (enp3s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6674] device (enp3s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6675] manager: NetworkManager state is now CONNECTED_LOCAL
Sep  7 18:12:21 mimir nm-dispatcher: req:3 'connectivity-change': new request (1 scripts)
Sep  7 18:12:21 mimir nm-dispatcher: req:3 'connectivity-change': start running ordered scripts...
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6708] manager: NetworkManager state is now CONNECTED_GLOBAL
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6709] policy: set 'Wired connection 1' (enp3s0) as default for IPv4 routing and DNS
Sep  7 18:12:21 mimir NetworkManager[961]: <info>  [1504764741.6710] device (enp3s0): Activation: successful, device activated.

```

we see the ethernet device/interface enp3s0. is using IPv6 with address 
fe80::a573:c4d8:4131:2f24 , Does Ethernet locks up if you ignore IPv6 
and go with IPv4 only ?

---

### Post by dazz100 on 2017-09-10
Hi
I don't have anything intentionally configured for IP6.  Maybe I need to disable IP6 on this machine.

I tried pinging both DNS server addresses but got no response.  IP lookup shows they are valid addresses owned by my ISP.  
My firewall also shows I am connected.
I can get around the Internet including this site so I don't think DNS IP is the problem.

This appears to log the network failure, but I don't understand enough of it to find the root cause.

```
Sep 10 16:16:07 mimir unity-settings-[1875]: failed to turn the kbd backlight off: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.freedesktop.UPower.KbdBacklight' on object at path /org/freedesktop/UPower/KbdBacklight
Sep 10 16:16:07 mimir gnome-session[1916]: gnome-session-binary[1916]: GLib-GIO-CRITICAL: g_dbus_connection_call_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
Sep 10 16:16:07 mimir gnome-session-binary[1916]: GLib-GIO-CRITICAL: g_dbus_connection_call_internal: assertion 'object_path != NULL && g_variant_is_object_path (object_path)' failed
Sep 10 16:16:07 mimir systemd[1566]: Starting Backing Service for the Unity Panel in Lockscreen mode...
Sep 10 16:16:07 mimir compiz[2083]: WARN  2017-09-10 16:16:07 unity.glib.dbus.proxy GLibDBusProxy.cpp:487 Calling method "EmitEvent" on object path: "/com/ubuntu/Upstart" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name com.canonical.Unity.Test.Upstart was not provided by any .service files
Sep 10 16:16:07 mimir unity-panel-ser[2096]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
Sep 10 16:16:07 mimir systemd[1566]: Started Backing Service for the Unity Panel in Lockscreen mode.
Sep 10 16:16:07 mimir systemd[1566]: Reached target A target that, when running, represents the screen being locked.
Sep 10 16:17:01 mimir CRON[3267]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 10 16:18:28 mimir unity-panel-ser[2096]: menus_destroyed: assertion 'IS_WINDOW_MENU(wm)' failed
Sep 10 16:18:28 mimir systemd[1566]: Stopped target A target that, when running, represents the screen being locked.
Sep 10 16:18:28 mimir systemd[1566]: Stopping Backing Service for the Unity Panel in Lockscreen mode...
Sep 10 16:18:28 mimir compiz[2083]: WARN  2017-09-10 16:18:28 unity.glib.dbus.proxy GLibDBusProxy.cpp:487 Calling method "EmitEvent" on object path: "/com/ubuntu/Upstart" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name com.canonical.Unity.Test.Upstart was not provided by any .service files
Sep 10 16:18:29 mimir systemd[1566]: Stopped Backing Service for the Unity Panel in Lockscreen mode.
Sep 10 16:19:04 mimir compiz[2083]: Promise rejected after context unloaded: Message manager disconnected
Sep 10 16:19:41 mimir compiz[2083]: message repeated 3 times: [ Promise rejected after context unloaded: Message manager disconnected]
Sep 10 16:26:43 mimir avahi-daemon[930]: Withdrawing address record for xxx.xx.xx.xxx on enp3s0.
Sep 10 16:26:43 mimir avahi-daemon[930]: Leaving mDNS multicast group on interface enp3s0.IPv4 with address xxx.xx.xx.xxx.
Sep 10 16:26:43 mimir avahi-daemon[930]: Interface enp3s0.IPv4 no longer relevant for mDNS.
Sep 10 16:26:43 mimir systemd-resolved[1212]: Switching to DNS server 210.55.111.1 for interface enp3s0.
Sep 10 16:26:43 mimir systemd-resolved[1212]: Switching to DNS server 122.56.237.1 for interface enp3s0.

```

---

