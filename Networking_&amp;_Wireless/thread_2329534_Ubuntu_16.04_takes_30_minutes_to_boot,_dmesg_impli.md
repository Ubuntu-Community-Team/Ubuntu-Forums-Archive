---
title: "Ubuntu 16.04 takes 30 minutes to boot, dmesg implies wifi is issue"
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by msbarton1958 on 2016-07-02
I'm an ubuntu newbie. I have installed it on a dell D630 laptop, and on an HP Pavilion 23 all-in-one.

```
sudo lsb_release -a output:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial
```



The Dell laptop installation went fine, except I had to hunt for drivers for the wifi card (Dell 1390). Once those were found, it worked perfect.

Using the same media to install on the HP All-in-One, the wireless card was found and drivers installed, but when rebooting, it takes 30 minutes for the logon screen to be available. Looking at dmesg, I see the following:


```
[   12.987605] ath9k 0000:04:00.0 wlp4s0: renamed from wlan0
[   13.104037] cfg80211: World regulatory domain updated:
[   13.104052] cfg80211:  DFS Master region: unset
[   13.104056] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.104062] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.104067] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.104070] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   13.104074] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   13.104079] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   13.104083] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   13.104086] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   13.104089] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   13.173068] Adding 3756028k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:3756028k SSFS
[   14.505623] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   14.547107] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   14.566904] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   14.754775] r8169 0000:03:00.0 eno1: link down
[   14.754961] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   14.982207] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   16.891872] random: nonblocking pool is initialized
[ 1933.400144] wlp4s0: authenticate with f8:18:97:7a:e6:3e
[ 1933.445016] wlp4s0: send auth to f8:18:97:7a:e6:3e (try 1/3)
[ 1933.453722] wlp4s0: authenticated
[ 1933.460609] wlp4s0: associate with f8:18:97:7a:e6:3e (try 1/3)
[ 1933.464661] wlp4s0: RX AssocResp from f8:18:97:7a:e6:3e (capab=0x411 status=0 aid=9)
[ 1933.464838] wlp4s0: associated
[ 1933.464865] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
[ 1933.759674] ath: EEPROM regdomain: 0x8348
[ 1933.759685] ath: EEPROM indicates we should expect a country code
[ 1933.759689] ath: doing EEPROM country->regdmn map search
[ 1933.759691] ath: country maps to regdmn code: 0x3a
[ 1933.759694] ath: Country alpha2 being used: US
[ 1933.759697] ath: Regpair used: 0x3a
[ 1933.759700] ath: regdomain 0x8348 dynamically updated by country IE
[ 1933.759801] cfg80211: Regulatory domain changed to country: US
[ 1933.759804] cfg80211:  DFS Master region: FCC
[ 1933.759808] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 1933.759813] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[ 1933.759817] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[ 1933.759822] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[ 1933.759825] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[ 1933.759829] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[ 1933.759832] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
```


Here is an excerpt from /var/log/system:  

