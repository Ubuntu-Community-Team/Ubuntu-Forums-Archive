---
title: "ubuntu 18.04 wifi flapping every other minute constantly"
date: 2021-04-10
forum: Networking &amp; Wireless
---

### Post by theexpert1234 on 2021-04-10
Hi Everyone,
my ubuntu 18.04 wifi is flapping constantly,so I am unable to access internet on wifi. I recorded the "journalctl --follow" output as below. I hope experts can guide me whats the problem and any possible resolution to this problem. 

[B]
ahmad@ahmad-VPCEG28FG:~$ journalctl --follow[/B]
-- Logs begin at Thu 2020-12-03 06:11:37 PKT. --
Apr 10 22:46:11 ahmad-VPCEG28FG systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 10 22:46:11 ahmad-VPCEG28FG nm-dispatcher[27787]: req:4 'connectivity-change': start running ordered scripts...
Apr 10 22:46:11 ahmad-VPCEG28FG sshd[890]: Received SIGHUP; restarting.
Apr 10 22:46:11 ahmad-VPCEG28FG systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 10 22:46:11 ahmad-VPCEG28FG sshd[890]: Server listening on 0.0.0.0 port 22.
Apr 10 22:46:11 ahmad-VPCEG28FG sshd[890]: Server listening on :: port 22.
Apr 10 22:46:53 ahmad-VPCEG28FG dbus-daemon[1782]: [session uid=1000 pid=1782] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.168' (uid=1000 pid=28027 comm="/usr/bin/gnome-terminal.real " label="unconfined")
Apr 10 22:46:53 ahmad-VPCEG28FG systemd[1757]: Starting GNOME Terminal Server...
Apr 10 22:46:53 ahmad-VPCEG28FG dbus-daemon[1782]: [session uid=1000 pid=1782] Successfully activated service 'org.gnome.Terminal'
Apr 10 22:46:53 ahmad-VPCEG28FG systemd[1757]: Started GNOME Terminal Server.
Apr 10 22:47:11 ahmad-VPCEG28FG systemd[1]: Starting Load/Save RF Kill Switch Status...
Apr 10 22:47:11 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076831.8916] manager: rfkill: WiFi now disabled by radio killswitch
Apr 10 22:47:11 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076831.8918] device (wlp2s0): state change: activated -> unavailable (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:11 ahmad-VPCEG28FG systemd[1]: Started Load/Save RF Kill Switch Status.
Apr 10 22:47:11 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076831.9245] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 27910
Apr 10 22:47:11 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076831.9245] dhcp4 (wlp2s0): state changed bound -> done
Apr 10 22:47:11 ahmad-VPCEG28FG avahi-daemon[728]: Withdrawing address record for 192.168.10.2 on wlp2s0.
Apr 10 22:47:11 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_DELROUTE: index:3
Apr 10 22:47:11 ahmad-VPCEG28FG avahi-daemon[728]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.10.2.
Apr 10 22:47:11 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_DELROUTE: index:3
Apr 10 22:47:11 ahmad-VPCEG28FG kernel: wlp2s0: deauthenticating from c8:5a:9f:ec:c9:fb by local choice (Reason: 3=DEAUTH_LEAVING)
Apr 10 22:47:11 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_DELADDR: index:3, addr:192.168.10.2
Apr 10 22:47:11 ahmad-VPCEG28FG avahi-daemon[728]: Interface wlp2s0.IPv4 no longer relevant for mDNS.
Apr 10 22:47:11 ahmad-VPCEG28FG avahi-daemon[728]: Withdrawing address record for fe80::f095:e4be:9ee9:5f28 on wlp2s0.
Apr 10 22:47:11 ahmad-VPCEG28FG avahi-daemon[728]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::f095:e4be:9ee9:5f28.
Apr 10 22:47:11 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:11 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:11 ahmad-VPCEG28FG vmnetBridge[1620]: Removing interface wlp2s0 index:3
Apr 10 22:47:11 ahmad-VPCEG28FG avahi-daemon[728]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Apr 10 22:47:11 ahmad-VPCEG28FG vmnetBridge[1620]: Stopped bridge wlp2s0 to virtual network 0.
Apr 10 22:47:11 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=c8:5a:9f:ec:c9:fb reason=3 locally_generated=1
Apr 10 22:47:11 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076831.9439] manager: NetworkManager state is now CONNECTED_SITE
Apr 10 22:47:11 ahmad-VPCEG28FG dbus-daemon[758]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.9' (uid=0 pid=782 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Apr 10 22:47:11 ahmad-VPCEG28FG whoopsie[1499]: [22:47:11] offline
Apr 10 22:47:11 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 10 22:47:11 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076831.9469] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:11 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:11 ahmad-VPCEG28FG dbus-daemon[758]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 10 22:47:11 ahmad-VPCEG28FG nm-dispatcher[28051]: req:1 'connectivity-change': new request (1 scripts)
Apr 10 22:47:11 ahmad-VPCEG28FG nm-dispatcher[28051]: req:1 'connectivity-change': start running ordered scripts...
Apr 10 22:47:11 ahmad-VPCEG28FG systemd[1]: Started Network Manager Script Dispatcher Service.
Apr 10 22:47:11 ahmad-VPCEG28FG nm-dispatcher[28051]: req:2 'down' [wlp2s0]: new request (1 scripts)
Apr 10 22:47:11 ahmad-VPCEG28FG nm-dispatcher[28051]: req:2 'down' [wlp2s0]: start running ordered scripts...
Apr 10 22:47:11 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001002
Apr 10 22:47:11 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001002
[B]Apr 10 22:47:11 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error: org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Apr 10 22:47:11 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Apr 10 22:47:11 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Apr 10 22:47:11 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit vino-server.service not loaded.
Apr 10 22:47:12 ahmad-VPCEG28FG wpa_supplicant[808]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0[/B]
Apr 10 22:47:12 ahmad-VPCEG28FG kernel: userif-0: sent link down event.
Apr 10 22:47:12 ahmad-VPCEG28FG kernel: userif-0: sent link up event.
Apr 10 22:47:15 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076835.6596] manager: rfkill: WiFi now enabled by radio killswitch
Apr 10 22:47:15 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:15 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:15 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:15 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:15 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076835.7448] sup-iface[0x561e1970ad00,wlp2s0]: supports 4 scan SSIDs
Apr 10 22:47:15 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076835.7472] device (wlp2s0): supplicant interface state: starting -> ready
Apr 10 22:47:15 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076835.7473] device (wlp2s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Apr 10 22:47:15 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:15 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6956] policy: auto-activating connection 'NTC-Woodys'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6974] device (wlp2s0): Activation: starting connection 'NTC-Woodys' (2d4f88e0-152d-41d1-9bf4-eec212163c78)
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6977] device (wlp2s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6979] manager: NetworkManager state is now CONNECTING
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6986] device (wlp2s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6988] device (wlp2s0): Activation: (wifi) access point 'NTC-Woodys' has security, but secrets are required.
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6989] device (wlp2s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.6990] sup-iface[0x561e1970ad00,wlp2s0]: wps: type pbc start...
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7039] device (wlp2s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7045] device (wlp2s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7048] device (wlp2s0): Activation: (wifi) connection 'NTC-Woodys' has security, and secrets exist.  No new secrets needed.
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7049] Config: added 'ssid' value 'NTC-Woodys'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7049] Config: added 'scan_ssid' value '1'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7049] Config: added 'bgscan' value 'simple:30:-80:86400'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7049] Config: added 'key_mgmt' value 'WPA-PSK'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7049] Config: added 'auth_alg' value 'OPEN'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7049] Config: added 'psk' value '<hidden>'
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: SME: Trying to authenticate with c8:5a:9f:ec:c9:fb (SSID='NTC-Woodys' freq=2462 MHz)
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: authenticate with c8:5a:9f:ec:c9:fb
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7364] device (wlp2s0): supplicant interface state: ready -> authenticating
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: Trying to associate with c8:5a:9f:ec:c9:fb (SSID='NTC-Woodys' freq=2462 MHz)
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: send auth to c8:5a:9f:ec:c9:fb (try 1/3)
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: authenticated
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: associate with c8:5a:9f:ec:c9:fb (try 1/3)
Apr 10 22:47:16 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00011003
Apr 10 22:47:16 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00011003
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: Associated with c8:5a:9f:ec:c9:fb
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=PK
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7439] device (wlp2s0): supplicant interface state: authenticating -> associated
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: RX AssocResp from c8:5a:9f:ec:c9:fb (capab=0x1411 status=0 aid=6)
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: associated
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: EEPROM regdomain: 0x824a
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: EEPROM indicates we should expect a country code
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: doing EEPROM country->regdmn map search
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: country maps to regdmn code: 0x3
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: Country alpha2 being used: PK
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: Regpair used: 0x3
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: ath: regdomain 0x824a dynamically updated by country element
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7630] device (wlp2s0): supplicant interface state: associated -> 4-way handshake
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: WPA: Key negotiation completed with c8:5a:9f:ec:c9:fb [PTK=CCMP GTK=TKIP]
Apr 10 22:47:16 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-CONNECTED - Connection to c8:5a:9f:ec:c9:fb completed [id=0 id_str=]
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
Apr 10 22:47:16 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00011043
Apr 10 22:47:16 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00011043
Apr 10 22:47:16 ahmad-VPCEG28FG vmnetBridge[1620]: Adding interface wlp2s0 index:3
Apr 10 22:47:16 ahmad-VPCEG28FG vmnetBridge[1620]: Started bridge wlp2s0 to virtual network 0.
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7835] device (wlp2s0): supplicant interface state: 4-way handshake -> completed
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7836] device (wlp2s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'NTC-Woodys'.
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7839] device (wlp2s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7850] dhcp4 (wlp2s0): activation: beginning transaction (timeout in 45 seconds)
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.7895] dhcp4 (wlp2s0): dhclient started with pid 28073
Apr 10 22:47:16 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00011043
Apr 10 22:47:16 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00011043
Apr 10 22:47:16 ahmad-VPCEG28FG avahi-daemon[728]: Joining mDNS multicast group on interface wlp2s0.IPv6 with address fe80::f095:e4be:9ee9:5f28.
Apr 10 22:47:16 ahmad-VPCEG28FG avahi-daemon[728]: New relevant interface wlp2s0.IPv6 for mDNS.
Apr 10 22:47:16 ahmad-VPCEG28FG avahi-daemon[728]: Registering new address record for fe80::f095:e4be:9ee9:5f28 on wlp2s0.*.
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: wlp2s0: Limiting TX power to 20 (20 - 0) dBm as advertised by c8:5a:9f:ec:c9:fb
Apr 10 22:47:16 ahmad-VPCEG28FG dhclient[28073]: DHCPREQUEST of 192.168.10.2 on wlp2s0 to 255.255.255.255 port 67 (xid=0x76d69a82)
Apr 10 22:47:16 ahmad-VPCEG28FG dhclient[28073]: DHCPACK of 192.168.10.2 from 192.168.10.1
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9382] dhcp4 (wlp2s0):   address 192.168.10.2
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9384] dhcp4 (wlp2s0):   plen 24 (255.255.255.0)
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9384] dhcp4 (wlp2s0):   gateway 192.168.10.1
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9385] dhcp4 (wlp2s0):   lease time 86400
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9386] dhcp4 (wlp2s0):   nameserver '192.168.10.1'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9387] dhcp4 (wlp2s0):   domain name 'Home'
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9388] dhcp4 (wlp2s0): state changed unknown -> bound
Apr 10 22:47:16 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWADDR: index:3, addr:192.168.10.2
Apr 10 22:47:16 ahmad-VPCEG28FG avahi-daemon[728]: Joining mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.10.2.
Apr 10 22:47:16 ahmad-VPCEG28FG avahi-daemon[728]: New relevant interface wlp2s0.IPv4 for mDNS.
Apr 10 22:47:16 ahmad-VPCEG28FG avahi-daemon[728]: Registering new address record for 192.168.10.2 on wlp2s0.IPv4.
Apr 10 22:47:16 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWROUTE: index:3
Apr 10 22:47:16 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWROUTE: index:3
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9462] device (wlp2s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG whoopsie[1499]: [22:47:16] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9481] device (wlp2s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9485] device (wlp2s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9487] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 10 22:47:16 ahmad-VPCEG28FG dhclient[28073]: bound to 192.168.10.2 -- renewal in 36738 seconds.
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9574] manager: NetworkManager state is now CONNECTED_SITE
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9576] policy: set 'NTC-Woodys' (wlp2s0) as default for IPv4 routing and DNS
Apr 10 22:47:16 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076836.9596] device (wlp2s0): Activation: successful, device activated.
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:16 ahmad-VPCEG28FG nm-dispatcher[28051]: req:3 'up' [wlp2s0]: new request (1 scripts)
Apr 10 22:47:16 ahmad-VPCEG28FG nm-dispatcher[28051]: req:3 'up' [wlp2s0]: start running ordered scripts...
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:16 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
**Apr 10 22:47:16 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error[B]: org**.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Apr 10 22:47:16 ahmad-VPCEG28FG systemd-resolved[713]: Using degraded feature set (UDP) for DNS server 192.168.10.1.
Apr 10 22:47:16 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error[/B]**: org**[B].freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Apr 10 22:47:16 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Apr 10 22:47:16 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit vino-server.service not loaded.[/B]
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: userif-0: sent link down event.
Apr 10 22:47:16 ahmad-VPCEG28FG kernel: userif-0: sent link up event.
Apr 10 22:47:17 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-57 noise=-95 txrate=135000
Apr 10 22:47:22 ahmad-VPCEG28FG systemd[1]: Reloading OpenBSD Secure Shell server.
Apr 10 22:47:22 ahmad-VPCEG28FG sshd[890]: Received SIGHUP; restarting.
Apr 10 22:47:22 ahmad-VPCEG28FG systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 10 22:47:22 ahmad-VPCEG28FG sshd[890]: Server listening on 0.0.0.0 port 22.
Apr 10 22:47:22 ahmad-VPCEG28FG sshd[890]: Server listening on :: port 22.
Apr 10 22:47:23 ahmad-VPCEG28FG systemd[1]: Starting Load/Save RF Kill Switch Status...
Apr 10 22:47:23 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076843.4142] manager: rfkill: WiFi now disabled by radio killswitch
Apr 10 22:47:23 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076843.4144] device (wlp2s0): state change: activated -> unavailable (reason 'none', sys-iface-state: 'managed')
Apr 10 22:47:23 ahmad-VPCEG28FG systemd[1]: Started Load/Save RF Kill Switch Status.
Apr 10 22:47:23 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076843.4468] dhcp4 (wlp2s0): canceled DHCP transaction, DHCP client pid 28073
Apr 10 22:47:23 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076843.4469] dhcp4 (wlp2s0): state changed bound -> done
Apr 10 22:47:23 ahmad-VPCEG28FG kernel: wlp2s0: deauthenticating from c8:5a:9f:ec:c9:fb by local choice (Reason: 3=DEAUTH_LEAVING)
Apr 10 22:47:23 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:23 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001003
Apr 10 22:47:23 ahmad-VPCEG28FG vmnetBridge[1620]: Removing interface wlp2s0 index:3
Apr 10 22:47:23 ahmad-VPCEG28FG vmnetBridge[1620]: Stopped bridge wlp2s0 to virtual network 0.
Apr 10 22:47:23 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_DELROUTE: index:3
Apr 10 22:47:23 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_DELROUTE: index:3
Apr 10 22:47:23 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-DISCONNECTED bssid=c8:5a:9f:ec:c9:fb reason=3 locally_generated=1
Apr 10 22:47:23 ahmad-VPCEG28FG wpa_supplicant[808]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 10 22:47:23 ahmad-VPCEG28FG avahi-daemon[728]: Withdrawing address record for 192.168.10.2 on wlp2s0.
Apr 10 22:47:23 ahmad-VPCEG28FG avahi-daemon[728]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.10.2.
Apr 10 22:47:23 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_DELADDR: index:3, addr:192.168.10.2
Apr 10 22:47:23 ahmad-VPCEG28FG avahi-daemon[728]: Interface wlp2s0.IPv4 no longer relevant for mDNS.
Apr 10 22:47:23 ahmad-VPCEG28FG whoopsie[1499]: [22:47:23] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
Apr 10 22:47:23 ahmad-VPCEG28FG avahi-daemon[728]: Withdrawing address record for fe80::f095:e4be:9ee9:5f28 on wlp2s0.
Apr 10 22:47:23 ahmad-VPCEG28FG avahi-daemon[728]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::f095:e4be:9ee9:5f28.
Apr 10 22:47:23 ahmad-VPCEG28FG avahi-daemon[728]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Apr 10 22:47:23 ahmad-VPCEG28FG NetworkManager[782]: <info>  [1618076843.4666] manager: NetworkManager state is now CONNECTED_LOCAL
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: reading /etc/resolv.conf
Apr 10 22:47:23 ahmad-VPCEG28FG dnsmasq[1216]: using nameserver 127.0.0.53#53
Apr 10 22:47:23 ahmad-VPCEG28FG nm-dispatcher[28051]: req:4 'down' [wlp2s0]: new request (1 scripts)
Apr 10 22:47:23 ahmad-VPCEG28FG vmnetBridge[1620]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001002
Apr 10 22:47:23 ahmad-VPCEG28FG vmnet-natd[1628]: RTM_NEWLINK: name:wlp2s0 index:3 flags:0x00001002
Apr 10 22:47:23 ahmad-VPCEG28FG systemd[1]: Reloading OpenBSD Secure Shell server.
**Apr 10 22:47:23 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error[B]: org**.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.
Apr 10 22:47:23 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Apr 10 22:47:23 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Apr 10 22:47:23 ahmad-VPCEG28FG gsd-sharing[2017]: Failed to StopUnit service: GDBus.Error**: org**.freedesktop.systemd1.NoSuchUnit: Unit vino-server.service not loaded.[/B]
Apr 10 22:47:23 ahmad-VPCEG28FG nm-dispatcher[28051]: req:4 'down' [wlp2s0]: start running ordered scripts...
Apr 10 22:47:23 ahmad-VPCEG28FG wpa_supplicant[808]: nl80211: deinit ifname=wlp2s0 disabled_11b_rates=0
Apr 10 22:47:23 ahmad-VPCEG28FG sshd[890]: Received SIGHUP; restarting.
Apr 10 22:47:23 ahmad-VPCEG28FG systemd[1]: Reloaded OpenBSD Secure Shell server.
Apr 10 22:47:23 ahmad-VPCEG28FG sshd[890]: Server listening on 0.0.0.0 port 22.
Apr 10 22:47:23 ahmad-VPCEG28FG sshd[890]: Server listening on :: port 22.
Apr 10 22:47:23 ahmad-VPCEG28FG kernel: userif-0: sent link down event.
Apr 10 22:47:23 ahmad-VPCEG28FG kernel: userif-0: sent link up event.

