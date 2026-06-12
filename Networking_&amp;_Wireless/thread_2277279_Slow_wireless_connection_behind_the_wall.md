---
title: "Slow wireless connection behind the wall"
date: 2015-05-07
forum: Networking &amp; Wireless
---

### Post by nganon2 on 2015-05-07
Hello!


I am having connection problems with Intel Corporation Centrino Ultimate-N 6300 wireless card on my laptop.


When the laptop is near the router, I get full internet speed but when I go behind the 20 cm thick wall (that is about one meter, about three feet total distance) the router is pingable but I cannot connect to its web interface or get internet access to any other website before connection timeout/closed.


Here us the output of ping next to the router 
```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=25 ttl=64 time=3.22 ms
64 bytes from 192.168.0.1: icmp_seq=26 ttl=64 time=2.24 ms
64 bytes from 192.168.0.1: icmp_seq=27 ttl=64 time=4.85 ms
64 bytes from 192.168.0.1: icmp_seq=28 ttl=64 time=3.24 ms
...

```
Behind the wall
```

...
64 bytes from 192.168.0.1: icmp_seq=265 ttl=64 time=5425 ms
64 bytes from 192.168.0.1: icmp_seq=268 ttl=64 time=7479 ms
64 bytes from 192.168.0.1: icmp_seq=269 ttl=64 time=8071 ms
64 bytes from 192.168.0.1: icmp_seq=271 ttl=64 time=7519 ms
...

```


