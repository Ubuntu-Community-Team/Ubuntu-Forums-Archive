---
title: "acer aspire one, recent update broke wireless"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Ossified65 on 2008-11-26
I just completed the last week or so worth of updates on my girlfriend's aspire one and the wireless broke as a result.  I tried Wicd and Network manager, and neither can find the wireless network.  There is an error during the boot up, but it scrolls by too fast to read. Is this information in a log file somewhere? (the only part of the error I can remember is "wifi%d" then something about hardware not supported)  Was there a kernel upgrade recently? Or Hal maybe?  Let me know what information you need to help and I will post it after work today, thank you!

---

### Post by seren6ipity on 2008-11-26
Is wired network working fine?

---

### Post by FHJay on 2008-11-26
I'm having the same problem as the OP. Wifi was working fine with Madwifi, then after I did an update a couple hours ago, no luck. Tried reinstalling Madwifi, removing then reinstalling, using NDISWrapper, nothing. Internet with a wired connection works fine, but wifi won't pick up any networks. Usually it will pick up a couple neighbors', so I know it's not just my router. Although I'm not running Xubuntu like the OP, I'm running 8.04 standard Ubuntu on an Acer Aspire One 110. Any suggestions would be helpful. Thanks a lot!

---

### Post by seren6ipity on 2008-11-26
Can you please post your wireless card name / network controller here? 
Following command on terminal should bring it up - 
lspci | grep controller

---

### Post by FHJay on 2008-11-26
Response is as follows:

