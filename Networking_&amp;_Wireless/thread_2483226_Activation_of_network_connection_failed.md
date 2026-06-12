---
title: "Activation of network connection failed"
date: 2023-01-23
forum: Networking &amp; Wireless
---

### Post by .Ricky. on 2023-01-23
Hello,

Premise - I've searched for this issue and found others reporting it, but found no conclusive answer or anything that could solve it for me.

I upgraded from Ubuntu 22.04 to 22.10 not too long ago, and I recently started having issues with the wifi.

Issue: apparently randomly, the wifi sometimes works and some times it doesn't. At times it will connect but with no internet access, at other times it won't connect at all, and at other times it will connect but internet will be rather slow.

It is 100% certain this is an Ubuntu software issue as I can exclude everything else:

- not a PC hardware issue: same PC has a separate HD with Windows on it, connection works (Windows fast load has been disabled, does not solve the issue)
- not a router issue: other devices can connect to the network
- (???) weirdly, some times I can hotspot from my phone (on the same wifi network) and my PC can connect to internet through there. Sometimes this does not work.

I don't know what kind of logs are useful, but I've gathered some after seeing similar issues online elsewhere. I hope they might be useful - I think the `dmesg` output might be as there's a bunch of red error messages there.

```
uname -r

5.19.0-29-generic
```

These are logs of when it connects to the network but with no internet access:

```
sudo journalctl  -b 0 -u NetworkManager

Jan 22 12:01:57 linux systemd[1]: Starting Network Manager...
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8012] NetworkManager (version 1.40.0) is starting... (boot:02193699-6355-43fd-811a-4c4f7772b05f)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8022] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: 10-ubuntu-fan.conf, default-wifi-powersave-on.conf)
Jan 22 12:01:57 linux systemd[1]: Started Network Manager.
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8060] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8288] manager[0x5590ac78d000]: monitoring kernel firmware directory '/lib/firmware'.
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8289] monitoring ifupdown state file '/run/network/ifstate'.
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8302] hostname: hostname: using hostnamed
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8302] hostname: static hostname changed from (none) to "linux"
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8340] dns-mgr: init: dns=systemd-resolved rc-manager=unmanaged (auto), plugin=systemd-resolved
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8366] rfkill1: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:01.2/0000:01:00.0/0000:02:03.0/0000:04:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8368] manager[0x5590ac78d000]: rfkill: Wi-Fi hardware radio set enabled
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8368] manager[0x5590ac78d000]: rfkill: WWAN hardware radio set enabled
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8529] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.40.0/libnm-device-plugin-team.so)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8559] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.40.0/libnm-device-plugin-adsl.so)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8644] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.40.0/libnm-device-plugin-wwan.so)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8725] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.40.0/libnm-device-plugin-wifi.so)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8816] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.40.0/libnm-device-plugin-bluetooth.so)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8818] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8833] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8833] manager: Networking is enabled by state file
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8897] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.40.0/libnm-settings-plugin-ifupdown.so")
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8897] settings: Loaded settings plugin: keyfile (internal)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8897] ifupdown: management mode: unmanaged
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8911] ifupdown:       interface-parser: parsing file /etc/network/interfaces
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.8928] ifupdown:       interface-parser: finished parsing file /etc/network/interfaces
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.9046] dhcp: init: Using DHCP client 'internal'
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.9046] device (lo): carrier: link connected
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.9048] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.9053] manager: (enp5s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.9058] settings: (enp5s0): created default wired connection 'Wired connection 1'
Jan 22 12:01:57 linux NetworkManager[1002]: <info>  [1674388917.9059] device (enp5s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.1374] device (wlp4s0): driver supports Access Point (AP) mode
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.1377] manager: (wlp4s0): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/3)
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.1379] device (wlp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3277] failed to open /run/network/ifstate
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3309] manager: (C4:93:D9:ED:2C:64): new Bluetooth device (/org/freedesktop/NetworkManager/Devices/4)
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3310] device (C4:93:D9:ED:2C:64): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3324] modem-manager: ModemManager available
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3326] device (C4:93:D9:ED:2C:64): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'managed')
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3819] device (wlp4s0): supplicant interface state: internal-starting -> disconnected
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3820] Wi-Fi P2P device controlled by interface wlp4s0 created
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3821] manager: (p2p-dev-wlp4s0): new 802.11 Wi-Fi P2P device (/org/freedesktop/NetworkManager/Devices/5)
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3822] device (p2p-dev-wlp4s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3825] device (wlp4s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Jan 22 12:01:58 linux NetworkManager[1002]: <info>  [1674388918.3828] device (p2p-dev-wlp4s0): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8807] policy: auto-activating connection 'EE-SPC2G8' (4502e7db-a86d-43c9-9221-026cf9fddb45)
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8810] device (wlp4s0): Activation: starting connection 'EE-SPC2G8' (4502e7db-a86d-43c9-9221-026cf9fddb45)
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8810] device (wlp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8812] manager: NetworkManager state is now CONNECTING
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8813] device (wlp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8815] device (wlp4s0): Activation: (wifi) access point 'EE-SPC2G8' has security, but secrets are required.
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8815] device (wlp4s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8815] sup-iface[8ff00259d9f21747,0,wlp4s0]: wps: type pbc start...
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8819] device (wlp4s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8820] device (wlp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] device (wlp4s0): Activation: (wifi) connection 'EE-SPC2G8' has security, and secrets exist.  No new secrets needed.
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] Config: added 'ssid' value 'EE-SPC2G8'
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] Config: added 'scan_ssid' value '1'
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] Config: added 'bgscan' value 'simple:30:-70:86400'
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] Config: added 'auth_alg' value 'OPEN'
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.8822] Config: added 'psk' value '<hidden>'
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.9001] device (wlp4s0): supplicant interface state: disconnected -> authenticating
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.9001] device (p2p-dev-wlp4s0): supplicant management interface state: disconnected -> authenticating
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.9623] device (wlp4s0): supplicant interface state: authenticating -> associating
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.9624] device (p2p-dev-wlp4s0): supplicant management interface state: authenticating -> associating
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.9774] device (wlp4s0): supplicant interface state: associating -> 4way_handshake
Jan 22 12:02:01 linux NetworkManager[1002]: <info>  [1674388921.9774] device (p2p-dev-wlp4s0): supplicant management interface state: associating -> 4way_handshake
Jan 22 12:02:02 linux NetworkManager[1002]: <info>  [1674388922.0635] device (wlp4s0): supplicant interface state: 4way_handshake -> completed
Jan 22 12:02:02 linux NetworkManager[1002]: <info>  [1674388922.0635] device (wlp4s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful. Connected to wireless network "EE-SPC2G8"
Jan 22 12:02:02 linux NetworkManager[1002]: <info>  [1674388922.0635] device (p2p-dev-wlp4s0): supplicant management interface state: 4way_handshake -> completed
Jan 22 12:02:02 linux NetworkManager[1002]: <info>  [1674388922.0636] device (wlp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:02 linux NetworkManager[1002]: <info>  [1674388922.0639] dhcp4 (wlp4s0): activation: beginning transaction (timeout in 45 seconds)
Jan 22 12:02:02 linux NetworkManager[1002]: <info>  [1674388922.5264] agent-manager: agent[07a64ed93e463163,:1.45/org.gnome.Shell.NetworkAgent/126]: agent registered
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1463] dhcp4 (wlp4s0): state changed new lease, address=192.168.1.198
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1467] policy: set 'EE-SPC2G8' (wlp4s0) as default for IPv4 routing and DNS
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1528] device (wlp4s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1547] device (wlp4s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1549] device (wlp4s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1551] manager: NetworkManager state is now CONNECTED_SITE
Jan 22 12:02:03 linux NetworkManager[1002]: <info>  [1674388923.1558] device (wlp4s0): Activation: successful, device activated.
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.1381] manager: startup complete
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.5476] manager: (docker0): new Bridge device (/org/freedesktop/NetworkManager/Devices/6)
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6156] device (docker0): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6159] device (docker0): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6162] device (docker0): Activation: starting connection 'docker0' (1ee04666-7634-4370-9cb4-b35b94c49873)
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6163] device (docker0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6164] device (docker0): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6165] device (docker0): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6182] device (docker0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6188] device (docker0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6189] device (docker0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.6190] device (docker0): Activation: successful, device activated.
Jan 22 12:02:04 linux NetworkManager[1002]: <info>  [1674388924.8649] manager: NetworkManager state is now CONNECTED_GLOBAL
Jan 22 12:02:13 linux NetworkManager[1002]: <info>  [1674388933.4011] agent-manager: agent[a05f095425069666,:1.81/org.gnome.Shell.NetworkAgent/1000]: agent registered
```

