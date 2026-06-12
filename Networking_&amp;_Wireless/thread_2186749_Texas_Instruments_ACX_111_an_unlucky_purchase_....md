---
title: "Texas Instruments ACX 111: an unlucky purchase ..."
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by caesar753 on 2013-11-08
Hello everybody,
few days ago i bought on ebay an used u.s. robotics wireless PCI card (model 5416).
When i put it into my (old) computer i discovered that the onboard chipset was a Texas Instruments ACX 111.
Googling around i found that this chipset is quite not supported (since 2004) by any linux distribution and i tried to find a way to get my "new" wireless card working.

1) tried to install ndiswrapper (btw. ndiswrapper deb package in ubuntu 12.04 is buggy, so i had to compile it by hand) and use Windows driver: if i have an unprotected network, the card works, but if i use wep or wpa encryption it does not (from dmesg i can understand that the wep/wpa key is used and works, but then it cannot obtain an IP address)

2) tried to compile acx100 driver (from [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)), got a way through git repository, but also this ("native") driver does not work with wep encryption (wpa is not supported)

Do you know something about this card? Is there a way to get it working?

Thanks!

---

### Post by caesar753 on 2013-11-08
btw this is dmesg output with ndiswrapper

```

[  278.946640] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  279.010424] ndiswrapper: driver tnet1130 (PLANEX COMMUNICATIONS INC.,03/10/2004,6.0.0.18) loaded
[  279.633924] ndiswrapper: using IRQ 11
[  279.868331] wlan0: ethernet device 00:c0:49:cb:fa:d7 using NDIS driver: tnet1130, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[  279.868500] wlan0: encryption modes supported: WEP; TKIP with WPA
[  279.868754] usbcore: registered new interface driver ndiswrapper
[  279.889000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  279.894241] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  420.454399] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

and this is that with acx100

```

[   86.228049] acx.acx_op_hw_scan: scan start
[   88.498135] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   88.900607] acx.acx_irq_work: scan completed
[   88.905052] wlan0: authenticate with 02:18:f8:7a:4b:43
[   88.905081] acx.acx1xx_update_tx: Updating TX: enable, channel=9
[   88.912057] acx.acx1xx_update_rx: Updating RX: enable, channel=9
[   88.920059] acx.acx_op_bss_info_changed: Join following bssid update
[   88.920069] acx.acx_cmd_join_bssid: rates_basic:0003, rates_supported:1FFF
[   88.928047] acx.acx_cmd_join_bssid: BSS_Type = 2
[   88.928056] acx.acx_print_mac2: JoinBSSID MAC:02:18:F8:7A:4B:43
[   88.928132] wlan0: send auth to 02:18:f8:7a:4b:43 (try 1/3)
[   88.930465] wlan0: authenticated
[   88.930712] acx.acx1xx_update_tx: Updating TX: enable, channel=9
[   88.936047] acx.acx1xx_update_rx: Updating RX: enable, channel=9
[   88.948054] wlan0: associate with 02:18:f8:7a:4b:43 (try 1/3)
[   89.152017] wlan0: associate with 02:18:f8:7a:4b:43 (try 2/3)
[   89.154154] wlan0: RX AssocResp from 02:18:f8:7a:4b:43 (capab=0x411 status=0 aid=1)
[   89.154385] wlan0: associated
[   89.155983] acx.acx_op_set_key: algorithm=4: ACX_SEC_ALGO_WEP104
[   89.155990] acx.acx_update_hw_encryption: Disabling hw-encryption
[   89.155994] acx.acx_interrogate: (type:ACX1xx_IE_FEATURE_CONFIG,len:8)
[   98.581847] wlan0: deauthenticating from 02:18:f8:7a:4b:43 by local choice (reason=3)
[   98.581953] acx.acx_op_bss_info_changed: Join following bssid update
[   98.583168] cfg80211: All devices are disconnected, going to restore regulatory settings
[   98.583175] cfg80211: Restoring regulatory settings
[   98.583180] cfg80211: Calling CRDA to update world regulatory domain
[   98.601572] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   98.601579] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   98.601583] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   98.601585] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   98.601587] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   98.601590] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

---

### Post by caesar753 on 2013-11-09
and this is my syslog

