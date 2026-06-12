---
title: "USB WiFi adapter dropped DNS but not connection"
date: 2017-01-24
forum: Networking &amp; Wireless
---

### Post by dbclin2 on 2017-01-24
Hi,
I'm trying to figure out if the USB WiFi adapter (TP-Link with an Atheros AR9271 Rev:1 chipset) I'm using for my Ubuntu 16.04 desktop needs replacing or if it might be a software problem.
The device does sometimes drop the connection, which can be restored by pulling the device and then replacing it. It's a pain, but it's reliable. However today, for the first time, I had connectivity, but DNS failed: I could ping 8.8.8.8 but not google.com. I know that it wasn't my router or ISP, because my laptop had complete and uninterrupted connectivity. Pulling the USB device and replacing it worked immediately. 
Does this look like a software problem?
Thanks.
Here's the output from journalctl:

```
Jan 24 16:38:50 workstation ddclient[22289]: WARNING:  cannot connect to checkip.dyndns.com:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.com'Jan 24 16:44:10 workstation ddclient[22451]: WARNING:  cannot connect to checkip.dyndns.com:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.com'
Jan 24 16:44:11 workstation dnsmasq-dhcp[1648]: DHCPREQUEST(lxcbr0) 10.0.3.141 00:16:3e:d3:14:10
Jan 24 16:44:11 workstation dnsmasq-dhcp[1648]: DHCPACK(lxcbr0) 10.0.3.141 00:16:3e:d3:14:10 base
Jan 24 16:48:23 workstation gnome-session[3003]: [3356:3393:0124/164823:ERROR:connection_factory_impl.cc(367)] Failed to connect to MCS endpoint with error -137
Jan 24 16:49:30 workstation ddclient[22539]: WARNING:  cannot connect to checkip.dyndns.com:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.com'
Jan 24 16:50:31 workstation sudo[22546]: dbclinton : TTY=pts/2 ; PWD=/home/dbclinton ; USER=root ; COMMAND=/bin/systemctl status networking
Jan 24 16:50:31 workstation sudo[22546]: pam_unix(sudo:session): session opened for user root by (uid=0)
Jan 24 16:50:36 workstation sudo[22546]: pam_unix(sudo:session): session closed for user root
Jan 24 16:50:43 workstation sudo[22554]: dbclinton : TTY=pts/2 ; PWD=/home/dbclinton ; USER=root ; COMMAND=/bin/systemctl restart networking
Jan 24 16:50:43 workstation sudo[22554]: pam_unix(sudo:session): session opened for user root by (uid=0)
Jan 24 16:50:44 workstation systemd[1]: Stopping Raise network interfaces...
Jan 24 16:50:44 workstation systemd[1]: Stopped Raise network interfaces.
Jan 24 16:50:44 workstation systemd[1]: Starting Raise network interfaces...
Jan 24 16:50:44 workstation systemd[1]: Started Raise network interfaces.
Jan 24 16:54:39 workstation org.gnome.panel.applet.GWeatherAppletFactory[2890]: (gweather-applet-2:3240): GLib-CRITICAL **: Source ID 639 was not found when attempting to remove it
Jan 24 16:55:48 workstation kernel: usb 8-2: USB disconnect, device number 3
Jan 24 16:55:48 workstation kernel: wlxec086b1ef0b3: deauthenticating from 00:23:6a:78:25:34 by local choice (Reason: 3=DEAUTH_LEAVING)
Jan 24 16:55:48 workstation kernel: ath: phy0: Failed to wakeup in 500us
Jan 24 16:55:48 workstation NetworkManager[1242]: <warn>  [1485294948.1271] sup-iface[0x24cdf70,wlxec086b1ef0b3]: connection disconnected (reason -3)
Jan 24 16:55:48 workstation wpa_supplicant[1364]: wlxec086b1ef0b3: CTRL-EVENT-DISCONNECTED bssid=00:23:6a:78:25:34 reason=3 locally_generated=1
Jan 24 16:55:48 workstation avahi-daemon[1246]: Interface wlxec086b1ef0b3.IPv6 no longer relevant for mDNS.
Jan 24 16:55:48 workstation dhclient[2532]: receive_packet failed on wlxec086b1ef0b3: Network is down
Jan 24 16:55:48 workstation kernel: ath: phy0: Failed to wakeup in 500us
Jan 24 16:55:48 workstation avahi-daemon[1246]: Leaving mDNS multicast group on interface wlxec086b1ef0b3.IPv6 with address fe80::d31:a846:4084:b994.
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.2641] device (wlxec086b1ef0b3): state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jan 24 16:55:48 workstation avahi-daemon[1246]: Interface wlxec086b1ef0b3.IPv4 no longer relevant for mDNS.
Jan 24 16:55:48 workstation avahi-daemon[1246]: Leaving mDNS multicast group on interface wlxec086b1ef0b3.IPv4 with address 192.168.1.3.
Jan 24 16:55:48 workstation avahi-daemon[1246]: Withdrawing address record for fe80::d31:a846:4084:b994 on wlxec086b1ef0b3.
Jan 24 16:55:48 workstation avahi-daemon[1246]: Withdrawing address record for 192.168.1.3 on wlxec086b1ef0b3.
Jan 24 16:55:48 workstation whoopsie[1153]: [16:55:48] Cannot reach: https://daisy.ubuntu.com
Jan 24 16:55:48 workstation whoopsie[1153]: [16:55:48] offline
Jan 24 16:55:48 workstation kernel: cfg80211: World regulatory domain updated:
Jan 24 16:55:48 workstation kernel: cfg80211:  DFS Master region: unset
Jan 24 16:55:48 workstation kernel: cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 24 16:55:48 workstation kernel: cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 24 16:55:48 workstation kernel: cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 24 16:55:48 workstation kernel: cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Jan 24 16:55:48 workstation kernel: cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Jan 24 16:55:48 workstation kernel: cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Jan 24 16:55:48 workstation kernel: cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Jan 24 16:55:48 workstation kernel: cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Jan 24 16:55:48 workstation kernel: cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Jan 24 16:55:48 workstation whoopsie[1153]: [16:55:48] Cannot reach: https://daisy.ubuntu.com
Jan 24 16:55:48 workstation wpa_supplicant[1364]: wlxec086b1ef0b3: CTRL-EVENT-SCAN-FAILED ret=-19 retry=1
Jan 24 16:55:48 workstation wpa_supplicant[1364]: wlxec086b1ef0b3: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jan 24 16:55:48 workstation kernel: usb 8-2: ath9k_htc: USB layer deinitialized
Jan 24 16:55:48 workstation systemd[1]: Starting Load/Save RF Kill Switch Status...
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.3071] dhcp4 (wlxec086b1ef0b3): canceled DHCP transaction, DHCP client pid 2532
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.3072] dhcp4 (wlxec086b1ef0b3): state changed bound -> done
Jan 24 16:55:48 workstation NetworkManager[1242]: <error> [1485294948.3080] platform-linux: do-change-link[4]: failure changing link: failure 19 (No such device)
Jan 24 16:55:48 workstation NetworkManager[1242]: <error> [1485294948.3082] platform-linux: do-change-link[4]: failure changing link: failure 19 (No such device)
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.3085] dns-mgr: Writing DNS information to /sbin/resolvconf
Jan 24 16:55:48 workstation systemd[1]: Started Load/Save RF Kill Switch Status.
Jan 24 16:55:48 workstation dnsmasq[2550]: setting upstream servers from DBus
Jan 24 16:55:48 workstation dnsmasq[1648]: reading /etc/resolv.conf
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.3513] manager: NetworkManager state is now CONNECTED_LOCAL
Jan 24 16:55:48 workstation dnsmasq[1648]: using nameserver 127.0.1.1#53
Jan 24 16:55:48 workstation dbus[1200]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jan 24 16:55:48 workstation NetworkManager[1242]: <error> [1485294948.4285] platform-linux: do-change-link[4]: failure changing link: failure 19 (No such device)
Jan 24 16:55:48 workstation NetworkManager[1242]: <warn>  [1485294948.4285] device (wlxec086b1ef0b3): failed to disable userspace IPv6LL address handling
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.4286] radio killswitch /sys/devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/ieee80211/phy0/rfkill0 disappeared
Jan 24 16:55:48 workstation NetworkManager[1242]: <info>  [1485294948.4289] devices removed (path: /sys/devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/net/wlxec086b1ef0b3, iface: wlxec086b1ef0b3)
Jan 24 16:55:48 workstation systemd[1]: Starting Network Manager Script Dispatcher Service...
Jan 24 16:55:48 workstation wpa_supplicant[1364]: nl80211: deinit ifname=wlxec086b1ef0b3 disabled_11b_rates=0
Jan 24 16:55:48 workstation dbus[1200]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 24 16:55:48 workstation systemd[1]: Started Network Manager Script Dispatcher Service.
Jan 24 16:55:48 workstation nm-dispatcher[22820]: req:1 'down' [wlxec086b1ef0b3]: new request (2 scripts)
Jan 24 16:55:48 workstation nm-dispatcher[22820]: req:1 'down' [wlxec086b1ef0b3]: start running ordered scripts...
Jan 24 16:55:48 workstation systemd[1]: Stopping LSB: Update dynamic domain name service entries...
Jan 24 16:55:48 workstation systemd[1]: Stopped LSB: Update dynamic domain name service entries.
Jan 24 16:55:50 workstation gnome-session[3003]: [3356:3393:0124/165550:ERROR:connection_factory_impl.cc(367)] Failed to connect to MCS endpoint with error -137
Jan 24 16:55:52 workstation colord-sane[22779]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 24 16:55:52 workstation kernel: usb 8-2: new high-speed USB device number 4 using xhci_hcd
Jan 24 16:55:53 workstation kernel: usb 8-2: New USB device found, idVendor=0cf3, idProduct=9271
Jan 24 16:55:53 workstation kernel: usb 8-2: New USB device strings: Mfr=16, Product=32, SerialNumber=48
Jan 24 16:55:53 workstation kernel: usb 8-2: Product: USB2.0 WLAN
Jan 24 16:55:53 workstation kernel: usb 8-2: Manufacturer: ATHEROS
Jan 24 16:55:53 workstation kernel: usb 8-2: SerialNumber: 12345
Jan 24 16:55:53 workstation kernel: usb 8-2: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
Jan 24 16:55:53 workstation kernel: usb 8-2: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
Jan 24 16:55:53 workstation kernel: ath9k_htc 8-2:1.0: ath9k_htc: HTC initialized with 33 credits
Jan 24 16:55:54 workstation kernel: ath9k_htc 8-2:1.0: ath9k_htc: FW Version: 1.4
Jan 24 16:55:54 workstation kernel: ath9k_htc 8-2:1.0: FW RMW support: On
Jan 24 16:55:54 workstation kernel: ath: EEPROM regdomain: 0x809c
Jan 24 16:55:54 workstation kernel: ath: EEPROM indicates we should expect a country code
Jan 24 16:55:54 workstation kernel: ath: doing EEPROM country->regdmn map search
Jan 24 16:55:54 workstation kernel: ath: country maps to regdmn code: 0x52
Jan 24 16:55:54 workstation kernel: ath: Country alpha2 being used: CN
Jan 24 16:55:54 workstation kernel: ath: Regpair used: 0x52
Jan 24 16:55:54 workstation kernel: ieee80211 phy1: Atheros AR9271 Rev:1
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.0067] (wlan0): using nl80211 for WiFi device control
Jan 24 16:55:54 workstation kernel: cfg80211: Regulatory domain changed to country: CN
Jan 24 16:55:54 workstation kernel: cfg80211:  DFS Master region: FCC
Jan 24 16:55:54 workstation kernel: cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 24 16:55:54 workstation kernel: cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 24 16:55:54 workstation kernel: cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (N/A)
Jan 24 16:55:54 workstation kernel: cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
Jan 24 16:55:54 workstation kernel: cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Jan 24 16:55:54 workstation kernel: cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jan 24 16:55:54 workstation kernel: cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jan 24 16:55:54 workstation kernel: cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.0069] device (wlan0): driver supports Access Point (AP) mode
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.0086] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/7)
Jan 24 16:55:54 workstation systemd[1]: Starting Load/Save RF Kill Switch Status...
Jan 24 16:55:54 workstation kernel: ath9k_htc 8-2:1.0 wlxec086b1ef0b3: renamed from wlan0
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.0887] rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/ieee80211/phy1/rfkill1) (driver ath9k_htc)
Jan 24 16:55:54 workstation systemd[1]: Started Load/Save RF Kill Switch Status.
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.1030] device (wlan0): interface index 8 renamed iface from 'wlan0' to 'wlxec086b1ef0b3'
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.1138] devices added (path: /sys/devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/net/wlxec086b1ef0b3, iface: wlxec086b1ef0b3)
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.1139] device added (path: /sys/devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/net/wlxec086b1ef0b3, iface: wlxec086b1ef0b3): no ifupdown configuration found.
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.1148] device (wlxec086b1ef0b3): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 24 16:55:54 workstation kernel: IPv6: ADDRCONF(NETDEV_UP): wlxec086b1ef0b3: link is not ready
Jan 24 16:55:54 workstation kernel: IPv6: ADDRCONF(NETDEV_UP): wlxec086b1ef0b3: link is not ready
Jan 24 16:55:54 workstation wpa_supplicant[1364]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jan 24 16:55:54 workstation wpa_supplicant[1364]: dbus: Failed to construct signal
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.2934] device (wlxec086b1ef0b3): supplicant interface state: starting -> ready
Jan 24 16:55:54 workstation NetworkManager[1242]: <info>  [1485294954.2935] device (wlxec086b1ef0b3): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 24 16:55:54 workstation kernel: IPv6: ADDRCONF(NETDEV_UP): wlxec086b1ef0b3: link is not ready
Jan 24 16:55:55 workstation NetworkManager[1242]: <info>  [1485294955.3406] device (wlxec086b1ef0b3): supplicant interface state: ready -> inactive
Jan 24 16:55:56 workstation ModemManager[1163]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:10.1/usb8/8-2': not supported by any plugin
Jan 24 16:55:57 workstation colord-sane[22906]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0743] policy: auto-activating connection 'Primus-2532'
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0756] device (wlxec086b1ef0b3): Activation: starting connection 'Primus-2532' (43731ea2-d06e-47d1-a3d4-dee258a2e742)
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0760] device (wlxec086b1ef0b3): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0762] manager: NetworkManager state is now CONNECTING
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0769] device (wlxec086b1ef0b3): state change: prepare -> config (reason 'none') [40 50 0]
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0772] device (wlxec086b1ef0b3): Activation: (wifi) access point 'Primus-2532' has security, but secrets are required.
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0782] device (wlxec086b1ef0b3): state change: config -> need-auth (reason 'none') [50 60 0]
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0826] device (wlxec086b1ef0b3): state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0836] device (wlxec086b1ef0b3): state change: prepare -> config (reason 'none') [40 50 0]
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0841] device (wlxec086b1ef0b3): Activation: (wifi) connection 'Primus-2532' has security, and secrets exist.  No new secrets needed.
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0846] Config: added 'ssid' value 'Primus-2532'
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0848] Config: added 'scan_ssid' value '1'
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0850] Config: added 'key_mgmt' value 'WPA-PSK'
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0850] Config: added 'auth_alg' value 'OPEN'
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0850] Config: added 'psk' value '<omitted>'
Jan 24 16:55:59 workstation NetworkManager[1242]: <info>  [1485294959.0887] sup-iface[0x2527400,wlxec086b1ef0b3]: config: set interface ap_scan to 1
Jan 24 16:55:59 workstation wpa_supplicant[1364]: wlxec086b1ef0b3: SME: Trying to authenticate with 00:23:6a:78:25:34 (SSID='Primus-2532' freq=2437 MHz)
```

---

