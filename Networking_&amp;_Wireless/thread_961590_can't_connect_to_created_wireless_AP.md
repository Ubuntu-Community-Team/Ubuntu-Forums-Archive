---
title: "can't connect to created wireless AP"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by shashilx on 2008-10-28
I have Dlink DWA-520 (Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)) and successfully configured card using madwifi-0.9.4 in Ubuntu 8.04 but other devices not see created network.
```
ath0      IEEE 802.11g  ESSID:"shashilx"  Nickname:""
          Mode:Master  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath0      Link encap:Ethernet  HWaddr 06:21:91:23:79:1a
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::421:91ff:fe23:791a/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-21-91-23-79-1A-00-00-00-00-00-00-00-00-00-00
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:16
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:280
          RX bytes:3289 (3.2 KB)  TX bytes:224 (224.0 B)

root@shashilx:~# dmesg|grep ath
[   55.524942] ath_hal: module license 'Proprietary' taints kernel.
[   57.755433] MadWifi: ath_attach: Switching rfkill capability off.
[   58.569949] ath_pci: wifi0: Atheros 5212: mem=0xf5000000, irq=20
[   84.879227] ath0: no IPv6 routers present


```

Is there anyone who can help with this problem?

---

