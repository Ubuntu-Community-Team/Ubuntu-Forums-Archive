---
title: "RTL8180L Driver doesn't work with encryption!"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by saman_b on 2007-10-02
Hello guys, 
I have a linksys wireless card with rtl8185v driver. I have upgraded to Gusty , the rtl8180l loads successfully and works fine if I don't use any encryption. but when I start to use the encryption using wpa_supplicant it hangs out and the system halts with caps luck light start to flashing. it gives the message : rtl8180 : WW:Phy writing 3 25 failed. 
I've found this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/129407")
related to this issue, I'll try to use [this manual]("http://rtl-wifi.sourceforge.net/wiki/Installing") and I'll inform you if it worked.:confused:

---

### Post by saman_b on 2007-10-03
I have tried to compile r8180 + ieee80211_rtl* modules from [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing), on my gutsy gibbon : 
> $ uname -r
2.6.22-12-generic
ieee80211_rtl* was compiled successfully , but could not compile rtl818x-newstack when I use the last version : 
> 
make -C /lib/modules/2.6.22-12-generic/build M=/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack CC=gcc-4.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-12-generic'
  CC [M]  /home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.o
In file included from /home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180.h:50,
                 from /home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:63:
include/net/ieee80211softmac.h: In function ‘ieee80211softmac_priv’:
include/net/ieee80211softmac.h:260: warning: implicit declaration of function ‘ieee80211_priv’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘proc_get_stats_rx’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:390: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:391: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘proc_get_stats_tx’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:505: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:506: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘get_curr_tx_free_desc’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:730: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘check_nic_enought_desc’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:773: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:776: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:776: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_hdr_3addr’ 
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘fix_tx_fifo’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:963: warning: implicit declaration of function ‘ieee80211_reset_queue’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_update_msr’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1194: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1200: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1202: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1204: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1206: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_rx_enable’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1245: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1259: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1265: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_rtx_disable’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1460: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_rx’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1868: error: variable ‘stats’ has initializer but incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1869: error: unknown field ‘signal’ specified in initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1869: warning: excess elements in struct initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1869: warning: (near initialization for ‘stats’)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1870: error: unknown field ‘noise’ specified in initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1870: warning: excess elements in struct initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1870: warning: (near initialization for ‘stats’)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1871: error: unknown field ‘rate’ specified in initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1871: warning: excess elements in struct initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1871: warning: (near initialization for ‘stats’)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1873: error: unknown field ‘freq’ specified in initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1873: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1873: error: (Each undeclared identifier is reported only once
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1873: error: for each function it appears in.)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1873: warning: excess elements in struct initializer
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1873: warning: (near initialization for ‘stats’)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1868: error: storage size of ‘stats’ isn’t known
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1886: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1995: error: ‘MAX_FRAG_THRESHOLD’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2061: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2156: warning: implicit declaration of function ‘ieee80211_rx’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:1868: warning: unused variable ‘stats’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_hard_data_xmit’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2306: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2309: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2325: warning: passing argument 1 of ‘ieee80211_stop_queue’ from incompatible pointer type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2325: error: too few arguments to function ‘ieee80211_stop_queue’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2329: warning: passing argument 1 of ‘ieee80211_stop_queue’ from incompatible pointer type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2329: error: too few arguments to function ‘ieee80211_stop_queue’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_hard_start_xmit’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2356: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2358: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2359: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_prepare_beacon’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2426: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2430: warning: implicit declaration of function ‘ieee80211_get_beacon’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2430: warning: assignment makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2433: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_tx’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2478: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_link_change’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2698: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2701: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2708: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2709: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2714: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_rq_tx_ack’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2757: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_is_tx_queue_empty’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2764: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_hw_wakeup’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2788: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_hw_sleep’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2804: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_init’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2857: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2887: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2918: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2919: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2920: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2920: error: ‘IEEE_SOFTMAC_SCAN’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2921: error: ‘IEEE_SOFTMAC_ASSOCIATE’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2921: error: ‘IEEE_SOFTMAC_PROBERQ’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2922: error: ‘IEEE_SOFTMAC_PROBERS’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2922: error: ‘IEEE_SOFTMAC_TX_QUEUE’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2923: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2924: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2925: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2925: error: ‘IEEE80211_CCK_MODULATION’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2926: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2927: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2928: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2929: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2930: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2931: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2956: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2957: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2958: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2959: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2960: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2961: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2962: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2963: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:2964: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3000: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3000: error: ‘IEEE80211_OFDM_MODULATION’ undeclared (first use in this function)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3001: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3268: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_no_hw_wep’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3288: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_set_hw_wep’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3314: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_adapter_start’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3526: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3627: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_stats’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3728: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3730: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘_rtl8180_up’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3736: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3747: warning: implicit declaration of function ‘ieee80211_softmac_start_protocol’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_open’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3755: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_up’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3768: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_close’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3778: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_down’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3791: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3804: warning: implicit declaration of function ‘ieee80211_softmac_stop_protocol’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_restart’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3823: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_commit’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3832: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘r8180_set_multicast’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3845: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘r8180_set_mac_adr’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3877: warning: initialization makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3884: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3885: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3885: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_ioctl’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3906: warning: implicit declaration of function ‘ieee80211_wpa_supplicant_ioctl’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3947: warning: implicit declaration of function ‘alloc_ieee80211’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3947: warning: assignment makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3950: warning: assignment makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:3958: warning: assignment makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4075: warning: implicit declaration of function ‘free_ieee80211’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_pci_remove’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4095: warning: assignment makes pointer from integer without a cast
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_try_wake_queue’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4180: warning: passing argument 1 of ‘ieee80211_wake_queue’ from incompatible pointer type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4180: error: too few arguments to function ‘ieee80211_wake_queue’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_tx_isr’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4329: warning: implicit declaration of function ‘ieee80211_ps_tx_ack’
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c: In function ‘rtl8180_interrupt’:
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4434: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4464: error: dereferencing pointer to incomplete type
/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.c:4477: error: dereferencing pointer to incomplete type
make[2]: *** [/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack/r8180_core.o] Error 1
make[1]: *** [_module_/home/saman/Documents/svn/rtl-wifi/rtl818x-newstack] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-12-generic'
make: *** [modules] Error 2



I tried other versions that told to be stable but some other errors appeared. could anyone compile it with 2.6.22 ?

---

### Post by vogeljh on 2007-11-26
I got the same error attempting to build rtl818x-newstack.  Not seeing a response, I am wondering if anyone knows the solution.  Thanks for your help!

---

### Post by kevdog on 2007-11-26
I dont know if this is going to help, however have you tried compiling a new kernel.  I think the rtl8180 drivers are in the kernel.  The master kernel thread may help.

---

