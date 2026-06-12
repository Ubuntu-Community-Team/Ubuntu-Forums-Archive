---
title: "Atheros AR9462 weak connection"
date: 2017-04-18
forum: Networking &amp; Wireless
---

### Post by grfokpr on 2017-04-18
Problems i'm having is weak wi-fi connection, compared to Windows my speed drops by 80-90%. any suggestions?

lspci -nnk | grep -iA3 net
0d:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Lite-On Communications Inc AR9462 Wireless Network Adapter [11ad:6621]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
0e:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Acer Incorporated [ALI] AR8151 v2.0 Gigabit Ethernet [1025:0686]
	Kernel driver in use: atl1c
	Kernel modules: atl1c

---

