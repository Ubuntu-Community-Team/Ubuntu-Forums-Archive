---
title: "Wireless trouble"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by brushtop on 2011-01-27
Did the usual updates this evening.  Never had a problem before.... however... today, after the updates (as they are normally so good and reliable I kind of just clicked ok without reading them... ooops), I have since have difficulty associating with my access point.  I have 2 AP's in my house, and they are all in good order.  Anyone had trouble?  What makes this stranger is the fact I can eventually get associated if I repeatedly attempt, so the behavior of my machine is not consistent - saying that, once I am on, I am on and seemingly stable.  So being a newbie etc. - this stage seems to be the weakest link in the process?  I dug out some commands from a separate thread that looks useful (although it looks like I am associating with a completely different AP fro some unknown reason -  HELP!!!)

nsheridan@GRV-LPT-002:~$ uname -a
Linux GRV-LPT-002 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux
nsheridan@GRV-LPT-002:~$ 

nsheridan@GRV-LPT-002:~$ dmesg | grep iw 
[   15.001784] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.001787] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   15.001872] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.001902] iwlagn 0000:0e:00.0: setting latency timer to 64
[   15.001958] iwlagn 0000:0e:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   15.028695] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.028826] iwlagn 0000:0e:00.0: irq 49 for MSI/MSI-X
[   15.043341] iwlagn 0000:0e:00.0: loaded firmware version 8.24.2.12
[   16.035625] phy0: Selected rate control algorithm 'iwl-agn-rs'
nsheridan@GRV-LPT-002:~$ 


     description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:56:31:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-25-generic-pae firmware=8.24.2.12 ip=192.168.1.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:49 memory:f6000000-f6001fff


nsheridan@GRV-LPT-002:~$ dmesg | grep iw                                                                                                                                         
[   15.001784] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.001787] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   15.001872] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.001902] iwlagn 0000:0e:00.0: setting latency timer to 64
[   15.001958] iwlagn 0000:0e:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   15.028695] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.028826] iwlagn 0000:0e:00.0: irq 49 for MSI/MSI-X
[   15.043341] iwlagn 0000:0e:00.0: loaded firmware version 8.24.2.12
[   16.035625] phy0: Selected rate control algorithm 'iwl-agn-rs'
nsheridan@GRV-LPT-002:~$ uname -r -m
2.6.35-25-generic-pae i686
nsheridan@GRV-LPT-002:~$ lspci | grep WiFi
0e:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
nsheridan@GRV-LPT-002:~$ dmesg | grep wlan0
[   16.469577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  351.651088] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[  351.848050] wlan0: authenticate with 00:25:9c:1c:11:05 (try 2)
[  351.849124] wlan0: authenticated
[  351.849158] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[  351.849666] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[  351.849670] wlan0: 00:25:9c:1c:11:05 denied association (code=18)
[  351.849684] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[  364.857287] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[  364.858454] wlan0: authenticated
[  364.858542] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[  364.859053] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[  364.859063] wlan0: 00:25:9c:1c:11:05 denied association (code=18)
[  364.859099] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[  378.068841] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[  378.069980] wlan0: authenticated
[  378.070033] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[  378.070544] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[  378.070552] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[  378.070585] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[  391.275722] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[  391.276958] wlan0: authenticated
[  391.276978] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[  391.277444] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[  391.277447] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[  391.277457] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[  404.487144] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[  404.488506] wlan0: authenticated
[  404.488527] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[  404.489208] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[  404.489213] wlan0: 00:25:9c:1c:11:05 denied association (code=18)
[  404.489229] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 1953.688077] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 1953.689857] wlan0: authenticated
[ 1953.689959] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 1953.690669] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 1953.690679] wlan0: 00:25:9c:1c:11:05 denied association (code=18)
[ 1953.690714] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 1966.900113] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 1966.901330] wlan0: authenticated
[ 1966.901638] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 1966.902337] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 1966.902347] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 1966.902380] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 1980.005077] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 1980.006163] wlan0: authenticated
[ 1980.006214] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 1980.006891] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 1980.006900] wlan0: 00:25:9c:1c:11:05 denied association (code=18)
[ 1980.006932] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 1993.216587] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 1993.217854] wlan0: authenticated
[ 1993.217904] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 1993.218468] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 1993.218478] wlan0: 00:25:9c:1c:11:05 denied association (code=18)
[ 1993.218515] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2006.322090] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2006.323208] wlan0: authenticated
[ 2006.323343] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2006.323874] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2006.323882] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2006.323912] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2017.382827] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2017.384173] wlan0: authenticated
[ 2017.384224] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2017.384744] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2017.384754] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2017.384795] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2030.594298] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2030.595647] wlan0: authenticated
[ 2030.596304] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2030.597724] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2030.597733] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2030.597765] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2043.799817] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2043.800835] wlan0: authenticated
[ 2043.800856] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2043.801394] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2043.801397] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2043.801407] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2056.909241] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2056.910423] wlan0: authenticated
[ 2056.910475] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2056.910976] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2056.910985] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2056.911017] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2070.116265] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2070.117354] wlan0: authenticated
[ 2070.117405] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2070.117974] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2070.117983] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2070.118015] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2084.864366] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2084.865480] wlan0: authenticated
[ 2084.865499] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2084.865986] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2084.865990] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2084.866003] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2097.969141] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2097.970732] wlan0: authenticated
[ 2097.971243] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2097.971766] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2097.971776] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2097.971806] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2111.078374] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2111.083188] wlan0: authenticated
[ 2111.083224] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2111.083716] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2111.083720] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2111.083738] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2124.286229] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2124.287308] wlan0: authenticated
[ 2124.287358] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2124.287856] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2124.287864] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2124.287896] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2137.395283] wlan0: authenticate with 00:25:9c:1c:11:05 (try 1)
[ 2137.396476] wlan0: authenticated
[ 2137.396532] wlan0: associate with 00:25:9c:1c:11:05 (try 1)
[ 2137.397121] wlan0: RX AssocResp from 00:25:9c:1c:11:05 (capab=0x11 status=18 aid=0)
[ 2137.397131] wlan0: 00:25:9c:1c:11:05 denied association (code=1
[ 2137.397166] wlan0: deauthenticating from 00:25:9c:1c:11:05 by local choice (reason=3)
[ 2396.568478] wlan0: authenticate with 00:24:17:fa:e9:cf (try 1)
[ 2396.570619] wlan0: authenticated
[ 2396.570675] wlan0: associate with 00:24:17:fa:e9:cf (try 1)
[ 2396.573619] wlan0: RX AssocResp from 00:24:17:fa:e9:cf (capab=0x411 status=0 aid=1)
[ 2396.573628] wlan0: associated
[ 2396.576664] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2406.704143] wlan0: no IPv6 routers present

---

### Post by AlphaLexman on 2011-01-27
It looks like MAC filtering is preventing you from the router. Look at the router logs.

---

