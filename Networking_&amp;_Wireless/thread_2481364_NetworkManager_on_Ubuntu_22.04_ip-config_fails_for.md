---
title: "NetworkManager on Ubuntu 22.04: ip-config fails for reason ip-config-unavailable"
date: 2022-11-27
forum: Networking &amp; Wireless
---

### Post by ssnover on 2022-11-27
Hello, I'm running Ubuntu 22.04 and have been since release earlier this year. I ran into an issue connecting to a WLAN connection today that I've had no problem connecting to in the past. I've managed to narrow it to this particular connection as I'm able to tether to my hotspotting phone (which is on the WLAN connection I'm trying to connect to).

Some things I've tried:
* A reboot
* `nmcli r wifi off && nmcli r wifi on` - I can see NetworkManager's widget in the toolbar attempt to connect and fail.
* `nmcli c delete <SSID>` and then re-adding in the NetworkManager GUI.

I've also compared the connection files side-by-side with no obvious difference between them, here's the one with the failing connection:
```

[connection]
id=<SSID_OMITTED>
uuid=c0ae667d-1b93-4f11-8e7b-4c066f54959d
type=wifi
interface-name=wlp1s0

[wifi]
mode=infrastructure
ssid=<SSID_OMITTED>

[wifi-security]
auth-alg=open
key-mgmt=wpa-psk
psk=<PASSWORD_OMITTED>

[ipv4]
dns-search=
method=auto

[ipv6]
addr-gen-mode=stable-privacy
method=auto

[proxy]

```

I've also checked the logs from NetworkManager reported to journalctl and determined that it seems to be a dhcp4 configuration problem (command is `journalctl -b | grep NetworkManager`):
```

Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7004] policy: auto-activating connection '<SSID>' (c0ae667d-1b93-4f11-8e7b-4c066f54959d)
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7015] device (wlp1s0): Activation: starting connection '<SSID>' (c0ae667d-1b93-4f11-8e7b-4c066f54959d)
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7017] device (wlp1s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7022] manager: NetworkManager state is now CONNECTING
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7027] device (wlp1s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7033] device (wlp1s0): Activation: (wifi) access point '<SSID>' has security, but secrets are required.
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7034] device (wlp1s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7057] device (wlp1s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7063] device (wlp1s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7069] device (wlp1s0): Activation: (wifi) connection '<SSID>' has security, and secrets exist.  No new secrets needed.
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7069] Config: added 'ssid' value '<SSID>'
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7070] Config: added 'scan_ssid' value '1'
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7070] Config: added 'bgscan' value 'simple:30:-70:86400'
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7070] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7071] Config: added 'auth_alg' value 'OPEN'
Nov 27 12:23:54 orre NetworkManager[779]: <info>  [1669577034.7071] Config: added 'psk' value '<hidden>'
Nov 27 12:23:58 orre NetworkManager[779]: <info>  [1669577038.8834] device (wlp1s0): supplicant interface state: disconnected -> scanning
Nov 27 12:24:02 orre NetworkManager[779]: <info>  [1669577042.8066] device (wlp1s0): supplicant interface state: scanning -> authenticating
Nov 27 12:24:02 orre NetworkManager[779]: <info>  [1669577042.8429] device (wlp1s0): supplicant interface state: authenticating -> associating
Nov 27 12:24:03 orre NetworkManager[779]: <info>  [1669577043.0146] device (wlp1s0): supplicant interface state: associating -> completed
Nov 27 12:24:03 orre NetworkManager[779]: <info>  [1669577043.0146] device (wlp1s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful. Connected to wireless network "<SSID>"
Nov 27 12:24:03 orre NetworkManager[779]: <info>  [1669577043.0148] device (wlp1s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Nov 27 12:24:03 orre NetworkManager[779]: <info>  [1669577043.0152] dhcp4 (wlp1s0): activation: beginning transaction (timeout in 45 seconds)
Nov 27 12:24:04 orre systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Nov 27 12:24:08 orre dbus-daemon[777]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=779 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Nov 27 12:24:18 orre systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Nov 27 12:24:48 orre NetworkManager[779]: <info>  [1669577088.1381] device (wlp1s0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Nov 27 12:24:48 orre NetworkManager[779]: <info>  [1669577088.1387] manager: NetworkManager state is now CONNECTED_LOCAL
Nov 27 12:24:48 orre NetworkManager[779]: <warn>  [1669577088.1392] device (wlp1s0): Activation: failed for connection '<SSID>'
Nov 27 12:24:48 orre NetworkManager[779]: <info>  [1669577088.1394] device (wlp1s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Nov 27 12:24:48 orre NetworkManager[779]: <info>  [1669577088.1854] dhcp4 (wlp1s0): canceled DHCP transaction
Nov 27 12:24:48 orre dbus-daemon[777]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.11' (uid=0 pid=779 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Nov 27 12:24:48 orre NetworkManager[779]: <info>  [1669577088.3554] device (wlp1s0): supplicant interface state: completed -> disconnected

```

No obvious problems in dmesg:
```

[ 1597.362059] wlp1s0: authenticate with 00:ab:48:28:90:26
[ 1597.593619] wlp1s0: send auth to 00:ab:48:28:90:26 (try 1/3)
[ 1597.620371] wlp1s0: authenticated
[ 1597.625751] wlp1s0: associate with 00:ab:48:28:90:26 (try 1/3)
[ 1597.631181] wlp1s0: RX AssocResp from 00:ab:48:28:90:26 (capab=0x1111 status=0 aid=5)
[ 1597.741776] wlp1s0: associated
[ 1597.741971] wlp1s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 00:ab:48:28:90:26
[ 1643.066789] wlp1s0: deauthenticating from 00:ab:48:28:90:26 by local choice (Reason: 3=DEAUTH_LEAVING)

```

NetworkManager version is 1.36.6
kernel version is 5.15.0-53

I'm looking for tips on additional things to check to fix this. If I wasn't able to connect to other networks I'd be suspicious of conflicting systemd services, but given that two networks of nearly identical setup (from a NetworkManager configuration context) behave differently, I suspect that something that's being received from the router is tripping it up. Any ideas on ways I can see the data being sent back directly (higher verbosity on NetworkManager somehow perhaps?). I see that I have dhclient configuration on my system as well, but it's not clear to me if that's being utilized by NetworkManager or if NetworkManager is using it's own internal implementation (I see in the source it has one at least).

---

### Post by romeotangosiera on 2022-12-02
Config may have failed because it did not get a DHCP response from connected wifi.

---

