---
title: "Ubutnu 14.04 Having issue in wifi connection"
date: 2015-03-05
forum: Networking &amp; Wireless
---

### Post by ketanbparmar on 2015-03-05
Hardware : Dell Latitude E 5440

 ```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
```


 ```
sudo rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


System Log

```
Mar  5 11:36:33 administrator-Latitude-E5440 avahi-daemon[782]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::1acf:5eff:fe20:320b.
Mar  5 11:36:33 administrator-Latitude-E5440 avahi-daemon[782]: Interface wlan0.IPv6 no longer relevant for mDNS.
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: All rights reserved.
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: 
Mar  5 11:36:33 administrator-Latitude-E5440 kernel: [ 5663.088841] audit: type=1400 audit(1425535593.200:93): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7315 comm="nm-dhcp-client." lport=60802 family="inet" sock_type="dgram" protocol=17
Mar  5 11:36:33 administrator-Latitude-E5440 kernel: [ 5663.088851] audit: type=1400 audit(1425535593.200:94): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7315 comm="nm-dhcp-client." lport=51140 family="inet6" sock_type="dgram" protocol=17
Mar  5 11:36:33 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: Listening on LPF/wlan0/18:cf:5e:20:32:0b
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: Sending on   LPF/wlan0/18:cf:5e:20:32:0b
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: Sending on   Socket/fallback
Mar  5 11:36:33 administrator-Latitude-E5440 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x3464b24f)
Mar  5 11:36:34 administrator-Latitude-E5440 avahi-daemon[782]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::1acf:5eff:fe20:320b.
Mar  5 11:36:34 administrator-Latitude-E5440 avahi-daemon[782]: New relevant interface wlan0.IPv6 for mDNS.
Mar  5 11:36:34 administrator-Latitude-E5440 avahi-daemon[782]: Registering new address record for fe80::1acf:5eff:fe20:320b on wlan0.*.
Mar  5 11:36:36 administrator-Latitude-E5440 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x3464b24f)
Mar  5 11:36:42 administrator-Latitude-E5440 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x3464b24f)
Mar  5 11:36:49 administrator-Latitude-E5440 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x3464b24f)
Mar  5 11:36:53 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar  5 11:36:53 administrator-Latitude-E5440 NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar  5 11:36:53 administrator-Latitude-E5440 NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar  5 11:36:53 administrator-Latitude-E5440 NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar  5 11:36:59 administrator-Latitude-E5440 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x3464b24f)
Mar  5 11:37:10 administrator-Latitude-E5440 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x3464b24f)
Mar  5 11:37:16 administrator-Latitude-E5440 avahi-daemon[782]: Invalid response packet from host fe80::ac0f:ddfb:99be:67b0.
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <warn> (wlan0): DHCPv4 request timed out.
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 7312
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <warn> Activation (wlan0) failed for connection 'Wi-Fi connection 1'
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.798871] wlan0: deauthenticating from 2c:e6:cc:8d:6c:a8 by local choice (Reason: 3=DEAUTH_LEAVING)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.808942] cfg80211: Calling CRDA to update world regulatory domain
Mar  5 11:37:18 administrator-Latitude-E5440 wpa_supplicant[6976]: wlan0: CTRL-EVENT-DISCONNECTED bssid=2c:e6:cc:8d:6c:a8 reason=3 locally_generated=1
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <warn> Connection disconnected (reason -3)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811938] cfg80211: World regulatory domain updated:
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811943] cfg80211:  DFS Master region: unset
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811945] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811948] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811950] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811952] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811954] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar  5 11:37:18 administrator-Latitude-E5440 kernel: [ 5708.811956] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar  5 11:37:18 administrator-Latitude-E5440 wpa_supplicant[6976]: wlan0: CTRL-EVENT-SCAN-STARTED 
Mar  5 11:37:18 administrator-Latitude-E5440 NetworkManager[862]: <warn> Connection disconnected (reason -3)
Mar  5 11:37:42 administrator-Latitude-E5440 avahi-daemon[782]: Invalid response packet from host 10.12.41.96.
Mar  5 11:38:55 administrator-Latitude-E5440 avahi-daemon[782]: Invalid response packet from host fe80::ac0f:ddfb:99be:67b0.
Mar  5 11:39:21 administrator-Latitude-E5440 avahi-daemon[782]: Invalid response packet from host 10.12.41.96.
Mar  5 11:40:34 administrator-Latitude-E5440 avahi-daemon[782]: Invalid response packet from host fe80::ac0f:ddfb:99be:67b0.
Mar  5 11:41:00 administrator-Latitude-E5440 avahi-daemon[782]: Invalid response packet from host 10.12.41.96.
```


Can anyone help to solve my wifi issue ?

---

