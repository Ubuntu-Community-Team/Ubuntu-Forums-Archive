---
title: "Persistent, brief wifi drops. Ubuntu 19.10, HP Envy x360, Realtek RTL8822BE"
date: 2020-04-30
forum: Networking &amp; Wireless
---

### Post by bandar-the-druid on 2020-04-30
[COLOR=#242729][FONT=Arial]I'm using my internal network card, has worked with no issues for months. No other devices on the network are experiencing drops. I changed the Wifi channel and checked for driver updates (none), reinstalled the drivers just in case. Drop happens every 2-3 minutes. It is brief enough that it only causes disruption when I'm livestreaming video or playing online games. [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My network card: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I ran journalctl --follow and screenshot the output when a drop occurred (attached image). 
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I don't really know what it means though. This line caught my eye: WARNING: CPU: 2 PID: 27181 at drivers/net/wireless/realtek/rtw88/phy.c:1590 rtw_get_tx_power_params+0x288/0x680 [rtw88][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]And of course the text in red.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I looked up process 27181: 0.1 0.1 14104 8624 Ss 15:20 0:21 /sbin/wpa_supplicant -u -s -O /run/wpa_supplicant[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Can anyone tell me what any of this means?[/FONT][/COLOR]

---

### Post by jeremy31 on 2020-04-30
Please see the wireless script link in my signature and post results

---

