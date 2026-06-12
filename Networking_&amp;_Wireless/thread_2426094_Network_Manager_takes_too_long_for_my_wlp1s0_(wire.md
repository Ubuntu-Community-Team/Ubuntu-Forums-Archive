---
title: "Network Manager takes too long for my wlp1s0 (wireless) interface to attain an IP"
date: 2019-09-04
forum: Networking &amp; Wireless
---

### Post by jy824212 on 2019-09-04
I have an Ubuntu 4.19.46 and I am using Network Manager to manage to connect to the wifi via my wlp1s0 which is a PCIe Wireless Module.

Every time after I reboot it takes very long to fetch the same IP address again and it suppose to have the IP address ready right after all the boot process is done since I connected to the same network previously.

Here is the log:```


Aug 29 20:35:20 byos NetworkManager[423]: <info>  [1567110920.6155] device (eth1): carrier: link connected
Aug 29 20:35:30 byos NetworkManager[423]: <error> [1567110930.2595] sup-iface[0x63f170,wlp1s0]: error adding interface: Timeout was reached
Aug 29 20:35:30 byos NetworkManager[423]: <info>  [1567110930.2597] device (wlp1s0): supplicant interface state: starting -> down
Aug 29 20:35:40 byos NetworkManager[423]: <warn>  [1567110940.4745] device (wlp1s0): re-acquiring supplicant interface (#1).
Aug 29 20:36:05 byos NetworkManager[423]: <error> [1567110965.5045] sup-iface[0x63f1d8,wlp1s0]: error adding interface: Timeout was reached
Aug 29 20:36:05 byos NetworkManager[423]: <info>  [1567110965.5048] device (wlp1s0): supplicant interface state: starting -> down
Aug 29 20:36:15 byos NetworkManager[423]: <warn>  [1567110975.4749] device (wlp1s0): re-acquiring supplicant interface (#2).
Aug 29 20:36:40 byos NetworkManager[423]: <error> [1567111000.5043] sup-iface[0x63f240,wlp1s0]: error adding interface: Timeout was reached
Aug 29 20:36:40 byos NetworkManager[423]: <info>  [1567111000.5045] device (wlp1s0): supplicant interface state: starting -> down
Aug 29 20:36:50 byos NetworkManager[423]: <warn>  [1567111010.4745] device (wlp1s0): re-acquiring supplicant interface (#3).
Aug 29 20:36:51 byos NetworkManager[423]: <info>  [1567111011.2760] device (wlp1s0): supplicant interface state: starting -> ready
Aug 29 20:36:51 byos NetworkManager[423]: <info>  [1567111011.2775] device (wlp1s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8027] policy: auto-activating connection 'MySSID'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8114] device (wlp1s0): Activation: starting connection 'MySSID' (b1272736-4e2a-4661-9db2-7198ed0b5c95)
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8135] device (wlp1s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8181] device (wlp1s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8194] device (wlp1s0): Activation: (wifi) access point 'MySSID' has security, but secrets are required.
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8196] device (wlp1s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8403] device (wlp1s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8433] device (wlp1s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8446] device (wlp1s0): Activation: (wifi) connection 'MySSID' has security, and secrets exist.  No new secrets needed.
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8451] Config: added 'ssid' value 'MySSID'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8452] Config: added 'scan_ssid' value '1'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8453] Config: added 'bgscan' value 'simple:30:-80:86400'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8454] Config: added 'key_mgmt' value 'WPA-PSK'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8455] Config: added 'auth_alg' value 'OPEN'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.8455] Config: added 'psk' value '<hidden>'
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.9528] device (wlp1s0): supplicant interface state: ready -> authenticating
Aug 29 20:36:56 byos NetworkManager[423]: <info>  [1567111016.9646] device (wlp1s0): supplicant interface state: authenticating -> associating
Aug 29 20:36:57 byos NetworkManager[423]: <info>  [1567111017.0149] device (wlp1s0): supplicant interface state: associating -> disconnected
Aug 29 20:36:57 byos NetworkManager[423]: <info>  [1567111017.1190] device (wlp1s0): supplicant interface state: disconnected -> scanning
Aug 29 20:36:57 byos NetworkManager[423]: <info>  [1567111017.9410] device (wlp1s0): supplicant interface state: scanning -> authenticating
Aug 29 20:36:57 byos NetworkManager[423]: <info>  [1567111017.9425] device (wlp1s0): supplicant interface state: authenticating -> associating
Aug 29 20:36:57 byos NetworkManager[423]: <info>  [1567111017.9815] device (wlp1s0): supplicant interface state: associating -> completed
Aug 29 20:36:57 byos NetworkManager[423]: <info>  [1567111017.9817] device (wlp1s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'MySSID'.
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.0601] device (wlp1s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.0649] dhcp4 (wlp1s0): activation: beginning transaction (timeout in 45 seconds)
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.0986] dhcp4 (wlp1s0): dhclient started with pid 1164
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2261] dhcp4 (wlp1s0):   address 10.20.2.187
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2270] dhcp4 (wlp1s0):   plen 22 (255.255.252.0)
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2271] dhcp4 (wlp1s0):   gateway 10.20.0.254
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2273] dhcp4 (wlp1s0):   lease time 432000
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2276] dhcp4 (wlp1s0):   nameserver '8.8.8.8'
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2277] dhcp4 (wlp1s0):   nameserver '8.8.4.4'
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2278] dhcp4 (wlp1s0): state changed unknown -> bound
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2393] device (wlp1s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2445] device (wlp1s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2471] device (wlp1s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2834] policy: set 'MySSID' (wlp1s0) as default for IPv4 routing and DNS
Aug 29 20:36:58 byos NetworkManager[423]: <info>  [1567111018.2872] device (wlp1s0): Activation: successful, device activated.
```

---