---

### Post by praseodym on 2021-04-10
Please run the wireless script from the sticky thread and show the outputs. Does LAN work?

---

### Post by theexpert1234 on 2021-04-11
Hi, yes the LAN is working . also attached is the output of the script in zip format.
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs. Does LAN work?

---

### Post by chili555 on 2021-04-11
We see this in your results:

```
##### rfkill ############################

0: sony-wifi: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
```The result of running the script with the wireless radio turned off by the hardware switch or key combination is that the wireless device can't report some valuable clues that we need in order to help.

Please turn the wireless radio on and run and post:

```
sudo iwlist wlp2s0 scan
```

Just show your networks and please redact the hardware addresses like this:

```
Cell 05 - Address: [COLOR="#FF0000"]XXXX[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MC2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000851a88e3a0
                    Extra: Last beacon: 3844ms ago
                    IE: Unknown: 00054D43322E34
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```Please also run and post:

```
nmcli device wifi list
```Again, please redact the MAC addresses:

```
xxxx  MC2.4  Infra  11    130 Mbit/s  47      &#9602;&#9604;__  WPA2   

```Here, we'd like to see the entire listing, not just your networks.

---

### Post by theexpert1234 on 2021-04-12
Hi,

I have attached the new file( by running script again), although my wifi hardware switch is always ON, but still somehow it is being hardware reset internally. I was able to get a small interval between two wifi flap events where I ran this script and collected this output.(as my wifi is flapping constantly)

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    **Hard blocked: no**
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    **Hard blocked: no**
2: phy0: Wireless LAN
    Soft blocked: no
    **Hard blocked: no**