```
Jul  2 12:11:57 angel-23-b364 systemd[1]: Starting Stop ureadahead data collection...
Jul  2 12:11:57 angel-23-b364 systemd[1]: Stopped Read required files in advance.
Jul  2 12:11:57 angel-23-b364 systemd[1]: Started Stop ureadahead data collection.
Jul  2 12:17:01 angel-23-b364 CRON[1153]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 12:26:17 angel-23-b364 systemd[1]: Starting Cleanup of Temporary Directories...
Jul  2 12:26:17 angel-23-b364 systemd-tmpfiles[1170]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jul  2 12:26:17 angel-23-b364 systemd[1]: Started Cleanup of Temporary Directories.
Jul  2 12:43:09 angel-23-b364 org.gtk.vfs.Daemon[970]: A connection to the bus can't be made
Jul  2 12:43:09 angel-23-b364 systemd[1]: Created slice User Slice of angel.
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7306] policy: auto-activating connection 'TEAROSE 1'
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7391] device (wlp4s0): Activation: starting connection 'TEAROSE 1' (4a2dacd8-a771-4f83-9d69-a0df2fb65fe1)
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7406] device (wlp4s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7457] manager: NetworkManager state is now CONNECTING
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7485] device (wlp4s0): state change: prepare -> config (reason 'none') [40 50 0]
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7550] device (wlp4s0): Activation: (wifi) access point 'TEAROSE 1' has security, but secrets are required.
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7661] device (wlp4s0): state change: config -> need-auth (reason 'none') [50 60 0]
Jul  2 12:43:09 angel-23-b364 whoopsie[744]: [12:43:09] offline
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7955] device (wlp4s0): state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7967] device (wlp4s0): state change: prepare -> config (reason 'none') [40 50 0]
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7  991] device (wlp4s0): Activation: (wifi) connection 'TEAROSE 1' has security, and secrets exist.  No new secrets needed.
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7993] Config: added 'ssid' value 'TEAROSE'
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7993] Config: added 'scan_ssid' value '1'
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7994] Config: added 'key_mgmt' value 'WPA-PSK'
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7994] Config: added 'auth_alg' value 'OPEN'
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.7995] Config: added 'psk' value '<omitted>'
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.8011] sup-iface[0x215efa0,wlp4s0]: config: set interface ap_scan to 1
Jul  2 12:43:09 angel-23-b364 systemd[1]: Starting User Manager for UID 1000...
Jul  2 12:43:09 angel-23-b364 systemd[1]: Started Session c2 of user angel.
Jul  2 12:43:09 angel-23-b364 NetworkManager[786]: <info>  [1467488589.8678] device (wlp4s0): supplicant interface state: inactive -> scanning
Jul  2 12:43:09 angel-23-b364 systemd[1214]: Reached target Timers.
Jul  2 12:43:09 angel-23-b364 systemd[1214]: Reached target Sockets.
Jul  2 12:43:09 angel-23-b364 systemd[1214]: Reached target Paths.
Jul  2 12:43:09 angel-23-b364 systemd[1214]: Reached target Basic System.
Jul  2 12:43:09 angel-23-b364 systemd[1214]: Reached target Default.
Jul  2 12:43:09 angel-23-b364 systemd[1214]: Startup finished in 83ms.
Jul  2 12:43:09 angel-23-b364 systemd[1]: Started User Manager for UID 1000.
Jul  2 12:43:10 angel-23-b364 wpa_supplicant[946]: wlp4s0: SME: Trying to authenticate with f8:18:97:7a:e6:3e (SSID='TEAROSE' freq=2452 MHz)
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.400144] wlp4s0: authenticate with f8:18:97:7a:e6:3e
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.445016] wlp4s0: send auth to f8:18:97:7a:e6:3e (try 1/3)
Jul  2 12:43:10 angel-23-b364 NetworkManager[786]: <info>  [1467488590.8770] device (wlp4s0): supplicant interface state: scanning -> authenticating
Jul  2 12:43:10 angel-23-b364 wpa_supplicant[946]: wlp4s0: Trying to associate with f8:18:97:7a:e6:3e (SSID='TEAROSE' freq=2452 MHz)
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.453722] wlp4s0: authenticated
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.460609] wlp4s0: associate with f8:18:97:7a:e6:3e (try 1/3)
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.464661] wlp4s0: RX AssocResp from f8:18:97:7a:e6:3e (capab=0x411 status=0 aid=9)
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.464838] wlp4s0: associated
Jul  2 12:43:10 angel-23-b364 kernel: [ 1933.464865] IPv6: ADDRCONF(NETDEV_CHANGE): wlp4s0: link becomes ready
Jul  2 12:43:10 angel-23-b364 wpa_supplicant[946]: wlp4s0: Associated with f8:18:97:7a:e6:3e
Jul  2 12:43:10 angel-23-b364 NetworkManager[786]: <info>  [1467488590.8997] device (wlp4s0): supplicant interface state: authenticating -> associating
Jul  2 12:43:10 angel-23-b364 NetworkManager[786]: <info>  [1467488590.8999] device (wlp4s0): supplicant interface state: associating -> associated
Jul  2 12:43:10 angel-23-b364 NetworkManager[786]: <info>  [1467488590.9128] device (wlp4s0): supplicant interface state: associated -> 4-way handshake
Jul  2 12:43:11 angel-23-b364 org.ayatana.bamf[1314]: bamfdaemon start/running, process 1385
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759674] ath: EEPROM regdomain: 0x8348
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759685] ath: EEPROM indicates we should expect a country code
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759689] ath: doing EEPROM country->regdmn map search
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759691] ath: country maps to regdmn code: 0x3a
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759694] ath: Country alpha2 being used: US
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759697] ath: Regpair used: 0x3a
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759700] ath: regdomain 0x8348 dynamically updated by country IE
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759801] cfg80211: Regulatory domain changed to country: US
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759804] cfg80211:  DFS Master region: FCC
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759808] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759813] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759817] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759822] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759825] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759829] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Jul  2 12:43:11 angel-23-b364 kernel: [ 1933.759832] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul  2 12:43:11 angel-23-b364 wpa_supplicant[946]: wlp4s0: WPA: Key negotiation completed with f8:18:97:7a:e6:3e [PTK=CCMP GTK=TKIP]
Jul  2 12:43:11 angel-23-b364 wpa_supplicant[946]: wlp4s0: CTRL-EVENT-CONNECTED - Connection to f8:18:97:7a:e6:3e completed [id=0 id_str=]
Jul  2 12:43:11 angel-23-b364 wpa_supplicant[946]: wlp4s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=US
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.2030] device (wlp4s0): supplicant interface state: 4-way handshake -> completed
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.2031] device (wlp4s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TEAROSE'.
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.2033] device (wlp4s0): state change: config -> ip-config (reason 'none') [50 70 0]
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.2110] dhcp4 (wlp4s0): activation: beginning transaction (timeout in 45 seconds)
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.2184] dhcp4 (wlp4s0): dhclient started with pid 1424
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <warn>  [1467488591.2264] platform-linux: support: kernel-extended-ifa-flags: unable to detect kernel support for handling IPv6 temporary addresses. Assume support
Jul  2 12:43:11 angel-23-b364 dhclient[1424]: DHCPREQUEST of 192.168.1.81 on wlp4s0 to 255.255.255.255 port 67 (xid=0x51687916)
Jul  2 12:43:11 angel-23-b364 dhclient[1424]: DHCPACK of 192.168.1.81 from 192.168.1.254
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4006]   address 192.168.1.81
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4007]   plen 24 (255.255.255.0)
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4007]   gateway 192.168.1.254
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4007]   server identifier 192.168.1.254
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4008]   lease time 86400
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4008]   nameserver '192.168.1.254'
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4008]   domain name 'attlocal.net'
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4009] dhcp4 (wlp4s0): state changed unknown -> bound
Jul  2 12:43:11 angel-23-b364 avahi-daemon[793]: Joining mDNS multicast group on interface wlp4s0.IPv4 with address 192.168.1.81.
Jul  2 12:43:11 angel-23-b364 avahi-daemon[793]: New relevant interface wlp4s0.IPv4 for mDNS.
Jul  2 12:43:11 angel-23-b364 avahi-daemon[793]: Registering new address record for 192.168.1.81 on wlp4s0.IPv4.
Jul  2 12:43:11 angel-23-b364 dhclient[1424]: bound to 192.168.1.81 -- renewal in 35149 seconds.
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4086] device (wlp4s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4357] device (wlp4s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4502] device (wlp4s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4512] manager: NetworkManager state is now CONNECTED_LOCAL
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4583] manager: NetworkManager state is now CONNECTED_GLOBAL
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4645] policy: set 'TEAROSE 1' (wlp4s0) as default for IPv4 routing and DNS
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4671] DNS: starting dnsmasq...
Jul  2 12:43:11 angel-23-b364 whoopsie[744]: [12:43:11] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <warn>  [1467488591.4956] dnsmasq[0x2134a20]: dnsmasq not found on the bus. The nameserver update will be sent when dnsmasq appears
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.4958] dns-mgr: Writing DNS information to /sbin/resolvconf
Jul  2 12:43:11 angel-23-b364 dnsmasq[1468]: started, version 2.75 cache disabled
Jul  2 12:43:11 angel-23-b364 dnsmasq[1468]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Jul  2 12:43:11 angel-23-b364 dnsmasq[1468]: DBus support enabled: connected to system bus
Jul  2 12:43:11 angel-23-b364 dnsmasq[1468]: warning: no upstream servers configured
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.8552] device (wlp4s0): Activation: successful, device activated.
Jul  2 12:43:11 angel-23-b364 dbus[742]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.8769] dnsmasq[0x2134a20]: dnsmasq appeared as :1.60
Jul  2 12:43:11 angel-23-b364 NetworkManager[786]: <info>  [1467488591.8774] dns-mgr: Writing DNS information to /sbin/resolvconf
Jul  2 12:43:11 angel-23-b364 whoopsie[744]: [12:43:11] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Jul  2 12:43:11 angel-23-b364 dnsmasq[1468]: setting upstream servers from DBus
Jul  2 12:43:11 angel-23-b364 systemd[1]: Starting Network Manager Script Dispatcher Service...
Jul  2 12:43:11 angel-23-b364 dnsmasq[1468]: using nameserver 192.168.1.254#53
Jul  2 12:43:11 angel-23-b364 dbus[742]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul  2 12:43:11 angel-23-b364 systemd[1]: Started Network Manager Script Dispatcher Service.
```



