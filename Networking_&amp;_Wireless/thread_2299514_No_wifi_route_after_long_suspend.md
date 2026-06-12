---
title: "No wifi route after long suspend"
date: 2015-10-19
forum: Networking &amp; Wireless
---

### Post by schroedinger2 on 2015-10-19
When resuming after suspend, a wifi connection is established between my laptop an the wifi router, but I cannot ping it or anything else in my home network. The routing table is empty.
This happens only when resume is after a longer time like hours. Immediate resume is no problem.

Machine:
- Dell Latitude E7440
- Ubuntu 15.4
- Linux 3.19.0-30-generic #34-Ubuntu SMP Fri Oct 2 22:08:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
sudo lshw -C network
...
  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 73
       serial: d8:fc:93:2b:c1:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-30-generic firmware=25.17.12.0 ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f7d00000-f7d01fff
...

```

I tried:
 - wifi hardware button off/on
 - nmcli r wifi off && nmcli r wifi on
 - sudo service network-manager restart
 - sudo dhclient -r
 - sudo /etc/init.d/networking restart
 - switch blutooth off

Won't help...

I also discovered that the routing table is only empty until this happens after a while without me doing anything:
```
[20468.487188] wlan0: AP 1c:c6:3c:80:ef:1b changed bandwidth, new config is 2452 MHz, width 1 (2452/0 MHz)
```

Then everything works just fine.

What can I do besides restarting or waiting serveral minutes until the problem solves itself?

Here's the complete output:
```
dmesg |grep wlan0
[   48.903550] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[   48.907217] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[   48.910834] wlan0: authenticated
[   48.914800] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[   48.944727] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[   48.946921] wlan0: associated
[  227.194287] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[  235.427691] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[  235.431371] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[  235.433123] wlan0: authenticated
[  235.435727] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[  235.463878] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[  235.468559] wlan0: associated
[  327.356623] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[  334.417717] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[  334.421721] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[  334.423566] wlan0: authenticated
[  334.424161] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[  334.463315] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[  334.469683] wlan0: associated
[  342.951176] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[  346.088291] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[  346.092176] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[  346.094086] wlan0: authenticated
[  346.095996] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[  346.124144] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[  346.130009] wlan0: associated
[  365.265642] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[  372.922427] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[  372.925950] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[  372.929878] wlan0: authenticated
[  372.930294] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[  372.958352] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[  372.961610] wlan0: associated
[  382.241567] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[  385.399797] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[  385.404085] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[  385.405893] wlan0: authenticated
[  385.409891] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[  385.441100] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[  385.444586] wlan0: associated
[  396.186178] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[  396.190047] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[  396.271567] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 2/3)
[  396.378497] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 3/3)
[  396.467273] wlan0: authentication with 1c:c6:3c:80:ef:1b timed out
[ 1109.443465] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 1109.447196] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 1109.448945] wlan0: authenticated
[ 1109.449411] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 1109.477461] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=1)
[ 1109.479179] wlan0: associated
[ 2061.566342] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2061.664959] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2069.696680] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2069.703420] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2069.705216] wlan0: authenticated
[ 2069.708798] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2069.737153] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2069.741502] wlan0: associated
[ 2073.712266] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[ 2076.866660] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2076.870366] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2076.872391] wlan0: authenticated
[ 2076.873401] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2076.902917] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2076.906319] wlan0: associated
[ 2079.854299] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2087.855290] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2087.859012] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2087.862495] wlan0: authenticated
[ 2087.864262] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2087.892286] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2087.896099] wlan0: associated
[ 2091.833524] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[ 2094.987740] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2094.991588] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2094.994549] wlan0: authenticated
[ 2094.996947] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2095.025289] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2095.029167] wlan0: associated
[ 2120.093107] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[ 2123.253633] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2123.257985] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2123.259745] wlan0: authenticated
[ 2123.263755] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2123.291809] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2123.295380] wlan0: associated
[ 2126.132098] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[ 2129.275174] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2129.278434] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2129.285881] wlan0: authenticated
[ 2129.288958] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2129.321589] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2129.330065] wlan0: associated
[ 2139.210946] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[ 2142.367438] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2142.374015] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2142.375828] wlan0: authenticated
[ 2142.378833] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2142.406893] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2142.417613] wlan0: associated
[ 2149.251198] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[ 2152.410165] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2152.414023] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2152.415780] wlan0: authenticated
[ 2152.418203] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2152.446258] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2152.449602] wlan0: associated
[ 2454.565992] wlan0: AP 1c:c6:3c:80:ef:1b changed bandwidth, new config is 2417 MHz, width 1 (2417/0 MHz)
[ 2629.254815] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[ 2629.258901] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[ 2629.260771] wlan0: authenticated
[ 2629.263435] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[ 2629.291515] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=3)
[ 2629.294896] wlan0: associated
[13288.521827] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[13288.624351] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13299.584100] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[13299.587620] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[13299.590830] wlan0: authenticated
[13299.608694] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[13299.636921] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[13299.647466] wlan0: associated
[13304.058578] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[13307.210808] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[13307.215095] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[13307.218573] wlan0: authenticated
[13307.221893] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[13307.250168] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[13307.253800] wlan0: associated
[13363.410136] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[13363.480318] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[13367.053887] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[13367.057146] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[13367.058956] wlan0: authenticated
[13367.059426] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[13367.087487] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[13367.093034] wlan0: associated
[13370.383740] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[13373.538932] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[13373.542734] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[13373.544507] wlan0: authenticated
[13373.548552] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[13373.576685] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[13373.580668] wlan0: associated
[13391.494395] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[13394.989787] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[13394.994009] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[13394.995830] wlan0: authenticated
[13394.996907] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[13395.024882] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[13395.035533] wlan0: associated
[13398.566995] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[13401.730355] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[13401.733843] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[13401.735636] wlan0: authenticated
[13401.738428] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[13401.766507] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[13401.777415] wlan0: associated
[13703.874000] wlan0: AP 1c:c6:3c:80:ef:1b changed bandwidth, new config is 2452 MHz, width 1 (2452/0 MHz)
[19327.590361] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[19327.657749] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19339.725518] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[19339.729767] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[19339.733430] wlan0: authenticated
[19339.733832] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[19339.762350] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[19339.773192] wlan0: associated
[19343.787629] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[19347.039024] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[19347.042999] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[19347.046226] wlan0: authenticated
[19347.047181] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[19347.075469] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[19347.080135] wlan0: associated
[19649.382385] wlan0: AP 1c:c6:3c:80:ef:1b changed bandwidth, new config is 2452 MHz, width 1 (2452/0 MHz)
[20092.736427] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[20092.748951] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20103.859932] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[20103.863429] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[20103.874750] wlan0: authenticated
[20103.879365] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[20104.104691] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[20104.118292] wlan0: associated
[20104.172061] wlan0: AP 1c:c6:3c:80:ef:1b changed bandwidth, new config is 2452 MHz, width 1 (2452/0 MHz)
[20124.111231] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[20124.174225] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20135.552454] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[20135.556112] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[20135.594200] wlan0: authenticated
[20135.597145] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[20135.667428] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[20135.748740] wlan0: associated
[20136.960069] wlan0: deauthenticating from 1c:c6:3c:80:ef:1b by local choice (Reason: 3=DEAUTH_LEAVING)
[20144.051062] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[20144.054740] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[20144.101141] wlan0: authenticated
[20144.101946] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[20144.189727] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[20144.210002] wlan0: associated
[20149.700731] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[20152.891918] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[20152.895318] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[20152.947250] wlan0: authenticated
[20152.950644] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[20153.023867] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[20153.062168] wlan0: associated
[20162.728232] wlan0: deauthenticated from 1c:c6:3c:80:ef:1b (Reason: 3=DEAUTH_LEAVING)
[20165.886243] wlan0: authenticate with 1c:c6:3c:80:ef:1b
[20165.889520] wlan0: send auth to 1c:c6:3c:80:ef:1b (try 1/3)
[20165.920273] wlan0: authenticated
[20165.921692] wlan0: associate with 1c:c6:3c:80:ef:1b (try 1/3)
[20165.959175] wlan0: RX AssocResp from 1c:c6:3c:80:ef:1b (capab=0x411 status=0 aid=2)
[20165.962653] wlan0: associated
[20468.487188] wlan0: AP 1c:c6:3c:80:ef:1b changed bandwidth, new config is 2452 MHz, width 1 (2452/0 MHz)

