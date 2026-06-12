---
title: "Panda Wireless PAU09 - Problem Establishing Connection to Wireless Networks"
date: 2018-01-05
forum: Networking &amp; Wireless
---

### Post by tmactharulah on 2018-01-05
[COLOR=#000000][I]*Posting my question and my resolve to potentially help others in the future*

I just got a PAU09 (Panda Wireless) 802.11 adapter with an Ralink Technology, Corp. RT5572 Chipset in Bus 001 Device 002: ID 148f:5572. I'm having trouble getting the wireless to establish a connection with the PnP that they claim. [/I][/COLOR]

[COLOR=#000000]*Some Info:*[/COLOR]
[COLOR=#000000]*There is no built in wireless nic for my Mobo so there shouldn't be interference there. The adapter is recognizing SSIDs after being plugged in, which without it, it doesn't. I tried to connect to my home 2.4 network and it won't connect. I've tried to establish the connection with, and without some eth plugged into my desktop.*[/COLOR]

[COLOR=#000000]*I think I need a driver update but I do not know how to do so. *[/COLOR]


> [COLOR=#000000]*lsmod | grep rt *[/COLOR]

[COLOR=#000000]*rt2800usb 28672 0*[/COLOR]
[COLOR=#000000]*rt2x00usb 20480 1 rt2800usb*[/COLOR]
[COLOR=#000000]*rt2800lib 94208 1 rt2800usb*[/COLOR]
[COLOR=#000000]*rt2x00lib 53248 3 rt2800lib,rt2800usb,rt2x00usb*[/COLOR]
[COLOR=#000000]*mac80211 782336 3 rt2800lib,rt2x00lib,rt2x00usb*[/COLOR]
[COLOR=#000000]*cfg80211 602112 2 rt2x00lib,mac80211*[/COLOR]
[COLOR=#000000]*hci_uart 98304 0*[/COLOR]
[COLOR=#000000]*btbcm 16384 1 hci_uart*[/COLOR]
[COLOR=#000000]*btqca 16384 1 hci_uart*[/COLOR]
[COLOR=#000000]*btintel 16384 1 hci_uart*[/COLOR]
[COLOR=#000000]*bluetooth 557056 11 hci_uart,btintel,btqca,bnep,btbcm*[/COLOR]
[COLOR=#000000]*ip6t_rt 16384 3*[/COLOR]
[COLOR=#000000]*scsi_transport_iscsi 98304 4 ib_iser,libiscsi,iscsi_tcp*[/COLOR]
[COLOR=#000000]*xt_addrtype 16384 4*[/COLOR]
[COLOR=#000000]*parport_pc 32768 1*[/COLOR]
[COLOR=#000000]*parport 49152 3 lp,parport_pc,ppdev*[/COLOR]
[COLOR=#000000]*x_tables 36864 17 xt_LOG,ipt_REJECT,iptable_mangle,ip_tables,ebtable s,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_limit ,ip6t_REJECT,xt_CHECKSUM,ip6table_filter,xt_addrty pe,ip6t_rt,xt_conntrack,ip6_tables,xt_hl*[/COLOR][COLOR=#000000][/COLOR]

---

### Post by tmactharulah on 2018-01-05
Resolve:

Please update Ubuntu to 17.10 or to the LTS 16.04. 17.04 has has an unresolved bug in Network Manager and is going EOL at the end of this month.

---

