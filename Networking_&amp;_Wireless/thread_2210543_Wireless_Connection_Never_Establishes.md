---
title: "Wireless Connection Never Establishes"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by Kirk Schnable on 2014-03-11
Hello,

I am troubleshooting an issue with a netbook whose wireless connection will never establish.  Here are the relevant excerpts from Syslog.

```
Feb 26 20:42:39 HOSTNAME kernel: [   32.345791] type=1400 audit(1393468959.648:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=674 comm="apparmor_parser"
Feb 26 20:42:40 HOSTNAME NetworkManager[805]: <info> NetworkManager (version 0.9.4.0) is starting...
Feb 26 20:42:40 HOSTNAME NetworkManager[805]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Feb 26 20:42:40 HOSTNAME NetworkManager[805]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Feb 26 20:42:40 HOSTNAME NetworkManager[805]: <info> DNS: loaded plugin dnsmasq
Feb 26 20:42:41 HOSTNAME kernel: [   33.705457] type=1400 audit(1393468961.008:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=853 comm="apparmor_parser"
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: init!
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: update_system_hostname
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPluginIfupdown: management mode: unmanaged
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: end _init.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    Ifupdown: get unmanaged devices count: 0
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: (153405864) ... get_connections.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: (153405864) ... get_connections (managed=false): return empty list.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    keyfile: parsing MCHS ... 
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    keyfile:     read connection 'MCHS'
Feb 26 20:42:41 HOSTNAME NetworkManager[805]:    Ifupdown: get unmanaged devices count: 0
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> modem-manager is now available
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> monitoring kernel firmware directory '/lib/firmware'.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1/rfkill1) (driver (unknown))
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/dell-laptop/rfkill/rfkill2) (driver dell-laptop)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> WiFi enabled by radio killswitch; enabled by state file
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> WWAN enabled by radio killswitch; enabled by state file
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> WiMAX enabled by radio killswitch; enabled by state file
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> Networking is enabled by state file
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): using nl80211 for WiFi device control
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <error> [1393468961.170650] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): now managed
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): bringing up device.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): preparing device.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth1): deactivating device (reason 'managed') [2]
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <warn> failed to allocate link cache: (-10) Operation not supported
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): carrier is OFF
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): now managed
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): bringing up device.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): preparing device.
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> (eth0): deactivating device (reason 'managed') [2]
Feb 26 20:42:41 HOSTNAME NetworkManager[805]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0
Feb 26 20:42:42 HOSTNAME NetworkManager[805]: <info> wpa_supplicant started
Feb 26 20:42:42 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: starting -> ready
Feb 26 20:42:42 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 26 20:42:42 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: ready -> inactive
Feb 26 20:42:42 HOSTNAME NetworkManager[805]: <warn> Trying to remove a non-existant call id.
Feb 26 20:42:42 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1)
Feb 26 20:42:42 HOSTNAME NetworkManager[805]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) starting connection 'Wireless_Guest_Network'
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1/wireless): access point 'Wireless_Guest_Network' has security, but secrets are required.
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 26 20:43:33 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1/wireless): connection 'Wireless_Guest_Network' has security, and secrets exist.  No new secrets needed.
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Config: added 'ssid' value 'Wireless_Guest_Network'
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Config: added 'scan_ssid' value '1'
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Config: added 'psk' value '<omitted>'
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> Config: set interface ap_scan to 1
Feb 26 20:43:57 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: inactive -> scanning
Feb 26 20:44:08 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:08 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:44:08 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:10 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:10 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:44:10 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:13 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:13 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:44:13 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:15 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:15 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:44:15 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:19 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:19 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:44:19 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:21 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:21 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:44:21 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): disconnecting for new activation request.
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: config -> disconnected (reason 'none') [50 30 0]
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): deactivating device (reason 'none') [0]
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) starting connection 'Wireless'
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> disconnected
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1/wireless): access point 'Wireless' has security, but secrets are required.
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1/wireless): connection 'Wireless' has security, and secrets exist.  No new secrets needed.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'ssid' value 'Wireless'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'scan_ssid' value '1'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'psk' value '<omitted>'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: set interface ap_scan to 1
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:37 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:57 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> scanning
Feb 26 20:45:01 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:45:11 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> scanning
Feb 26 20:45:13 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:45:23 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> scanning
Feb 26 20:45:26 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <warn> Activation (eth1/wireless): association took too long.
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <warn> Activation (eth1/wireless): asking for new secrets
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> disconnected
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1/wireless): connection 'Wireless' has security, and secrets exist.  No new secrets needed.
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Config: added 'ssid' value 'Wireless'
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Config: added 'scan_ssid' value '1'
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Config: added 'psk' value '<omitted>'
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> Config: set interface ap_scan to 1
Feb 26 20:45:44 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
```

