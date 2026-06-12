---
title: "NetworkManager unable to connect to Wi-Fi.  (53) The Wi-Fi network could not be found"
date: 2022-09-02
forum: Networking &amp; Wireless
---

### Post by marmalade57534 on 2022-09-02
[COLOR=#333333][FONT=Verdana]NetworkManager unable to connect to Wi-Fi. nmtui repeatedly keeps on prompting for password and nmcli is unable to find the WiFi. The WiFi is visible and available. My other devices are connecting to it without any problem. Same problem exists with all the SSIDs.
[/FONT][/COLOR]```
:~$ nmcli device wifi rescan
              //I'll wait 10-30 seconds//
:~$ nmcli device wifi connect "mywifi" password "12345678"
Error: Connection activation failed: (53) The Wi-Fi network could not be found.

```
[COLOR=#333333][FONT=Verdana]Now I discovered that if instead I restart my NetworkManager services, I get a different output
[/FONT][/COLOR]
```

:~$ nmcli con delete mywifi
:~$ sudo systemctl restart NetworkManager  <<-- I didn't use this before.
:~$ sudo nmcli device wifi rescan 
:~$ sudo nmcli device wifi connect "mywifi" password "12345678"
Error: Connection activation failed: (7) Secrets were required, but not provided.

```

[COLOR=#333333][FONT=Verdana]Here's some output which I thought might be useful. Let me know what else I need to add to this. Sorry I wan't sure which information would be useful alongside the post. I am running xubuntu 4.16
[/FONT][/COLOR]```
  =>  :~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy


  =>  :~$ sudo systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2022-09-01 20:36:22 IST; 55min ago
       Docs: man:NetworkManager(8)
   Main PID: 1233 (NetworkManager)
      Tasks: 3 (limit: 3274)
     Memory: 10.7M
        CPU: 937ms
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1233 /usr/sbin/NetworkManager --no-daemon
```


My journalctl from when I deleted the "mywifi" profile until when I received and error.
```

        :~$ journalctl -f
<info>  [1662059690.0451] device (wlp3s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
<warn>  [1662059690.0457] device (wlp3s0): Activation: (wifi) asking for new secrets
<warn>  [1662059690.0462] device (wlp3s0): no secrets: No agents were available for this request.
<info>  [1662059690.0463] device (wlp3s0): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
<warn>  [1662059690.0469] device (wlp3s0): Activation: failed for connection 'mywifi'
<info>  [1662059690.0472] device (wlp3s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
pam_unix(sudo:session): session closed for user root
<info>  [1662059690.4952] device (wlp3s0): supplicant interface state: scanning -> disconnected
privileged : TTY=pts/0 ; PWD=/home/privileged ; USER=root ; COMMAND=/usr/bin/systemctl status NetworkManager
pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
pam_unix(sudo:session): session closed for user root
<info>  [1662059851.1881] audit: op="connection-delete" uuid="1f51093e-a998-42f4-82ff-494a9b4e6903" name="mywifi" pid=3349094 uid=1000 result="success"
privileged : TTY=pts/0 ; PWD=/home/privileged ; USER=root ; COMMAND=/usr/bin/systemctl restart NetworkManager
pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Stopping Network Manager...
<info>  [1662059876.3366] caught SIGTERM, shutting down normally.
<info>  [1662059876.3529] dhcp4 (enp4s0): canceled DHCP transaction
<info>  [1662059876.3529] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
<info>  [1662059876.3530] dhcp4 (enp4s0): state changed no lease
<info>  [1662059876.3533] dhcp6 (enp4s0): canceled DHCP transaction
<info>  [1662059876.3533] dhcp6 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
<info>  [1662059876.3533] dhcp6 (enp4s0): state changed no lease
<info>  [1662059876.3537] manager: NetworkManager state is now CONNECTED_SITE
<info>  [1662059876.3541] device (wlp3s0): state change: disconnected -> unmanaged (reason 'unmanaged', sys-iface-state: 'managed')
[system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.500' (uid=0 pid=3277130 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Starting Network Manager Script Dispatcher Service...
wlp3s0: Link DOWN
<info>  [1662059876.3763] device (78:02:F8:85:CE:7E): state change: disconnected -> unmanaged (reason 'unmanaged', sys-iface-state: 'managed')
wlp3s0: CTRL-EVENT-DSCP-POLICY clear_all
[system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Started Network Manager Script Dispatcher Service.
<info>  [1662059876.3939] exiting (success)
wlp3s0: CTRL-EVENT-DSCP-POLICY clear_all
nl80211: deinit ifname=wlp3s0 disabled_11b_rates=0
NetworkManager.service: Deactivated successfully.
Stopped Network Manager.
Starting Network Manager...
<info>  [1662059876.4758] NetworkManager (version 1.36.6) is starting... (after a restart)
<info>  [1662059876.4759] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
Started Network Manager.
pam_unix(sudo:session): session closed for user root
<info>  [1662059876.4845] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
<info>  [1662059876.4888] manager[0x5632ed87e040]: monitoring kernel firmware directory '/lib/firmware'.
<info>  [1662059876.4889] monitoring ifupdown state file '/run/network/ifstate'.
[system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.506' (uid=0 pid=3357852 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Starting Hostname Service...
[system] Successfully activated service 'org.freedesktop.hostname1'
Started Hostname Service.
<info>  [1662059876.6949] hostname: hostname: using hostnamed
<info>  [1662059876.6950] hostname: static hostname changed from (none) to "privileged-Inspiron-N4010"
<info>  [1662059876.6956] dns-mgr[0x5632ed8592a0]: init: dns=systemd-resolved rc-manager=unmanaged (auto), plugin=systemd-resolved
<info>  [1662059876.6970] rfkill0: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver iwlwifi)
<info>  [1662059876.6973] manager[0x5632ed87e040]: rfkill: Wi-Fi hardware radio set enabled
<info>  [1662059876.6974] manager[0x5632ed87e040]: rfkill: WWAN hardware radio set enabled
<info>  [1662059876.6994] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-team.so)
<info>  [1662059876.6998] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-adsl.so)
<info>  [1662059876.7016] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
<info>  [1662059876.7020] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wwan.so)
<info>  [1662059876.7025] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-wifi.so)
<info>  [1662059876.7029] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
<info>  [1662059876.7030] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
<info>  [1662059876.7031] manager: Networking is enabled by state file
<info>  [1662059876.7036] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-settings-plugin-ifupdown.so")
<info>  [1662059876.7036] settings: Loaded settings plugin: keyfile (internal)
<info>  [1662059876.7036] ifupdown: management mode: unmanaged
<info>  [1662059876.7037] ifupdown:       interface-parser: parsing file /etc/network/interfaces
<info>  [1662059876.7037] ifupdown:       interface-parser: source line includes interfaces file(s) /etc/network/interfaces.d/*
<info>  [1662059876.7038] ifupdown: interfaces file /etc/network/interfaces.d/* doesn't exist
<info>  [1662059876.7038] ifupdown:       interface-parser: finished parsing file /etc/network/interfaces
<info>  [1662059876.7070] dhcp-init: Using DHCP client 'internal'
<info>  [1662059876.7071] device (lo): carrier: link connected
<info>  [1662059876.7076] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
<info>  [1662059876.7104] device (enp4s0): carrier: link connected
<info>  [1662059876.7115] manager: (enp4s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
<info>  [1662059876.7124] manager: (enp4s0): assume: will attempt to assume matching connection 'Wired connection 1' (a90c1a12-047a-377a-892a-30457dd809f6) (indicated)
<info>  [1662059876.7125] device (enp4s0): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'assume')
<info>  [1662059876.7136] device (enp4s0): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'assume')
<info>  [1662059876.7147] device (enp4s0): Activation: starting connection 'Wired connection 1' (a90c1a12-047a-377a-892a-30457dd809f6)
<info>  [1662059876.7162] manager: (wlp3s0): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/3)
<info>  [1662059876.7168] device (wlp3s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
wlp3s0: Link UP
<info>  [1662059876.8317] failed to open /run/network/ifstate
<info>  [1662059876.8431] modem-manager: ModemManager available
<info>  [1662059876.8449] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'assume')
<info>  [1662059876.8455] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'assume')
<info>  [1662059876.8459] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'assume')
<info>  [1662059876.8464] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
<info>  [1662059876.8497] manager: (78:02:F8:85:CE:7E): new Bluetooth device (/org/freedesktop/NetworkManager/Devices/4)
<info>  [1662059876.8501] device (78:02:F8:85:CE:7E): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
<info>  [1662059876.8509] device (78:02:F8:85:CE:7E): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'managed')
<info>  [1662059876.8589] agent-manager: agent[866393a090102650,:1.54/org.freedesktop.nm-applet/1000]: agent registered
<info>  [1662059876.8726] dhcp4 (enp4s0): state changed new lease, address=192.168.1.17
<info>  [1662059876.8747] device (enp4s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'assume')
dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface.P2PDevice dbus_property=P2PDeviceConfig getter failed
<info>  [1662059876.8826] device (wlp3s0): supplicant interface state: internal-starting -> disconnected
<info>  [1662059876.8827] device (enp4s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'assume')
<info>  [1662059876.8831] device (wlp3s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
<info>  [1662059876.8839] device (enp4s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'assume')
<info>  [1662059876.8844] manager: NetworkManager state is now CONNECTED_LOCAL
<info>  [1662059876.8850] manager: NetworkManager state is now CONNECTED_SITE
<info>  [1662059876.8857] policy: set 'Wired connection 1' (enp4s0) as default for IPv4 routing and DNS
<info>  [1662059876.8868] device (enp4s0): Activation: successful, device activated.
<info>  [1662059876.8886] manager: NetworkManager state is now CONNECTED_GLOBAL
enp4s0: Bus client set DNS server list to: 192.168.1.1
/etc/network/if-up.d/resolved: 12: mystatedir: not found
/etc/network/if-up.d/resolved: 12: mystatedir: not found
<info>  [1662059877.0312] dhcp6 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
<info>  [1662059877.0320] policy: set 'Wired connection 1' (enp4s0) as default for IPv6 routing and DNS
enp4s0: Bus client set DNS server list to: 192.168.1.1, fe80::1
<info>  [1662059877.0587] dhcp6 (enp4s0): state changed new lease
<info>  [1662059877.3907] manager: startup complete
NetworkManager-dispatcher.service: Deactivated successfully.
privileged : TTY=pts/0 ; PWD=/home/privileged ; USER=root ; COMMAND=/usr/bin/nmcli device wifi rescan
pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
pam_unix(sudo:session): session closed for user root
systemd-hostnamed.service: Deactivated successfully.
privileged : TTY=pts/0 ; PWD=/home/privileged ; USER=root ; COMMAND=/usr/bin/nmcli device wifi connect mywifi password 12345678
pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
<info>  [1662059911.2320] device (wlp3s0): Activation: starting connection 'mywifi' (83488540-dead-42f8-8d1c-1ac07d7baed8)
<info>  [1662059911.2324] audit: op="connection-add-activate" uuid="83488540-dead-42f8-8d1c-1ac07d7baed8" name="mywifi" pid=3369832 uid=0 result="success"
<info>  [1662059911.2376] device (wlp3s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
<info>  [1662059911.2384] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
<info>  [1662059911.2388] device (wlp3s0): Activation: (wifi) access point 'mywifi' has security, but secrets are required.
<info>  [1662059911.2389] device (wlp3s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
<info>  [1662059911.2400] device (wlp3s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
<info>  [1662059911.2403] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
<info>  [1662059911.2405] device (wlp3s0): Activation: (wifi) connection 'mywifi' has security, and secrets exist.  No new secrets needed.
<info>  [1662059911.2406] Config: added 'ssid' value 'mywifi'
<info>  [1662059911.2406] Config: added 'scan_ssid' value '1'
<info>  [1662059911.2406] Config: added 'bgscan' value 'simple:30:-70:86400'
<info>  [1662059911.2406] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK'
<info>  [1662059911.2406] Config: added 'auth_alg' value 'OPEN'
<info>  [1662059911.2406] Config: added 'psk' value '<hidden>'
<info>  [1662059911.2727] device (wlp3s0): supplicant interface state: disconnected -> scanning
wlp3s0: SME: Trying to authenticate with 62:5d:fb:ee:1f:e6 (SSID='mywifi' freq=2412 MHz)
wlp3s0: authenticate with 62:5d:fb:ee:1f:e6
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 1/3)
<info>  [1662059911.7054] device (wlp3s0): supplicant interface state: scanning -> authenticating
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 2/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 3/3)
wlp3s0: authentication with 62:5d:fb:ee:1f:e6 timed out
<info>  [1662059911.9043] device (wlp3s0): supplicant interface state: authenticating -> disconnected
<info>  [1662059912.0041] device (wlp3s0): supplicant interface state: disconnected -> scanning
wlp3s0: SME: Trying to authenticate with 62:5d:fb:ee:1f:e6 (SSID='mywifi' freq=2412 MHz)
wlp3s0: authenticate with 62:5d:fb:ee:1f:e6
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 1/3)
<info>  [1662059912.4839] device (wlp3s0): supplicant interface state: scanning -> authenticating
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 2/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 3/3)
wlp3s0: authentication with 62:5d:fb:ee:1f:e6 timed out
<info>  [1662059912.6657] device (wlp3s0): supplicant interface state: authenticating -> disconnected
<info>  [1662059913.1659] device (wlp3s0): supplicant interface state: disconnected -> scanning
wlp3s0: SME: Trying to authenticate with 62:5d:fb:ee:1f:e6 (SSID='mywifi' freq=2412 MHz)
wlp3s0: authenticate with 62:5d:fb:ee:1f:e6
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 1/3)
<info>  [1662059913.5962] device (wlp3s0): supplicant interface state: scanning -> authenticating
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 2/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 3/3)
wlp3s0: authentication with 62:5d:fb:ee:1f:e6 timed out
<info>  [1662059913.7803] device (wlp3s0): supplicant interface state: authenticating -> disconnected
<info>  [1662059914.7813] device (wlp3s0): supplicant interface state: disconnected -> scanning
wlp3s0: SME: Trying to authenticate with 62:5d:fb:ee:1f:e6 (SSID='mywifi' freq=2412 MHz)
wlp3s0: authenticate with 62:5d:fb:ee:1f:e6
<info>  [1662059915.2149] device (wlp3s0): supplicant interface state: scanning -> authenticating
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 1/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 2/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 3/3)
wlp3s0: authentication with 62:5d:fb:ee:1f:e6 timed out
wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="mywifi" auth_failures=1 duration=10 reason=CONN_FAILED
<info>  [1662059915.4288] device (wlp3s0): supplicant interface state: authenticating -> disconnected
<info>  [1662059920.4306] device (wlp3s0): supplicant interface state: disconnected -> scanning
wlp3s0: CTRL-EVENT-SSID-REENABLED id=0 ssid="mywifi"
wlp3s0: SME: Trying to authenticate with 62:5d:fb:ee:1f:e6 (SSID='mywifi' freq=2412 MHz)
wlp3s0: authenticate with 62:5d:fb:ee:1f:e6
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 1/3)
<info>  [1662059926.3244] device (wlp3s0): supplicant interface state: scanning -> authenticating
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 2/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 3/3)
wlp3s0: authentication with 62:5d:fb:ee:1f:e6 timed out
BSSID 62:5d:fb:ee:1f:e6 ignore list count incremented to 2, ignoring for 10 seconds
wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="mywifi" auth_failures=2 duration=20 reason=CONN_FAILED
<info>  [1662059926.5303] device (wlp3s0): supplicant interface state: authenticating -> disconnected
<warn>  [1662059936.0460] device (wlp3s0): Activation: (wifi) association took too long, failing activation
<info>  [1662059936.0461] device (wlp3s0): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
<warn>  [1662059936.0467] device (wlp3s0): Activation: failed for connection 'mywifi'
<info>  [1662059936.0470] device (wlp3s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
pam_unix(sudo:session): session closed for user root
<info>  [1662059936.5302] device (wlp3s0): supplicant interface state: disconnected -> inactive
<info>  [1662059936.5657] policy: auto-activating connection 'mywifi' (83488540-dead-42f8-8d1c-1ac07d7baed8)
<info>  [1662059936.5666] device (wlp3s0): Activation: starting connection 'mywifi' (83488540-dead-42f8-8d1c-1ac07d7baed8)
<info>  [1662059936.5668] device (wlp3s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
<info>  [1662059936.5674] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
<info>  [1662059936.5679] device (wlp3s0): Activation: (wifi) access point 'mywifi' has security, but secrets are required.
<info>  [1662059936.5679] device (wlp3s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
<info>  [1662059936.5698] device (wlp3s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
<info>  [1662059936.5703] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
<info>  [1662059936.5707] device (wlp3s0): Activation: (wifi) connection 'mywifi' has security, and secrets exist.  No new secrets needed.
<info>  [1662059936.5708] Config: added 'ssid' value 'mywifi'
<info>  [1662059936.5708] Config: added 'scan_ssid' value '1'
<info>  [1662059936.5708] Config: added 'bgscan' value 'simple:30:-70:86400'
<info>  [1662059936.5709] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK'
<info>  [1662059936.5709] Config: added 'auth_alg' value 'OPEN'
<info>  [1662059936.5709] Config: added 'psk' value '<hidden>'
wlp3s0: SME: Trying to authenticate with 62:5d:fb:ee:1f:e6 (SSID='mywifi' freq=2412 MHz)
wlp3s0: authenticate with 62:5d:fb:ee:1f:e6
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 1/3)
<info>  [1662059936.6021] device (wlp3s0): supplicant interface state: inactive -> authenticating
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 2/3)
wlp3s0: send auth to 62:5d:fb:ee:1f:e6 (try 3/3)
wlp3s0: authentication with 62:5d:fb:ee:1f:e6 timed out
wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="mywifi" auth_failures=1 duration=10 reason=CONN_FAILED
<info>  [1662059936.7958] device (wlp3s0): supplicant interface state: authenticating -> disconnected
<info>  [1662059946.7986] device (wlp3s0): supplicant interface state: disconnected -> scanning
```

---

### Post by chili555 on 2022-09-02
> nmcli device wifi connect "mywifi" password "12345678"Is the result the same with the particuars *not* enclosed in quotes; e.g.:

```
nmcli device wifi connect mywifi password 12345678
```

---

### Post by marmalade57534 on 2022-09-04
> **chili555 said:**
> Is the result the same with the particuars *not* enclosed in quotes; e.g.:

```
nmcli device wifi connect mywifi password 12345678
```

Yes. I've tried the same commands with and without quotes. No difference.

---

### Post by marmalade57534 on 2022-09-05
@chili555 do you know of any alternative to Network manager that I should try switching to. Maybe that's what causing the issue?

---

### Post by chili555 on 2022-09-05
> **marmalade57534 said:**
> @chili555 do you know of any alternative to Network manager that I should try switching to. Maybe that's what causing the issue?I am unaware of any better performing alternative.

May I ask why you are using nmcli? Aren't you able to click the Network Manager icon at the upper right, see your network, click on it, supply the password and connect?

Here are some troubleshooting steps that you may consider: [https://askubuntu.com/questions/1364239/tp-link-usb-wireless-adapter-keep-losing-data-every-several-minutes-without-disc/1364295#1364295](https://askubuntu.com/questions/1364239/tp-link-usb-wireless-adapter-keep-losing-data-every-several-minutes-without-disc/1364295#1364295)

---

### Post by marmalade57534 on 2022-09-06
> [COLOR=#000000]Here are some troubleshooting steps that you may consider: [/COLOR]https://askubuntu.com/questions/1364239/tp-link-usb-wireless-adapter-keep-losing-data-every-several-minutes-without-disc/1364295#1364295

Yeah that solved the problem. Thanks a lot chilli! I went through a lot of stack and reddit posts and tried countless solutions but all in vein.

I don't know how you got this but it finally did the trick for me. :)
```
[FONT=var(--ff-mono)]sudo iw reg set ${REGION_CODE- example: IS}[/FONT][/COLOR]
``` 

> [COLOR=#000000]May I ask why you are using nmcli? [/COLOR][COLOR=#000000]Aren't you able to click the Network Manager icon at the upper right, see your network, click on it, supply the password and connect?[/COLOR]

[COLOR=#000000]Simply to get some error message. The GUI wouldn't connect but also won't give me any error message.


Thanks again and hope you have a cheerfuller and wonderful day[/COLOR][CENTER][COLOR=#000000][FONT=arial](&#12389; &#9685;&#8255;&#9685; )&#12389;[/FONT][/COLOR][/CENTER]
[COLOR=#000000]
[/COLOR][COLOR=#000000]


[/COLOR]

---

