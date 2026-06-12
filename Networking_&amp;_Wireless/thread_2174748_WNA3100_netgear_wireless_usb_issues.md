---
title: "WNA3100 netgear wireless usb issues"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by vanquishedangel on 2013-09-16
OK I live in a small town that does have a walmart, however my options are limited as to what I can buy there because they offer very little. so I bought this card hopeing it would work and it sort of does.

However when I down load large files or watch youtube the internet freezes, this also happens when updating or loading sites with comments on them, like youtube. It still sees the internet as connected, but pages never load, videos never buffer etc. I am using ubuntu 13.04

I am using ndiswrapper 1.58 and have ndisgtk as well. Here are some outputs:

Lsusb:

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ lsusb
Bus 001 Device 002: ID 046d:0829 Logitech, Inc. 
Bus 001 Device 013: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 004 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 

ndiswrapper -l

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9020) present
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 

dmesg | grep ndis

6000, 5
[ 6019.750995] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000731b580, 16000, 5
[ 6019.750997] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000731f400, 16000, 5
[ 6019.751001] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007323280, 16000, 5
[ 6019.751004] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007327100, 16000, 4
[ 6019.751006] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000732af80, 16000, 5
[ 6019.751009] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000732ee00, 16000, 5
[ 6019.751012] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007332c80, 16000, 5
[ 6019.751015] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007336b00, 16000, 5
[ 6019.751018] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000733a980, 16000, 5
[ 6019.751020] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000733e800, 16000, 5
[ 6019.751023] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007342680, 16000, 5
[ 6019.751026] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007346500, 16000, 5
[ 6019.751029] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000734a380, 16000, 5
[ 6019.751031] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000734e200, 16000, 5
[ 6019.751034] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007352080, 16000, 4
[ 6019.751037] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007355f00, 16000, 5
[ 6019.751039] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007359d80, 16000, 5
[ 6019.751042] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000735dc00, 16000, 5
[ 6019.751044] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007361a80, 16000, 5
[ 6019.751047] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007365900, 16000, 5
[ 6019.751050] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007369780, 16000, 5
[ 6019.751053] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000736d600, 16000, 5
[ 6019.751055] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007371480, 16000, 5
[ 6019.751058] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007375300, 16000, 5
[ 6019.751061] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007379180, 16000, 4
[ 6019.751063] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000737d000, 16000, 4
[ 6019.751066] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007380e80, 16000, 5
[ 6019.751069] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007384d00, 16000, 5
[ 6019.751072] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007388b80, 16000, 5
[ 6019.751074] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000738ca00, 16000, 5
[ 6019.751077] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007390880, 16000, 5
[ 6019.751079] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007394700, 16000, 5
[ 6019.751082] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007398580, 16000, 5
[ 6019.751084] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000739c400, 16000, 5
[ 6019.751087] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073a0280, 16000, 5
[ 6019.751089] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073a4100, 16000, 4
[ 6019.751092] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073a7f80, 16000, 5
[ 6019.751094] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073abe00, 16000, 5
[ 6019.751097] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073afc80, 16000, 5
[ 6019.751100] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073b3b00, 16000, 5
[ 6019.751102] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073b7980, 16000, 5
[ 6019.751106] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073bb800, 16000, 5
[ 6019.751109] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073bf680, 16000, 5
[ 6019.767006] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[ 6020.105209] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[35325.552880] ndiswrapper: device wlan1 removed
[35330.034878] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[35330.440031] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055ec000, 16000, 4
[35330.440037] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055efe80, 16000, 5
[35330.440040] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055f3d00, 16000, 5
[35330.440043] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055f7b80, 16000, 5
[35330.440046] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055fba00, 16000, 5
[35330.440049] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055ff880, 16000, 5
[35330.440051] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005603700, 16000, 5
[35330.440054] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005607580, 16000, 5
[35330.440056] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000560b400, 16000, 5
[35330.440058] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000560f280, 16000, 5
[35330.440061] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005613100, 16000, 4
[35330.440063] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005616f80, 16000, 5
[35330.440067] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000561ae00, 16000, 5
[35330.440070] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000561ec80, 16000, 5
[35330.440072] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005622b00, 16000, 5
[35330.440075] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005626980, 16000, 5
[35330.440077] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000562a800, 16000, 5
[35330.440080] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000562e680, 16000, 5
[35330.440083] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005632500, 16000, 5
[35330.440086] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005636380, 16000, 5
[35330.440088] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000563a200, 16000, 5
[35330.440091] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000563e080, 16000, 4
[35330.440093] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005641f00, 16000, 5
[35330.440095] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005645d80, 16000, 5
[35330.440098] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005649c00, 16000, 5
[35330.440100] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000564da80, 16000, 5
[35330.440103] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005651900, 16000, 5
[35330.440105] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005655780, 16000, 5
[35330.440107] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005659600, 16000, 5
[35330.440110] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000565d480, 16000, 5
[35330.440113] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005661300, 16000, 5
[35330.440116] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005665180, 16000, 4
[35330.440118] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005669000, 16000, 4
[35330.440121] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000566ce80, 16000, 5
[35330.440124] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005670d00, 16000, 5
[35330.440126] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005674b80, 16000, 5
[35330.440128] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005678a00, 16000, 5
[35330.440132] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000567c880, 16000, 5
[35330.440135] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005680700, 16000, 5
[35330.440137] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005684580, 16000, 5
[35330.440140] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005688400, 16000, 5
[35330.440142] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000568c280, 16000, 5
[35330.440145] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005690100, 16000, 4
[35330.440147] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005693f80, 16000, 5
[35330.440150] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005697e00, 16000, 5
[35330.440152] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000569bc80, 16000, 5
[35330.440154] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000569fb00, 16000, 5
[35330.440157] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900056a3980, 16000, 5
[35330.440159] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900056a7800, 16000, 5
[35330.440162] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900056ab680, 16000, 5
[35330.455596] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[35330.793169] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[35437.088292] ndiswrapper (iw_get_network_type:361): getting network type failed: C001000C
[35437.117003] ndiswrapper: device wlan1 removed
[35437.771135] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[35438.123580] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000734a000, 16000, 4
[35438.123587] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000734de80, 16000, 5
[35438.123590] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007351d00, 16000, 5
[35438.123593] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007355b80, 16000, 5
[35438.123595] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007359a00, 16000, 5
[35438.123597] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000735d880, 16000, 5
[35438.123600] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007361700, 16000, 5
[35438.123603] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007365580, 16000, 5
[35438.123606] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007369400, 16000, 5
[35438.123608] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000736d280, 16000, 5
[35438.123611] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007371100, 16000, 4
[35438.123613] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007374f80, 16000, 5
[35438.123616] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007378e00, 16000, 5
[35438.123619] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000737cc80, 16000, 5
[35438.123621] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007380b00, 16000, 5
[35438.123624] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007384980, 16000, 5
[35438.123627] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007388800, 16000, 5
[35438.123630] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000738c680, 16000, 5
[35438.123633] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007390500, 16000, 5
[35438.123636] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007394380, 16000, 5
[35438.123638] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007398200, 16000, 5
[35438.123641] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000739c080, 16000, 4
[35438.123644] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000739ff00, 16000, 5
[35438.123647] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073a3d80, 16000, 5
[35438.123650] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073a7c00, 16000, 5
[35438.123652] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073aba80, 16000, 5
[35438.123655] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073af900, 16000, 5
[35438.123658] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073b3780, 16000, 5
[35438.123660] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073b7600, 16000, 5
[35438.123663] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073bb480, 16000, 5
[35438.123666] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073bf300, 16000, 5
[35438.123668] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073c3180, 16000, 4
[35438.123671] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073c7000, 16000, 4
[35438.123673] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073cae80, 16000, 5
[35438.123676] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073ced00, 16000, 5
[35438.123680] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073d2b80, 16000, 5
[35438.123683] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073d6a00, 16000, 5
[35438.123685] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073da880, 16000, 5
[35438.123688] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073de700, 16000, 5
[35438.123691] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073e2580, 16000, 5
[35438.123694] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073e6400, 16000, 5
[35438.123696] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073ea280, 16000, 5
[35438.123699] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073ee100, 16000, 4
[35438.123701] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073f1f80, 16000, 5
[35438.123704] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073f5e00, 16000, 5
[35438.123706] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073f9c80, 16000, 5
[35438.123709] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900073fdb00, 16000, 5
[35438.123712] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007401980, 16000, 5
[35438.123715] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007405800, 16000, 5
[35438.123718] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007409680, 16000, 5
[35438.140400] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[35438.468170] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[35508.804898] ndiswrapper: device wlan1 removed
[35510.203438] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[35510.614912] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005462000, 16000, 4
[35510.614927] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005465e80, 16000, 5
[35510.614936] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005469d00, 16000, 5
[35510.614944] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000546db80, 16000, 5
[35510.614951] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005471a00, 16000, 5
[35510.614958] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005475880, 16000, 5
[35510.614965] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005479700, 16000, 5
[35510.614975] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000547d580, 16000, 5
[35510.614983] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005481400, 16000, 5
[35510.614989] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005485280, 16000, 5
[35510.614996] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005489100, 16000, 4
[35510.615003] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000548cf80, 16000, 5
[35510.615009] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005490e00, 16000, 5
[35510.615016] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005494c80, 16000, 5
[35510.615023] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005498b00, 16000, 5
[35510.615029] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000549c980, 16000, 5
[35510.615036] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054a0800, 16000, 5
[35510.615043] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054a4680, 16000, 5
[35510.615051] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054a8500, 16000, 5
[35510.615057] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054ac380, 16000, 5
[35510.615063] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054b0200, 16000, 5
[35510.615070] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054b4080, 16000, 4
[35510.615079] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054b7f00, 16000, 5
[35510.615087] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054bbd80, 16000, 5
[35510.615094] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054bfc00, 16000, 5
[35510.615100] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054c3a80, 16000, 5
[35510.615107] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054c7900, 16000, 5
[35510.615114] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054cb780, 16000, 5
[35510.615121] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054cf600, 16000, 5
[35510.615128] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054d3480, 16000, 5
[35510.615134] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054d7300, 16000, 5
[35510.615141] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054db180, 16000, 4
[35510.615148] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054df000, 16000, 4
[35510.615154] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054e2e80, 16000, 5
[35510.615165] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054e6d00, 16000, 5
[35510.615173] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054eab80, 16000, 5
[35510.615180] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054eea00, 16000, 5
[35510.615186] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054f2880, 16000, 5
[35510.615194] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054f6700, 16000, 5
[35510.615200] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054fa580, 16000, 5
[35510.615207] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900054fe400, 16000, 5
[35510.615213] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005502280, 16000, 5
[35510.615220] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005506100, 16000, 4
[35510.615227] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005509f80, 16000, 5
[35510.615234] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000550de00, 16000, 5
[35510.615240] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005511c80, 16000, 5
[35510.615248] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005515b00, 16000, 5
[35510.615255] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005519980, 16000, 5
[35510.615262] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000551d800, 16000, 5
[35510.615270] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005521680, 16000, 5
[35510.637046] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[35510.988590] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[35514.834722] ndiswrapper: device wlan1 removed
[35542.979337] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[35543.374101] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072b7000, 16000, 4
[35543.374107] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072bae80, 16000, 5
[35543.374111] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072bed00, 16000, 5
[35543.374114] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072c2b80, 16000, 5
[35543.374117] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072c6a00, 16000, 5
[35543.374120] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072ca880, 16000, 5
[35543.374122] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072ce700, 16000, 5
[35543.374125] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072d2580, 16000, 5
[35543.374129] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072d6400, 16000, 5
[35543.374132] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072da280, 16000, 5
[35543.374135] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072de100, 16000, 4
[35543.374138] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072e1f80, 16000, 5
[35543.374140] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072e5e00, 16000, 5
[35543.374143] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072e9c80, 16000, 5
[35543.374145] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072edb00, 16000, 5
[35543.374148] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072f1980, 16000, 5
[35543.374150] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072f5800, 16000, 5
[35543.374153] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072f9680, 16000, 5
[35543.374155] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900072fd500, 16000, 5
[35543.374158] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007301380, 16000, 5
[35543.374161] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007305200, 16000, 5
[35543.374164] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007309080, 16000, 4
[35543.374167] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000730cf00, 16000, 5
[35543.374169] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007310d80, 16000, 5
[35543.374172] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007314c00, 16000, 5
[35543.374175] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007318a80, 16000, 5
[35543.374178] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000731c900, 16000, 5
[35543.374181] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007320780, 16000, 5
[35543.374183] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007324600, 16000, 5
[35543.374186] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007328480, 16000, 5
[35543.374189] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000732c300, 16000, 5
[35543.374192] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007330180, 16000, 4
[35543.374195] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007334000, 16000, 4
[35543.374198] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007337e80, 16000, 5
[35543.374200] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000733bd00, 16000, 5
[35543.374203] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000733fb80, 16000, 5
[35543.374206] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007343a00, 16000, 5
[35543.374209] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007347880, 16000, 5
[35543.374214] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000734b700, 16000, 5
[35543.374217] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000734f580, 16000, 5
[35543.374219] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007353400, 16000, 5
[35543.374222] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007357280, 16000, 5
[35543.374225] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000735b100, 16000, 4
[35543.374228] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000735ef80, 16000, 5
[35543.374231] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007362e00, 16000, 5
[35543.374233] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007366c80, 16000, 5
[35543.374236] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000736ab00, 16000, 5
[35543.374239] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000736e980, 16000, 5
[35543.374242] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007372800, 16000, 5
[35543.374245] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007376680, 16000, 5
[35543.389796] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[35543.724422] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ 