Ethnernet controller: Realtek Semiconductor co., Ltd. RTL8101E PCI Express Fast Ethernet Controller (rev 02)
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by seren6ipity on 2008-11-26
According to this bug [https://bugs.launchpad.net/ubuntu/+bug/209414](https://bugs.launchpad.net/ubuntu/+bug/209414) Atheros 5007 reported incorrectly as "Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter.

Please try to blacklist the card in /etc/modprobe.d/blacklist by adding following line - 
blacklist ath_pci

Reboot and it should work fine.

---

### Post by FHJay on 2008-11-26
Just tried it, didn't work. Don't know why. Tried re-installing and such again, but no go.

---

### Post by seren6ipity on 2008-11-27
Sorry to hear that. See if this helps, good luck.
[http://ubuntuforums.org/showthread.php?t=756318](http://ubuntuforums.org/showthread.php?t=756318)

---

### Post by kaffeboy on 2008-11-27
I just bought my Acer Aspire One and Im wondering if the issue is resolved by installing 8.10 on this little baby? Since I know that Ubuntu 8.10 currently supports this wireless card Out of The Box (It´s the wireless card in my current laptop). Any info would be greatly appreciated.

---

### Post by thor2002ro on 2008-11-27
i got this laptop and no problems what so ever wifi works with linux-backports-modules

---

### Post by FHJay on 2008-11-27
Maybe I'll just try upgrading to 8.10 and see if that makes a difference. I really wish I hadn't updated, it's been nothing but a bother.

---

### Post by vanessa on 2008-11-28
**Update:** now it works. Maybe it is because I've installed linux-backports-modules

--

Same problem here. I was using the madwifi solution before.
Now, when I try modprobe ath_pci I get the following error:

FATAL: Error inserting ath_pci (/lib/modules/2.6.24-22-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg has lots of errors about ieee80211, since I don't know what to look for, here are all of them:

[ 2402.456862] ath_pci: Unknown symbol ieee80211_check_mic
[ 2402.457058] ath_pci: disagrees about version of symbol ieee80211_encap
[ 2402.457066] ath_pci: Unknown symbol ieee80211_encap
[ 2402.457252] ath_pci: disagrees about version of symbol ieee80211_input
[ 2402.457260] ath_pci: Unknown symbol ieee80211_input
[ 2402.457426] ath_pci: disagrees about version of symbol ieee80211_ifattach
[ 2402.457433] ath_pci: Unknown symbol ieee80211_ifattach
[ 2402.457798] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[ 2402.457806] ath_pci: Unknown symbol ieee80211_beacon_update
[ 2402.458076] ath_pci: disagrees about version of symbol ieee80211_find_rxnode
[ 2402.458112] ath_pci: Unknown symbol ieee80211_find_rxnode
[ 2402.458436] ath_pci: Unknown symbol ieee80211_skb_track
[ 2402.458603] ath_pci: Unknown symbol ieee80211_dev_kfree_skb_list
[ 2402.458771] ath_pci: Unknown symbol ieee80211_ref_node
[ 2402.458965] ath_pci: disagrees about version of symbol ieee80211_vap_setup
[ 2402.458973] ath_pci: Unknown symbol ieee80211_vap_setup
[ 2402.459091] ath_pci: disagrees about version of symbol ieee80211_ifdetach
[ 2402.459098] ath_pci: Unknown symbol ieee80211_ifdetach
[ 2402.459286] ath_pci: disagrees about version of symbol ieee80211_input_monitor
[ 2402.459293] ath_pci: Unknown symbol ieee80211_input_monitor
[ 2402.459461] ath_pci: Unknown symbol ieee80211_dev_kfree_skb
[ 2402.459637] ath_pci: Unknown symbol ieee80211_unref_node
[ 2402.459917] ath_pci: disagrees about version of symbol ieee80211_crypto_newkey
[ 2402.459923] ath_pci: Unknown symbol ieee80211_crypto_newkey
[ 2402.460129] ath_pci: disagrees about version of symbol ieee80211_crypto_setkey
[ 2402.460136] ath_pci: Unknown symbol ieee80211_crypto_setkey
[ 2402.460369] ath_pci: disagrees about version of symbol ieee80211_dump_pkt
[ 2402.460375] ath_pci: Unknown symbol ieee80211_dump_pkt
[ 2402.460500] ath_pci: disagrees about version of symbol ieee80211_ioctl_create_vap
[ 2402.460508] ath_pci: Unknown symbol ieee80211_ioctl_create_vap
[ 2402.460733] ath_pci: Unknown symbol ieee80211_dev_alloc_skb
[ 2402.460960] ath_pci: disagrees about version of symbol ieee80211_stop_running
[ 2402.460967] ath_pci: Unknown symbol ieee80211_stop_running
[ 2402.461237] ath_pci: disagrees about version of symbol ieee80211_cipher_none
[ 2402.461247] ath_pci: Unknown symbol ieee80211_cipher_none
[ 2402.461544] ath_pci: disagrees about version of symbol ieee80211_crypto_delkey
[ 2402.461553] ath_pci: Unknown symbol ieee80211_crypto_delkey
[ 2402.461786] ath_pci: Unknown symbol ath_debug_global
[ 2402.461945] ath_pci: Unknown symbol ieee80211_skb_untrack
[ 2402.462211] ath_pci: disagrees about version of symbol ieee80211_beacon_miss
[ 2402.462218] ath_pci: Unknown symbol ieee80211_beacon_miss
[ 2402.462336] ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
[ 2402.462344] ath_pci: Unknown symbol ieee80211_beacon_alloc
[ 2402.462465] ath_pci: disagrees about version of symbol ieee80211_getcfframe
[ 2402.462472] ath_pci: Unknown symbol ieee80211_getcfframe
[ 2402.462601] ath_pci: disagrees about version of symbol ieee80211_iterate_nodes
[ 2402.462608] ath_pci: Unknown symbol ieee80211_iterate_nodes
[ 2402.462752] ath_pci: disagrees about version of symbol ieee80211_vap_attach
[ 2402.462759] ath_pci: Unknown symbol ieee80211_vap_attach
[ 2402.462930] ath_pci: Unknown symbol ieee80211_wme_updateparams
[ 2402.463049] ath_pci: disagrees about version of symbol ieee80211_ibss_merge
[ 2402.463056] ath_pci: Unknown symbol ieee80211_ibss_merge
[ 2402.463670] ath_pci: disagrees about version of symbol ieee80211_rate_attach
[ 2402.463678] ath_pci: Unknown symbol ieee80211_rate_attach
[ 2402.464005] ath_pci: disagrees about version of symbol ieee80211_rate_detach
[ 2402.464013] ath_pci: Unknown symbol ieee80211_rate_detach
[ 2402.464309] ath_pci: disagrees about version of symbol ieee80211_send_qosnulldata
[ 2402.464316] ath_pci: Unknown symbol ieee80211_send_qosnulldata
[ 2402.464449] ath_pci: disagrees about version of symbol ieee80211_create_vap
[ 2402.464456] ath_pci: Unknown symbol ieee80211_create_vap
[ 2402.464796] ath_pci: disagrees about version of symbol ieee80211_input_all
[ 2402.464803] ath_pci: Unknown symbol ieee80211_input_all
[ 2402.465057] ath_pci: disagrees about version of symbol ieee80211_start_running
[ 2402.465065] ath_pci: Unknown symbol ieee80211_start_running
[ 2402.465177] ath_pci: disagrees about version of symbol ieee80211_vap_detach
[ 2402.465184] ath_pci: Unknown symbol ieee80211_vap_detach
[ 2402.465289] ath_pci: disagrees about version of symbol ieee80211_announce
[ 2402.465294] ath_pci: Unknown symbol ieee80211_announce
[ 2402.465397] ath_pci: disagrees about version of symbol ieee80211_mark_dfs
[ 2402.465403] ath_pci: Unknown symbol ieee80211_mark_dfs
[ 2402.465549] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[ 2402.465558] ath_pci: Unknown symbol ieee80211_chan2ieee
[ 2402.466179] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch
[ 2402.466187] ath_pci: Unknown symbol ieee80211_dturbo_switch
[ 2402.466313] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[ 2402.466320] ath_pci: Unknown symbol ieee80211_crypto_encap
[ 2402.466552] ath_pci: disagrees about version of symbol ieee80211_getrssi
[ 2402.466559] ath_pci: Unknown symbol ieee80211_getrssi
[ 2402.466671] ath_pci: disagrees about version of symbol ieee80211_find_txnode
[ 2402.466678] ath_pci: Unknown symbol ieee80211_find_txnode
[ 2402.466861] ath_pci: Unknown symbol ieee80211_cancel_scan

---

