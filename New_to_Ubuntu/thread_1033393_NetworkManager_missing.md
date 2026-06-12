---
title: "NetworkManager missing"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by steve.klebanoff on 2009-01-07
Hi,

I installed Ibex on this machine yesterday.  It was working great.  I edited /etc/network/interfaces to give myself a static ip.  It worked fine.  

Today I booted up the computer and the network manager is missing.  I have removed and re-added the Notifications area.  I can run it from the terminal and it seems to run but I can't see it anywhere.  I also can't connect to the internet anymore.

There's some confusing stuff in my syslog from today.  Anyone have any idea?  Thank you!
```

Here's the syslog:
Jan  6 13:08:45 steve-laptop NetworkManager: <debug> [1231265325.457790] periodic_update(): Roamed from BSSID 00:1E:E5:4E:DC:11 (teamvisor) to (none) ((none)) 
Jan  6 13:08:51 steve-laptop NetworkManager: <debug> [1231265331.461140] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:E5:4E:DC:11 (teamvisor) 
Jan  6 13:12:45 steve-laptop NetworkManager: <debug> [1231265565.601770] periodic_update(): Roamed from BSSID 00:1E:E5:4E:DC:11 (teamvisor) to (none) ((none)) 
Jan  6 13:12:51 steve-laptop NetworkManager: <debug> [1231265571.604942] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:E5:4E:DC:11 (teamvisor) 
Jan  6 13:14:45 steve-laptop NetworkManager: <debug> [1231265685.684902] periodic_update(): Roamed from BSSID 00:1E:E5:4E:DC:11 (teamvisor) to (none) ((none)) 
Jan  6 13:14:51 steve-laptop NetworkManager: <debug> [1231265691.684978] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:E5:4E:DC:11 (teamvisor) 
Jan  6 13:21:58 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 13:21:58 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 13:21:58 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 13:21:58 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 14:20:57 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 14:20:57 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 14:20:57 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 14:20:57 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 14:20:57 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 14:20:57 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 15:20:11 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 15:20:11 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 15:36:42 steve-laptop NetworkManager: <info>  (eth1): device state change: 8 -> 2 
Jan  6 15:36:42 steve-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Jan  6 15:36:42 steve-laptop NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 9930 
Jan  6 15:36:42 steve-laptop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jan  6 15:36:42 steve-laptop NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Jan  6 15:36:42 steve-laptop NetworkManager: <info>  (eth1): taking down device. 
Jan  6 15:36:44 steve-laptop NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): bringing up device. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto teamvisor' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 

Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'Auto teamvisor' has security, but secrets are required. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 6 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): device state change: 6 -> 4 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto teamvisor' has security, and secrets exist.  No new secrets needed. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'ssid' value 'teamvisor' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Jan  6 15:36:44 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jan  6 15:36:49 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'teamvisor'. 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  dhclient started with pid 27469 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan  6 15:36:50 steve-laptop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    address 192.168.0.44 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    gateway 192.168.0.1 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    nameserver '192.168.0.103' 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    nameserver '216.254.95.2' 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    nameserver '216.231.41.2' 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>    domain name 'laptop.net' 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jan  6 15:37:03 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jan  6 15:37:04 steve-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jan  6 15:37:04 steve-laptop NetworkManager: <info>  Policy set 'Auto teamvisor' (eth1) as default for routing and DNS. 
Jan  6 15:37:04 steve-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jan  6 15:37:04 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  6 15:37:47 steve-laptop NetworkManager: <info>  (eth1): device state change: 8 -> 2 
Jan  6 15:37:47 steve-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Jan  6 15:37:47 steve-laptop NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 27469 
Jan  6 15:37:47 steve-laptop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jan  6 15:37:47 steve-laptop NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Jan  6 15:37:47 steve-laptop NetworkManager: <info>  (eth1): taking down device. 
Jan  6 15:37:49 steve-laptop NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): bringing up device. 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto teamvisor' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto teamvisor' has security, and secrets exist.  No new secrets needed. 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'ssid' value 'teamvisor' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Jan  6 15:37:49 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'teamvisor'. 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  dhclient started with pid 27637 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan  6 15:37:54 steve-laptop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    address 192.168.0.44 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    gateway 192.168.0.1 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    nameserver '192.168.0.103' 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    nameserver '216.254.95.2' 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    nameserver '216.231.41.2' 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>    domain name 'laptop.net' 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jan  6 15:37:58 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jan  6 15:37:59 steve-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jan  6 15:37:59 steve-laptop NetworkManager: <info>  Policy set 'Auto teamvisor' (eth1) as default for routing and DNS. 
Jan  6 15:37:59 steve-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jan  6 15:37:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  6 15:38:55 steve-laptop NetworkManager: <info>  (eth1): device state change: 8 -> 2 
Jan  6 15:38:55 steve-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 0). 
Jan  6 15:38:55 steve-laptop NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 27637 
Jan  6 15:38:55 steve-laptop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jan  6 15:38:55 steve-laptop NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Jan  6 15:38:55 steve-laptop NetworkManager: <info>  (eth1): taking down device. 
Jan  6 15:38:59 steve-laptop NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): bringing up device. 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) starting connection 'Auto teamvisor' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto teamvisor' has security, and secrets exist.  No new secrets needed. 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'ssid' value 'teamvisor' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Jan  6 15:38:59 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'teamvisor'. 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  dhclient started with pid 27827 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan  6 15:39:04 steve-laptop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    address 192.168.0.44 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    gateway 192.168.0.1 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    nameserver '192.168.0.103' 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    nameserver '216.254.95.2' 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    nameserver '216.231.41.2' 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>    domain name 'laptop.net' 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jan  6 15:39:05 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jan  6 15:39:06 steve-laptop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Jan  6 15:39:06 steve-laptop NetworkManager: <info>  Policy set 'Auto teamvisor' (eth1) as default for routing and DNS. 
Jan  6 15:39:06 steve-laptop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jan  6 15:39:06 steve-laptop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jan  6 16:18:41 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 16:18:41 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 16:41:59 steve-laptop NetworkManager: <debug> [1231278119.414271] periodic_update(): Roamed from BSSID 00:1E:E5:4E:DC:11 (teamvisor) to (none) ((none)) 
Jan  6 16:42:05 steve-laptop NetworkManager: <debug> [1231278125.417755] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:E5:4E:DC:11 (teamvisor) 
Jan  6 16:43:59 steve-laptop NetworkManager: <debug> [1231278239.506005] periodic_update(): Roamed from BSSID 00:1E:E5:4E:DC:11 (teamvisor) to (none) ((none)) 
Jan  6 16:44:05 steve-laptop NetworkManager: <debug> [1231278245.509985] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:E5:4E:DC:11 (teamvisor) 
Jan  6 16:45:59 steve-laptop NetworkManager: <debug> [1231278359.584867] periodic_update(): Roamed from BSSID 00:1E:E5:4E:DC:11 (teamvisor) to (none) ((none)) 
Jan  6 16:46:05 steve-laptop NetworkManager: <debug> [1231278365.584937] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1E:E5:4E:DC:11 (teamvisor) 
Jan  6 17:17:22 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 17:17:22 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 17:17:22 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 6 
Jan  6 17:17:22 steve-laptop NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Jan  6 17:21:32 steve-laptop NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Jan  6 17:21:32 steve-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 38). 
Jan  6 17:21:32 steve-laptop NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 27827 
Jan  6 17:21:32 steve-laptop NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jan  6 17:21:33 steve-laptop NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  starting... 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  eth0: driver is 'r8169'. 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_21_70_d3_f7_ee 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  eth1: driver is 'wl'. 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_23_4e_9f_e2_73 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  Trying to start the supplicant... 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  (eth1): supplicant manager is now in state 1 (from 0). 
Jan  7 09:02:08 steve-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:02:08 steve-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:02:08 steve-laptop NetworkManager: <info>  (eth1): now unmanaged 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): bringing up device. 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): preparing device. 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Jan  7 09:02:12 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:02:12 steve-laptop NetworkManager: <WARN>  auto_activate_device(): Connection 'Ifupdown (eth1)' auto-activation failed: (2) Device not managed by NetworkManager 
Jan  7 09:02:48 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:03:54 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  starting... 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  eth0: driver is 'r8169'. 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_21_70_d3_f7_ee 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  eth1: driver is 'wl'. 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_23_4e_9f_e2_73 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  Trying to start the supplicant... 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  (eth1): supplicant manager is now in state 1 (from 0). 
Jan  7 09:06:31 steve-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:06:31 steve-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:06:31 steve-laptop NetworkManager: <info>  (eth1): now unmanaged 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): bringing up device. 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): preparing device. 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Jan  7 09:06:35 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:06:35 steve-laptop NetworkManager: <WARN>  auto_activate_device(): Connection 'Ifupdown (eth1)' auto-activation failed: (2) Device not managed by NetworkManager 
Jan  7 09:06:59 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:09:37 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  starting... 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  eth0: driver is 'r8169'. 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_21_70_d3_f7_ee 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  eth1: driver is 'wl'. 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_23_4e_9f_e2_73 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  Trying to start the supplicant... 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  (eth1): supplicant manager is now in state 1 (from 0). 
Jan  7 09:18:46 steve-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:18:46 steve-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:18:46 steve-laptop NetworkManager: <info>  (eth1): now unmanaged 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): bringing up device. 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): preparing device. 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Jan  7 09:18:50 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:18:50 steve-laptop NetworkManager: <WARN>  auto_activate_device(): Connection 'Ifupdown (eth1)' auto-activation failed: (2) Device not managed by NetworkManager 
Jan  7 09:19:14 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:20:40 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:25:13 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:25:53 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:26:51 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:29:38 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:29:44 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:32:11 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  starting... 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  eth0: driver is 'r8169'. 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_21_70_d3_f7_ee 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  eth1: driver is 'wl'. 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'eth1'. 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_00_23_4e_9f_e2_73 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  Trying to start the supplicant... 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  (eth1): supplicant manager is now in state 1 (from 0). 
Jan  7 09:47:03 steve-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:47:03 steve-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  7 09:47:03 steve-laptop NetworkManager: <info>  (eth1): now unmanaged 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): bringing up device. 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): preparing device. 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Jan  7 09:47:07 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:47:07 steve-laptop NetworkManager: <WARN>  auto_activate_device(): Connection 'Ifupdown (eth1)' auto-activation failed: (2) Device not managed by NetworkManager 
Jan  7 09:47:30 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:48:19 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:51:03 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:54:35 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:55:19 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:55:54 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:56:32 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:57:46 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 09:58:20 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  7 10:01:19 steve-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

```

