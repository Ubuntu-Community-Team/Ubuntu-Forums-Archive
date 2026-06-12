---
title: "Issue in connecting to a specific AP"
date: 2018-07-26
forum: Networking &amp; Wireless
---

### Post by mickmack8302 on 2018-07-26
I'm facing a rather strange issue where my 16.04 LTS can't connect to a specific AP (hidden). My Alienware 17r3  could usually connect to this AP, but it suddenly stopped connecting about a month ago with this problem:

```
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1591] device (wlp60s0): Activation: starting connection 'XXXXXXXX' (cba54f63-889d-4444-8271-9d96d60b2076)
Jul 26 10:13:15 dbus[809]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jul 26 10:13:15 NetworkManager[904]: <warn>  [1532580195.1600] sup-iface[0x1045210,wlp60s0]: connection disconnected (reason -3)
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1601] device (wlp60s0): supplicant interface state: completed -> disconnected
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1619] device (wlp60s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1624] manager: NetworkManager state is now CONNECTING
Jul 26 10:13:15 gnome-session[1730]: ERROR:dbus.connection:Exception in handler for D-Bus signal:
Jul 26 10:13:15 gnome-session[1730]: Traceback (most recent call last):
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
Jul 26 10:13:15 gnome-session[1730]:     self._handler(*args, **kwargs)
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/UpdateManager/Core/AlertWatcher.py", line 78, in _on_network_state_changed
Jul 26 10:13:15 gnome-session[1730]:     self._update_3g_state()
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/UpdateManager/Core/AlertWatcher.py", line 83, in _update_3g_state
Jul 26 10:13:15 gnome-session[1730]:     on_3g = nm.is_active_connection_gsm_or_cdma()
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/UpdateManager/Core/roam.py", line 172, in is_active_connection_gsm_or_cdma
Jul 26 10:13:15 gnome-session[1730]:     active, self.NM_DBUS_IFACE + ".Connection.Active", 'Default')
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/UpdateManager/Core/roam.py", line 162, in get_dbus_property
Jul 26 10:13:15 gnome-session[1730]:     property = props.Get(interface, property)
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
Jul 26 10:13:15 gnome-session[1730]:     return self._proxy_method(*args, **keywords)
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
Jul 26 10:13:15 gnome-session[1730]:     **keywords)
Jul 26 10:13:15 gnome-session[1730]:   File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
Jul 26 10:13:15 gnome-session[1730]:     message, timeout)
Jul 26 10:13:15 gnome-session[1730]: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.freedesktop.DBus.Properties' on object at path /org/freedesktop/NetworkManager/ActiveConnection/3
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1637] device (wlp60s0): state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 10:13:15 gnome-session[1730]: (nm-applet:1892): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Jul 26 10:13:15 gnome-session[1730]: (nm-applet:1892): nm-applet-CRITICAL **: get_menu_item_for_ap: assertion 'dup_data.hash != NULL' failed
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1641] device (wlp60s0): Activation: (wifi) access point 'XXXXXXXX' has security, but secrets are required.
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1641] device (wlp60s0): state change: config -> need-auth (reason 'none') [50 60 0]
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1683] device (wlp60s0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1686] device (wlp60s0): state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1688] device (wlp60s0): Activation: (wifi) connection 'XXXXXXXX' has security, and secrets exist.  No new secrets needed.
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1688] Config: added 'ssid' value 'XXXXXXXX'
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1688] Config: added 'scan_ssid' value '1'
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1689] Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1689] Config: added 'psk' value '<omitted>'
Jul 26 10:13:15 NetworkManager[904]: <info>  [1532580195.1695] sup-iface[0x1045210,wlp60s0]: config: set interface ap_scan to 1
Jul 26 10:13:15 systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul 26 10:13:15 dbus[809]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 10:13:15 systemd[1]: Started Network Manager Script Dispatcher Service.
Jul 26 10:13:15 nm-dispatcher: req:1 'down' [wlp60s0]: new request (1 scripts)
Jul 26 10:13:15 nm-dispatcher: req:1 'down' [wlp60s0]: start running ordered scripts...
Jul 26 10:13:15 wpa_supplicant[1052]: p2p-dev-wlp60s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Jul 26 10:13:16 wpa_supplicant[1052]: p2p-dev-wlp60s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Jul 26 10:13:20 NetworkManager[904]: <info>  [1532580200.1904] device (wlp60s0): supplicant interface state: disconnected -> scanning
Jul 26 10:13:40 NetworkManager[904]: <warn>  [1532580220.8958] device (wlp60s0): Activation: (wifi) association took too long, failing activation
Jul 26 10:13:40 NetworkManager[904]: <info>  [1532580220.8959] device (wlp60s0): state change: config -> failed (reason 'ssid-not-found') [50 120 53]
Jul 26 10:13:40 NetworkManager[904]: <info>  [1532580220.8962] manager: NetworkManager state is now DISCONNECTED
Jul 26 10:13:40 NetworkManager[904]: <warn>  [1532580220.8975] device (wlp60s0): Activation: failed for connection 'XXXXXXXX'
Jul 26 10:13:40 NetworkManager[904]: <info>  [1532580220.8990] device (wlp60s0): state change: failed -> disconnected (reason 'none') [120 30 0]
Jul 26 10:13:40 kernel: [ 2736.367488] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready
Jul 26 10:13:40 NetworkManager[904]: <info>  [1532580220.9027] device (wlp60s0): supplicant interface state: scanning -> disconnected

```

- This doesn't seem to be a hardware issue: I can connect using the inbuilt Killer Wifi chip on WIndows, and several other endpoints on Linux. I also tried with a TP-Link dongle (RTL8192-XX) and it connected once on Linux, but it's stopped connecting now (works flawlessly on Windows)
- This doesn't seem to be a region issue/11n issue: I configured iwlwifi to use the AP region (TW) and several other regions and permanently disabled 802.11n, but didn't work 
- This doesn't seem to be an AP issue - I can connect on WIndows, and several other devices work flawlessly
- I can see the BSSID if running ```
iwlist wlp60s0 scan
```
I disabled NetworkManager and tried connecting directly through wpa_supplicand, but it doesn't associate with the AP

I have literally run out of ideas at the moment - the wifi card seems to be all right, but just doesn't work with this specific AP

Any idea what could be going wrong?

---

### Post by TheFu on 2018-07-27
Signal width can be controlled in such a way as to prevent some clients from connecting.  This is usually setup to prevent older, slower, wifi clients from connecting to new, fast, SSIDs.

---

