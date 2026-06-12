---
title: "ASUS X553S drops connection, Ubuntu 15.04"
date: 2016-01-24
forum: Networking &amp; Wireless
---

### Post by eugene23 on 2016-01-24
Hi.
I got the issue with Wi-Fi network. After loading Ubuntu ethernet working for a several minutes and after this just stop to send packedges.
System showing me, that connection still exists. I tried to solve this problem by reinstalling the Ubuntu 14.04, install Kernel, but no results.
Here is my Wireless-info list: 

This is what shows lspci
```

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lite-On Communications Inc Device [11ad:1723]
    Kernel driver in use: rtl8723be

```

This is what shows iwconfig
```

wlp3s0    IEEE 802.11bgn  ESSID:"Balalaika"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:CC:20:6B:95:4E   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:140   Missed beacon:0

```

---

