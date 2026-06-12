---
title: "Wifi keeps disconnecting"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Bob24601 on 2011-03-11
Hi, 

I have only had Ubuntu 10.10 installed since yesterday, but have been tearing out my hair trying to get the wifi to stay connected.

I am using a brand new netbox.

[http://www.novatech.co.uk/novatech/pc/range/nbox.html](http://www.novatech.co.uk/novatech/pc/range/nbox.html)

Ubuntu installed all fine, but after about 30seconds to a minute the Wireless keeps dropping out.

I have tried to install wicd network manager, and also reinstalled Ubuntu and get the same issues.

Can anyone point me in the right direction to get this sorted? Would I be better getting an older version of Ubuntu?

Appreciate anyone who can help me.

Bob

---

### Post by cek on 2011-03-11
Open a terminal and post up the output of dmesg.

There are some bugs with the kernel drivers relating to some access points.  In most cases this can be solved by getting the latest wireless drivers from wireless.kernel.org.

By the way, is your user name a reference to Les Miserables?

---

### Post by Bob24601 on 2011-03-11
Hi,

Thanks for your reply. I have gone to that website, but unsure what I am looking for??

Anyway see below for the output of the terminal.



> [  207.229900] Successfully associated, ht enabled
[  207.229904] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  207.229909] =====>rtl8192_set_chan()====ch:10
[  207.239871] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  207.239880] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  207.284108] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  207.284121] ====>to send ADDBARSP
[  207.287568] RX: IEEE802.1X EAPOL frame!
[  208.291493] RX: IEEE802.1X EAPOL frame!
[  209.286701] RX: IEEE802.1X EAPOL frame!
[  210.286442] RX: IEEE802.1X EAPOL frame!
[  210.287242] ==========>received disassoc/deauth(c0) frame, reason code:2
[  210.287258] notify_wx_assoc_event(): Tell user space disconnected
[  210.287269] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  210.287273] ====>remove Tx_TS_admin_list
[  210.287321] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  210.409788] =====>rtl8192_set_chan()====ch:1
[  210.520025] =====>rtl8192_set_chan()====ch:2
[  210.632022] =====>rtl8192_set_chan()====ch:3
[  210.744022] =====>rtl8192_set_chan()====ch:4
[  210.860020] =====>rtl8192_set_chan()====ch:5
[  210.972025] =====>rtl8192_set_chan()====ch:6
[  211.084022] =====>rtl8192_set_chan()====ch:7
[  211.196019] =====>rtl8192_set_chan()====ch:8
[  211.308024] =====>rtl8192_set_chan()====ch:9
[  211.424025] =====>rtl8192_set_chan()====ch:10
[  211.536025] =====>rtl8192_set_chan()====ch:11
[  211.648028] =====>rtl8192_set_chan()====ch:12
[  211.760026] =====>rtl8192_set_chan()====ch:13
[  211.873845] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  211.873883] ===>rtllib_associate_procedure_wq(), chan:10
[  211.873890] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  211.873897] =====>rtl8192_set_chan()====ch:10
[  211.883900] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  211.883927] ===>rtllib_associate_procedure_wq(), chan:10
[  211.883934] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  211.883940] =====>rtl8192_set_chan()====ch:10
[  211.898835] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  211.903260] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  211.903267] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  211.903272] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  211.903277] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  211.903284] Associated successfully
[  211.903287] normal associate
[  211.903305] Using G rates:108
[  211.903308] Successfully associated, ht enabled
[  211.903313] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  211.903318] =====>rtl8192_set_chan()====ch:10
[  211.913291] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  211.913299] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  211.980955] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  211.980968] ====>to send ADDBARSP
[  211.984466] RX: IEEE802.1X EAPOL frame!
[  212.982365] RX: IEEE802.1X EAPOL frame!
[  213.983681] RX: IEEE802.1X EAPOL frame!
[  214.988207] ==========>received disassoc/deauth(c0) frame, reason code:2
[  214.988224] notify_wx_assoc_event(): Tell user space disconnected
[  214.988235] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  214.988285] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  214.995912] RX: IEEE802.1X EAPOL frame!
[  215.105859] =====>rtl8192_set_chan()====ch:1
[  215.216023] =====>rtl8192_set_chan()====ch:2
[  215.328024] =====>rtl8192_set_chan()====ch:3
[  215.440024] =====>rtl8192_set_chan()====ch:4
[  215.552026] =====>rtl8192_set_chan()====ch:5
[  215.664026] =====>rtl8192_set_chan()====ch:6
[  215.776021] =====>rtl8192_set_chan()====ch:7
[  215.888029] =====>rtl8192_set_chan()====ch:8
[  216.000019] =====>rtl8192_set_chan()====ch:9
[  216.112023] =====>rtl8192_set_chan()====ch:10
[  216.224024] =====>rtl8192_set_chan()====ch:11
[  216.336021] =====>rtl8192_set_chan()====ch:12
[  216.448018] =====>rtl8192_set_chan()====ch:13
[  216.565588] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  216.565629] ===>rtllib_associate_procedure_wq(), chan:10
[  216.565637] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  216.565643] =====>rtl8192_set_chan()====ch:10
[  216.575652] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  216.575681] ===>rtllib_associate_procedure_wq(), chan:10
[  216.575687] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  216.575694] =====>rtl8192_set_chan()====ch:10
[  216.603230] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  216.611293] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  216.611299] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  216.611304] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  216.611309] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  216.611316] Associated successfully
[  216.611319] normal associate
[  216.611336] Using G rates:108
[  216.611339] Successfully associated, ht enabled
[  216.611344] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  216.611349] =====>rtl8192_set_chan()====ch:10
[  216.621310] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  216.621319] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  216.679774] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  216.679786] ====>to send ADDBARSP
[  216.683358] RX: IEEE802.1X EAPOL frame!
[  217.680635] RX: IEEE802.1X EAPOL frame!
[  218.680432] RX: IEEE802.1X EAPOL frame!
[  219.686954] RX: IEEE802.1X EAPOL frame!
[  219.687738] ==========>received disassoc/deauth(c0) frame, reason code:2
[  219.687755] notify_wx_assoc_event(): Tell user space disconnected
[  219.687765] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  219.687810] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  219.805783] =====>rtl8192_set_chan()====ch:1
[  219.916022] =====>rtl8192_set_chan()====ch:2
[  220.028021] =====>rtl8192_set_chan()====ch:3
[  220.140020] =====>rtl8192_set_chan()====ch:4
[  220.252026] =====>rtl8192_set_chan()====ch:5
[  220.364025] =====>rtl8192_set_chan()====ch:6
[  220.476023] =====>rtl8192_set_chan()====ch:7
[  220.588019] =====>rtl8192_set_chan()====ch:8
[  220.700022] =====>rtl8192_set_chan()====ch:9
[  220.812021] =====>rtl8192_set_chan()====ch:10
[  220.924022] =====>rtl8192_set_chan()====ch:11
[  221.036020] =====>rtl8192_set_chan()====ch:12
[  221.148027] =====>rtl8192_set_chan()====ch:13
[  221.261629] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  221.261675] ===>rtllib_associate_procedure_wq(), chan:10
[  221.261682] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  221.261689] =====>rtl8192_set_chan()====ch:10
[  221.271688] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  221.271715] ===>rtllib_associate_procedure_wq(), chan:10
[  221.271721] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  221.271727] =====>rtl8192_set_chan()====ch:10
[  221.290125] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  221.302027] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  221.302033] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  221.302038] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  221.302043] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  221.302050] Associated successfully
[  221.302053] normal associate
[  221.302071] Using G rates:108
[  221.302074] Successfully associated, ht enabled
[  221.302078] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  221.302083] =====>rtl8192_set_chan()====ch:10
[  221.312042] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  221.312051] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  221.375204] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  221.375216] ====>to send ADDBARSP
[  221.386743] RX: IEEE802.1X EAPOL frame!
[  222.379563] RX: IEEE802.1X EAPOL frame!
[  223.378230] RX: IEEE802.1X EAPOL frame!
[  224.380593] ==========>received disassoc/deauth(c0) frame, reason code:2
[  224.380609] notify_wx_assoc_event(): Tell user space disconnected
[  224.380619] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  224.380667] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  224.384337] RX: IEEE802.1X EAPOL frame!
[  224.481622] =====>rtl8192_set_chan()====ch:1
[  224.592038] =====>rtl8192_set_chan()====ch:2
[  224.704025] =====>rtl8192_set_chan()====ch:3
[  224.816042] =====>rtl8192_set_chan()====ch:4
[  224.928019] =====>rtl8192_set_chan()====ch:5
[  225.040020] =====>rtl8192_set_chan()====ch:6
[  225.152022] =====>rtl8192_set_chan()====ch:7
[  225.264018] =====>rtl8192_set_chan()====ch:8
[  225.376020] =====>rtl8192_set_chan()====ch:9
[  225.488021] =====>rtl8192_set_chan()====ch:10
[  225.600018] =====>rtl8192_set_chan()====ch:11
[  225.712020] =====>rtl8192_set_chan()====ch:12
[  225.824031] =====>rtl8192_set_chan()====ch:13
[  225.937536] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  225.937575] ===>rtllib_associate_procedure_wq(), chan:10
[  225.937583] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  225.937589] =====>rtl8192_set_chan()====ch:10
[  225.947591] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  225.947617] ===>rtllib_associate_procedure_wq(), chan:10
[  225.947622] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  225.947627] =====>rtl8192_set_chan()====ch:10
[  225.962650] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  225.969133] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  225.969140] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  225.969145] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  225.969149] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  225.969156] Associated successfully
[  225.969160] normal associate
[  225.969178] Using G rates:108
[  225.969181] Successfully associated, ht enabled
[  225.969186] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  225.969191] =====>rtl8192_set_chan()====ch:10
[  225.972154] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  225.972164] ====>to send ADDBARSP
[  225.979161] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  225.979169] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  225.981065] RX: IEEE802.1X EAPOL frame!
[  226.980307] RX: IEEE802.1X EAPOL frame!
[  227.976098] RX: IEEE802.1X EAPOL frame!
[  228.978433] ==========>received disassoc/deauth(c0) frame, reason code:2
[  228.978449] notify_wx_assoc_event(): Tell user space disconnected
[  228.978461] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  228.978501] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  229.079401] =====>rtl8192_set_chan()====ch:1
[  229.192021] =====>rtl8192_set_chan()====ch:2
[  229.304022] =====>rtl8192_set_chan()====ch:3
[  229.420016] =====>rtl8192_set_chan()====ch:4
[  229.532016] =====>rtl8192_set_chan()====ch:5
[  229.644019] =====>rtl8192_set_chan()====ch:6
[  229.756022] =====>rtl8192_set_chan()====ch:7
[  229.868019] =====>rtl8192_set_chan()====ch:8
[  229.980019] =====>rtl8192_set_chan()====ch:9
[  230.092025] =====>rtl8192_set_chan()====ch:10
[  230.208023] =====>rtl8192_set_chan()====ch:11
[  230.320020] =====>rtl8192_set_chan()====ch:12
[  230.432021] =====>rtl8192_set_chan()====ch:13
[  230.545614] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  230.545651] ===>rtllib_associate_procedure_wq(), chan:10
[  230.545659] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  230.545666] =====>rtl8192_set_chan()====ch:10
[  230.555667] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  230.555693] ===>rtllib_associate_procedure_wq(), chan:10
[  230.555699] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  230.555705] =====>rtl8192_set_chan()====ch:10
[  230.580263] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  230.611106] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  230.611112] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  230.611116] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  230.611121] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  230.611128] Associated successfully
[  230.611131] normal associate
[  230.611149] Using G rates:108
[  230.611152] Successfully associated, ht enabled
[  230.611156] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  230.611161] =====>rtl8192_set_chan()====ch:10
[  230.621122] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  230.621130] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  230.670754] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  230.670766] ====>to send ADDBARSP
[  230.678682] RX: IEEE802.1X EAPOL frame!
[  231.676566] RX: IEEE802.1X EAPOL frame!
[  232.677599] RX: IEEE802.1X EAPOL frame!
[  233.675405] RX: IEEE802.1X EAPOL frame!
[  233.676201] ==========>received disassoc/deauth(c0) frame, reason code:2
[  233.676218] notify_wx_assoc_event(): Tell user space disconnected
[  233.676229] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  233.676274] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  233.793771] =====>rtl8192_set_chan()====ch:1
[  233.904027] =====>rtl8192_set_chan()====ch:2
[  234.016533] =====>rtl8192_set_chan()====ch:3
[  234.128023] =====>rtl8192_set_chan()====ch:4
[  234.240538] =====>rtl8192_set_chan()====ch:5
[  234.352029] =====>rtl8192_set_chan()====ch:6
[  234.464029] =====>rtl8192_set_chan()====ch:7
[  234.576026] =====>rtl8192_set_chan()====ch:8
[  234.688540] =====>rtl8192_set_chan()====ch:9
[  234.800537] =====>rtl8192_set_chan()====ch:10
[  234.912527] =====>rtl8192_set_chan()====ch:11
[  235.024018] =====>rtl8192_set_chan()====ch:12
[  235.136523] =====>rtl8192_set_chan()====ch:13
[  235.250894] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  235.250940] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  235.251072] ===>rtllib_associate_procedure_wq(), chan:10
[  235.251080] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  235.251087] =====>rtl8192_set_chan()====ch:10
[  235.263880] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  235.270414] Associated successfully
[  235.270419] normal associate
[  235.270437] Using G rates:108
[  235.270440] Successfully associated, ht enabled
[  235.270445] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  235.270450] =====>rtl8192_set_chan()====ch:10
[  235.280412] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  235.280421] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  235.281914] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  235.281923] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  235.281930] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  235.281937] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  235.366984] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  235.366997] ====>to send ADDBARSP
[  235.370452] RX: IEEE802.1X EAPOL frame!
[  236.370220] RX: IEEE802.1X EAPOL frame!
[  237.372343] RX: IEEE802.1X EAPOL frame!
[  238.373721] ==========>received disassoc/deauth(c0) frame, reason code:2
[  238.373737] notify_wx_assoc_event(): Tell user space disconnected
[  238.373748] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  238.373795] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  238.375381] RX: IEEE802.1X EAPOL frame!
[  238.505874] =====>rtl8192_set_chan()====ch:1
[  238.616023] =====>rtl8192_set_chan()====ch:2
[  238.728027] =====>rtl8192_set_chan()====ch:3
[  238.840015] =====>rtl8192_set_chan()====ch:4
[  238.952020] =====>rtl8192_set_chan()====ch:5
[  239.064020] =====>rtl8192_set_chan()====ch:6
[  239.176023] =====>rtl8192_set_chan()====ch:7
[  239.288019] =====>rtl8192_set_chan()====ch:8
[  239.400022] =====>rtl8192_set_chan()====ch:9
[  239.516019] =====>rtl8192_set_chan()====ch:10
[  239.632019] =====>rtl8192_set_chan()====ch:11
[  239.744022] =====>rtl8192_set_chan()====ch:12
[  239.856020] =====>rtl8192_set_chan()====ch:13
[  239.969813] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  239.969851] ===>rtllib_associate_procedure_wq(), chan:10
[  239.969858] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  239.969865] =====>rtl8192_set_chan()====ch:10
[  239.979869] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  239.979897] ===>rtllib_associate_procedure_wq(), chan:10
[  239.979904] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  239.979910] =====>rtl8192_set_chan()====ch:10
[  239.999634] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  240.004266] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  240.004272] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  240.004277] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  240.004281] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  240.004289] Associated successfully
[  240.004292] normal associate
[  240.004310] Using G rates:108
[  240.004313] Successfully associated, ht enabled
[  240.004318] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  240.004323] =====>rtl8192_set_chan()====ch:10
[  240.014287] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  240.014295] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  240.064953] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  240.064965] ====>to send ADDBARSP
[  240.069402] RX: IEEE802.1X EAPOL frame!
[  241.068682] RX: IEEE802.1X EAPOL frame!
[  242.070287] RX: IEEE802.1X EAPOL frame!
[  243.070113] RX: IEEE802.1X EAPOL frame!
[  243.070911] ==========>received disassoc/deauth(c0) frame, reason code:2
[  243.070927] notify_wx_assoc_event(): Tell user space disconnected
[  243.070938] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  243.070986] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  243.199737] =====>rtl8192_set_chan()====ch:1
[  243.312021] =====>rtl8192_set_chan()====ch:2
[  243.424022] =====>rtl8192_set_chan()====ch:3
[  243.536019] =====>rtl8192_set_chan()====ch:4
[  243.648021] =====>rtl8192_set_chan()====ch:5
[  243.760018] =====>rtl8192_set_chan()====ch:6
[  243.872031] =====>rtl8192_set_chan()====ch:7
[  243.984018] =====>rtl8192_set_chan()====ch:8
[  244.096024] =====>rtl8192_set_chan()====ch:9
[  244.208020] =====>rtl8192_set_chan()====ch:10
[  244.320020] =====>rtl8192_set_chan()====ch:11
[  244.432024] =====>rtl8192_set_chan()====ch:12
[  244.544019] =====>rtl8192_set_chan()====ch:13
[  244.656949] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  244.656986] ===>rtllib_associate_procedure_wq(), chan:10
[  244.656993] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  244.656999] =====>rtl8192_set_chan()====ch:10
[  244.667027] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  244.667054] ===>rtllib_associate_procedure_wq(), chan:10
[  244.667061] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  244.667067] =====>rtl8192_set_chan()====ch:10
[  244.681811] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  244.708091] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  244.708097] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  244.708102] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  244.708106] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  244.708114] Associated successfully
[  244.708117] normal associate
[  244.708134] Using G rates:108
[  244.708137] Successfully associated, ht enabled
[  244.708142] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  244.708147] =====>rtl8192_set_chan()====ch:10
[  244.718108] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  244.718116] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  245.658212] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  245.658224] ====>to send ADDBARSP
[  245.670453] RX: IEEE802.1X EAPOL frame!
[  245.770235] RX: IEEE802.1X EAPOL frame!
[  246.770557] RX: IEEE802.1X EAPOL frame!
[  247.769703] RX: IEEE802.1X EAPOL frame!
[  247.770497] ==========>received disassoc/deauth(c0) frame, reason code:2
[  247.770515] notify_wx_assoc_event(): Tell user space disconnected
[  247.770527] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  247.770580] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  247.885706] =====>rtl8192_set_chan()====ch:1
[  247.996023] =====>rtl8192_set_chan()====ch:2
[  248.109034] =====>rtl8192_set_chan()====ch:3
[  248.220026] =====>rtl8192_set_chan()====ch:4
[  248.332019] =====>rtl8192_set_chan()====ch:5
[  248.444017] =====>rtl8192_set_chan()====ch:6
[  248.556024] =====>rtl8192_set_chan()====ch:7
[  248.668019] =====>rtl8192_set_chan()====ch:8
[  248.780018] =====>rtl8192_set_chan()====ch:9
[  248.892030] =====>rtl8192_set_chan()====ch:10
[  249.004019] =====>rtl8192_set_chan()====ch:11
[  249.116020] =====>rtl8192_set_chan()====ch:12
[  249.228018] =====>rtl8192_set_chan()====ch:13
[  249.341957] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  249.341996] ===>rtllib_associate_procedure_wq(), chan:10
[  249.342003] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  249.342009] =====>rtl8192_set_chan()====ch:10
[  249.352037] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  249.352065] ===>rtllib_associate_procedure_wq(), chan:10
[  249.352070] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  249.352075] =====>rtl8192_set_chan()====ch:10
[  249.369179] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  249.388928] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  249.388936] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  249.388942] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  249.388948] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  249.388956] Associated successfully
[  249.388961] normal associate
[  249.388980] Using G rates:108
[  249.388984] Successfully associated, ht enabled
[  249.388990] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  249.388996] =====>rtl8192_set_chan()====ch:10
[  249.398987] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  249.398996] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  249.460139] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  249.460153] ====>to send ADDBARSP
[  249.466665] RX: IEEE802.1X EAPOL frame!
[  250.464103] RX: IEEE802.1X EAPOL frame!
[  251.470384] RX: IEEE802.1X EAPOL frame!
[  252.072767] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  252.128045] =====>rtl8192_set_chan()====ch:1
[  252.240020] =====>rtl8192_set_chan()====ch:2
[  252.352020] =====>rtl8192_set_chan()====ch:3
[  252.464024] =====>rtl8192_set_chan()====ch:4
[  252.576020] =====>rtl8192_set_chan()====ch:5
[  252.688020] =====>rtl8192_set_chan()====ch:6
[  252.800026] =====>rtl8192_set_chan()====ch:7
[  252.912030] =====>rtl8192_set_chan()====ch:8
[  253.024021] =====>rtl8192_set_chan()====ch:9
[  253.136018] =====>rtl8192_set_chan()====ch:10
[  253.248036] =====>rtl8192_set_chan()====ch:11
[  253.360024] =====>rtl8192_set_chan()====ch:12
[  253.472019] =====>rtl8192_set_chan()====ch:13
[  253.584035] =====>rtl8192_set_chan()====ch:10
[  253.584056] =====>rtl8192_set_chan()====ch:1
[  253.584061] rtl8192_phy_SwChnl: SwChnl is in progress
[  253.594016] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  253.594024] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  259.260213] ===>rtl819x_watchdog_wqcallback(): AP is power off,chan:1, connect another one
[  259.260222] ===========>RemovePeerTS,00:24:17:e1:b7:99
[  259.260239] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  259.260255] notify_wx_assoc_event(): Tell user space disconnected
[  259.360688] =====>rtl8192_set_chan()====ch:1
[  259.472018] =====>rtl8192_set_chan()====ch:2
[  259.584548] =====>rtl8192_set_chan()====ch:3
[  259.696074] =====>rtl8192_set_chan()====ch:4
[  259.808520] =====>rtl8192_set_chan()====ch:5
[  259.920093] =====>rtl8192_set_chan()====ch:6
[  260.032050] =====>rtl8192_set_chan()====ch:7
[  260.144034] =====>rtl8192_set_chan()====ch:8
[  260.256557] =====>rtl8192_set_chan()====ch:9
[  260.369525] =====>rtl8192_set_chan()====ch:10
[  260.480039] =====>rtl8192_set_chan()====ch:11
[  260.592027] =====>rtl8192_set_chan()====ch:12
[  260.705529] =====>rtl8192_set_chan()====ch:13
[  260.821137] =====>rtl8192_set_chan()====ch:1
[  260.936523] =====>rtl8192_set_chan()====ch:2
[  261.048030] =====>rtl8192_set_chan()====ch:3
[  261.160546] =====>rtl8192_set_chan()====ch:4
[  261.273542] =====>rtl8192_set_chan()====ch:5
[  261.385532] =====>rtl8192_set_chan()====ch:6
[  261.496522] =====>rtl8192_set_chan()====ch:7
[  261.608522] =====>rtl8192_set_chan()====ch:8
[  261.720028] =====>rtl8192_set_chan()====ch:9
[  261.832027] =====>rtl8192_set_chan()====ch:10
[  261.944024] =====>rtl8192_set_chan()====ch:11
[  262.056024] =====>rtl8192_set_chan()====ch:12
[  262.168017] =====>rtl8192_set_chan()====ch:13
[  262.285430] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  262.285470] ===>rtllib_associate_procedure_wq(), chan:10
[  262.285478] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  262.285485] =====>rtl8192_set_chan()====ch:10
[  262.295524] Linking with O2wirelessE1B799,channel:10, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  262.295551] ===>rtllib_associate_procedure_wq(), chan:10
[  262.295556] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  262.295561] =====>rtl8192_set_chan()====ch:10
[  262.308925] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  262.317927] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:0:a42b
[  262.317934] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:1:a44f
[  262.317939] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:2:5e4322
[  262.317943] SetHwReg8192SE():HW_VAR_AC_PARAM eACI:3:2f3222
[  262.317951] Associated successfully
[  262.317954] normal associate
[  262.317968] Using G rates:108
[  262.317971] Successfully associated, ht enabled
[  262.317976] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[  262.317981] =====>rtl8192_set_chan()====ch:10
[  262.327942] ===>rtl8192se_link_change():ieee->iw_mode is 2
[  262.327951] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[  262.354318] ====>rx ADDBAREQ from :00:24:17:e1:b7:99
[  262.354331] ====>to send ADDBARSP
[  262.360361] RX: IEEE802.1X EAPOL frame!
[  262.462064] RX: IEEE802.1X EAPOL frame!
[  262.462238] alg name:CCMP
[  262.462856] ===========>set_swcam():EntryNo is 4,KeyIndex is 0,KeyType is 4,is_mesh is 0
[  262.462988] alg name:TKIP
[  262.463615] ===========>set_swcam():EntryNo is 1,KeyIndex is 1,KeyType is 2,is_mesh is 0
[  264.660300] wlan0: Michael MIC verification failed for MSDU from 00:24:17:e1:b7:99 keyidx=1
[  264.660307] 1, force_mic_error = 0
[  264.660311] skb->dev != NULL
[  264.660324] wlan0: MSDU decryption/MIC verification failed (SA=00:24:17:e1:b7:99 keyidx=1)
[  264.660329] rtllib_rx_decrypt: ==>decrypt msdu error


---

### Post by Bob24601 on 2011-03-12
Hello, 

I have gone to [http://wireless.kernel.org](http://wireless.kernel.org), but as I have no idea what I'm doing I do not know where to download the correct driver, or how to install it.

Can anyone help me further?

Bob

---

### Post by Spike the Dingo on 2011-03-25
I have something like every now and then, but not all the time.
I had it on 10.10, and right now on Natty. I run amd_64 on a ThinkPad X201.

I can't for the life of me figure out what it is. (aside from a Kernel/NM issue)
Might be related to your problem, I'm going to have a look.

Anyone have a bug report?
I've attached a portion of dmesg.

---

### Post by cek on 2011-04-07
It looks like a decryption problem.  Are you sure the encryption key you entered was correct, and you selected the correct encryption type?  Any chance you can temporarily change your access point to Open (no encryption) and see if you can connect?  This would allow you to rule out hardware failure.

---

### Post by Spike the Dingo on 2011-04-07
Yeah, cek, the keys are correct. Majority of the time wifi works fine... that's the odd thing, unless there is a sporadic bug with the way keys are handled...
I'm going to check it out the next time I have this problem.

---

