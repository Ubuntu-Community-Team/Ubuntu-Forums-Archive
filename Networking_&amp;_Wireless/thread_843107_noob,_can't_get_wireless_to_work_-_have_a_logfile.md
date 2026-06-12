---
title: "noob, can't get wireless to work - have a logfile"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by paulcg on 2008-06-28
found a msg last night about possible cause - update libssl..... did the updates, found that file included, still no joy...
here is a log of tonight's attempts

Jun 27 23:08:27 paulcg-laptop hcid[5199]: Default passkey agent (:1.19, /org/bluez/passkey) registered
Jun 27 23:08:27 paulcg-laptop hcid[5199]: Default authorization agent (:1.19, /org/bluez/auth) registered
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Jun 27 23:08:38 paulcg-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Will activate connection 'eth1/linksys'. 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1) started... 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 27 23:08:38 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'linksys' is unencrypted, no key needed. 
Jun 27 23:08:40 paulcg-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Jun 27 23:08:40 paulcg-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=2) 
Jun 27 23:08:41 paulcg-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=3) 
Jun 27 23:08:41 paulcg-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=4) 
Jun 27 23:08:41 paulcg-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=5) 
Jun 27 23:08:41 paulcg-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 27 23:08:42 paulcg-laptop kernel: [   36.891075] NET: Registered protocol family 17
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: response was '0' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b737973' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  Supplicant state changed: 1 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys'. 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jun 27 23:08:42 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jun 27 23:08:42 paulcg-laptop kernel: [   37.181338] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 27 23:08:43 paulcg-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jun 27 23:08:43 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jun 27 23:08:43 paulcg-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jun 27 23:08:43 paulcg-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 27 23:08:43 paulcg-laptop avahi-daemon[4863]: Registering new address record for fe80::213:ceff:fe65:da15 on eth1.*.
Jun 27 23:08:46 paulcg-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jun 27 23:08:50 paulcg-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun 27 23:08:52 paulcg-laptop kernel: [   80.563968] eth1: no IPv6 routers present
Jun 27 23:08:54 paulcg-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Jun 27 23:09:04 paulcg-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
Jun 27 23:09:21 paulcg-laptop dhclient: No DHCPOFFERS received.
Jun 27 23:09:21 paulcg-laptop avahi-autoipd(eth1)[5851]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jun 27 23:09:21 paulcg-laptop avahi-autoipd(eth1)[5851]: Successfully called chroot().
Jun 27 23:09:21 paulcg-laptop avahi-autoipd(eth1)[5851]: Successfully dropped root privileges.
Jun 27 23:09:21 paulcg-laptop avahi-autoipd(eth1)[5851]: Starting with address 169.254.6.176
Jun 27 23:09:26 paulcg-laptop avahi-autoipd(eth1)[5851]: Callout BIND, address 169.254.6.176 on interface eth1
Jun 27 23:09:26 paulcg-laptop avahi-daemon[4863]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.6.176.
Jun 27 23:09:26 paulcg-laptop avahi-daemon[4863]: New relevant interface eth1.IPv4 for mDNS.
Jun 27 23:09:26 paulcg-laptop avahi-daemon[4863]: Registering new address record for 169.254.6.176 on eth1.IPv4.
Jun 27 23:09:30 paulcg-laptop avahi-autoipd(eth1)[5851]: Successfully claimed IP address 169.254.6.176
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface eth1 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Jun 27 23:09:30 paulcg-laptop dhcdbd: Unrequested down ?:3
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface eth1 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed for access point (linksys) 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed. 
Jun 27 23:09:30 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 
Jun 27 23:09:30 paulcg-laptop avahi-daemon[4863]: Withdrawing address record for 169.254.6.176 on eth1.
Jun 27 23:09:30 paulcg-laptop avahi-daemon[4863]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.6.176.
Jun 27 23:09:30 paulcg-laptop avahi-daemon[4863]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun 27 23:09:30 paulcg-laptop avahi-daemon[4863]: Withdrawing address record for fe80::213:ceff:fe65:da15 on eth1.
Jun 27 23:12:00 paulcg-laptop NetworkManager: <debug> [1214622720.777912] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'wme' 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / wme 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1) started... 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 27 23:12:00 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'wme' is encrypted, and a key exists.  No new key needed. 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  kernel_driver for non broadcast check: ipw2200 (has_scan_capa_ssid=1) 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  Using has_buggy_scan_capa fix for ipw2200 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was '0' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 776d65' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:12:02 paulcg-laptop kernel: [   93.463056] ieee80211_crypt: registered algorithm 'WEP'
Jun 27 23:12:02 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 27 23:12:07 paulcg-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 27 23:12:39 paulcg-laptop last message repeated 4 times
Jun 27 23:13:00 paulcg-laptop last message repeated 3 times
Jun 27 23:13:02 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Jun 27 23:13:02 paulcg-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jun 27 23:13:02 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed for access point (wme) 
Jun 27 23:13:02 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed. 
Jun 27 23:13:02 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <debug> [1214622794.340455] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'wme' 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / wme 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) started... 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'wme' is encrypted, but NO valid key exists.  New key needed. 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'wme'. 
Jun 27 23:13:14 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'wme' received. 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 27 23:14:31 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'wme' is encrypted, and a key exists.  No new key needed. 
Jun 27 23:14:32 paulcg-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 27 23:14:32 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was '0' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 776d65' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 27 23:14:33 paulcg-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 27 23:15:10 paulcg-laptop last message repeated 5 times
Jun 27 23:15:31 paulcg-laptop last message repeated 3 times
Jun 27 23:15:33 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Jun 27 23:15:33 paulcg-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jun 27 23:15:33 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed for access point (wme) 
Jun 27 23:15:33 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed. 
Jun 27 23:15:33 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <debug> [1214622985.791293] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'wme' 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / wme 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Device eth1 activation scheduled... 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) started... 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'wme' is encrypted, but NO valid key exists.  New key needed. 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'wme'. 
Jun 27 23:16:25 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 27 23:17:01 paulcg-laptop /USR/SBIN/CRON[6290]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'wme' received. 
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jun 27 23:18:44 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'wme' is encrypted, and a key exists.  No new key needed. 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was '0' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 776d65' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 auth_alg SHARED' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  SUP: response was 'OK' 
Jun 27 23:18:45 paulcg-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jun 27 23:18:50 paulcg-laptop NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Jun 27 23:19:22 paulcg-laptop last message repeated 5 times
Jun 27 23:19:38 paulcg-laptop last message repeated 2 times
Jun 27 23:19:45 paulcg-laptop NetworkManager: <info>  Activation (eth1/wireless): association took too long (>60s), failing activation. 
Jun 27 23:19:45 paulcg-laptop NetworkManager: <info>  Activation (eth1) failure scheduled... 
Jun 27 23:19:45 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed for access point (wme) 
Jun 27 23:19:45 paulcg-laptop NetworkManager: <info>  Activation (eth1) failed. 
Jun 27 23:19:45 paulcg-laptop NetworkManager: <info>  Deactivating device eth1. 

