---
title: "Madwifi with AR5006EG - installation issues"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by smooveg on 2008-02-02
So I've received some errors in my dmesg, although the install went fine -- was wondering if someone could help diagnose the issues??

Running Ubuntu 7.10, so I disabled restricted drivers from running ath_hal, then rebooted, then installed.

lspci -d 168c:001c
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Install snapshot: [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz) (see this madwifi ticket: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679))

I used this snapshot because of the reported issues with lspci reporting the 5007 as 5006, and also the compatibility reports that show users having success with this snapshot and a 5006 chipset.

Here is my selected dmesg output, and thanks in advance!

[   13.544000] wlan: 0.8.4.2 (0.9.3.2)
[   13.564000] ath_pci: Unknown symbol _ath_hal_attach
[   13.564000] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   13.564000] ath_pci: Unknown symbol ath_hal_computetxtime
[   13.568000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   13.568000] ath_pci: Unknown symbol ath_hal_detach
[   13.568000] ath_pci: Unknown symbol ath_hal_probe
[   13.568000] ath_pci: Unknown symbol ath_hal_init_channels
[   13.568000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[ 4324.716000] ath_hal: module license 'Proprietary' taints kernel.
[ 4324.720000] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_encap
[ 4324.720000] ath_pci: Unknown symbol ieee80211_encap
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_input
[ 4324.720000] ath_pci: Unknown symbol ieee80211_input
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_ifattach
[ 4324.720000] ath_pci: Unknown symbol ieee80211_ifattach
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[ 4324.720000] ath_pci: Unknown symbol ieee80211_beacon_update
[ 4324.720000] ath_pci: Unknown symbol _ieee80211_free_node
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_vap_setup
[ 4324.720000] ath_pci: Unknown symbol ieee80211_vap_setup
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_ifdetach
[ 4324.720000] ath_pci: Unknown symbol ieee80211_ifdetach
[ 4324.720000] ath_pci: Unknown symbol ieee80211_find_txnode_debug
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_input_monitor
[ 4324.720000] ath_pci: Unknown symbol ieee80211_input_monitor
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_crypto_newkey
[ 4324.720000] ath_pci: Unknown symbol ieee80211_crypto_newkey
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_crypto_setkey
[ 4324.720000] ath_pci: Unknown symbol ieee80211_crypto_setkey
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_dump_pkt
[ 4324.720000] ath_pci: Unknown symbol ieee80211_dump_pkt
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_ioctl_create_vap
[ 4324.720000] ath_pci: Unknown symbol ieee80211_ioctl_create_vap
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_stop_running
[ 4324.720000] ath_pci: Unknown symbol ieee80211_stop_running
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_cipher_none
[ 4324.720000] ath_pci: Unknown symbol ieee80211_cipher_none
[ 4324.720000] ath_pci: disagrees about version of symbol ieee80211_note
[ 4324.720000] ath_pci: Unknown symbol ieee80211_note
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_crypto_delkey
[ 4324.724000] ath_pci: Unknown symbol ieee80211_crypto_delkey
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_beacon_miss
[ 4324.724000] ath_pci: Unknown symbol ieee80211_beacon_miss
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
[ 4324.724000] ath_pci: Unknown symbol ieee80211_beacon_alloc
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_getcfframe
[ 4324.724000] ath_pci: Unknown symbol ieee80211_getcfframe
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_iterate_nodes
[ 4324.724000] ath_pci: Unknown symbol ieee80211_iterate_nodes
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_vap_attach
[ 4324.724000] ath_pci: Unknown symbol ieee80211_vap_attach
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_ibss_merge
[ 4324.724000] ath_pci: Unknown symbol ieee80211_ibss_merge
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_rate_attach
[ 4324.724000] ath_pci: Unknown symbol ieee80211_rate_attach
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_rate_detach
[ 4324.724000] ath_pci: Unknown symbol ieee80211_rate_detach
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_send_qosnulldata
[ 4324.724000] ath_pci: Unknown symbol ieee80211_send_qosnulldata
[ 4324.724000] ath_pci: Unknown symbol ieee80211_find_rxnode_debug
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_create_vap
[ 4324.724000] ath_pci: Unknown symbol ieee80211_create_vap
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_input_all
[ 4324.724000] ath_pci: Unknown symbol ieee80211_input_all
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_start_running
[ 4324.724000] ath_pci: Unknown symbol ieee80211_start_running
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_vap_detach
[ 4324.724000] ath_pci: Unknown symbol ieee80211_vap_detach
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_announce
[ 4324.724000] ath_pci: Unknown symbol ieee80211_announce
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[ 4324.724000] ath_pci: Unknown symbol ieee80211_chan2ieee
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch
[ 4324.724000] ath_pci: Unknown symbol ieee80211_dturbo_switch
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[ 4324.724000] ath_pci: Unknown symbol ieee80211_crypto_encap
[ 4324.724000] ath_pci: disagrees about version of symbol ieee80211_getrssi
[ 4324.724000] ath_pci: Unknown symbol ieee80211_getrssi
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_find_channel
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_find_channel
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_scan_dump_channels
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_scan_dump_channels
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_create_ibss
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_create_ibss
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_note
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_note
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_start_scan
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_start_scan
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_sta_join
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_sta_join
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_note_mac
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_note_mac
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_scanner_register
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_scanner_register
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_chan2ieee
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_chan2ieee
[ 4353.972000] wlan_scan_sta: disagrees about version of symbol ieee80211_scanner_unregister_all
[ 4353.972000] wlan_scan_sta: Unknown symbol ieee80211_scanner_unregister_all

---

### Post by Stoneface on 2008-07-14
I have similar problems. I asked my question in the madwifi mail group. If I get news I will let you know...

---

### Post by Stoneface on 2008-07-14
I had to madwifi installations running and some modules were blocking each other. Check all your Atheros modules using:```
find /lib/modules/`uname -r` -name 'ath*'
``` to see if there is a conflict (modules in two or more different folders (net/madwifi and or others). In that case a new install will be necessary. You will have to remove all madwifi modules installed first though.
Pavel at Gmane explained ```
 dpkg -S /lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko
``` (your kernel version might be different so in that case you will have to change the command accordingly) showed what package had to be removed in Synaptic Package manager. Actually he is the expert you should talk to if my help doesn't pan out Here is the [link]("http://news.gmane.org/gmane.linux.drivers.madwifi.user").

Good luck!

---