3: hci0: Bluetooth
    Soft blocked: no
    **Hard blocked: no**






> **chili555 said:**
> We see this in your results:

```
##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    [COLOR=#FF0000]Hard blocked: yes[/COLOR]
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    [COLOR=#FF0000]Hard blocked: yes[/COLOR]
```The result of running the script with the wireless radio turned off by the hardware switch or key combination is that the wireless device can't report some valuable clues that we need in order to help.

Please turn the wireless radio on and run and post:

```
sudo iwlist wlp2s0 scan
```

Just show your networks and please redact the hardware addresses like this:

```
Cell 05 - Address: [COLOR=#FF0000]XXXX[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MC2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000851a88e3a0
                    Extra: Last beacon: 3844ms ago
                    IE: Unknown: 00054D43322E34
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```Please also run and post:

```
nmcli device wifi list
```Again, please redact the MAC addresses:

```
xxxx  MC2.4  Infra  11    130 Mbit/s  47      &#9602;&#9604;__  WPA2   

```Here, we'd like to see the entire listing, not just your networks.

---

### Post by praseodym on 2021-04-12
```
auto [COLOR="#FF0000"]tap 0[/COLOR]
iface [COLOR="#FF0000"]tap0[/COLOR] inet static
	address	10.1.1.1
	netmask	255.255.255.0
```
This "space" is too much as well. What is that config about?

---

### Post by chili555 on 2021-04-12
```
Cell 02 - Address: <MAC 'NTC-Woodys' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"NTC-Woodys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f8a74f59
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

### Post by theexpert1234 on 2021-04-28
> **praseodym said:**
> ```
auto [COLOR=#FF0000]tap 0[/COLOR]
iface [COLOR=#FF0000]tap0[/COLOR] inet static
    address    10.1.1.1
    netmask    255.255.255.0
```
This "space" is too much as well. What is that config about?

Hi ,
Thanks for your reply.I am not sure , but I believe I tried to make a Tap0 interface back some time ago for some testing purpose, but I am not using it. I can remove it if it can cause any issues with my wireless hopefully ?

---

### Post by theexpert1234 on 2021-04-28
Hi Thanks for your reply, I have implemented the power saving solution recommended as above and monitoring the wireless performance, hopefully it should correct the flapping issue.
I will post my performance observation once done.Thanks.

> **chili555 said:**
> ```
Cell 02 - Address: <MAC 'NTC-Woodys' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"NTC-Woodys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f8a74f59
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#FF0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR=#FF0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