```
lspci -nn output:00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7340] [1002:9808]
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port [1022:1512]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7812] (rev 03)
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7801] (rev 40)
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 14)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge [1022:780f] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller [1022:7809] (rev 11)
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) [1022:43a0]
00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 1) [1022:43a1]
00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2) [1022:43a2]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7 [1022:1719]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
04:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
```




sudo lshw -C network output:
 ```
 *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eno1
       version: 05
       serial: 54:be:f7:35:95:56
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:32 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: a4:db:30:69:0c:c7 
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-28-generic firmware=N/A ip=192.168.1.81 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fea00000-fea7ffff memory:fea80000-fea8ffff
```



iwconfig output:
```
iwconfig
lo        no wireless extensions.


eno1      no wireless extensions.   


wlp4s0    IEEE 802.11bgn  ESSID:"TEAROSE"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: F8:18:97:7A:E6:3E   
          Bit Rate=52 Mb/s   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:200   Missed beacon:0
```

---

### Post by jeremy31 on 2016-07-02
Welcome to the forums.  Please use code tags when posting terminal output or commands.  From this part of your logs
```
Jul  2 12:11:57 angel-23-b364 systemd[1]: Starting Stop ureadahead data collection...
Jul  2 12:11:57 angel-23-b364 systemd[1]: Stopped Read required files in advance.
Jul  2 12:11:57 angel-23-b364 systemd[1]: Started Stop ureadahead data collection.
Jul  2 12:17:01 angel-23-b364 CRON[1153]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  2 12:26:17 angel-23-b364 systemd[1]: Starting Cleanup of Temporary Directories...
Jul  2 12:26:17 angel-23-b364 systemd-tmpfiles[1170]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Jul  2 12:26:17 angel-23-b364 systemd[1]: Started Cleanup of Temporary Directories.
Jul  2 12:43:09 angel-23-b364 org.gtk.vfs.Daemon[970]: A connection to the bus can't be made
Jul  2 12:43:09 angel-23-b364 systemd[1]: Created slice User Slice of angel.
```

I would say your long boot time is not caused by wireless or networking

Did the HP have windows 8 or 10 on it?

---

### Post by msbarton1958 on 2016-07-02
Yes, it previously had windows 10 on it. When installing I chose to have the partition formatted.

---

### Post by msbarton1958 on 2016-07-02
I found the issue, you were right, it was not networking, I had earlier done some googling and saw some issue about SSD drives and AHCI. On a lark, I went into the BIOS and changesd the drive form AHCI to IDE emulation, and now it boots in a few seconds.

This can be closed. Thanks.

---

### Post by jeremy31 on 2016-07-02
Glad you found the cause, you can use thread tools near the top of the page to mark as solved

---