```

ifconfig
```

wlan0     Link encap:Ethernet  HWaddr d8:fc:93:2b:c1:f4  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::dafc:93ff:fe2b:c1f4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:350628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:397226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224845405 (224.8 MB)  TX bytes:453779411 (453.7 MB)

```

iwconfig
```

wlan0     IEEE 802.11abgn  ESSID:"LOOPING_LOUIS"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 1C:C6:3C:80:EF:1B   
          Bit Rate=2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo lshw -C network
```

  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 73
       serial: d8:fc:93:2b:c1:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-30-generic firmware=25.17.12.0 ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f7d00000-f7d01fff

```

iwlist scan
```
eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 1C:C6:3C:80:EF:1B
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"LOOPING_LOUIS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bf84cbe62
                    Extra: Last beacon: 172632ms ago
                    IE: Unknown: 000D4C4F4F50494E475F4C4F554953
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1609070600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500011A7A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD8D0050F204104A00011010440001021041000100103B00010310470010000000000000000300001CC63C80EF1A102100066F3220426F781023000941525637353244505710240007312E30312E32351042000A323035333031303838351054000800060050F20400011011001B6F3220426F7820576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 0706444520010D10
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409070600000000000000000000000000000000000000

wwan0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

```

lsmod
```
Module                  Size  Used by
ctr                    16384  2 
ccm                    20480  2 
binfmt_misc            20480  1 
bnep                   20480  2 
arc4                   16384  2 
iwlmvm                278528  0 
mac80211              724992  1 iwlmvm
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
pn544_mei              16384  0 
mei_phy                16384  1 pn544_mei
pn544                  20480  1 pn544_mei
hci                    45056  2 pn544,mei_phy
nfc                   102400  2 hci,pn544
uvcvideo               90112  0 
cdc_mbim               16384  0 
cdc_wdm                24576  2 cdc_mbim
cdc_ncm                32768  1 cdc_mbim
usbnet                 45056  2 cdc_mbim,cdc_ncm
qcserial               20480  0 
usb_wwan               20480  1 qcserial
usbserial              49152  2 qcserial,usb_wwan
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
crct10dif_pclmul       16384  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
mii                    16384  1 usbnet
crc32_pclmul           16384  0 
media                  24576  2 uvcvideo,videodev
ghash_clmulni_intel    16384  0 
iwlwifi               196608  1 iwlmvm
dell_wmi               16384  0 
btusb                  40960  0 
aesni_intel           172032  4 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
sparse_keymap          16384  1 dell_wmi
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
snd_hda_codec_hdmi     53248  1 
i8k                    16384  0 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
joydev                 20480  0 
serio_raw              16384  0 
bluetooth             491520  8 bnep,btusb
snd_hda_intel          36864  6 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_compress           20480  1 snd_soc_core
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      16384  1 snd_soc_core
lpc_ich                24576  0 
i2c_hid                20480  0 
i915                 1060864  4 
snd_soc_sst_acpi       16384  0 
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
hid                   110592  1 i2c_hid
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
drm_kms_helper        131072  1 i915
drm                   348160  5 i915,drm_kms_helper
i2c_algo_bit           16384  1 i915
8250_dw                16384  0 
8250_fintek            16384  0 
mei_me                 20480  0 
soundcore              16384  2 snd,snd_hda_codec
mei                    90112  3 pn544_mei,mei_phy,mei_me
dw_dmac                16384  0 
shpchp                 40960  0 
dw_dmac_core           24576  1 dw_dmac
dell_rbtn              16384  1 
wmi                    20480  1 dell_wmi
dell_smo8800           16384  0 
i2c_designware_platform    16384  0 
i2c_designware_core    16384  1 i2c_designware_platform
video                  20480  1 i915
mac_hid                16384  0 
spi_pxa2xx_platform    24576  0 
cuse                   16384  3 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
uas                    24576  0 
usb_storage            69632  4 uas
psmouse               118784  0 
ahci                   36864  0 
e1000e                237568  0 
libahci                32768  1 ahci
sdhci_pci              24576  0 
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
sdhci_acpi             16384  0 
sdhci                  45056  2 sdhci_acpi,sdhci_pci

```

---

### Post by schroedinger2 on 2015-10-20
Anybody? Please, I have no idea how to solve this...

---

