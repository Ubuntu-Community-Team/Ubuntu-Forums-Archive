---
title: "Intel Wireless 8260 (rev 3a) connection issues, Ubuntu 16.04"
date: 2018-05-24
forum: Networking &amp; Wireless
---

### Post by quadrupol on 2018-05-24
I have experienced issues with my wifi on my Thinkpad L560 in the last  couple of weeks: Sometimes I have no internet connection with the  notebook (the icon at the staus bar says all is ok). Disable and enable the wifi with the dropdown-menu of the wifi icon leads to a new connection, but the problem occurs later again. As I am new to the linux world, I have no idea how to solve the problem, so any suggestions would be very nice. I executed the network-script twice, one time without the issue and one time at the moment the problem occured.

The network-script: [http://paste.ubuntu.com/p/WX6ptTSsxF](http://paste.ubuntu.com/p/WX6ptTSsxF)
The network-script (executed at a time the connection dropped): [http://paste.ubuntu.com/p/N96VytgwWy](http://paste.ubuntu.com/p/N96VytgwWy)

Thank you for your time!

---

### Post by chili555 on 2018-05-24
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I suggest that you disable power saving in Network Manager. From the terminal:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Reboot the computer and tell us if there is any improvement.

---

### Post by quadrupol on 2018-05-24
First: Thank you for your detailed instructions!

Unfortunately, the problem persists without improvement.

---

### Post by chili555 on 2018-05-24
Your pastes simply show a perfect connection for the wireless, not a drop. After the connection drops and you reconnect, please run and paste:```
cat /var/log/syslog | grep -e etwork -e wlp
```Please show us the last 30 or so lines.

---

### Post by quadrupol on 2018-05-24
This is the output:
```
May 24 18:44:49 schlepptop kernel: [ 5000.339388] wlp2s0: deauthenticating from c0:25:e9:5d:5b:61 by local choice (Reason: 3=DEAUTH_LEAVING)
May 24 18:44:49 schlepptop wpa_supplicant[1055]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=c0:25:e9:5d:5b:61 reason=3 locally_generated=1
May 24 18:44:49 schlepptop kernel: [ 5000.354034] wlp2s0: failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware (-22)
May 24 18:44:49 schlepptop dhclient[3651]: receive_packet failed on wlp2s0: Network is down
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.7290] manager: WiFi hardware radio set disabled
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.7292] device (wlp2s0): state change: activated -> unavailable (reason 'none') [100 20 0]
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.7684] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 3651
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.7684] dhcp4 (wlp2s0): state changed bound -> done
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.7692] dhcp6 (wlp2s0): canceled DHCP transaction
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.7708] dns-mgr: Writing DNS information to /sbin/resolvconf
May 24 18:44:49 schlepptop dnsmasq[1326]: Benutze Namensserver fd00::3a10:d5ff:fe0e:e218#53(via wlp2s0)
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.8086] dns-mgr: Writing DNS information to /sbin/resolvconf
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.8190] manager: NetworkManager state is now CONNECTED_LOCAL
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.8195] manager: NetworkManager state is now DISCONNECTED
May 24 18:44:49 schlepptop wpa_supplicant[1055]: nl80211: deinit ifname=p2p-dev-wlp2s0 disabled_11b_rates=0
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.8321] audit: op="radio-control" arg="wireless-enabled:0" pid=1825 uid=1000 result="success"
May 24 18:44:49 schlepptop NetworkManager[903]: <info>  [1527180289.8326] manager: WiFi now disabled by radio killswitch
May 24 18:44:49 schlepptop systemd[1]: Starting Network Manager Script Dispatcher Service...
May 24 18:44:49 schlepptop systemd[1]: Started Network Manager Script Dispatcher Service.
May 24 18:44:49 schlepptop nm-dispatcher: req:1 'down' [wlp2s0]: new request (1 scripts)
May 24 18:44:49 schlepptop nm-dispatcher: req:1 'down' [wlp2s0]: start running ordered scripts...
May 24 18:44:49 schlepptop wpa_supplicant[1055]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0
May 24 18:44:52 schlepptop NetworkManager[903]: <info>  [1527180292.9660] manager: WiFi hardware radio set enabled
May 24 18:44:53 schlepptop kernel: [ 5003.887414] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
May 24 18:44:53 schlepptop NetworkManager[903]: <info>  [1527180293.2412] audit: op="radio-control" arg="wireless-enabled:1" pid=1825 uid=1000 result="success"
May 24 18:44:53 schlepptop NetworkManager[903]: <info>  [1527180293.2425] manager: WiFi now enabled by radio killswitch
May 24 18:44:53 schlepptop wpa_supplicant[1055]: Could not read interface p2p-dev-wlp2s0 flags: No such device
May 24 18:44:53 schlepptop NetworkManager[903]: <info>  [1527180293.3058] device (wlp2s0): supplicant interface state: starting -> ready
May 24 18:44:53 schlepptop NetworkManager[903]: <info>  [1527180293.3059] device (wlp2s0): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 24 18:44:53 schlepptop kernel: [ 5003.953981] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6748] device (wlp2s0): supplicant interface state: ready -> inactive
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6845] policy: auto-activating connection 'TP-LINK_5B62_5G'
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6856] device (wlp2s0): Activation: starting connection 'TP-LINK_5B62_5G' (a88df454-6e63-440e-a9ab-e106f53f803d)
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6857] device (wlp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6859] manager: NetworkManager state is now CONNECTING
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6864] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6866] device (wlp2s0): Activation: (wifi) access point 'TP-LINK_5B62_5G' has security, but secrets are required.
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6867] device (wlp2s0): state change: config -> need-auth (reason 'none') [50 60 0]
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6900] device (wlp2s0): state change: need-auth -> prepare (reason 'none') [60 40 0]
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6904] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6907] device (wlp2s0): Activation: (wifi) connection 'TP-LINK_5B62_5G' has security, and secrets exist.  No new secrets needed.
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6910] Config: added 'ssid' value 'TP-LINK_5B62_5G'
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6910] Config: added 'scan_ssid' value '1'
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6911] Config: added 'key_mgmt' value 'WPA-PSK'
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6911] Config: added 'auth_alg' value 'OPEN'
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.6911] Config: added 'psk' value '<omitted>'
May 24 18:44:56 schlepptop NetworkManager[903]: <info>  [1527180296.7108] sup-iface[0x11a7ce0,wlp2s0]: config: set interface ap_scan to 1
May 24 18:44:57 schlepptop wpa_supplicant[1055]: wlp2s0: SME: Trying to authenticate with c0:25:e9:5d:5b:61 (SSID='TP-LINK_5B62_5G' freq=5200 MHz)
May 24 18:44:57 schlepptop kernel: [ 5008.472620] wlp2s0: authenticate with c0:25:e9:5d:5b:61
May 24 18:44:57 schlepptop kernel: [ 5008.483986] wlp2s0: send auth to c0:25:e9:5d:5b:61 (try 1/3)
May 24 18:44:57 schlepptop kernel: [ 5008.489977] wlp2s0: authenticated
May 24 18:44:57 schlepptop wpa_supplicant[1055]: wlp2s0: Trying to associate with c0:25:e9:5d:5b:61 (SSID='TP-LINK_5B62_5G' freq=5200 MHz)
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8425] device (wlp2s0): supplicant interface state: inactive -> authenticating
May 24 18:44:57 schlepptop kernel: [ 5008.495884] wlp2s0: associate with c0:25:e9:5d:5b:61 (try 1/3)
May 24 18:44:57 schlepptop kernel: [ 5008.498063] wlp2s0: RX AssocResp from c0:25:e9:5d:5b:61 (capab=0x411 status=0 aid=1)
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8591] device (wlp2s0): supplicant interface state: authenticating -> associating
May 24 18:44:57 schlepptop kernel: [ 5008.510964] wlp2s0: associated
May 24 18:44:57 schlepptop kernel: [ 5008.511010] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
May 24 18:44:57 schlepptop wpa_supplicant[1055]: wlp2s0: Associated with c0:25:e9:5d:5b:61
May 24 18:44:57 schlepptop wpa_supplicant[1055]: wlp2s0: WPA: Key negotiation completed with c0:25:e9:5d:5b:61 [PTK=CCMP GTK=CCMP]
May 24 18:44:57 schlepptop wpa_supplicant[1055]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to c0:25:e9:5d:5b:61 completed [id=0 id_str=]
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8707] device (wlp2s0): supplicant interface state: associating -> completed
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8708] device (wlp2s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'TP-LINK_5B62_5G'.
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8709] device (wlp2s0): state change: config -> ip-config (reason 'none') [50 70 0]
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8713] dhcp4 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.8769] dhcp4 (wlp2s0): dhclient started with pid 4988
May 24 18:44:57 schlepptop dhclient[4988]: DHCPREQUEST of 192.168.178.45 on wlp2s0 to 255.255.255.255 port 67 (xid=0x3108314c)
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9145]   address 192.168.178.45
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9146]   plen 24 (255.255.255.0)
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9146]   gateway 192.168.178.1
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9146]   server identifier 192.168.178.1
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9146]   lease time 864000
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9146]   nameserver '192.168.178.1'
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9146]   domain name 'fritz.box'
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9147] dhcp4 (wlp2s0): state changed unknown -> bound
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9177] device (wlp2s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9190] device (wlp2s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9198] device (wlp2s0): state change: secondaries -> activated (reason 'none') [90 100 0]
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9203] manager: NetworkManager state is now CONNECTED_LOCAL
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9296] manager: NetworkManager state is now CONNECTED_GLOBAL
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9301] policy: set 'TP-LINK_5B62_5G' (wlp2s0) as default for IPv4 routing and DNS
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9303] dns-mgr: Writing DNS information to /sbin/resolvconf
May 24 18:44:57 schlepptop dnsmasq[1326]: Benutze Namensserver 192.168.178.1#53(via wlp2s0)
May 24 18:44:57 schlepptop NetworkManager[903]: <info>  [1527180297.9532] device (wlp2s0): Activation: successful, device activated.
May 24 18:44:57 schlepptop nm-dispatcher: req:2 'up' [wlp2s0]: new request (1 scripts)
May 24 18:44:57 schlepptop nm-dispatcher: req:2 'up' [wlp2s0]: start running ordered scripts...
May 24 18:44:57 schlepptop whoopsie[1259]: [18:44:57] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/8
May 24 18:44:57 schlepptop whoopsie[1259]: [18:44:57] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/8
May 24 18:44:57 schlepptop whoopsie[1259]: [18:44:57] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/8
May 24 18:44:59 schlepptop NetworkManager[903]: <info>  [1527180299.5733] dhcp6 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
May 24 18:44:59 schlepptop NetworkManager[903]: <info>  [1527180299.5786] dhcp6 (wlp2s0): dhclient started with pid 5099
May 24 18:44:59 schlepptop NetworkManager[903]: <info>  [1527180299.5836] dns-mgr: Writing DNS information to /sbin/resolvconf
May 24 18:44:59 schlepptop dnsmasq[1326]: Benutze Namensserver 192.168.178.1#53(via wlp2s0)
May 24 18:44:59 schlepptop dnsmasq[1326]: Benutze Namensserver fd00::3a10:d5ff:fe0e:e218#53(via wlp2s0)
May 24 18:45:00 schlepptop dhclient[5099]: XMT: Info-Request on wlp2s0, interval 1030ms.
May 24 18:45:00 schlepptop dhclient[5099]: RCV: Reply message on wlp2s0 from fe80::3a10:d5ff:fe0e:e218.
May 24 18:45:00 schlepptop NetworkManager[903]: <info>  [1527180300.2784]   nameserver 'fd00::3a10:d5ff:fe0e:e218'
May 24 18:45:00 schlepptop NetworkManager[903]: <info>  [1527180300.2785] dhcp6 (wlp2s0): state changed unknown -> bound
May 24 18:45:00 schlepptop NetworkManager[903]: <info>  [1527180300.2878] dhcp6 (wlp2s0): client pid 5099 exited with status 0
May 24 18:45:00 schlepptop NetworkManager[903]: <info>  [1527180300.2890] dhcp6 (wlp2s0): state changed bound -> done
May 24 18:45:00 schlepptop nm-dispatcher: req:3 'dhcp6-change' [wlp2s0]: new request (1 scripts)
May 24 18:45:00 schlepptop nm-dispatcher: req:3 'dhcp6-change' [wlp2s0]: start running ordered scripts...
```

At the same time (before I disabled wifi) I pinged a server:
```
PING 134.94.118.40 (134.94.118.40) 56(84) bytes of data.
From 192.168.178.45 icmp_seq=6 Destination Host Unreachable
From 192.168.178.45 icmp_seq=7 Destination Host Unreachable
From 192.168.178.45 icmp_seq=8 Destination Host Unreachable
From 192.168.178.45 icmp_seq=9 Destination Host Unreachable
From 192.168.178.45 icmp_seq=10 Destination Host Unreachable
From 192.168.178.45 icmp_seq=11 Destination Host Unreachable
^C
--- 134.94.118.40 ping statistics ---
12 packets transmitted, 0 received, +6 errors, 100% packet loss, time 11212ms
pipe 4


```

---

