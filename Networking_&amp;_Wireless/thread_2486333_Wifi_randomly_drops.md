---
title: "Wifi randomly drops"
date: 2023-04-26
forum: Networking &amp; Wireless
---

### Post by coley9225 on 2023-04-26
Hello again friends. Until about 3 months ago, my system ran without any issues(that I didn't cause), but now the wifi just randomly drops. It did it again at 4:50am this morning. Until now, the 'fix' was to reboot the computer. This morning I looked at the logs and saw this:
```
Apr 26 04:50:29 coleys-home NetworkManager[754]: <info>  [1682499029.8606] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> inactiveApr 26 04:50:29 coleys-home NetworkManager[754]: <info>  [1682499029.8605] device (wlp3s0): supplicant interface state: disconnected -> inactive
Apr 26 04:50:22 coleys-home systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6845] device (wlp3s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:18 coleys-home NetworkManager[754]: <warn>  [1682499018.6825] device (wlp3s0): Activation: failed for connection 'PrettyFlyForAWIFI'
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6800] manager: NetworkManager state is now DISCONNECTED
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6767] device (wlp3s0): state change: need-auth -> failed (reason 'no-secrets', sys-iface-state: 'managed')
Apr 26 04:50:18 coleys-home NetworkManager[754]: <warn>  [1682499018.6766] device (wlp3s0): no secrets: No agents were available for this request.
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6726] device (p2p-dev-wlp3s0): supplicant management interface state: 4way_handshake -> disconnected
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6717] device (wlp3s0): state change: config -> need-auth (reason 'supplicant-disconnect', sys-iface-state: 'managed')
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6715] device (wlp3s0): Activation: (wifi) disconnected during association, asking for new key
Apr 26 04:50:18 coleys-home NetworkManager[754]: <info>  [1682499018.6712] device (wlp3s0): supplicant interface state: 4way_handshake -> disconnected
Apr 26 04:50:18 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 26 04:50:18 coleys-home wpa_supplicant[804]: BSSID 74:37:5f:70:ee:56 ignore list count incremented to 2, ignoring for 10 seconds
Apr 26 04:50:18 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="PrettyFlyForAWIFI" auth_failures=1 duration=10 reason=WRONG_KEY
Apr 26 04:50:18 coleys-home wpa_supplicant[804]: wlp3s0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Apr 26 04:50:18 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=74:37:5f:70:ee:56 reason=15
Apr 26 04:50:18 coleys-home kernel: wlp3s0: deauthenticated from 74:37:5f:70:ee:56 (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
Apr 26 04:50:16 coleys-home kernel: wlp3s0: Limiting TX power to 27 (30 - 3) dBm as advertised by 74:37:5f:70:ee:56
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.5425] device (p2p-dev-wlp3s0): supplicant management interface state: associated -> 4way_handshake
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.5424] device (wlp3s0): supplicant interface state: associated -> 4way_handshake
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.5344] device (p2p-dev-wlp3s0): supplicant management interface state: associating -> associated
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.5343] device (wlp3s0): supplicant interface state: associating -> associated
Apr 26 04:50:15 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=US
Apr 26 04:50:15 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Apr 26 04:50:15 coleys-home wpa_supplicant[804]: wlp3s0: Associated with 74:37:5f:70:ee:56
Apr 26 04:50:15 coleys-home kernel: wlp3s0: associated
Apr 26 04:50:15 coleys-home kernel: wlp3s0: RX AssocResp from 74:37:5f:70:ee:56 (capab=0x1511 status=0 aid=3)
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.5147] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> associating
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.5146] device (wlp3s0): supplicant interface state: disconnected -> associating
Apr 26 04:50:15 coleys-home kernel: wlp3s0: associate with 74:37:5f:70:ee:56 (try 1/3)
Apr 26 04:50:15 coleys-home kernel: wlp3s0: authenticated
Apr 26 04:50:15 coleys-home wpa_supplicant[804]: wlp3s0: Trying to associate with 74:37:5f:70:ee:56 (SSID='PrettyFlyForAWIFI' freq=5785 MHz)
Apr 26 04:50:15 coleys-home kernel: wlp3s0: send auth to 74:37:5f:70:ee:56 (try 1/3)
Apr 26 04:50:15 coleys-home kernel: wlp3s0: authenticate with 74:37:5f:70:ee:56
Apr 26 04:50:15 coleys-home wpa_supplicant[804]: wlp3s0: SME: Trying to authenticate with 74:37:5f:70:ee:56 (SSID='PrettyFlyForAWIFI' freq=5785 MHz)
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4727] Config: added 'psk' value '<hidden>'
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4726] Config: added 'auth_alg' value 'OPEN'
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4726] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4725] Config: added 'bgscan' value 'simple:30:-70:86400'
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4725] Config: added 'scan_ssid' value '1'
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4724] Config: added 'ssid' value 'PrettyFlyForAWIFI'
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4723] device (wlp3s0): Activation: (wifi) connection 'PrettyFlyForAWIFI' has security, and secrets exist.  No new secre>
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4716] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4706] device (wlp3s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4612] device (wlp3s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4608] device (wlp3s0): Activation: (wifi) access point 'PrettyFlyForAWIFI' has security, but secrets are required.
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4597] device (wlp3s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4589] manager: NetworkManager state is now CONNECTING
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4579] device (wlp3s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4554] device (wlp3s0): Activation: starting connection 'PrettyFlyForAWIFI' (c4daf75a-271a-4406-b616-a924dd6b62c9)
Apr 26 04:50:15 coleys-home NetworkManager[754]: <info>  [1682499015.4506] policy: auto-activating connection 'PrettyFlyForAWIFI' (c4daf75a-271a-4406-b616-a924dd6b62c9)
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.3056] device (p2p-dev-wlp3s0): supplicant management interface state: 4way_handshake -> disconnected
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.3055] device (wlp3s0): supplicant interface state: 4way_handshake -> disconnected
Apr 26 04:50:12 coleys-home dbus-daemon[753]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 26 04:50:12 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 26 04:50:12 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-DSCP-POLICY clear_all
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Apr 26 04:50:12 coleys-home systemd[1]: Started Network Manager Script Dispatcher Service.
Apr 26 04:50:12 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="PrettyFlyForAWIFI" auth_failures=1 duration=10 reason=WRONG_KEY
Apr 26 04:50:12 coleys-home wpa_supplicant[804]: wlp3s0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Apr 26 04:50:12 coleys-home systemd-resolved[692]: wlp3s0: Bus client reset DNS server list.
Apr 26 04:50:12 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=74:37:5f:70:ee:56 reason=3 locally_generated=1
Apr 26 04:50:12 coleys-home systemd-resolved[692]: wlp3s0: Bus client set default route setting: no
Apr 26 04:50:12 coleys-home systemd-resolved[692]: wlp3s0: Bus client reset search domain list.
Apr 26 04:50:12 coleys-home systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.1.125.
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.2707] dhcp6 (wlp3s0): canceled DHCP transaction
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Withdrawing address record for 192.168.1.125 on wlp3s0.
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.2703] dhcp4 (wlp3s0): canceled DHCP transaction
Apr 26 04:50:12 coleys-home kernel: wlp3s0: deauthenticating from 74:37:5f:70:ee:56 by local choice (Reason: 3=DEAUTH_LEAVING)
Apr 26 04:50:12 coleys-home dbus-daemon[753]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by '>
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::d9a7:dcf8:ca5e:78d8.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Withdrawing address record for fe80::d9a7:dcf8:ca5e:78d8 on wlp3s0.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Registering new address record for fe80::d9a7:dcf8:ca5e:78d8 on wlp3s0.*.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::d9a7:dcf8:ca5e:78d8.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address 2603:9000:de00:50b5:c9bf:5b69:439:f930.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Withdrawing address record for 2603:9000:de00:50b5:c9bf:5b69:439:f930 on wlp3s0.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Withdrawing address record for 2603:9000:de00:50b5::13a2 on wlp3s0.
Apr 26 04:50:12 coleys-home avahi-daemon[749]: Withdrawing address record for 2603:9000:de00:50b5:4c93:7810:d09c:5bd6 on wlp3s0.
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.2500] device (wlp3s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Apr 26 04:50:12 coleys-home NetworkManager[754]: <warn>  [1682499012.2443] device (wlp3s0): Activation: failed for connection 'PrettyFlyForAWIFI'
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.2408] manager: NetworkManager state is now DISCONNECTED
Apr 26 04:50:12 coleys-home NetworkManager[754]: <info>  [1682499012.2334] device (wlp3s0): state change: activated -> failed (reason 'supplicant-timeout', sys-iface-state: 'managed')
Apr 26 04:50:12 coleys-home NetworkManager[754]: <warn>  [1682499012.2330] device (wlp3s0): link timed out.
Apr 26 04:50:04 coleys-home kernel: wlp3s0: Limiting TX power to 27 (30 - 3) dBm as advertised by 74:37:5f:70:ee:56
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0565] dhcp6 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0561] dhcp6 (wlp3s0): state changed no lease
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0555] dhcp6 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0551] dhcp6 (wlp3s0): canceled DHCP transaction
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0547] device (wlp3s0): ip:dhcp6: restarting
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0534] dhcp4 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0531] dhcp4 (wlp3s0): state changed no lease
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0530] dhcp4 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0530] dhcp4 (wlp3s0): canceled DHCP transaction
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0520] device (wlp3s0): ip:dhcp4: restarting
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0508] device (p2p-dev-wlp3s0): supplicant management interface state: associating -> 4way_handshake
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0502] device (wlp3s0): supplicant interface state: associating -> 4way_handshake
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0453] device (p2p-dev-wlp3s0): supplicant management interface state: authenticating -> associating
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0447] device (wlp3s0): supplicant interface state: authenticating -> associating
Apr 26 04:50:04 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=US
Apr 26 04:50:04 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0312] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> authenticating
Apr 26 04:50:04 coleys-home wpa_supplicant[804]: wlp3s0: Associated with 74:37:5f:70:ee:56
Apr 26 04:50:04 coleys-home kernel: wlp3s0: associated
Apr 26 04:50:04 coleys-home kernel: wlp3s0: RX AssocResp from 74:37:5f:70:ee:56 (capab=0x1511 status=0 aid=3)
Apr 26 04:50:04 coleys-home kernel: wlp3s0: associate with 74:37:5f:70:ee:56 (try 1/3)
Apr 26 04:50:04 coleys-home NetworkManager[754]: <info>  [1682499004.0303] device (wlp3s0): supplicant interface state: scanning -> authenticating
Apr 26 04:50:04 coleys-home wpa_supplicant[804]: wlp3s0: Trying to associate with 74:37:5f:70:ee:56 (SSID='PrettyFlyForAWIFI' freq=5785 MHz)
Apr 26 04:50:04 coleys-home kernel: wlp3s0: authenticated
Apr 26 04:50:04 coleys-home kernel: wlp3s0: send auth to 74:37:5f:70:ee:56 (try 1/3)
Apr 26 04:50:04 coleys-home kernel: wlp3s0: authenticate with 74:37:5f:70:ee:56
Apr 26 04:50:04 coleys-home wpa_supplicant[804]: wlp3s0: SME: Trying to authenticate with 74:37:5f:70:ee:56 (SSID='PrettyFlyForAWIFI' freq=5785 MHz)
Apr 26 04:50:00 coleys-home NetworkManager[754]: <info>  [1682499000.9110] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> scanning
Apr 26 04:50:00 coleys-home NetworkManager[754]: <info>  [1682499000.9109] device (wlp3s0): supplicant interface state: disconnected -> scanning
Apr 26 04:50:00 coleys-home NetworkManager[754]: <info>  [1682499000.4117] device (p2p-dev-wlp3s0): supplicant management interface state: authenticating -> disconnected
Apr 26 04:50:00 coleys-home NetworkManager[754]: <info>  [1682499000.4108] device (wlp3s0): supplicant interface state: authenticating -> disconnected
Apr 26 04:50:00 coleys-home kernel: wlp3s0: authentication with 74:37:5f:70:ee:57 timed out
Apr 26 04:50:00 coleys-home kernel: wlp3s0: send auth to 74:37:5f:70:ee:57 (try 3/3)
Apr 26 04:50:00 coleys-home kernel: wlp3s0: send auth to 74:37:5f:70:ee:57 (try 2/3)
Apr 26 04:50:00 coleys-home NetworkManager[754]: <info>  [1682499000.1029] device (p2p-dev-wlp3s0): supplicant management interface state: scanning -> authenticating
Apr 26 04:50:00 coleys-home NetworkManager[754]: <info>  [1682499000.1013] device (wlp3s0): supplicant interface state: scanning -> authenticating
Apr 26 04:50:00 coleys-home kernel: wlp3s0: send auth to 74:37:5f:70:ee:57 (try 1/3)
Apr 26 04:50:00 coleys-home kernel: wlp3s0: authenticate with 74:37:5f:70:ee:57
Apr 26 04:50:00 coleys-home wpa_supplicant[804]: wlp3s0: SME: Trying to authenticate with 74:37:5f:70:ee:57 (SSID='PrettyFlyForAWIFI' freq=2437 MHz)
Apr 26 04:49:56 coleys-home NetworkManager[754]: <info>  [1682498996.9453] device (p2p-dev-wlp3s0): supplicant management interface state: disconnected -> scanning
Apr 26 04:49:56 coleys-home NetworkManager[754]: <info>  [1682498996.9451] device (wlp3s0): supplicant interface state: disconnected -> scanning
Apr 26 04:49:56 coleys-home NetworkManager[754]: <info>  [1682498996.8708] device (p2p-dev-wlp3s0): supplicant management interface state: completed -> disconnected
Apr 26 04:49:56 coleys-home NetworkManager[754]: <info>  [1682498996.8707] device (wlp3s0): supplicant interface state: completed -> disconnected
Apr 26 04:49:56 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 26 04:49:56 coleys-home wpa_supplicant[804]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=74:37:5f:70:ee:56 reason=4 locally_generated=1
Apr 26 04:49:56 coleys-home kernel: wlp3s0: Connection to AP 74:37:5f:70:ee:56 lost
Apr 26 04:49:56 coleys-home kernel: rtlwifi: AP off, try to reconnect now




```

Rather that reboot, I launched 2 more terminals, 1 for running commands and 1 for 'man nmcli'.
Aftr much reading, and some trial and error, I was able to restore wifi with this command:
```
nmcli connection up c4daf75a-271a-4406-b616-a924dd6b62c9
```

Talk about timing. My wifi dropped as I was typing this.
What I would like to know, is there a way to determine if this is a software issue or is my wifi card about to fail totally.

If more info is needed, please ask. I am not affraid of running commands and posting output here to help sort out the root cause of my troubles.

Thanks in advance.

---

### Post by chili555 on 2023-04-26
We see this:

```
wlp3s0: SME: Trying to authenticate with 74:37:5f:70:ee:[COLOR="#FF0000"]57[/COLOR] 
```

And this:

```
wlp3s0: Trying to associate with 74:37:5f:70:ee:[COLOR="#FF0000"]56[/COLOR]
```

It appears that you have two SSIDs with the same name and that your device is roaming among them looking for a better connection. Sounds like my old girlfriend!

I suspect that they are the 2.4 gHz and 5 gHz segments of your router. I suggest that you rename them to differentiate them. I suggest router2.4 and router5 or something similar. After all the changes I recommend, see which segment offers the best speed and stick to it.

Reboot the router and tell us if there is any improvement.

---

### Post by coley9225 on 2023-04-26
chili555, thanks for the rapid response.

I got to thinking about it, and remembered we recently got a new modem/router. My son set up the old one as [name]5g and [name]2g. With the new one he only set [name], no 2g or 5g. After some more4 digging, i ran this:

```
charles:$:nmcli -p -m multil;ine -f all con showwlp3s0: connected to PrettyFlyForAWIFI
        "Realtek RTL8821AE"
        wifi (rtl8821ae), 60:14:B3:B4:49:BD, hw, mtu 1500
        ip4 default, ip6 default
        inet4 192.168.1.125/24
        route4 192.168.1.0/24 metric 600
        route4 default via 192.168.1.1 metric 600
        inet6 2603:9000:de00:50b5:a9fe:b81b:fc7b:89c4/64
        inet6 2603:9000:de00:50b5::13a2/128
        inet6 2603:9000:de00:50b5:c9bf:5b69:439:f930/64
        inet6 fe80::d9a7:dcf8:ca5e:78d8/64
        route6 fe80::/64 metric 1024
        route6 2603:9000:de00:50b5::/64 via fe80::7637:5fff:fe70:ee54 metric 600
        route6 default via fe80::7637:5fff:fe70:ee54 metric 600
        route6 2603:9000:de00:50b5::13a2/128 metric 600


p2p-dev-wlp3s0: disconnected
        "p2p-dev-wlp3s0"
        wifi-p2p, hw


enp2s0: unavailable
        "Realtek RTL810xE"
        ethernet (r8169), 54:E1:AD:99:E9:DF, hw, mtu 1500


lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536


DNS configuration:
        servers: 192.168.1.1
        domains: lan
        interface: wlp3s0


        servers: 2603:9000:de00:50b5::1
        domains: example.com
        interface: wlp3s0



```

If I'm not mistaken, this shows I only have the 1 connection setup, which is the only ssid attached to the router. So I decided to scan:

```

charles:$:nmcli device wifiIN-USE  BSSID              SSID                           MODE   CHAN  RATE        SIGNAL  BARS  SECURITY    
        74:37:5F:70:EE:57  PrettyFlyForAWIFI              Infra  6     260 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2        
        AE:AE:19:CA:F0:6A  --                             Infra  6     65 Mbit/s   100     &#9602;&#9604;&#9606;&#9608;  WPA2        
*       74:37:5F:70:EE:56  PrettyFlyForAWIFI              Infra  157   540 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2        
        F0:81:75:E2:B6:BE  MySpectrumWiFib8-2G            Infra  11    195 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2        
        74:37:5F:07:76:AF  SpectrumSetup-AD               Infra  6     260 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2        
        F0:81:75:E2:B6:BF  MySpectrumWiFib8-5G            Infra  157   540 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2        
        1E:12:B0:1B:6A:B8  DIRECT-EA-FireTV_64b5          Infra  157   130 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2        
        56:37:5F:07:76:AE  Spectrum Mobile                Infra  157   540 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X 
        F4:05:95:E6:96:10  MommyDaddyBaby=3               Infra  1     540 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2        
        EC:8E:B5:AA:6D:AE  DIRECT-AD-HP ENVY 5660 series  Infra  6     65 Mbit/s   60      &#9602;&#9604;&#9606;_  WPA2        
        74:37:5F:07:76:AE  SpectrumSetup-AD               Infra  157   540 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2        
        88:DE:7C:EE:26:18  SpectrumSetup-1A               Infra  1     260 Mbit/s  55      &#9602;&#9604;__  WPA2        
        1A:F7:81:42:A7:E0  SpectrumSetup-DE               Infra  44    540 Mbit/s  47      &#9602;&#9604;__  WPA2        
        7A:F7:81:42:A7:E0  Spectrum Mobile                Infra  44    540 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X 
        88:DE:7C:EE:26:19  SpectrumSetup-1A               Infra  157   540 Mbit/s  45      &#9602;&#9604;__  WPA2        
        5C:FA:25:D6:FA:FD  SpectrumSetup-F7               Infra  1     540 Mbit/s  44      &#9602;&#9604;__  WPA2        
        34:53:D2:3D:ED:66  FBI CHANNEL 4976               Infra  1     195 Mbit/s  44      &#9602;&#9604;__  WPA2        
        6A:DE:7C:EE:26:19  Spectrum Mobile                Infra  157   540 Mbit/s  44      &#9602;&#9604;__  WPA2 802.1X 
        3E:94:ED:52:3B:7B  Our House                      Infra  3     260 Mbit/s  40      &#9602;&#9604;__  WPA2        
        FC:12:63:25:92:15  SpectrumSetup-17               Infra  6     260 Mbit/s  40      &#9602;&#9604;__  WPA2        
        4C:19:5D:36:1C:AD  SpectrumSetup-A7               Infra  11    540 Mbit/s  40      &#9602;&#9604;__  WPA2        
        4C:19:5D:20:41:F2  God Bless This Home            Infra  11    540 Mbit/s  40      &#9602;&#9604;__  WPA2        
        38:94:ED:52:40:4F  --                             Infra  3     260 Mbit/s  37      &#9602;&#9604;__  WPA2        
        7C:78:B2:AB:2C:6B  wzap32146275                   Infra  6     65 Mbit/s   37      &#9602;&#9604;__  WPA2        
        A4:97:33:76:F9:69  SpectrumSetup-6B               Infra  6     260 Mbit/s  35      &#9602;&#9604;__  WPA2        
        70:89:76:26:77:77  Tzumi-SL-7776                  Infra  6     65 Mbit/s   30      &#9602;___  --          
charles:$:



```
This shows 2 listings for our router, with only 1 connected( the 3rd entry).

I believe you may be on the right track with the network manager being 'confused', and this is in fact a software issue.

Now the biggie. How can I make this issue go away without changing the router back to 2 different ssid names, like it was before. My other concern is that it just drops. Already running, working fine, then BOOM, no wifi. That's why I was wondering if this is hardware issue, or does the network manager randomly recheck available connections. As I said, at reboot, or running the mentioned command, it connects without issue.
If further info needed, let me know.

---

### Post by chili555 on 2023-04-26
I believe the dropping is precisely because Network Manager is roaming between the two SSIDs. 

 > 74:37:5F:70:EE:56  PrettyFlyForAWIFI  This is the 5 gHz segment and clearly the faster. I suggest that you try binding that exact MAC address like this in Network Manager: [https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112](https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112)

---

### Post by coley9225 on 2023-04-27
Thanks for that info chili555. I make the suggested adjustments, and now it's wait and see. The drops were random, sometimes after a couple hours, somtimes a couple of days. I'll reply again if it goes down, or if it works well for a couple of days, I'll come back and mark as solved. I greatly appreciate the help.

---

