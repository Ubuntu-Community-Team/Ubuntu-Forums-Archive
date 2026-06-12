---
title: "no vpn item in network-manager-vpnc"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by tnk2k on 2008-09-08
Dear all,

I'm trying to get VPNC to work with the Network Manager applet, however i can't seem to get the VPN tab in the network-manager

I installed vpnc & network-manager-vpnc

Does anybody have an idea?

```


NetworkManager: <info>  starting...
NetworkManager: <info>  New VPN service 'vpnc' (org.freedesktop.NetworkManager.vpnc).
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch
NetworkManager: <info>  eth1: Device is fully-supported using driver 'ipw3945'.
NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00).
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'.
NetworkManager: <info>  Deactivating device eth1.
NetworkManager: <info>  eth0: Device is fully-supported using driver 'tg3'.
NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start
NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.
NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'.
NetworkManager: <info>  Deactivating device eth0.
NetworkManager: <info>  Updating allowed wireless network lists.
NetworkManager: <info>  Wireless now enabled by radio killswitch
NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'.
NetworkManager: <info>  Will activate connection 'eth1/xxxxxxxxxxx'.
NetworkManager: <info>  Device eth1 activation scheduled...
NetworkManager: <info>  Activation (eth1) started...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  Activation (eth1/wireless): access point 'xxxxxxxxx' is encrypted, but NO valid key exists.  New key needed.
NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'xxxxxxxxxxxxxxx'.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth1) New wireless user key for network 'xxxxxxxxxxxxxxx' received.
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  Activation (eth1/wireless): access point 'xxxxxxx' is encrypted, and a key exists.  No new key needed.
NetworkManager: <info>  retry to connect to global supplicant socket (try=1)
NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1		wext	/var/run/wpa_supplicant0	'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
NetworkManager: <info>  SUP: response was '0'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <info>  SUP: response was 'OK'
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <debug> [1220868751.117417] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx on wireless network 'xxxxxxxxxx'
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
NetworkManager: <info>  Supplicant state changed: 0
Trying to associate with xxxxxxxxxxxx (SSID='xxxxxxxxxx' freq=2437 MHz)
Associated with xxxxxxxxxxxxxxxxxxxxxx
WPA: Key negotiation completed with xxxxxxxxxxxxxxx [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to xxxxxxxxxxxxxxxxx completed (auth) [id=0 id_str=]
NetworkManager: <info>  Supplicant state changed: 1
NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'xxxxxxxxxxxxxxxxxxx'.
NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction.
NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1
NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1
NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1
NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started...
NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon:
NetworkManager: <info>    address 192.168.42.190
NetworkManager: <info>    netmask 255.255.255.0
NetworkManager: <info>    broadcast 192.168.42.255
NetworkManager: <info>    gateway 192.168.42.1
NetworkManager: <info>    nameserver xxx
NetworkManager: <info>    nameserver xxx
NetworkManager: <info>    hostname 'xxxxxxxxxxxxxxxxxx'
NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete.
NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
NetworkManager: <info>  Clearing nscd hosts cache.
NetworkManager: <info>  Activation (eth1) Finish handler scheduled.
NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
NetworkManager: <info>  Activation (eth1) successful, device activated.

```

---

### Post by tnk2k on 2008-09-08
right, i had to left click the icon not right click.

thnx

---