```
cat /etc/network/interfaces

auto lo iface lo inet loopback auto wlan0 iface wlan0 inet dhcp wpa-essid myssid wpa-psk mypasscode
```

```
cat /etc/netplan/*.yaml

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

```
dpkg -l wpasupplicant

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version         Architecture Description
+++-==============-===============-============-==============================================
ii  wpasupplicant  2:2.10-9ubuntu1 amd64        client support for WPA and WPA2 (IEEE 802.11i)
```

```
sudo dmesg
```
(too long to post, please see here [https://pastebin.ubuntu.com/p/HmsY8xCwkV/](https://pastebin.ubuntu.com/p/HmsY8xCwkV/) )

And this is dmesg when the connection was successful:

```
sudo dmesg
```
(too long to post, please see here [https://pastebin.ubuntu.com/p/PrMpxGsmgY/](https://pastebin.ubuntu.com/p/PrMpxGsmgY/) )

---

### Post by .Ricky. on 2023-01-27
Sorry - just noticed that there was a [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108") with a script to run to display helpful info for troubleshooting, I'm attaching the results here.

Also - seems like nobody has opened this thread. Looks like the forums aren't used anymore. Where should I ask for help?

---

### Post by .Ricky. on 2023-01-28
Solved here [https://askubuntu.com/questions/1452234/wifi-intermittent-on-ubuntu-22-10](https://askubuntu.com/questions/1452234/wifi-intermittent-on-ubuntu-22-10)

---