iwconfig

wlan1     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:10:35:51:36   
          Bit Rate=65 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:20298   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$

---

### Post by vanquishedangel on 2013-10-23
Just to update: This is still an issue in 13.10

I have used wondershaper and it helps but still has the problem

I have also reduced the txpower to 16dm from 32, that also has helped.

The problem still remains when updating things however and when watching videos.

---

### Post by rylan1963 on 2013-11-18
I too Have the same problem with the Same Wireless adapter wna3100 I will watch a video and looks like I'm connected but wont work.... its like its frozen or something so I try'ed uninstalling The driver and re-installing it but it Still doesn't stop the problem.... any ideas? I think it has something to do with this mesg I receive every time I boot up > **ndiswrapper (ndis_encode_setting:383): unknown type: 3** and its also in dmesg | grep ndis

---

### Post by vanquishedangel on 2013-11-29
honestly I still havent found any solution, I am hopeing the built in wireless drivers in the linux kernel will cover it soon though. If the wireless cards follow a naming scheme at all, then the drivers for this card shouldnt be far off. (BCM43231) since Linux has 43xxx drivers up to 43228, but I dont know.

---

### Post by vanquishedangel on 2013-11-29
I have now come up with something! yey! LOL!

**I also installed firmware-b43-installer, and b43-cutter in synaptic (unsure if they do anything for this however)Ok here it is, I used the driver from here (you will have to uninstall previous drivers):**