I'm particularly concerned about the SSID called "Wireless", as this is the one that is not working.  I am told the correct encryption key was entered.

This is the particularly useful excerpt:
[quote="syslog"]Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation  (eth1/wireless): access point 'Wireless' has security, but secrets are  required.
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info>  (eth1): device state change: config -> need-auth (reason 'none') [50  60 0]
Feb 26 20:44:23 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb  26 20:44:35 HOSTNAME NetworkManager[805]: <info> (eth1): device  state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb  26 20:44:35 HOSTNAME NetworkManager[805]: <info> (eth1): device  state change: prepare -> config (reason 'none') [40 50 0]
Feb 26  20:44:35 HOSTNAME NetworkManager[805]: <info> Activation  (eth1/wireless): connection 'Wireless' has security, and secrets exist.   No new secrets needed.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'ssid' value 'Wireless'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'scan_ssid' value '1'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: added 'psk' value '<omitted>'
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> Config: set interface ap_scan to 1
Feb 26 20:44:35 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 26 20:44:37 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:44:57 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> scanning
Feb 26 20:45:01 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:45:11 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> scanning
Feb 26 20:45:13 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:45:23 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: associating -> scanning
Feb 26 20:45:26 HOSTNAME NetworkManager[805]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <warn> Activation (eth1/wireless): association took too long.
Feb  26 20:45:36 HOSTNAME NetworkManager[805]: <info> (eth1): device  state change: config -> need-auth (reason 'none') [50 60 0]
Feb 26 20:45:36 HOSTNAME NetworkManager[805]: <warn> Activation (eth1/wireless): asking for new secrets[/quote]

What exactly is going on here?

---

### Post by Hadaka on 2014-03-11
Hi Kirk, let's take a look at your com cards
to verify your drivers and the like. Please do.
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
post the output..thanks.

---

### Post by Kirk Schnable on 2014-03-18
Hello, apologies for the delay on this.

> **Hadaka said:**
> Hi Kirk, let's take a look at your com cards
to verify your drivers and the like. Please do.
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
post the output..thanks.

```
# lspci -nnk | grep -iA3 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57760 Gigabit Ethernet PCIe [14e4:1690] (rev 01)
    Subsystem: Dell Device [1028:04a5]
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Dell Device [1028:0014]
    Kernel driver in use: wl
    Kernel modules: wl
```

```
# lsmod
Module                  Size  Used by
nf_conntrack_ipv4      19084  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  1 
nf_conntrack           73847  2 nf_conntrack_ipv4,xt_state
xt_tcpudp              12531  2 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  4 xt_state,xt_tcpudp,iptable_filter,ip_tables
promethean             47575  0 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_realtek   174313  1 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
rts_pstor             353252  0 
i915                  428282  2 
lib80211_crypt_tkip    17240  0 
mac_hid                13077  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2906597  0 
drm_kms_helper         45466  1 i915
wmi                    18744  1 dell_wmi
snd                    62218  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197641  3 i915,drm_kms_helper
cfg80211              178877  1 wl
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
lib80211               14040  2 lib80211_crypt_tkip,wl
video                  19115  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
psmouse                96744  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
```

```
# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by Hadaka on 2014-03-18
Hi, let's try a different driver...please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo modprobe -r wl
```
then do,,
```
sudo modprobe -v brcmsmac
```
boot and report back please
thanks.

---