---

### Post by superprash2003 on 2009-01-07
what about System->preferences->network configuration ??

---

### Post by theozzlives on 2009-01-07
You have to GET a static IP from your ISP... you can't just ""give:  yourself one.

---

### Post by alphaniner on 2009-01-07
theozzlives has a point.  Is the machine connected to a router, local DHCP server, firewall, etc?  Or directly to a cable modem or suchness?  In my case, I have a router but I disabled its DHCP service, so I have to assign static IPs.  Find out, then dump Network Mangler for good and stick with the scripts.

And speaking of scripts, if you really are in a position to use static IP, you need an /etc/resolv.conf file to hold your DNS information.

---

### Post by steve.klebanoff on 2009-01-07
This is my work machine, and I have been assigned a specific static ip by them.  

After a reverting my /etc/network/interfaces file to the original default and many, many restarts for some reason the network manager is appearing again.  I haven't messed with a static ip again for fear of it disappearing. 

Will look into this more when I have time later today

---

### Post by Big_astur on 2009-01-07
To use an static IP i suggest you to use WICD.

There are many posts about it but i already posted how to install it here:
[http://ubuntuforums.org/showpost.php?p=6461541&postcount=3](http://ubuntuforums.org/showpost.php?p=6461541&postcount=3)

I did it an no problems so far. You might search the forums or google for more info about wicd and ubuntu 8.10 anyways.

---

### Post by steve.klebanoff on 2009-01-07
> **Big_astur said:**
> To use an static IP i suggest you to use WICD.

There are many posts about it but i already posted how to install it here:
[http://ubuntuforums.org/showpost.php?p=6461541&postcount=3](http://ubuntuforums.org/showpost.php?p=6461541&postcount=3)

I did it an no problems so far. You might search the forums or google for more info about wicd and ubuntu 8.10 anyways.

I installed wicd and now it works flawlessly.  So much better than gnome network manager.  Thank you!

---

### Post by superprash2003 on 2009-01-08
please mark this thread as SOLVED

---

### Post by hyper_ch on 2009-01-08
bigastur: better to add the wicd repo than just downloading and installing the .deb

---

### Post by Big_astur on 2009-01-19
> **hyper_ch said:**
> bigastur: better to add the wicd repo than just downloading and installing the .deb
Thanks for the info.

---