```

Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Auto-activating connection 'prova_wpa'.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) starting connection 'prova_wpa'
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0/wireless): access point 'prova_wpa' has security, but secrets are required.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0/wireless): connection 'prova_wpa' has security, and secrets exist.  No new secrets needed.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Config: added 'ssid' value 'prova_wpa'
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Config: added 'scan_ssid' value '1'
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Config: added 'key_mgmt' value 'NONE'
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Config: added 'wep_key0' value '<omitted>'
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Config: added 'wep_tx_keyidx' value '0'
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> Config: set interface ap_scan to 1
Nov  9 17:34:58 finallyhome kernel: [  179.024063] acx.acx_op_hw_scan: scan start
Nov  9 17:34:58 finallyhome NetworkManager[900]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov  9 17:35:00 finallyhome kernel: [  181.294413] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
Nov  9 17:35:01 finallyhome wpa_supplicant[1096]: Trying to authenticate with 02:18:f8:7a:4b:43 (SSID='prova_wpa' freq=2452 MHz)
Nov  9 17:35:01 finallyhome kernel: [  181.594187] acx.acx_irq_work: scan completed
Nov  9 17:35:01 finallyhome kernel: [  181.594766] wlan0: authenticate with 02:18:f8:7a:4b:43
Nov  9 17:35:01 finallyhome kernel: [  181.594789] acx.acx1xx_update_tx: Updating TX: enable, channel=9
Nov  9 17:35:01 finallyhome kernel: [  181.600022] acx.acx1xx_update_rx: Updating RX: enable, channel=9
Nov  9 17:35:01 finallyhome kernel: [  181.608023] acx.acx_op_bss_info_changed: Join following bssid update
Nov  9 17:35:01 finallyhome kernel: [  181.608029] acx.acx_cmd_join_bssid: rates_basic:0003, rates_supported:1FFF
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov  9 17:35:01 finallyhome wpa_supplicant[1096]: Trying to associate with 02:18:f8:7a:4b:43 (SSID='prova_wpa' freq=2452 MHz)
Nov  9 17:35:01 finallyhome kernel: [  181.616039] acx.acx_cmd_join_bssid: BSS_Type = 2
Nov  9 17:35:01 finallyhome kernel: [  181.616048] acx.acx_print_mac2: JoinBSSID MAC:02:18:F8:7A:4B:43
Nov  9 17:35:01 finallyhome kernel: [  181.616111] wlan0: send auth to 02:18:f8:7a:4b:43 (try 1/3)
Nov  9 17:35:01 finallyhome kernel: [  181.618327] wlan0: authenticated
Nov  9 17:35:01 finallyhome kernel: [  181.618544] acx.acx1xx_update_tx: Updating TX: enable, channel=9
Nov  9 17:35:01 finallyhome kernel: [  181.624017] acx.acx1xx_update_rx: Updating RX: enable, channel=9
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov  9 17:35:01 finallyhome wpa_supplicant[1096]: Associated with 02:18:f8:7a:4b:43
Nov  9 17:35:01 finallyhome wpa_supplicant[1096]: CTRL-EVENT-CONNECTED - Connection to 02:18:f8:7a:4b:43 completed (reauth) [id=0 id_str=]
Nov  9 17:35:01 finallyhome kernel: [  181.636551] wlan0: associate with 02:18:f8:7a:4b:43 (try 1/3)
Nov  9 17:35:01 finallyhome kernel: [  181.638712] wlan0: RX AssocResp from 02:18:f8:7a:4b:43 (capab=0x411 status=0 aid=1)
Nov  9 17:35:01 finallyhome kernel: [  181.638967] wlan0: associated
Nov  9 17:35:01 finallyhome kernel: [  181.640710] acx.acx_op_set_key: algorithm=4: ACX_SEC_ALGO_WEP104
Nov  9 17:35:01 finallyhome kernel: [  181.640715] acx.acx_update_hw_encryption: Disabling hw-encryption
Nov  9 17:35:01 finallyhome kernel: [  181.640718] acx.acx_interrogate: (type:ACX1xx_IE_FEATURE_CONFIG,len:8)
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> (wlan0): supplicant interface state: associating -> completed
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'prova_wpa'.
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> dhclient started with pid 1996
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov  9 17:35:01 finallyhome dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  9 17:35:01 finallyhome dhclient: Copyright 2004-2011 Internet Systems Consortium.
Nov  9 17:35:01 finallyhome dhclient: All rights reserved.
Nov  9 17:35:01 finallyhome dhclient: For info, please visit https://www.isc.org/software/dhcp/
Nov  9 17:35:01 finallyhome dhclient: 
Nov  9 17:35:01 finallyhome dhclient: Listening on LPF/wlan0/00:c0:49:cb:fa:d7
Nov  9 17:35:01 finallyhome NetworkManager[900]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov  9 17:35:01 finallyhome dhclient: Sending on   LPF/wlan0/00:c0:49:cb:fa:d7
Nov  9 17:35:01 finallyhome dhclient: Sending on   Socket/fallback
Nov  9 17:35:01 finallyhome dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov  9 17:35:02 finallyhome NetworkManager[900]: <info> (wlan0): device state change: ip-config -> unavailable (reason 'none') [70 20 0]
Nov  9 17:35:02 finallyhome NetworkManager[900]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov  9 17:35:02 finallyhome NetworkManager[900]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1996
Nov  9 17:35:02 finallyhome NetworkManager[900]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Nov  9 17:35:02 finallyhome NetworkManager[900]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Nov  9 17:35:02 finallyhome NetworkManager[900]: <info> (wlan0): taking down device.
Nov  9 17:35:02 finallyhome wpa_supplicant[1096]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Nov  9 17:35:02 finallyhome kernel: [  183.120660] wlan0: deauthenticating from 02:18:f8:7a:4b:43 by local choice (reason=3)
Nov  9 17:35:02 finallyhome kernel: [  183.120747] acx.acx_op_bss_info_changed: Join following bssid update
Nov  9 17:35:02 finallyhome kernel: [  183.122043] cfg80211: All devices are disconnected, going to restore regulatory settings
Nov  9 17:35:02 finallyhome kernel: [  183.122051] cfg80211: Restoring regulatory settings
Nov  9 17:35:02 finallyhome kernel: [  183.122057] cfg80211: Calling CRDA to update world regulatory domain
Nov  9 17:35:02 finallyhome kernel: [  183.129763] acx.acx_update_mode: Updating to mode=0x00ff
Nov  9 17:35:02 finallyhome kernel: [  183.129770] acx.acx1xx_update_tx: Updating TX: disable, channel=9

```

it seems that, for some reasons, dhcp doesn't work.
Any idea?

---

