---
title: "ubuntu edgy, madwifi-ng and orinoco"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by braincat on 2007-01-13
I am trying to connect a laptop (T23 Thinkpad) running Ubuntu Edgy with
latest svn madwifi drivers, to an access point WRT54GL.  The laptop is
using PCMCIA card, Orinoco Gold 802.11a/b, model 8460-03.
The card never associates.  I doubt there is anything wrong with hardware,
the card connects fine in Windows and FreeBSD6.
The command I am using is:
iwconfig ath0 essid kot enc 3456789012 restricted channel 6

Thanks.

Here is the 80211debug output:

Jan 13 09:43:43 kitten kernel: [17212833.040000]  080 ^ 00:18:39:c1:ca:a5 00:18:39:c1:ca:a5    6   +
50  11M   ess  wep  "kot"
Jan 13 09:43:43 kitten kernel: [17212833.040000]  010 - 00:0c:41:74:8f:db 00:0c:41:74:8f:db    6   +
25  11M   ess  wep  0x00000000000000!
Jan 13 09:43:43 kitten kernel: [17212833.040000]  110 - 00:11:50:0a:50:01 00:11:50:0a:50:01    6    
+7! 11M   ess  wep  "Ry Guy"!
Jan 13 09:43:43 kitten kernel: [17212833.044000] ath0: sta_pick_bss: select_bss failed
Jan 13 09:43:43 kitten kernel: [17212833.044000] ath0: scan_next: done, restart [jiffies 8240965, dw
ell min 5 scanend 2155723921]
Jan 13 09:43:43 kitten kernel: [17212833.044000] ath0: scan_next: chan   6b ->   1b [active, dwell m
in 5 max 50]
Jan 13 09:43:43 kitten kernel: [17212833.048000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 3
Jan 13 09:43:43 kitten kernel: [17212833.048000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 1
Jan 13 09:43:43 kitten kernel: [17212833.048000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 3
Jan 13 09:43:43 kitten kernel: [17212833.048000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 4
Jan 13 09:43:43 kitten kernel: [17212833.048000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 1
Jan 13 09:43:43 kitten kernel: [17212833.048000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 4
Jan 13 09:43:43 kitten kernel: [17212833.052000] ath0: received probe_resp from 00:14:51:78:6b:f1 rs
si 12
Jan 13 09:43:43 kitten kernel: [17212833.052000] [ath0:00:14:51:78:6b:f1] discard unhandled informat
ion element, id 47, len 1
Jan 13 09:43:43 kitten kernel: [17212833.052000] [00:14:51:78:6b:f1] new probe_resp on chan 1 (bss c
han 1) "Apple Network 786bf1"
Jan 13 09:43:43 kitten kernel: [17212833.052000] [00:14:51:78:6b:f1] caps 0x1 bintval 100 erp 0x3
Jan 13 09:43:43 kitten kernel: [17212833.068000] ath0: received beacon from 00:0f:b5:ab:74:e2 rssi 1
3
Jan 13 09:43:43 kitten kernel: [17212833.068000] [ath0:00:0f:b5:ab:74:e2] discard unhandled informat
ion element, id 47, len 1
Jan 13 09:43:43 kitten kernel: [17212833.068000] [00:0f:b5:ab:74:e2] new beacon on chan 1 (bss chan 
1) "urban13"
Jan 13 09:43:43 kitten kernel: [17212833.068000] [00:0f:b5:ab:74:e2] caps 0x401 bintval 100 erp 0x6
Jan 13 09:43:43 kitten kernel: [17212833.068000] ath0: ieee80211_add_scan: chan   1b min dwell met (
8240971 > 8240971)
Jan 13 09:43:43 kitten kernel: [17212833.072000] ath0: scan_next: chan   1b ->   6b [active, dwell m
in 5 max 50]
Jan 13 09:43:43 kitten kernel: [17212833.076000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 3
Jan 13 09:43:43 kitten kernel: [17212833.076000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 6
Jan 13 09:43:43 kitten kernel: [17212833.076000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 3
Jan 13 09:43:43 kitten kernel: [17212833.076000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 4
Jan 13 09:43:43 kitten kernel: [17212833.076000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 6
Jan 13 09:43:43 kitten kernel: [17212833.076000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 4
Jan 13 09:43:43 kitten kernel: [17212833.080000] ath0: received probe_resp from 00:13:10:f6:d7:c3 rs
si 22
Jan 13 09:43:43 kitten kernel: [17212833.080000] [ath0:00:13:10:f6:d7:c3] discard unhandled informat
ion element, id 47, len 1
Jan 13 09:43:43 kitten kernel: [17212833.080000] [00:13:10:f6:d7:c3] new probe_resp on chan 6 (bss c
han 6) "soleshome"
Jan 13 09:43:43 kitten kernel: [17212833.080000] [00:13:10:f6:d7:c3] caps 0x411 bintval 100 erp 0x4
Jan 13 09:43:43 kitten kernel: [17212833.084000] ath0: received probe_resp from 00:18:39:c1:ca:a5 rs
si 51
Jan 13 09:43:43 kitten kernel: [17212833.084000] [ath0:00:18:39:c1:ca:a5] discard unhandled informat
ion element, id 47, len 1
Jan 13 09:43:43 kitten kernel: [17212833.084000] [00:18:39:c1:ca:a5] new probe_resp on chan 6 (bss c
han 6) "kot"
Jan 13 09:43:43 kitten kernel: [17212833.084000] [00:18:39:c1:ca:a5] caps 0x11 bintval 100 erp 0x5
Jan 13 09:43:43 kitten kernel: [17212833.092000] ath0: received beacon from 00:0c:41:74:8f:db rssi 2
Jan 13 09:43:43 kitten kernel: [17212833.092000] [ath0:00:0c:41:74:8f:db] discard unhandled informat
ion element, id 47, len 1
Jan 13 09:43:43 kitten kernel: [17212833.092000] [00:0c:41:74:8f:db] new beacon on chan 6 (bss chan 
6) 0x00000000000000
Jan 13 09:43:43 kitten kernel: [17212833.092000] [00:0c:41:74:8f:db] caps 0x411 bintval 100 erp 0x6
Jan 13 09:43:43 kitten kernel: [17212833.096000] ath0: received beacon from 00:14:95:12:8e:e9 rssi 6
Jan 13 09:43:43 kitten kernel: [17212833.096000] [00:14:95:12:8e:e9] new beacon on chan 6 (bss chan 
6) "2WIRE456"
Jan 13 09:43:43 kitten kernel: [17212833.096000] [00:14:95:12:8e:e9] caps 0x431 bintval 100 erp 0x2 
country info 55 53 20 01 0b 14
Jan 13 09:43:43 kitten kernel: [17212833.096000] ath0: ieee80211_add_scan: chan   6b min dwell met (
8240978 > 8240978)
Jan 13 09:43:43 kitten kernel: [17212833.100000] ath0: scan_next: chan   6b ->  11b [active, dwell m
in 5 max 50]
Jan 13 09:43:43 kitten kernel: [17212833.104000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 3
Jan 13 09:43:43 kitten kernel: [17212833.104000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 11
Jan 13 09:43:43 kitten kernel: [17212833.104000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 3
Jan 13 09:43:43 kitten kernel: [17212833.104000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 4
Jan 13 09:43:43 kitten kernel: [17212833.104000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 11
Jan 13 09:43:43 kitten kernel: [17212833.104000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 4
Jan 13 09:43:43 kitten kernel: [17212833.108000] ath0: received probe_resp from 00:11:50:1a:ad:a7 rs
si 17
Jan 13 09:43:43 kitten kernel: [17212833.108000] [ath0:00:11:50:1a:ad:a7] discard unhandled informat
ion element, id 47, len 1
Jan 13 09:43:43 kitten kernel: [17212833.108000] [00:11:50:1a:ad:a7] new probe_resp on chan 11 (bss 
chan 11) "belkin54g"
Jan 13 09:43:43 kitten kernel: [17212833.108000] [00:11:50:1a:ad:a7] caps 0x1 bintval 100 erp 0x7
Jan 13 09:43:43 kitten kernel: [17212833.124000] ath0: ieee80211_add_scan: chan  11b min dwell met (
8240985 > 8240985)
Jan 13 09:43:43 kitten kernel: [17212833.128000] ath0: scan_next: chan  11b ->   7b [active, dwell m
in 5 max 50]
Jan 13 09:43:43 kitten kernel: [17212833.132000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 3
Jan 13 09:43:43 kitten kernel: [17212833.132000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 7
Jan 13 09:43:43 kitten kernel: [17212833.132000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 3
Jan 13 09:43:43 kitten kernel: [17212833.132000] ath0: ieee80211_ref_node (ieee80211_send_probereq:1
721) d4ed1000<00:18:39:c1:ca:a5> refcnt 4
Jan 13 09:43:43 kitten kernel: [17212833.132000] ath0: [ff:ff:ff:ff:ff:ff] send probe req on channel
 7
Jan 13 09:43:43 kitten kernel: [17212833.132000] ath0: ath_tx_start: d4ed1000<00:18:39:c1:ca:a5> ref
cnt 4
Jan 13 09:43:43 kitten kernel: [17212833.148000] ath0: received probe_resp from 00:18:39:c1:ca:a5 rs
si 52
Jan 13 09:43:43 kitten kernel: [17212833.148000] [ath0:00:18:39:c1:ca:a5] discard unhandled informat
ion element, id 47, len 1

---

### Post by tturrisi on 2007-01-13
Have you tried connecting using net-admin?
System>Administration>Networking
I have same card an no issues using madwifi I built.
/etc/network/interfaces should look like this fior WEP:

iface ath0 inet dhcp
wireless-essid kot
wireless-key 3456789012
auto ath0

and if no joy use:
wireless-key 3456-7890-12

There's no need to specify a channel, it will connect to the channel in use by the ap.

fyi, this card works very well w/ kismet using this in the kismet.conf
source=madwifi_ag,wifi0,madwifi

---

### Post by braincat on 2007-01-13
tturrisi,

thanks, yes, I tried the interfaces file and the admin program.
It's probably a driver issue since the other two systems 
work ok in the same setting.   I can also connect  to one of
my neighbor's wrt54gs AP that has WEP disabled.

---

### Post by braincat on 2007-01-13
...and the mystery solved.    I had to change Authentication Type
in the AP menu to Auto from "Shared Key".    AP is still forced
to use WEP, so I don't understand why this fixed the probem,
but at least it's working now.

---

