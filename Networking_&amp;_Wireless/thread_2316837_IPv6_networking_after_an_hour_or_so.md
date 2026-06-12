---
title: "IPv6 networking after an hour or so"
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by lorenzo-milesi on 2016-03-11
Hi.
Since when I upgraded (reinstalled) my laptop to the latest 15.10 (from 15.04), IPv6 has been badly working on my PC.

Some background: I've a tunneled IPv6 network working in my LAN, RA provided by pfSense 2.1. 
I have some hosts with fixed IPv6 address on which the connection is working without glitches. On my laptop, configured in DHCP, it works for some time and at a certain point the IPv6 address vanishes and I'm back to IPv4.

I'm attaching a syslog excerpt. As you can see at 07:33:29 I receive a DHCPv4 address, then at  07:33:31 a DHCPv6 one which vanishes at 10:53:48!

What could it be?
thanks


```
Mar 11 07:33:25 dharma systemd[1]: Starting Network Manager Script Dispatcher Service...Mar 11 07:33:25 dharma dbus[756]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 11 07:33:25 dharma systemd[1]: Started Network Manager Script Dispatcher Service.
Mar 11 07:33:25 dharma nm-dispatcher: Dispatching action 'up' for virbr0
Mar 11 07:33:25 dharma wpa_supplicant[1206]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Mar 11 07:33:25 dharma wpa_supplicant[1206]: dbus: Failed to construct signal
Mar 11 07:33:25 dharma NetworkManager[781]: <info>  (wlp1s0): supplicant interface state: starting -> ready
Mar 11 07:33:25 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 11 07:33:25 dharma kernel: [    7.342463] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
Mar 11 07:33:25 dharma NetworkManager[781]: <info>  Device 'wlp1s0' has no connection; scheduling activate_check in 0 seconds.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): supplicant interface state: ready -> inactive
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Auto-activating connection 'mySSID 1'.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): Activation: starting connection 'mySSID 1' (c9708b59-0b12-40b7-aa2e-d2b5bf5a1589)
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  NetworkManager state is now CONNECTING
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): Activation: (wifi) connection 'mySSID 1' has security, and secrets exist.  No new secrets needed.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Config: added 'ssid' value 'mySSID'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Config: added 'scan_ssid' value '1'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Config: added 'psk' value '<omitted>'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Config: set interface ap_scan to 1
Mar 11 07:33:29 dharma wpa_supplicant[1206]: wlp1s0: SME: Trying to authenticate with c0:c1:c0:ce:60:8f (SSID='mySSID' freq=2437 MHz)
Mar 11 07:33:29 dharma kernel: [   10.559372] wlp1s0: authenticate with c0:c1:c0:ce:60:8f
Mar 11 07:33:29 dharma wpa_supplicant[1206]: wlp1s0: Trying to associate with c0:c1:c0:ce:60:8f (SSID='mySSID' freq=2437 MHz)
Mar 11 07:33:29 dharma kernel: [   10.562033] wlp1s0: send auth to c0:c1:c0:ce:60:8f (try 1/3)
Mar 11 07:33:29 dharma kernel: [   10.563845] wlp1s0: authenticated
Mar 11 07:33:29 dharma kernel: [   10.565084] wlp1s0: associate with c0:c1:c0:ce:60:8f (try 1/3)
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): supplicant interface state: inactive -> associating
Mar 11 07:33:29 dharma kernel: [   10.567771] wlp1s0: RX AssocResp from c0:c1:c0:ce:60:8f (capab=0x411 status=0 aid=2)
Mar 11 07:33:29 dharma wpa_supplicant[1206]: wlp1s0: Associated with c0:c1:c0:ce:60:8f
Mar 11 07:33:29 dharma kernel: [   10.570158] wlp1s0: associated
Mar 11 07:33:29 dharma kernel: [   10.570191] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): supplicant interface state: associating -> 4-way handshake
Mar 11 07:33:29 dharma wpa_supplicant[1206]: wlp1s0: WPA: Key negotiation completed with c0:c1:c0:ce:60:8f [PTK=CCMP GTK=TKIP]
Mar 11 07:33:29 dharma wpa_supplicant[1206]: wlp1s0: CTRL-EVENT-CONNECTED - Connection to c0:c1:c0:ce:60:8f completed [id=0 id_str=]
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): supplicant interface state: 4-way handshake -> completed
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'mySSID'.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Activation (wlp1s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  dhclient started with pid 1330
Mar 11 07:33:29 dharma dhclient: DHCPDISCOVER on wlp1s0 to 255.255.255.255 port 67 interval 3 (xid=0x5bab3921)
Mar 11 07:33:29 dharma dhclient: DHCPREQUEST of 192.168.1.73 on wlp1s0 to 255.255.255.255 port 67 (xid=0x2139ab5b)
Mar 11 07:33:29 dharma dhclient: DHCPOFFER of 192.168.1.73 from 192.168.1.190
Mar 11 07:33:29 dharma dhclient: DHCPACK of 192.168.1.73 from 192.168.1.190
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    address 192.168.1.73
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    plen 24 (255.255.255.0)
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    gateway 192.168.1.1
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    server identifier 192.168.1.190
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    lease time 43200
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    hostname 'dharma'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    nameserver '192.168.1.190'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>    domain name 'mySSID.it'
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): DHCPv4 state changed unknown -> bound
Mar 11 07:33:29 dharma avahi-daemon[750]: Joining mDNS multicast group on interface wlp1s0.IPv4 with address 192.168.1.73.
Mar 11 07:33:29 dharma avahi-daemon[750]: New relevant interface wlp1s0.IPv4 for mDNS.
Mar 11 07:33:29 dharma avahi-daemon[750]: Registering new address record for 192.168.1.73 on wlp1s0.IPv4.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Mar 11 07:33:29 dharma dhclient: bound to 192.168.1.73 -- renewal in 18123 seconds.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  NetworkManager state is now CONNECTED_LOCAL
Mar 11 07:33:29 dharma whoopsie[789]: [07:33:29] Cannot reach: https://daisy.ubuntu.com
Mar 11 07:33:29 dharma whoopsie[789]: [07:33:29] Cannot reach: https://daisy.ubuntu.com
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Policy set 'mySSID 1' (wlp1s0) as default for IPv4 routing and DNS.
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  DNS: starting dnsmasq...
Mar 11 07:33:29 dharma NetworkManager[781]: <warn>  dnsmasq not available on the bus, can't update servers.
Mar 11 07:33:29 dharma NetworkManager[781]: <error> [1457678009.223743] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Mar 11 07:33:29 dharma NetworkManager[781]: <warn>  DNS: plugin dnsmasq update failed
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Writing DNS information to /sbin/resolvconf
Mar 11 07:33:29 dharma dnsmasq[1340]: avviato, versione 2.75 cache disabilitata
Mar 11 07:33:29 dharma dnsmasq[1340]: opzioni tempo di compilazione: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Mar 11 07:33:29 dharma dnsmasq[1340]: supporto DBus abilitato: connesso al bus di sistema
Mar 11 07:33:29 dharma dnsmasq[1340]: attenzione: nessun server upstream configurato
Mar 11 07:33:29 dharma NetworkManager[781]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  (wlp1s0): Activation: successful, device activated.
Mar 11 07:33:29 dharma NetworkManager[781]: <warn>  dnsmasq appeared on DBus: :1.52
Mar 11 07:33:29 dharma nm-dispatcher: Dispatching action 'up' for wlp1s0
Mar 11 07:33:29 dharma dnsmasq[1340]: impostazione del server upstream da DBus
Mar 11 07:33:29 dharma dnsmasq[1340]: utilizzo del server dei nomi 192.168.1.190#53
Mar 11 07:33:29 dharma NetworkManager[781]: <info>  Writing DNS information to /sbin/resolvconf
Mar 11 07:33:29 dharma NetworkManager[781]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /run/resolvconf/resolv.conf
Mar 11 07:33:29 dharma whoopsie[789]: [07:33:29] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Mar 11 07:33:29 dharma whoopsie[789]: [07:33:29] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Mar 11 07:33:29 dharma whoopsie[789]: [07:33:29] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Mar 11 07:33:29 dharma org.freedesktop.Notifications[997]: ** (notify-osd:1364): WARNING **: dnd_is_idle_inhibited(): got error "Metodo "IsInhibited" inesistente"
Mar 11 07:33:30 dharma avahi-daemon[750]: Joining mDNS multicast group on interface wlp1s0.IPv6 with address fe80::8a53:2eff:fe8f:f0ac.
Mar 11 07:33:30 dharma avahi-daemon[750]: New relevant interface wlp1s0.IPv6 for mDNS.
Mar 11 07:33:30 dharma avahi-daemon[750]: Registering new address record for fe80::8a53:2eff:fe8f:f0ac on wlp1s0.*.
Mar 11 07:33:30 dharma whoopsie[789]: [07:33:30] online
Mar 11 07:33:30 dharma NetworkManager[781]: <info>  Activation (wlp1s0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Mar 11 07:33:30 dharma NetworkManager[781]: <info>  dhclient started with pid 1503
Mar 11 07:33:30 dharma dhclient: XMT: Confirm on wlp1s0, interval 1000ms.
Mar 11 07:33:31 dharma dhclient: XMT: Confirm on wlp1s0, interval 1960ms.
Mar 11 07:33:31 dharma dhclient: RCV: Reply message on wlp1s0 from fe80::5054:ff:fefa:e161.
Mar 11 07:33:31 dharma dhclient: message status code Success: "All addresses still on link."
Mar 11 07:33:31 dharma NetworkManager[781]: <info>    valid_lft 7200
Mar 11 07:33:31 dharma NetworkManager[781]: <info>    preferred_lft 4500
Mar 11 07:33:31 dharma NetworkManager[781]: <info>    address 2000:1010:a12:858b::ff7b
Mar 11 07:33:31 dharma NetworkManager[781]: <info>    nameserver '2000:1010:a12:858b::190'
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  (wlp1s0): DHCPv6 state changed unknown -> bound
Mar 11 07:33:31 dharma dhclient: PRC: Rebinding lease on wlp1s0.
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  Policy set 'mySSID 1' (wlp1s0) as default for IPv6 routing and DNS.
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  Writing DNS information to /sbin/resolvconf
Mar 11 07:33:31 dharma dnsmasq[1340]: impostazione del server upstream da DBus
Mar 11 07:33:31 dharma dnsmasq[1340]: utilizzo del server dei nomi 2000:1010:a12:858b::190#53
Mar 11 07:33:31 dharma dnsmasq[1340]: utilizzo del server dei nomi 192.168.1.190#53
Mar 11 07:33:31 dharma nm-dispatcher: Dispatching action 'dhcp6-change' for wlp1s0
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  (wlp1s0): DHCPv6 state changed bound -> unknown
Mar 11 07:33:31 dharma dhclient: PRC: Address 2000:1010:a12:858b::ff7b depreferred.
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  (wlp1s0): DHCPv6 state changed unknown -> expire
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  (wlp1s0): canceled DHCP transaction, DHCP client pid 1503
Mar 11 07:33:31 dharma NetworkManager[781]: <info>  (wlp1s0): DHCPv6 state changed expire -> done
Mar 11 07:33:33 dharma avahi-daemon[750]: Leaving mDNS multicast group on interface wlp1s0.IPv6 with address fe80::8a53:2eff:fe8f:f0ac.
Mar 11 07:33:33 dharma avahi-daemon[750]: Joining mDNS multicast group on interface wlp1s0.IPv6 with address 2000:1010:a12:858b::ff7b.
Mar 11 07:33:33 dharma avahi-daemon[750]: Registering new address record for 2000:1010:a12:858b::ff7b on wlp1s0.*.
Mar 11 07:33:33 dharma avahi-daemon[750]: Withdrawing address record for fe80::8a53:2eff:fe8f:f0ac on wlp1s0.
Mar 11 07:33:35 dharma NetworkManager[781]: <info>  WiFi hardware radio set enabled
Mar 11 07:33:35 dharma NetworkManager[781]: <info>  WWAN hardware radio set enabled
Mar 11 07:33:35 dharma NetworkManager[781]: <info>  startup complete
Mar 11 07:33:35 dharma systemd[1]: Started Network Manager Wait Online.
Mar 11 07:33:35 dharma systemd[1]: Reached target Network is Online.


[...]


Mar 11 09:20:07 dharma thermald[730]: Read set point 0
Mar 11 09:20:07 dharma thermald[730]: Dropped below poll threshold
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 5:Processor
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 10:intel_powerclamp
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 12:intel_pstate
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 11:rapl_controller
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 5:Processor
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 10:intel_powerclamp
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 12:intel_pstate
Mar 11 09:20:07 dharma thermald[730]: thd_trip_cdev_state_reset index 11:rapl_controller
Mar 11 09:20:25 dharma thermald[730]: Read set point 0
Mar 11 09:20:25 dharma thermald[730]: Dropped below poll threshold
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 5:Processor
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 10:intel_powerclamp
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 12:intel_pstate
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 11:rapl_controller
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 5:Processor
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 10:intel_powerclamp
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 12:intel_pstate
Mar 11 09:20:25 dharma thermald[730]: thd_trip_cdev_state_reset index 11:rapl_controller
Mar 11 09:21:39 dharma kernel: [ 6495.771653] ------------[ cut here ]------------
Mar 11 09:21:39 dharma kernel: [ 6495.771733] WARNING: CPU: 0 PID: 0 at /build/linux-C6fFlA/linux-4.2.0/drivers/gpu/drm/i915/intel_display.c:11104 intel_check_page_flip+0xfc/0x110 [i915]()
Mar 11 09:21:39 dharma kernel: [ 6495.771739] Kicking stuck page flip: queued at 389373, now 389413
Mar 11 09:21:39 dharma kernel: [ 6495.771743] Modules linked in: ppp_deflate bsd_comp ppp_async crc_ccitt hid_generic usbhid hid nvram msr drbg ansi_cprng ctr ccm rfcomm xt_CHECKSUM iptable_mangle ipt_MASQUERADE nf_nat_masquerade_ipv4 iptable_nat nf_nat_ipv4 nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_conntrack nf_conntrack ipt_REJECT nf_reject_ipv4 xt_tcpudp bridge stp llc ebtable_filter ebtables ip6table_filter ip6_tables iptable_filter ip_tables x_tables bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media btusb btrtl btbcm btintel bluetooth binfmt_misc intel_rapl snd_hda_codec_hdmi x86_pkg_temp_thermal snd_hda_codec_realtek intel_powerclamp arc4 samsung_laptop snd_hda_codec_generic coretemp snd_hda_intel kvm_intel snd_hda_codec iwldvm snd_hda_core kvm snd_hwdep mac80211 snd_pcm crct10dif_pclmul crc32_pclmul snd_seq_midi aesni_intel snd_seq_midi_event aes_x86_64 snd_rawmidi lrw gf128mul glue_helper iwlwifi ablk_helper cryptd snd_seq snd_seq_device cfg80211 joydev snd_timer input_leds serio_raw snd mei_me soundcore mei lpc_ich shpchp dell_smo8800 mac_hid parport_pc ppdev lp parport autofs4 i915 i2c_algo_bit psmouse drm_kms_helper ahci libahci drm r8169 mii video
Mar 11 09:21:39 dharma kernel: [ 6495.771896] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 4.2.0-33-generic #38-Ubuntu
Mar 11 09:21:39 dharma kernel: [ 6495.771900] Hardware name: SAMSUNG ELECTRONICS CO., LTD. 530U3BI/530U4BI/530U4BH/530U3BI/530U4BI/530U4BH, BIOS 03XK 01/04/2012
Mar 11 09:21:39 dharma kernel: [ 6495.771905]  0000000000000000 4a3fc994c60b5927 ffff88021fa03d08 ffffffff817ebed3
Mar 11 09:21:39 dharma kernel: [ 6495.771913]  0000000000000000 ffff88021fa03d60 ffff88021fa03d48 ffffffff8107b986
Mar 11 09:21:39 dharma kernel: [ 6495.771918]  ffff88021fa03d78 ffff8802162ab000 ffff8800d5b57000 ffff8802162ab1a8
Mar 11 09:21:39 dharma kernel: [ 6495.771924] Call Trace:
Mar 11 09:21:39 dharma kernel: [ 6495.771928]  <IRQ>  [<ffffffff817ebed3>] dump_stack+0x45/0x57
Mar 11 09:21:39 dharma kernel: [ 6495.771949]  [<ffffffff8107b986>] warn_slowpath_common+0x86/0xc0
Mar 11 09:21:39 dharma kernel: [ 6495.771956]  [<ffffffff8107ba15>] warn_slowpath_fmt+0x55/0x70
Mar 11 09:21:39 dharma kernel: [ 6495.772023]  [<ffffffffc01a1cac>] intel_check_page_flip+0xfc/0x110 [i915]
Mar 11 09:21:39 dharma kernel: [ 6495.772063]  [<ffffffffc0169a70>] ironlake_irq_handler+0x410/0xc40 [i915]
Mar 11 09:21:39 dharma kernel: [ 6495.772070]  [<ffffffff810a569d>] ? ttwu_do_activate.constprop.89+0x5d/0x70
Mar 11 09:21:39 dharma kernel: [ 6495.772077]  [<ffffffff810d48e4>] handle_irq_event_percpu+0x74/0x180
Mar 11 09:21:39 dharma kernel: [ 6495.772082]  [<ffffffff810d4a39>] handle_irq_event+0x49/0x70
Mar 11 09:21:39 dharma kernel: [ 6495.772087]  [<ffffffff810d7dd1>] handle_edge_irq+0x81/0x150
Mar 11 09:21:39 dharma kernel: [ 6495.772092]  [<ffffffff810172c5>] handle_irq+0x25/0x40
Mar 11 09:21:39 dharma kernel: [ 6495.772098]  [<ffffffff817f58ef>] do_IRQ+0x4f/0xe0
Mar 11 09:21:39 dharma kernel: [ 6495.772102]  [<ffffffff817f386b>] common_interrupt+0x6b/0x6b
Mar 11 09:21:39 dharma kernel: [ 6495.772104]  <EOI>  [<ffffffff810e7f71>] ? enqueue_hrtimer+0x41/0x80
Mar 11 09:21:39 dharma kernel: [ 6495.772115]  [<ffffffff8168858d>] ? cpuidle_enter_state+0x12d/0x270
Mar 11 09:21:39 dharma kernel: [ 6495.772120]  [<ffffffff8168856b>] ? cpuidle_enter_state+0x10b/0x270
Mar 11 09:21:39 dharma kernel: [ 6495.772124]  [<ffffffff81688707>] cpuidle_enter+0x17/0x20
Mar 11 09:21:39 dharma kernel: [ 6495.772129]  [<ffffffff810bdb12>] call_cpuidle+0x32/0x60
Mar 11 09:21:39 dharma kernel: [ 6495.772133]  [<ffffffff816886e3>] ? cpuidle_select+0x13/0x20
Mar 11 09:21:39 dharma kernel: [ 6495.772137]  [<ffffffff810bddad>] cpu_startup_entry+0x26d/0x330
Mar 11 09:21:39 dharma kernel: [ 6495.772143]  [<ffffffff817e043c>] rest_init+0x7c/0x80
Mar 11 09:21:39 dharma kernel: [ 6495.772150]  [<ffffffff81d50025>] start_kernel+0x48b/0x4ac
Mar 11 09:21:39 dharma kernel: [ 6495.772156]  [<ffffffff81d4f120>] ? early_idt_handler_array+0x120/0x120
Mar 11 09:21:39 dharma kernel: [ 6495.772161]  [<ffffffff81d4f339>] x86_64_start_reservations+0x2a/0x2c
Mar 11 09:21:39 dharma kernel: [ 6495.772166]  [<ffffffff81d4f485>] x86_64_start_kernel+0x14a/0x16d
Mar 11 09:21:39 dharma kernel: [ 6495.772169] ---[ end trace 988162c55aca566c ]---
Mar 11 09:25:01 dharma CRON[23890]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 09:31:19 dharma kernel: [ 7075.445441] usb 3-1.2: clear tt 1 (0060) error -71
Mar 11 09:31:19 dharma kernel: [ 7075.452218] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.456449] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.462590] usb 3-1.2: clear tt 1 (0050) error -71
Mar 11 09:31:19 dharma kernel: [ 7075.464942] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.469171] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.473435] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.473442] usb 3-1.2-port3: Cannot enable. Maybe the USB cable is bad?
Mar 11 09:31:19 dharma kernel: [ 7075.477675] usb 3-1.2-port3: cannot disable (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.481924] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.486168] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.490427] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.494671] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.498915] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.498921] usb 3-1.2-port3: Cannot enable. Maybe the USB cable is bad?
Mar 11 09:31:19 dharma kernel: [ 7075.503157] usb 3-1.2-port3: cannot disable (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.507386] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.511645] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.515904] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.520142] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.524388] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.524395] usb 3-1.2-port3: Cannot enable. Maybe the USB cable is bad?
Mar 11 09:31:19 dharma kernel: [ 7075.528641] usb 3-1.2-port3: cannot disable (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.532898] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.537144] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.541385] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma kernel: [ 7075.545387] usb 3-1.2: USB disconnect, device number 4
Mar 11 09:31:19 dharma kernel: [ 7075.545397] usb 3-1.2.2: USB disconnect, device number 5
Mar 11 09:31:19 dharma kernel: [ 7075.545612] usb 3-1.2-port3: cannot reset (err = -71)
Mar 11 09:31:19 dharma acpid: input device has been disconnected, fd 15
Mar 11 09:31:19 dharma kernel: [ 7075.676230] usb 3-1.2.3: USB disconnect, device number 6
Mar 11 09:31:29 dharma kernel: [ 7084.793203] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:31:29 dharma kernel: [ 7084.793348] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:31:29 dharma kernel: [ 7084.793428] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:31:29 dharma kernel: [ 7084.793460] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:31:29 dharma kernel: [ 7084.793783] pci_bus 0000:01: Allocating resources
Mar 11 09:31:29 dharma kernel: [ 7084.793856] pcieport 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
Mar 11 09:31:29 dharma kernel: [ 7084.793865] pcieport 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000 add_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793880] pci_bus 0000:02: Allocating resources
Mar 11 09:31:29 dharma kernel: [ 7084.793905] pcieport 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 400000 add_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793920] pci_bus 0000:03: Allocating resources
Mar 11 09:31:29 dharma kernel: [ 7084.793945] pcieport 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
Mar 11 09:31:29 dharma kernel: [ 7084.793951] pcieport 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793957] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:31:29 dharma kernel: [ 7084.793965] pcieport 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793970] pcieport 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793975] pcieport 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 400000 min_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793979] pcieport 0000:00:1c.3: res[14]=[mem 0x00100000-0x004fffff] res_to_dev_res add_size 400000 min_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793984] pcieport 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793989] pcieport 0000:00:1c.4: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Mar 11 09:31:29 dharma kernel: [ 7084.793993] pcieport 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Mar 11 09:31:29 dharma kernel: [ 7084.793998] pcieport 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Mar 11 09:31:29 dharma kernel: [ 7084.794003] pcieport 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Mar 11 09:31:29 dharma kernel: [ 7084.794008] pcieport 0000:00:1c.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Mar 11 09:31:29 dharma kernel: [ 7084.794023] pcieport 0000:00:1c.0: BAR 15: assigned [mem 0xdfa00000-0xdfbfffff 64bit pref]
Mar 11 09:31:29 dharma kernel: [ 7084.794028] pcieport 0000:00:1c.3: BAR 14: assigned [mem 0xdfc00000-0xdfffffff]
Mar 11 09:31:29 dharma kernel: [ 7084.794038] pcieport 0000:00:1c.4: BAR 15: assigned [mem 0xf0800000-0xf09fffff 64bit pref]
Mar 11 09:31:29 dharma kernel: [ 7084.794046] pcieport 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
Mar 11 09:31:29 dharma kernel: [ 7084.794051] pcieport 0000:00:1c.4: BAR 13: assigned [io  0x6000-0x6fff]
Mar 11 09:31:29 dharma kernel: [ 7084.794267] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:32:11 dharma kernel: [ 7126.718669] usb 3-1.2: new high-speed USB device number 7 using ehci-pci
Mar 11 09:32:11 dharma kernel: [ 7126.812365] usb 3-1.2: New USB device found, idVendor=05e3, idProduct=0608
Mar 11 09:32:11 dharma kernel: [ 7126.812372] usb 3-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Mar 11 09:32:11 dharma kernel: [ 7126.812375] usb 3-1.2: Product: USB2.0 Hub
Mar 11 09:32:11 dharma kernel: [ 7126.813030] hub 3-1.2:1.0: USB hub found
Mar 11 09:32:11 dharma kernel: [ 7126.813321] hub 3-1.2:1.0: 4 ports detected
Mar 11 09:32:11 dharma kernel: [ 7127.086418] usb 3-1.2.2: new low-speed USB device number 8 using ehci-pci
Mar 11 09:32:11 dharma kernel: [ 7127.185432] usb 3-1.2.2: New USB device found, idVendor=046d, idProduct=c312
Mar 11 09:32:11 dharma kernel: [ 7127.185441] usb 3-1.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Mar 11 09:32:11 dharma kernel: [ 7127.185445] usb 3-1.2.2: Product: USB Multimedia Keyboard
Mar 11 09:32:11 dharma kernel: [ 7127.185449] usb 3-1.2.2: Manufacturer: LITEON Technology
Mar 11 09:32:11 dharma kernel: [ 7127.189569] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2.2/3-1.2.2:1.0/0003:046D:C312.0003/input/input13
Mar 11 09:32:11 dharma kernel: [ 7127.243089] hid-generic 0003:046D:C312.0003: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1.2.2/input0
Mar 11 09:32:11 dharma kernel: [ 7127.314248] usb 3-1.2.3: new low-speed USB device number 9 using ehci-pci
Mar 11 09:32:11 dharma kernel: [ 7127.411019] usb 3-1.2.3: New USB device found, idVendor=046d, idProduct=c016
Mar 11 09:32:11 dharma kernel: [ 7127.411027] usb 3-1.2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Mar 11 09:32:11 dharma kernel: [ 7127.411032] usb 3-1.2.3: Product: Optical USB Mouse
Mar 11 09:32:11 dharma kernel: [ 7127.411035] usb 3-1.2.3: Manufacturer: Logitech
Mar 11 09:32:11 dharma kernel: [ 7127.414545] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2.3/3-1.2.3:1.0/0003:046D:C016.0004/input/input14
Mar 11 09:32:11 dharma kernel: [ 7127.415058] hid-generic 0003:046D:C016.0004: input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1a.0-1.2.3/input0
Mar 11 09:32:11 dharma mtp-probe: checking bus 3, device 9: "/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2.3"
Mar 11 09:32:11 dharma mtp-probe: checking bus 3, device 8: "/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2.2"
Mar 11 09:32:11 dharma mtp-probe: bus: 3, device: 9 was not an MTP device
Mar 11 09:32:11 dharma mtp-probe: bus: 3, device: 8 was not an MTP device
Mar 11 09:32:12 dharma kernel: [ 7128.187016] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:32:12 dharma kernel: [ 7128.187124] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:32:12 dharma kernel: [ 7128.187187] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:32:12 dharma kernel: [ 7128.187208] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:32:12 dharma kernel: [ 7128.187444] pci_bus 0000:01: Allocating resources
Mar 11 09:32:12 dharma kernel: [ 7128.187503] pci_bus 0000:02: Allocating resources
Mar 11 09:32:12 dharma kernel: [ 7128.187531] pci_bus 0000:03: Allocating resources
Mar 11 09:32:12 dharma kernel: [ 7128.187551] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:32:12 dharma kernel: [ 7128.187700] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Mar 11 09:35:01 dharma CRON[25031]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 09:38:03 dharma avahi-daemon[750]: Registering new address record for fe80::8a53:2eff:fe8f:f0ac on wlp1s0.*.
Mar 11 09:39:01 dharma CRON[25459]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Mar 11 09:40:01 dharma CRON[25573]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)
Mar 11 09:45:01 dharma CRON[26935]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 09:55:01 dharma CRON[27790]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 10:00:01 dharma CRON[28245]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)
Mar 11 10:03:28 dharma smartd[742]: Device: /dev/sdb [SAT], is in STANDBY mode, suspending checks
Mar 11 10:05:01 dharma CRON[29637]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 10:09:01 dharma CRON[29984]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Mar 11 10:37:23 dharma thermald[730]: Read set point 0
Mar 11 10:37:23 dharma thermald[730]: Dropped below poll threshold
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 5:Processor
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 10:intel_powerclamp
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 12:intel_pstate
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 11:rapl_controller
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 5:Processor
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 10:intel_powerclamp
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 12:intel_pstate
Mar 11 10:37:23 dharma thermald[730]: thd_trip_cdev_state_reset index 11:rapl_controller
Mar 11 10:39:01 dharma CRON[1842]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Mar 11 10:40:01 dharma CRON[1953]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)
Mar 11 10:45:01 dharma CRON[3750]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 10:53:48 dharma avahi-daemon[750]: Withdrawing address record for 2000:1010:a12:858b::ff7b on wlp1s0.
Mar 11 10:53:48 dharma avahi-daemon[750]: Leaving mDNS multicast group on interface wlp1s0.IPv6 with address 2000:1010:a12:858b::ff7b.
Mar 11 10:53:48 dharma avahi-daemon[750]: Joining mDNS multicast group on interface wlp1s0.IPv6 with address fe80::8a53:2eff:fe8f:f0ac.
Mar 11 10:55:01 dharma CRON[4656]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 10:59:20 dharma systemd-timesyncd[598]: Timed out waiting for reply from [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com).
Mar 11 10:59:20 dharma systemd-timesyncd[598]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Mar 11 11:00:01 dharma CRON[5138]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)
Mar 11 11:05:01 dharma CRON[6478]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 11:09:01 dharma CRON[6815]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)
Mar 11 11:15:01 dharma CRON[7361]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 11 11:17:01 dharma CRON[7546]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)



```

---

### Post by habana on 2016-03-16
Hi

I'm no expert but there seems to be a warning about dnsmasq in your log. See my recent thread [http://ubuntuforums.org/showthread.php?t=2317186](http://ubuntuforums.org/showthread.php?t=2317186)

It might be worth disabling it and it's easy to reverse if it doesn't fix your problem

Good luck
Bill

---