I have seen similar issues on other forums.  But their suggestions like setting the regulatory domain to correct frequency or following the instructions  [http://www.linksys.com/us/support-article?articleNum=135766](http://www.linksys.com/us/support-article?articleNum=135766) didn't help.


This is likely driver issue, I think, but I am not sure what to do with it. Here is some noteworthy details, hope you can help me with.
Please note that the output is from Gentoo but I can reproduce this on Kubuntu as well. 

Wireless adapter:
```
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
        Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
        Kernel driver in use: iwlwifi
```

Firmware installed:
```
[I] sys-firmware/iwl6000-ucode (9.221.4.1{tbz2}@04/24/2015): Intel (R) Wireless WiFi Ultimate-N 6300 and Advanced-N 6000 ucode

```
and in kernel config I have
```
CONFIG_FW_LOADER_USER_HELPER_FALLBACK=y

```


dmesg output snipped from where system is booted and ready.
```

... 
[    2.565589] e1000e 0000:00:19.0 enp0s25: renamed from eth0
[    3.494567] EXT4-fs (sda4): re-mounted. Opts: discard
[    4.455785] random: nonblocking pool is initialized
[    4.622011] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[    4.854010] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[    7.342454] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    7.605361] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12
[   10.379766] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   12.558164] psmouse serio3: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   12.824484] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio3/input/input13
[   60.491137] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[B][   60.491147] iwlwifi 0000:03:00.0: Falling back to user helper
[  120.511236] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[/B][  120.511278] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  120.511285] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS disabled
[  120.511290] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING disabled
[  120.511296] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[  120.511371] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[  120.523902] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  120.531922] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[  120.547308] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  120.547491] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[  120.547679] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  120.766625] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[  120.766846] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  120.845075] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  120.885376] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready

```
Please notice how late iwlwifi is (not) loaded! It is always about 60 seconds + 60 seconds. 


Hopefully syslog messages will be most helpful.
```

May  7 04:45:56 Gentoo-T420s NetworkManager[3595]: <info>  caught signal 15, shutting down normally.
May  7 04:45:56 Gentoo-T420s NetworkManager[3595]: <info>  (enp0s25): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
May  7 02:01:35 Gentoo-T420s kernel: e1000e: enp0s25 NIC Link is Down
May  7 04:45:56 Gentoo-T420s NetworkManager[3595]: <info>  (wlp3s0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
May  7 04:45:56 Gentoo-T420s NetworkManager[3595]: <info>  exiting (success)
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  NetworkManager (version 1.0.0) is starting...
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Read config: /etc/NetworkManager/NetworkManager.conf
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  WEXT support is enabled
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  VPN: loaded org.freedesktop.NetworkManager.vpnc
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Loaded plugin keyfile: (c) 2007 - 2013 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  new connection /etc/NetworkManager/system-connections/Wired connection 1
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  new connection /etc/NetworkManager/system-connections/NetMASTER Uydunet-6B35
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <warn>      error in connection /etc/NetworkManager/system-connections/.keep_net-misc_networkmanager-0: invalid connection: connection.type: property is missing
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  monitoring kernel firmware directory '/lib/firmware'.
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  WiFi hardware radio set enabled
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  WWAN hardware radio set enabled
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Loaded device plugin: /usr/lib64/NetworkManager/libnm-device-plugin-adsl.so
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Loaded device plugin: /usr/lib64/NetworkManager/libnm-device-plugin-bluetooth.so
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Loaded device plugin: /usr/lib64/NetworkManager/libnm-device-plugin-wwan.so
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Loaded device plugin: /usr/lib64/NetworkManager/libnm-device-plugin-wifi.so
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  WiFi enabled by radio killswitch; enabled by state file
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  WWAN enabled by radio killswitch; enabled by state file
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  WiMAX enabled by radio killswitch; enabled by state file
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  Networking is enabled by state file
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (lo): link connected
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (lo): carrier is ON
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (lo): new Generic device (driver: 'unknown' ifindex: 1)
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (lo): exported as /org/freedesktop/NetworkManager/Devices/0
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (enp0s25): carrier is OFF
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (enp0s25): new Ethernet device (driver: 'e1000e' ifindex: 2)
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (enp0s25): exported as /org/freedesktop/NetworkManager/Devices/1
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (enp0s25): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  7 04:46:20 Gentoo-T420s kernel: IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
May  7 04:46:20 Gentoo-T420s kernel: IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (enp0s25): preparing device
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (sit0): new Generic device (driver: 'sit' ifindex: 3)
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  (sit0): exported as /org/freedesktop/NetworkManager/Devices/2
May  7 04:46:20 Gentoo-T420s ModemManager[3529]: <info>  ModemManager (version 1.4.6) starting in system bus...
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  ModemManager disappeared from bus
May  7 04:46:20 Gentoo-T420s NetworkManager[3514]: <info>  ModemManager available in the bus
May  7 04:46:21 Gentoo-T420s /etc/init.d/NetworkManager[3491]: WARNING: NetworkManager has started, but is inactive
May  7 04:46:21 Gentoo-T420s /etc/init.d/dhcpd[3585]: WARNING: dhcpd will start when NetworkManager has started
May  7 04:46:21 Gentoo-T420s /etc/init.d/netmount[4331]: WARNING: netmount will start when NetworkManager has started
May  7 04:46:22 Gentoo-T420s ModemManager[3529]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:19.0': not supported by any plugin
May  7 04:46:25 Gentoo-T420s NetworkManager[3514]: <info>  startup complete
May  7 04:46:38 Gentoo-T420s ModemManager[3529]: <info>  Creating modem with plugin 'Generic' and '1' ports
May  7 04:46:38 Gentoo-T420s ModemManager[3529]: <warn>  Could not grab port (tty/ttyS0): 'Cannot add port 'tty/ttyS0', unhandled serial type'
May  7 04:46:38 Gentoo-T420s ModemManager[3529]: <warn>  Couldn't create modem for device at '/sys/devices/pci0000:00/0000:00:16.3': Failed to find primary AT port
May  7 04:47:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
May  7 04:47:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: Falling back to user helper
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS disabled
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING disabled
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
May  7 04:48:16 Gentoo-T420s kernel: ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): using nl80211 for WiFi device control
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): exported as /org/freedesktop/NetworkManager/Devices/3
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  7 04:48:16 Gentoo-T420s kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
May  7 04:48:16 Gentoo-T420s kernel: iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): preparing device
May  7 04:48:16 Gentoo-T420s kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  wpa_supplicant started
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0) supports 5 scan SSIDs
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: starting -> ready
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May  7 04:48:16 Gentoo-T420s kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: ready -> disconnected
May  7 04:48:16 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0) supports 5 scan SSIDs
May  7 04:48:18 Gentoo-T420s ModemManager[3529]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0': not supported by any plugin
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  Auto-activating connection 'NetMASTER Uydunet-6B35'.
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: starting connection 'NetMASTER Uydunet-6B35'
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 1 of 5 (Device Prepare) scheduled...
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 1 of 5 (Device Prepare) started...
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  NetworkManager state is now CONNECTING
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 2 of 5 (Device Configure) scheduled...
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 1 of 5 (Device Prepare) complete.
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 2 of 5 (Device Configure) starting...
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: (wifi) access point 'NetMASTER Uydunet-6B35' has security, but secrets are required.
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: config -> need-auth (reason 'none') [50 60 0]
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 2 of 5 (Device Configure) complete.
May  7 04:48:19 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: disconnected -> inactive
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 1 of 5 (Device Prepare) scheduled...
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 1 of 5 (Device Prepare) started...
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 2 of 5 (Device Configure) scheduled...
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 1 of 5 (Device Prepare) complete.
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 2 of 5 (Device Configure) starting...
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: (wifi) connection 'NetMASTER Uydunet-6B35' has security, and secrets exist.  No new secrets needed.
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  Config: added 'ssid' value 'NetMASTER Uydunet-6B35'
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  Config: added 'scan_ssid' value '1'
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  Config: added 'psk' value '<omitted>'
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 2 of 5 (Device Configure) complete.
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  Config: set interface ap_scan to 1
May  7 04:49:31 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: inactive -> scanning
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: authenticate with 00:1c:7b:fd:75:74
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: send auth to 00:1c:7b:fd:75:74 (try 1/3)
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: authenticated
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: waiting for beacon from 00:1c:7b:fd:75:74
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: scanning -> associating
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: associate with 00:1c:7b:fd:75:74 (try 1/3)
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: RX AssocResp from 00:1c:7b:fd:75:74 (capab=0x411 status=0 aid=1)
May  7 04:49:35 Gentoo-T420s kernel: wlp3s0: associated
May  7 04:49:35 Gentoo-T420s kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: associating -> associated
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NetMASTER Uydunet-6B35'.
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 3 of 5 (IP Configure Start) scheduled.
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 3 of 5 (IP Configure Start) started...
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 3 of 5 (IP Configure Start) complete.
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 5 of 5 (IPv4 Commit) started...
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <warn>  (wlp3s0): arping could not be found; no ARPs will be sent
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 5 of 5 (IPv4 Commit) complete.
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  NetworkManager state is now CONNECTED_LOCAL
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  NetworkManager state is now CONNECTED_GLOBAL
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  Policy set 'NetMASTER Uydunet-6B35' (wlp3s0) as default for IPv4 routing and DNS.
May  7 04:49:35 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: successful, device activated.
May  7 04:49:35 Gentoo-T420s dbus[3342]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May  7 04:49:35 Gentoo-T420s dbus[3342]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May  7 04:49:35 Gentoo-T420s nm-dispatcher[5066]: Dispatching action 'up' for wlp3s0
May  7 04:49:35 Gentoo-T420s /etc/init.d/NetworkManager[5079]: status: inactive
May  7 04:49:35 Gentoo-T420s /etc/init.d/NetworkManager[5091]: status: inactive
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: Internet Systems Consortium DHCP Server 4.3.2 Gentoo-r0
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: Copyright 2004-2015 Internet Systems Consortium.
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: All rights reserved.
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: For info, please visit https://www.isc.org/software/dhcp/
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: Not searching LDAP since ldap-server, ldap-port and ldap-base-dn were not specified in the config file
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: Config file: /etc/dhcp/dhcpd.conf
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: Database file: /var/lib/dhcp/dhcpd.leases
May  7 04:49:35 Gentoo-T420s dhcpd[5130]: PID file: /var/run/dhcp/dhcpd.pid
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: Not searching LDAP since ldap-server, ldap-port and ldap-base-dn were not specified in the config file
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: Wrote 0 leases to leases file.
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: 
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: No subnet declaration for wlp3s0 (192.168.0.36).
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: ** Ignoring requests on wlp3s0.  If this is not what
May  7 04:49:35 Gentoo-T420s dhcpd[5165]:    you want, please write a subnet declaration
May  7 04:49:35 Gentoo-T420s dhcpd[5165]:    in your dhcpd.conf file for the network segment
May  7 04:49:35 Gentoo-T420s dhcpd[5165]:    to which interface wlp3s0 is attached. **
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: 
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: 
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: Not configured to listen on any interfaces!
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: 
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: If you think you have received this message due to a bug rather
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: than a configuration issue please read the section on submitting
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: bugs on either our web page at www.isc.org or in the README file
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: before submitting a bug.  These pages explain the proper
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: process and the information we find helpful for debugging..
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: 
May  7 04:49:35 Gentoo-T420s dhcpd[5165]: exiting.
May  7 04:49:35 Gentoo-T420s /etc/init.d/dhcpd[5164]: start-stop-daemon: failed to start `/usr/sbin/dhcpd'
May  7 04:49:35 Gentoo-T420s /etc/init.d/dhcpd[5104]: ERROR: dhcpd failed to start
May  7 04:49:37 Gentoo-T420s NetworkManager[3514]: <warn>  (wlp3s0): arping could not be found; no ARPs will be sent
May  7 04:50:07 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  7 04:50:07 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 4 of 5 (IPv6 Configure Timeout) started...
May  7 04:50:07 Gentoo-T420s NetworkManager[3514]: <info>  (wlp3s0): Activation: Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

FWIW, android devices and another, rather old, laptop running win7 do not have this issue.

Can you please tell me what else I can check and what can I do with all these?


Thanks very much for your time in advance!

---

### Post by nganon2 on 2015-05-12
bump

---