Thanks for any assistance in advance, I can get other logs or info as requested.

---

### Post by paulcg on 2008-06-28
BTW, that first connection attempt to "linksys" is NOT my network, one of my neighbors, to which I can connnect because no security, etc but it's weak.

---

### Post by wyclif on 2008-06-28
I have a T40 with ethernet.  Today I tried to upgrade to Hardy, but now I have no ethernet/wireless. I've tried many of the solutions offered in the "wireless" threads, to no avail.

I understand this is an ndiswrapper problem? How do I solve this?

Thanks in advance!

---

### Post by wyclif on 2008-06-28
I fixed this problem, which had to do with the Aironet driver, by blacklisting some airo driver modules.

I followed the directions here:

[http://ubuntuforums.org/showpost.php?p=4974456&postcount=5](http://ubuntuforums.org/showpost.php?p=4974456&postcount=5)

---

### Post by paulcg on 2008-06-28
I fail to see how your post (basically a hijack to my thread) has anything to do with my problem. I'm glad you solved it. However it had nothing to do with this thread.

---

### Post by paulcg on 2008-06-28
I guess over 50 people are having problems themselves and not one of them can help me. I can post additionsl logs or run commands as needed.

[COLOR="Purple"]:popcorn:[SIZE="5"]:(:([/SIZE][/COLOR]

---

### Post by paulcg on 2008-06-30
ttt

---

### Post by paulcg on 2008-07-04
ttt:confused:

---