[http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)


[B]Unzip the folder somewhere (you need to keep this folder) and open ndis-gtk, (or use command line to install driver) and click "install new driver", then navigate to the folder you downloaded and unzipped, select "bcmn43xx64.inf" if you have 64 bit, bcmn43xx32.inf if 32 bit. Now it still did the same thing as before except I had not applied wonder shaper to it, also it went a lot longer before diconnecting. You will need to find the name of your internet connection, used the command "iwconfig". It looks like this:
[/B]
[I]vmnet8    no wireless extensions.

**wlan1**     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1C:10:35:51:36   
          Bit Rate=216 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:41467   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

vmnet1    no wireless extensions.
[/I]

**As you can see my connection is "wlan1". With wondershaper installed enter this command interminal:**


*sudo wondershaper wlan1 114688 28672*


**And it no longer disconnects or anything. However this is my milage, yours may vary. Wondershaper throttles internet connection, so the numbers need to be tailored to your internet connection, generally about 80% or so. I left the txpower alone. Here is the terminal output of my attempts to find the sweet spot (so if you want to try these numbers you may copy and paste):**

[I]shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 4096 1024
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 8192 2048
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 16384 4096
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$  sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 32768 8192
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 65536 16384
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 131072 32768
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 98304 24576
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper clear wlan1
Wondershaper queues have been cleared.
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ sudo wondershaper wlan1 114688 28672[/I]


**And here are some places to test internet speed, I used them as trial and error:**

[http://www.ispgeeks.com/wild/modules/Bandwidth_Meter_DSL/results.php?kbps=10498.1&downloadtime=2.341&KB=3000&recorded=1](http://www.ispgeeks.com/wild/modules/Bandwidth_Meter_DSL/results.php?kbps=10498.1&downloadtime=2.341&KB=3000&recorded=1)

[http://testmy.net/download](http://testmy.net/download) (this one used to stop internet all the time, I used the 50 mb test)


**Once you have the settings you want, you can make them perminent by entering this command:**

*sudo gedit /etc/network/interfaces*

And entering this to the file (replace "wlan1" with your connection name, and the numbers with your numbers):

up /sbin/wondershaper wlan1 114688 28672
down /sbin/wondershaper remove wlan1


**And dmesg | grep ndis now says this:**

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ dmesg | grep ndis
[   33.396103] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   34.145619] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   34.683267] usbcore: registered new interface driver ndiswrapper
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$

---

