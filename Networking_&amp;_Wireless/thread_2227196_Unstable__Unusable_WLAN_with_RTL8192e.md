---
title: "Unstable / Unusable WLAN with RTL8192e"
date: 2014-05-31
forum: Networking &amp; Wireless
---

### Post by killerlink23 on 2014-05-31
Hello Community!

To beginn with, I have read a lot in the Forums till today, yet this is my first post. Second, my main language is German, therefore my Englisch may not be perfect. If something i wrote is unclear/wrong please feel free to ask or correct me, and I will try to rephrase it. 

I recently decided to give Ubuntu a try on a Laptop. Works like a charm except the WLAN. As the Title already mentions, the Chipset should be RTL8192e/ce.
(I dont know which of both, e or ce, because its mentioned like that by "lspci | grep wireless", what would be the difference?) 

At first I had Ubuntu 12.04 running, i have gotten it to work somehow, but the connection worked only for 1 minute, then i always had to restart the drivers via "modprobe" for another minute of internet.
(I also looked intro various Logfiles, one of them repeatedly said something like "TxCheckStuck queueid=1 tcb_desc" and a few more things)

After 2 days of Trial and Error, i noticed Ubuntu 14.04 is available. I installed it and got a whole new other Error. Whenever I tried to connect to a Network, it keeps asking for the password every 30 seconds. I have tested this with two different networks, althought the both are very similiar (1b/g/n mixed mode, WPA2-PSK, AES). 

Further Information:
Laptop is a Toshiba Satellite L350 (Part Number PSLDCE-00Q00DGR)
Wired Networks work perfectly by the way.
The Laptop is not in use yet, this means i can try everything since in case of failure, i can just reinstall.
I am usually very skilled when talking about computers, hardware as well as software, but im happy about every explanation and information i can get. 
I also have a lot of equipment for testing (multiple PCs, Switches, (WLAN-)Routers) and an adequate amount of background-knowledge.

I can gather any further information required relatively quick, since the Laptop is right next to me, please just tell me what is needed.

Could someone please help me to get the WLAN working?

best regards to everyone, thanks in advance
Theodor

---

### Post by Joel_Ross on 2014-05-31
try installing [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver) the maintianer is very good at responsing to any questions/issues you may have. 

hope this helps 

Joel

---

### Post by killerlink23 on 2014-05-31
At first I made a small mistake in my starting post, i wrote rtl8192e/ce but it is rtl8192e/_**s**_e. My Apologies.

I have done what you suggested. I now have the same / similar Problems i had with Ubuntu 12.04.
To clarify, the connection seems to be available all the time now, but most of the time websites aren't loaded completly, althought it works rarely.

I have used "dmesg" for some errormessages, they seem to be the same as in Ubuntu 12.04 aswell.
(i cut out some of the beginning, starting where i was thinking it was going to get relevant)
(also, i marked the lines i think that are suspicious)

```

[   17.435874] cfg80211: Calling CRDA to update world regulatory domain
[   17.481878] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMBA 1 (20131115/utaddress-251)
[   17.481888] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.481892] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   17.481897] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.481899] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   17.481903] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.481905] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.549700] WARNING! power/level is deprecated; use power/control instead
[   17.702049] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[   17.705415] lib80211: common routines for IEEE802.11 drivers
[   17.705419] lib80211_crypt: registered algorithm 'NULL'
[   17.716203] rtllib: module is from the staging directory, the quality is unknown, you have been warned.
[   17.765009] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   17.766838] 
[   17.766838] Linux kernel driver for RTL8192E WLAN cards
[   17.766839] Copyright (c) 2007-2008, Realsil Wlan Driver
[   17.770879] Memory mapped space start: 0xd4100000
[   17.843365] Linux video capture interface: v2.00
[   17.885153] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   17.896951] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[   17.919689] SKU: Nid=0x1d sku_cfg=0x4016892d
[   17.919692] SKU: port_connectivity=0x1
[   17.919694] SKU: enable_pcbeep=0x1
[   17.919695] SKU: check_sum=0x00000006
[   17.919697] SKU: customization=0x00000089
[   17.919698] SKU: external_amp=0x5
[   17.919700] SKU: platform_type=0x1
[   17.919701] SKU: swap=0x0
[   17.919703] SKU: override=0x1
[   17.919887] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   17.919889]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.919891]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   17.919893]    mono: mono_out=0x0
[   17.919894]    inputs:
[   17.919896]      Internal Mic=0x19
[   17.919898]      Mic=0x18
[   17.919900] realtek: No valid SSID, checking pincfg 0x4016892d for NID 0x1d
[   17.919902] realtek: Enabling init ASM_ID=0x892d CODEC_ID=10ec0272
[   17.924921] input: CNF7051 as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input10
[   17.925467] usbcore: registered new interface driver uvcvideo
[   17.925470] USB Video Class driver (1.1.1)
[   17.959479] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.960934] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.172095] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   18.193651] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[   18.194260] radeon 0000:01:00.0: WB enabled
[   18.194266] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8800b285dc00
[   18.194269] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff8800b285dc0c
[   18.198063] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0xffffc9000489c598
[   18.198068] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   18.198070] [drm] Driver supports precise vblank timestamp query.
[   18.198115] radeon 0000:01:00.0: irq 47 for MSI/MSI-X
[   18.198139] radeon 0000:01:00.0: radeon: using MSI.
[   18.198197] [drm] radeon: irq initialized.
[   18.246970] cfg80211: World regulatory domain updated:
[   18.246976] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.246979] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.246981] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.246983] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.246985] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.246987] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.247655] [drm] ring test on 0 succeeded in 1 usecs
[   18.247720] [drm] ring test on 3 succeeded in 1 usecs
[   18.443028] [drm] ring test on 5 succeeded in 1 usecs
[   18.443039] [drm] UVD initialized successfully.
[   18.443515] [drm] Enabling audio 0 support
[   18.443578] [drm] ib test on ring 0 succeeded in 0 usecs
[   18.443630] [drm] ib test on ring 3 succeeded in 0 usecs
[   18.605809] [drm] ib test on ring 5 succeeded
[   18.632031] [drm] radeon atom DIG backlight initialized
[   18.632038] [drm] Radeon Display Connectors
[   18.632041] [drm] Connector 0:
[   18.632043] [drm]   VGA-1
[   18.632046] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   18.632047] [drm]   Encoders:
[   18.632049] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   18.632050] [drm] Connector 1:
[   18.632052] [drm]   LVDS-1
[   18.632054] [drm]   DDC: 0x7f68 0x7f68 0x7f6c 0x7f6c 0x7f70 0x7f70 0x7f74 0x7f74
[   18.632056] [drm]   Encoders:
[   18.632057] [drm]     LCD1: INTERNAL_UNIPHY2
[   18.632059] [drm] Connector 2:
[   18.632060] [drm]   HDMI-A-1
[   18.632062] [drm]   HPD1
[   18.632064] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   18.632065] [drm]   Encoders:
[   18.632067] [drm]     DFP1: INTERNAL_UNIPHY
[   18.632068] [drm] Connector 3:
[   18.632070] [drm]   DP-1
[   18.632071] [drm]   HPD2
[   18.632073] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   18.632075] [drm]   Encoders:
[   18.632076] [drm]     DFP2: INTERNAL_UNIPHY
[   18.639623] [drm] radeon: dpm initialized
[   18.931953] Bluetooth: Core ver 2.17
[   18.932047] NET: Registered protocol family 31
[   18.932050] Bluetooth: HCI device and connection manager initialized
[   18.932062] Bluetooth: HCI socket layer initialized
[   18.932065] Bluetooth: L2CAP socket layer initialized
[   18.932072] Bluetooth: SCO socket layer initialized
[   18.944591] Bluetooth: RFCOMM TTY layer initialized
[   18.944608] Bluetooth: RFCOMM socket layer initialized
[   18.944616] Bluetooth: RFCOMM ver 1.11
[   18.948153] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.948157] Bluetooth: BNEP filters: protocol multicast
[   18.948169] Bluetooth: BNEP socket layer initialized
[   19.137774] type=1400 audit(1401553048.475:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=523 comm="apparmor_parser"
[   19.137783] type=1400 audit(1401553048.475:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
[   19.137789] type=1400 audit(1401553048.475:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[   19.138305] type=1400 audit(1401553048.475:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
[   19.138314] type=1400 audit(1401553048.475:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[   19.138581] type=1400 audit(1401553048.475:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[   19.143299] type=1400 audit(1401553048.479:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=524 comm="apparmor_parser"
[   19.143311] type=1400 audit(1401553048.479:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=524 comm="apparmor_parser"
[   19.143317] type=1400 audit(1401553048.479:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=524 comm="apparmor_parser"
[   19.143818] type=1400 audit(1401553048.479:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=524 comm="apparmor_parser"
[   19.334742] init: cups main process (577) killed by HUP signal
[   19.334763] init: cups main process ended, respawning
[   19.621381] init: failsafe main process (590) killed by TERM signal
[   19.680524] [drm] fb mappable at 0xC045E000
[   19.680528] [drm] vram apper at 0xC0000000
[   19.680530] [drm] size 5324800
[   19.680532] [drm] fb depth is 24
[   19.680534] [drm]    pitch is 5888
[   19.680724] fbcon: radeondrmfb (fb0) is primary device
[   20.364590] Console: switching to colour frame buffer device 180x56
[   20.375092] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   20.375095] radeon 0000:01:00.0: registered panic notifier
[   20.375374] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   20.375521] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   20.375525] hda-intel 0000:01:00.1: Using LPIB position fix
[   20.375590] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
[   20.385890] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   20.399209] HDMI ATI/AMD: no speaker allocation for ELD
[   20.399425] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   21.265209] r8169 0000:02:00.0 eth0: link down
[   21.265263] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.265705] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.251859] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.252292] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.125908] init: plymouth-upstart-bridge main process ended, respawning
[   24.144339] init: plymouth-upstart-bridge main process ended, respawning
[   25.521124] Linking with TP-Link-Cyn2.4,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[   25.521139] Linking with TP-Link-Cyn2.4,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[   25.521266] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   25.542212] Associated successfully
[   25.542216] normal associate
[   25.542225] Using G rates:108
[   25.542226] Successfully associated, ht enabled
[   25.542229] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[   25.542582] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.544078] RX: IEEE802.1X EAPOL frame!
[   25.562211] RX: IEEE802.1X EAPOL frame!
[   25.562475] alg name:R-CCMP
[   25.565561] rtllib_crypt_ccmp: module is from the staging directory, the quality is unknown, you have been warned.
[   25.567519] lib80211_crypt: registered algorithm 'R-CCMP'
[   25.568997] alg name:R-CCMP
[   26.256214] dm_check_edca_turbo():iot peer is atheros, bssid: f8:1a:67:a2:b9:45
[   49.431789] audit_printk_skb: 186 callbacks suppressed
[   49.431794] type=1400 audit(1401553078.764:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2033 comm="apparmor_parser"
[   49.431804] type=1400 audit(1401553078.764:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2033 comm="apparmor_parser"
[   49.432372] type=1400 audit(1401553078.768:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2033 comm="apparmor_parser"
[B][  118.440296] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  118.497157] ===>tx queue is not empty:1, 19
[  118.804505] ===>tx queue is not empty:1, 22
[  118.906946] ===>tx queue is not empty:1, 22
[  119.009410] ===>tx queue is not empty:1, 22
[  119.111862] ===>tx queue is not empty:1, 22[/B]
[B][  120.444301] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  122.449743] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  122.697663] ===>tx queue is not empty:1, 57
[  122.800102] ===>tx queue is not empty:1, 57
[  123.005008] ===>tx queue is not empty:1, 57
[  123.209889] ===>tx queue is not empty:1, 57
[  123.619716] ===>tx queue is not empty:1, 61
[  123.927068] ===>tx queue is not empty:1, 63
[  124.029530] ===>tx queue is not empty:1, 63
[  124.131982] ===>tx queue is not empty:1, 63
[  124.234421] ===>tx queue is not empty:1, 63
[  124.336888] ===>tx queue is not empty:1, 63
[  124.439322] ===>tx queue is not empty:1, 63
[  124.452437] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  124.541778] ===>tx queue is not empty:1, 63
[  124.644225] ===>tx queue is not empty:1, 63
[  124.746678] ===>tx queue is not empty:1, 63
[  124.849139] ===>tx queue is not empty:1, 63
[  124.951587] ===>tx queue is not empty:1, 63
[  125.156497] ===>tx queue is not empty:1, 54
[  125.463840] ===>tx queue is not empty:1, 43
[  125.566313] ===>tx queue is not empty:1, 43
[  125.668750] ===>tx queue is not empty:1, 43
[  125.771204] ===>tx queue is not empty:1, 43
[  125.873652] ===>tx queue is not empty:1, 43
[  125.976107] ===>tx queue is not empty:1, 43
[  126.078550] ===>tx queue is not empty:1, 43
[  126.181008] ===>tx queue is not empty:1, 43
[  126.283454] ===>tx queue is not empty:1, 43
[  128.460281] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  128.537374] ===>tx queue is not empty:1, 43
[  128.742279] ===>tx queue is not empty:1, 43
[  128.844738] ===>tx queue is not empty:1, 43
[  128.947196] ===>tx queue is not empty:1, 43
[  129.152111] ===>tx queue is not empty:1, 43
[  129.254533] ===>tx queue is not empty:1, 43
[  129.356978] ===>tx queue is not empty:1, 43
[  129.459460] ===>tx queue is not empty:1, 43
[  129.561916] ===>tx queue is not empty:1, 43
[  129.664349] ===>tx queue is not empty:1, 43
[  129.766822] ===>tx queue is not empty:1, 43
[  129.869243] ===>tx queue is not empty:1, 43
[  129.971725] ===>tx queue is not empty:1, 43
[  130.074166] ===>tx queue is not empty:1, 43
[  130.176606] ===>tx queue is not empty:1, 43
[  130.464303] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  132.468315] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  132.468326] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  133.461073] ieee->state is RTLLIB_LINKED
[  133.493949] Associated successfully
[  133.493961] Using G rates:108
[  133.493964] Successfully associated, ht enabled
[  133.493969] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  133.508904] silent reset associate
[  137.484332] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  137.484343] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  138.477176] ieee->state is RTLLIB_LINKED
[  138.509997] Associated successfully
[  138.510007] Using G rates:108
[  138.510010] Successfully associated, ht enabled
[  138.510015] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  138.524902] silent reset associate
[  142.500309] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  144.504301] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  146.508256] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  146.508267] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  147.501030] ieee->state is RTLLIB_LINKED
[  147.533968] Associated successfully
[  147.533979] Using G rates:108
[  147.533983] Successfully associated, ht enabled
[  147.533987] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  147.548911] silent reset associate
[  151.524273] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  151.524284] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  152.517007] ieee->state is RTLLIB_LINKED
[  152.549940] Associated successfully
[  152.549950] Using G rates:108
[  152.549953] Successfully associated, ht enabled
[  152.549957] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  152.564906] silent reset associate
[  160.548248] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  160.548260] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  161.541029] ieee->state is RTLLIB_LINKED
[  161.573967] Associated successfully
[  161.573979] Using G rates:108
[  161.573982] Successfully associated, ht enabled
[  161.573987] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  161.588912] silent reset associate
[  167.568274] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  169.572278] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  171.576237] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  173.580285] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  173.616082] ===>tx queue is not empty:1, 63
[  173.718503] ===>tx queue is not empty:1, 63
[  173.820944] ===>tx queue is not empty:1, 63
[  173.923410] ===>tx queue is not empty:1, 63
[  174.025857] ===>tx queue is not empty:1, 63
[  174.128305] ===>tx queue is not empty:1, 63
[  174.230750] ===>tx queue is not empty:1, 63
[  174.333202] ===>tx queue is not empty:1, 63
[  174.435664] ===>tx queue is not empty:1, 63
[  174.538129] ===>tx queue is not empty:1, 63
[  174.640569] ===>tx queue is not empty:1, 63
[  174.743014] ===>tx queue is not empty:1, 63
[  174.845467] ===>tx queue is not empty:1, 63
[  174.947929] ===>tx queue is not empty:1, 63
[  175.152825] ===>tx queue is not empty:1, 63
[  175.255286] ===>tx queue is not empty:1, 63
[  175.460190] ===>tx queue is not empty:1, 63
[  175.562649] ===>tx queue is not empty:1, 63
[  175.584309] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=6
[  175.665079] ===>tx queue is not empty:1, 63
[  175.869982] ===>tx queue is not empty:1, 63
[  175.972427] ===>tx queue is not empty:1, 63
[  176.074898] ===>tx queue is not empty:1, 63
[  176.177327] ===>tx queue is not empty:1, 63
[  176.279818] ===>tx queue is not empty:1, 63
[  176.382238] ===>tx queue is not empty:1, 63
[  176.484692] ===>tx queue is not empty:1, 63
[  176.587130] ===>tx queue is not empty:1, 63
[  176.689599] ===>tx queue is not empty:1, 63
[  176.792050] ===>tx queue is not empty:1, 63
[  176.996964] ===>tx queue is not empty:1, 63
[  177.099405] ===>tx queue is not empty:1, 63
[  177.201861] ===>tx queue is not empty:1, 63
[  177.304307] ===>tx queue is not empty:1, 63
[  177.406771] ===>tx queue is not empty:1, 63
[  177.509211] ===>tx queue is not empty:1, 63
[  177.588313] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=7
[  177.588324] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  178.581025] ieee->state is RTLLIB_LINKED
[  178.613942] Associated successfully
[  178.613954] Using G rates:108
[  178.613957] Successfully associated, ht enabled
[  178.613961] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  178.628922] silent reset associate
[  182.604267] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  184.608257] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  186.613595] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  188.616710] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  190.620332] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=6
[  192.624242] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=7
[  192.624253] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  193.616950] ieee->state is RTLLIB_LINKED
[  193.649954] Associated successfully
[  193.649966] Using G rates:108
[  193.649969] Successfully associated, ht enabled
[  193.649974] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  193.664906] silent reset associate
[  197.640243] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  199.644288] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  201.648268] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  203.652285] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  203.652296] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  204.645123] ieee->state is RTLLIB_LINKED
[  204.677944] Associated successfully
[  204.677955] Using G rates:108
[  204.677958] Successfully associated, ht enabled
[  204.677963] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  204.692918] silent reset associate
[  210.672286] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  210.672297] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  211.665058] ieee->state is RTLLIB_LINKED
[  211.697939] Associated successfully
[  211.697950] Using G rates:108
[  211.697953] Successfully associated, ht enabled
[  211.697957] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  211.712895] silent reset associate
[  215.688314] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  217.692268] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  219.696278] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  219.696289] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  220.689097] ieee->state is RTLLIB_LINKED
[  220.721942] Associated successfully
[  220.721951] Using G rates:108
[  220.721954] Successfully associated, ht enabled
[  220.721959] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  220.736914] silent reset associate
[  224.712273] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  226.716276] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  226.716287] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  227.709048] ieee->state is RTLLIB_LINKED
[  227.741962] Associated successfully
[  227.741972] Using G rates:108
[  227.741975] Successfully associated, ht enabled
[  227.741980] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  227.756914] silent reset associate
[  233.736296] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  235.740255] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  237.744495] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  239.748345] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  239.748355] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  240.741037] ieee->state is RTLLIB_LINKED
[  240.773958] Associated successfully
[  240.773969] Using G rates:108
[  240.773972] Successfully associated, ht enabled
[  240.773977] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  240.788902] silent reset associate
[  246.768289] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  248.772285] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  250.776277] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  252.780306] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  252.780317] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  253.773021] ieee->state is RTLLIB_LINKED
[  253.805943] Associated successfully
[  253.805952] Using G rates:108
[  253.805955] Successfully associated, ht enabled
[  253.805960] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  253.820909] silent reset associate
[  257.796292] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  259.800286] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  261.804266] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  261.804278] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  262.797095] ieee->state is RTLLIB_LINKED
[  262.829939] Associated successfully
[  262.829949] Using G rates:108
[  262.829952] Successfully associated, ht enabled
[  262.829957] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  262.844895] silent reset associate
[  268.824249] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  270.828241] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  272.832254] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  274.836291] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  276.840258] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=6
[  278.844242] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=7
[  280.848270] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=8
[  282.852311] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=9
[  284.856415] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=10
[  286.860247] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=11
[  286.927445] ===>tx queue is not empty:1, 63
[  287.029855] ===>tx queue is not empty:1, 63
[  287.132351] ===>tx queue is not empty:1, 63
[  287.234787] ===>tx queue is not empty:1, 63
[  287.337244] ===>tx queue is not empty:1, 63
[  287.542121] ===>tx queue is not empty:1, 63
[  287.644595] ===>tx queue is not empty:1, 63
[  287.747065] ===>tx queue is not empty:1, 63
[  287.849533] ===>tx queue is not empty:1, 63
[  287.951972] ===>tx queue is not empty:1, 63
[  288.054409] ===>tx queue is not empty:1, 63
[  288.156861] ===>tx queue is not empty:1, 63
[  288.259301] ===>tx queue is not empty:1, 63
[  288.361767] ===>tx queue is not empty:1, 63
[  288.464214] ===>tx queue is not empty:1, 63
[  288.566632] ===>tx queue is not empty:1, 63
[  288.669115] ===>tx queue is not empty:1, 63
[  288.771555] ===>tx queue is not empty:1, 63
[  288.864294] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=12
[  288.864305] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  289.856989] ieee->state is RTLLIB_LINKED
[  289.890013] Associated successfully
[  289.890024] Using G rates:108
[  289.890028] Successfully associated, ht enabled
[  289.890032] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  289.904925] silent reset associate
[  291.332843] ===>tx queue is not empty:1, 4
[  291.640202] ===>tx queue is not empty:1, 4
[  293.884283] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  295.884337] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  297.888256] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  299.892210] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  301.896266] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=6
[  303.900885] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=7
[  303.900896] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  304.893654] ieee->state is RTLLIB_LINKED
[  304.925956] Associated successfully
[  304.925966] Using G rates:108
[  304.925970] Successfully associated, ht enabled
[  304.925974] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  304.940964] silent reset associate
[  308.544685] ===>tx queue is not empty:1, 12
[  308.749596] ===>tx queue is not empty:1, 12
[  310.920286] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  310.920297] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  311.913134] ieee->state is RTLLIB_LINKED
[  311.945928] Associated successfully
[  311.945939] Using G rates:108
[  311.945942] Successfully associated, ht enabled
[  311.945947] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  311.960905] silent reset associate
[  319.944208] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  319.944217] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  320.936923] ieee->state is RTLLIB_LINKED
[  320.969953] Associated successfully
[  320.969965] Using G rates:108
[  320.969968] Successfully associated, ht enabled
[  320.969973] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  320.984920] silent reset associate[/B]

```

Any further suggestions?

**Edit: **
I noticed something i have read earlier, with "lsmod" i can find 2 modules loaded.
To name them, i can find "r8192e_pci" and "rtl8192se".
I unloaded both via "modprobe -r <modulname>" and loaded them each alone.
With only "r8192e_pci" it works with described problems, plus it appears to be even worse.
With only "rtl8192se" the Networkmanager is not able to detect any Wireless at all.

---

### Post by Joel_Ross on 2014-05-31
> **killerlink23 said:**
> At first I made a small mistake in my starting post, i wrote rtl8192e/ce but it is rtl8192e/_**s**_e. My Apologies.

Yeah the RTL8192SE is supported, but the maintaner doesn't test that chipset . Luckliy I have the RTL8192CE and it's tested and works. In my opinion it's best to stay away from Realtek chipsets on Linux systems, have you thought about reseaching a USB wireless stick and trying that out?

To help get a better idea of your system run the following commands:

```
echo "lsmod...."; lsmod | grep rtl; echo "lspic...."; lspci | grep -i rtl; echo "uname...."; uname -a; echo "modprobe.conf......"; cat /etc/modprobe.d/modprobe.conf; echo "list modporbe confs....."; ls -l /etc/modprobe.d/
```

and post it's output here, maybe this can give us some idea of the problem.

regrading the dmesg log. I dont like the look of ***"rtlwifi: module verification failed: signature and/or required key missing - tainting kernel"*** maybe someone can shed some light on whats happening here.

---

### Post by killerlink23 on 2014-06-01
Hello Joel_Ross, thanks for your Reply!
This is the output of the commands you asked me to execute:

```

**lsmod....**
rtllib_crypt_ccmp      12829  -1 
rtllib                151694  1 r8192e_pci
lib80211               14381  2 rtllib,rtllib_crypt_ccmp
rtl8192se              63095  0 
rtlwifi                77765  1 rtl8192se
mac80211              626511  2 rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi
**lspic....**
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
**uname....**
Linux brimi-Satellite-L350 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
**modprobe.conf......**
# disable power save and enable sw encryption (added by FreedomBen's driver)
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1
**list modporbe confs.....**
insgesamt 52
-rw-r--r-- 1 root root 2507 Feb 13  2013 alsa-base.conf
-rw-r--r-- 1 root root  325 Apr 10 16:07 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 Apr 10 16:07 blacklist.conf
-rw-r--r-- 1 root root  210 Apr 10 16:07 blacklist-firewire.conf
-rw-r--r-- 1 root root  677 Apr 10 16:07 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Feb 13  2013 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Mai 26 19:49 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Apr 10 16:07 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Apr 10 16:07 blacklist-watchdog.conf
-rw-r--r-- 1 root root  456 Apr 14 18:34 fbdev-blacklist.conf
-rw-r--r-- 1 root root  347 Apr 10 16:07 iwlwifi.conf
-rw-r--r-- 1 root root  104 Apr 10 16:07 mlx4.conf
-rw-r--r-- 1 root root  153 Mai 31 18:14 modprobe.conf
-rw-r--r-- 1 root root   30 Apr 10 10:56 vmwgfx-fbdev.conf

```

I personally would like to stay away from Realtek aswell, but unluckily its hard to change Laptops internal WLAN modules :grin: thats why i love my Desktop-PCs.
I  have a working WLAN-USB-Stick, but i would prefer to get internal WLAN  working because the Laptop only has 3 USB Ports. Plus, it would be  better if I dont need to carry around the WLAN Stick all the time, the  idee behind Laptops should be an All-In-One Device, working without any  externals, atleast that's what i think.

As always, thanks in Advance!

---

### Post by Joel_Ross on 2014-06-02
> **killerlink23 said:**
> I dont need to carry around the WLAN Stick all the time, the  idee behind Laptops should be an All-In-One Device, working without any  externals, atleast that's what i think.

Couldn't agree more. 

what's the output of ```
modinfo rtl8192se
```

post here, i want to see what it's parameters are

---

### Post by killerlink23 on 2014-06-02
Here, this is the output of the command you requested:

"modinfo rtl8192se"
```

filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     21FEB9B2E4FF24EF04BC0BA
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```

best regards!

---

### Post by Joel_Ross on 2014-06-02
try replacing the content of /etc/modprobe.d/modprobe.conf by removing current content and replacing with 


```

options rtl8192se ips=1
options rtl8192se swenc=1
options rtl8192se fwlps=0
options rtl8192se debug=5

```

then run 

```

rmmod rtl8192se; modprobe rtl8192se

```

then post dmesg output here.

---

### Post by killerlink23 on 2014-06-02
I did what you suggested. 
Interesting enough the old content of modprobe.conf already included the first 3 options, just for "ce" and not "se". I changed it to exactly what you have written now.

Here is the new dmesg output:
```

[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bfd6bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfd6c000-0x00000000bfdbefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bfdbf000-0x00000000bfe85fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfe86000-0x00000000bfebefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bfebf000-0x00000000bfeebfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bfeec000-0x00000000bfefefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bfeff000-0x00000000bfefffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bff00000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000013fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: TOSHIBA Satellite L350/Portable PC, BIOS 1.00 06/23/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-CFFFF uncachable
[    0.000000]   D0000-DFFFF write-protect
[    0.000000]   E0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFFE0000 mask FFFFE0000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 base 100000000 mask FC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbff00 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13fe00000-0x13fffffff]
[    0.000000]  [mem 0x13fe00000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x13c000000-0x13fdfffff]
[    0.000000]  [mem 0x13c000000-0x13fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x13bffffff]
[    0.000000]  [mem 0x100000000-0x13bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbfd6bfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbfbfffff] page 2M
[    0.000000]  [mem 0xbfc00000-0xbfd6bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbfdbf000-0xbfe85fff]
[    0.000000]  [mem 0xbfdbf000-0xbfe85fff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbfebf000-0xbfeebfff]
[    0.000000]  [mem 0xbfebf000-0xbfeebfff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbfeff000-0xbfefffff]
[    0.000000]  [mem 0xbfeff000-0xbfefffff] page 4k
[    0.000000] RAMDISK: [mem 0x35b80000-0x36db7fff]
[    0.000000] ACPI: RSDP 00000000000fe020 000024 (v02 TOSINV)
[    0.000000] ACPI: XSDT 00000000bfefe120 000064 (v01 TOSINV TOSINV00 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bfefd000 0000F4 (v04 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bfeef000 0095DC (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bfe93000 000040
[    0.000000] ACPI: HPET 00000000bfefc000 000038 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bfefb000 00006C (v02 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bfefa000 00003C (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 00000000bfef9000 0000A5 (v32 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bfeee000 000176 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 00000000bfeed000 000028 (v01 TOSINV TOSINV00 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bfeec000 000655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000013fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x13fffffff]
[    0.000000]   NODE_DATA [mem 0x13fff8000-0x13fffcfff]
[    0.000000]  [ffffea0000000000-ffffea0004ffffff] PMD -> [ffff88013b600000-ffff88013f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x13fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xbfd6bfff]
[    0.000000]   node   0: [mem 0xbfdbf000-0xbfe85fff]
[    0.000000]   node   0: [mem 0xbfebf000-0xbfeebfff]
[    0.000000]   node   0: [mem 0xbfeff000-0xbfefffff]
[    0.000000]   node   0: [mem 0x100000000-0x13fffffff]
[    0.000000] On node 0 totalpages: 1048062
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12218 pages used for memmap
[    0.000000]   DMA32 zone: 781921 pages, LIFO batch:31
[    0.000000]   Normal zone: 4096 pages used for memmap
[    0.000000]   Normal zone: 262144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfd6c000-0xbfdbefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfe86000-0xbfebefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbfeec000-0xbfefefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbff00000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfff00000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88013fc00000 s86336 r8192 d24256 u524288
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031663
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=23d0f4f8-ae79-438f-aa36-c83a6d37a4f2 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4024900K/4192248K available (7354K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 167348K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2094.784 MHz processor
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.56 BogoMIPS (lpj=8379136)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004044] Security Framework initialized
[    0.004071] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004541] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.008268] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.009351] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.009363] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.009716] Initializing cgroup subsys memory
[    0.009729] Initializing cgroup subsys devices
[    0.009731] Initializing cgroup subsys freezer
[    0.009734] Initializing cgroup subsys blkio
[    0.009736] Initializing cgroup subsys perf_event
[    0.009740] Initializing cgroup subsys hugetlb
[    0.009770] CPU: Physical Processor ID: 0
[    0.009772] CPU: Processor Core ID: 0
[    0.009775] mce: CPU supports 6 MCE banks
[    0.009784] CPU0: Thermal monitoring enabled (TM2)
[    0.009793] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.009793] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.009793] tlb_flushall_shift: -1
[    0.009916] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.011664] ACPI: Core revision 20131115
[    0.011668] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.011778] ACPI: Forced DSDT copy: length 0x095DC copied locally, original unmapped
[    0.018598] ACPI: All ACPI Tables successfully acquired
[    0.020011] ftrace: allocating 28458 entries in 112 pages
[    0.032544] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074174] smpboot: CPU0: Intel Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz (fam: 06, model: 17, stepping: 0a)
[    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.076000] ... version:                2
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   3
[    0.076000] ... event mask:             0000000700000003
[    0.077487] x86: Booting SMP configuration:
[    0.077491] .... node  #0, CPUs:      #1
[    0.090576] x86: Booted up 1 node, 2 CPUs
[    0.090580] smpboot: Total of 2 processors activated (8379.13 BogoMIPS)
[    0.090712] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.091760] devtmpfs: initialized
[    0.094932] EVM: security.selinux
[    0.094934] EVM: security.SMACK64
[    0.094936] EVM: security.ima
[    0.094937] EVM: security.capability
[    0.096031] PM: Registering ACPI NVS region [mem 0xbfe86000-0xbfebefff] (233472 bytes)
[    0.097019] pinctrl core: initialized pinctrl subsystem
[    0.097019] regulator-dummy: no parameters
[    0.097019] RTC time:  0:14:23, date: 06/03/14
[    0.097019] NET: Registered protocol family 16
[    0.097019] cpuidle: using governor ladder
[    0.097019] cpuidle: using governor menu
[    0.097019] ACPI: bus type PCI registered
[    0.097019] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.097019] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.097019] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.103325] PCI: Using configuration type 1 for base access
[    0.103516] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.103517] mtrr: probably your BIOS does not setup all CPUs.
[    0.103519] mtrr: corrected configuration.
[    0.104626] bio: create slab <bio-0> at 0
[    0.104626] ACPI: Added _OSI(Module Device)
[    0.104626] ACPI: Added _OSI(Processor Device)
[    0.104626] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.104626] ACPI: Added _OSI(Processor Aggregator Device)
[    0.109223] ACPI: Executed 1 blocks of module-level executable AML code
[    0.110281] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.113483] ACPI: SSDT 00000000bfd77c98 000229 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.114006] ACPI: Dynamic OEM Table Load:
[    0.114009] ACPI: SSDT           (null) 000229 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.114176] ACPI: SSDT 00000000bfd75598 000537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.114681] ACPI: Dynamic OEM Table Load:
[    0.114684] ACPI: SSDT           (null) 000537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.124310] ACPI: SSDT 00000000bfd76e18 0001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.124848] ACPI: Dynamic OEM Table Load:
[    0.124851] ACPI: SSDT           (null) 0001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.128132] ACPI: SSDT 00000000bfd77f18 00008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.128650] ACPI: Dynamic OEM Table Load:
[    0.128653] ACPI: SSDT           (null) 00008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.132027] ACPI : EC: GPE storm detected(73 GPEs), transactions will use polling mode
[    0.260477] ACPI: Interpreter enabled
[    0.260487] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.260496] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.260524] ACPI: (supports S0 S3 S4 S5)
[    0.260526] ACPI: Using IOAPIC for interrupt routing
[    0.260564] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.260714] ACPI: No dock devices found.
[    0.270760] ACPI: Power Resource [FN00] (on)
[    0.271936] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.271943] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.271950] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.272510] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.272710] PCI host bridge to bus 0000:00
[    0.272713] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.272716] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.272719] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.272721] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.272724] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    0.272735] pci 0000:00:00.0: [8086:2a40] type 00 class 0x060000
[    0.272760] DMAR: Forcing write-buffer flush capability
[    0.272762] DMAR: Disabling IOMMU for graphics on this chipset
[    0.272857] pci 0000:00:01.0: [8086:2a41] type 01 class 0x060400
[    0.272908] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.273039] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
[    0.273117] pci 0000:00:1a.0: reg 0x20: [io  0x70e0-0x70ff]
[    0.273256] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
[    0.273344] pci 0000:00:1a.1: reg 0x20: [io  0x70c0-0x70df]
[    0.273503] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
[    0.273534] pci 0000:00:1a.7: reg 0x10: [mem 0xd6304c00-0xd6304fff]
[    0.273664] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.273766] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
[    0.273789] pci 0000:00:1b.0: reg 0x10: [mem 0xd6300000-0xd6303fff 64bit]
[    0.273887] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.273944] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.273990] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
[    0.274086] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.274148] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.274191] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
[    0.274290] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.274394] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
[    0.274487] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.274590] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
[    0.274666] pci 0000:00:1d.0: reg 0x20: [io  0x70a0-0x70bf]
[    0.274814] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.274862] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
[    0.274948] pci 0000:00:1d.1: reg 0x20: [io  0x7080-0x709f]
[    0.275089] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.275136] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
[    0.275218] pci 0000:00:1d.2: reg 0x20: [io  0x7060-0x707f]
[    0.275382] pci 0000:00:1d.3: [8086:2939] type 00 class 0x0c0300
[    0.275467] pci 0000:00:1d.3: reg 0x20: [io  0x7040-0x705f]
[    0.275635] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
[    0.275666] pci 0000:00:1d.7: reg 0x10: [mem 0xd6304800-0xd6304bff]
[    0.275795] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.275871] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.275914] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.276041] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.276086] pci 0000:00:1f.0: [8086:2919] type 00 class 0x060100
[    0.276303] pci 0000:00:1f.2: [8086:2929] type 00 class 0x010601
[    0.276331] pci 0000:00:1f.2: reg 0x10: [io  0x7108-0x710f]
[    0.276342] pci 0000:00:1f.2: reg 0x14: [io  0x7114-0x7117]
[    0.276353] pci 0000:00:1f.2: reg 0x18: [io  0x7100-0x7107]
[    0.276364] pci 0000:00:1f.2: reg 0x1c: [io  0x7110-0x7113]
[    0.276376] pci 0000:00:1f.2: reg 0x20: [io  0x7020-0x703f]
[    0.276388] pci 0000:00:1f.2: reg 0x24: [mem 0xd6304000-0xd63047ff]
[    0.276459] pci 0000:00:1f.2: PME# supported from D3hot
[    0.276555] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
[    0.276578] pci 0000:00:1f.3: reg 0x10: [mem 0xd6305000-0xd63050ff 64bit]
[    0.276611] pci 0000:00:1f.3: reg 0x20: [io  0x7000-0x701f]
[    0.276781] pci 0000:01:00.0: [1002:9480] type 00 class 0x030000
[    0.276799] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff pref]
[    0.276812] pci 0000:01:00.0: reg 0x14: [io  0x6000-0x60ff]
[    0.276825] pci 0000:01:00.0: reg 0x18: [mem 0xd6200000-0xd620ffff]
[    0.276868] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.276924] pci 0000:01:00.0: supports D1 D2
[    0.276993] pci 0000:01:00.1: [1002:aa38] type 00 class 0x040300
[    0.277011] pci 0000:01:00.1: reg 0x10: [mem 0xd6210000-0xd6213fff]
[    0.277127] pci 0000:01:00.1: supports D1 D2
[    0.284020] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.284024] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    0.284028] pci 0000:00:01.0:   bridge window [mem 0xd6200000-0xd62fffff]
[    0.284033] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.284188] pci 0000:02:00.0: [10ec:8136] type 00 class 0x020000
[    0.284253] pci 0000:02:00.0: reg 0x10: [io  0x4000-0x40ff]
[    0.284367] pci 0000:02:00.0: reg 0x18: [mem 0xd0010000-0xd0010fff 64bit pref]
[    0.284437] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd000ffff 64bit pref]
[    0.284483] pci 0000:02:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.284748] pci 0000:02:00.0: supports D1 D2
[    0.284751] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.284945] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.284951] pci 0000:00:1c.0:   bridge window [io  0x4000-0x5fff]
[    0.284956] pci 0000:00:1c.0:   bridge window [mem 0xd5200000-0xd61fffff]
[    0.284964] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd10fffff 64bit pref]
[    0.285070] pci 0000:03:00.0: [10ec:8192] type 00 class 0x028000
[    0.285094] pci 0000:03:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.285111] pci 0000:03:00.0: reg 0x14: [mem 0xd4100000-0xd4103fff]
[    0.285259] pci 0000:03:00.0: supports D1 D2
[    0.285261] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.292027] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.292033] pci 0000:00:1c.1:   bridge window [io  0x2000-0x3fff]
[    0.292039] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd51fffff]
[    0.292046] pci 0000:00:1c.1:   bridge window [mem 0xd1100000-0xd20fffff 64bit pref]
[    0.292144] acpiphp: Slot [1] registered
[    0.292152] pci 0000:00:1c.4: PCI bridge to [bus 07-08]
[    0.292157] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.292162] pci 0000:00:1c.4:   bridge window [mem 0xd3100000-0xd40fffff]
[    0.292170] pci 0000:00:1c.4:   bridge window [mem 0xd2100000-0xd30fffff 64bit pref]
[    0.292267] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.292281] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.292284] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.292287] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.292289] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.292457] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12)
[    0.292532] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.292604] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.292675] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.292747] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.292820] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.292891] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.292962] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.293737] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.293752] ACPI: \_SB_.PCI0: notify handler is installed
[    0.293806] Found 1 acpi root devices
[    0.293868] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.296026] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.296029] vgaarb: loaded
[    0.296031] vgaarb: bridge control possible 0000:01:00.0
[    0.296264] SCSI subsystem initialized
[    0.296291] libata version 3.00 loaded.
[    0.296291] ACPI: bus type USB registered
[    0.296291] usbcore: registered new interface driver usbfs
[    0.296291] usbcore: registered new interface driver hub
[    0.296291] usbcore: registered new device driver usb
[    0.296291] PCI: Using ACPI for IRQ routing
[    0.298113] PCI: pci_cache_line_size set to 64 bytes
[    0.298207] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.298209] e820: reserve RAM buffer [mem 0xbfd6c000-0xbfffffff]
[    0.298212] e820: reserve RAM buffer [mem 0xbfe86000-0xbfffffff]
[    0.298214] e820: reserve RAM buffer [mem 0xbfeec000-0xbfffffff]
[    0.298216] e820: reserve RAM buffer [mem 0xbff00000-0xbfffffff]
[    0.298337] NetLabel: Initializing
[    0.298340] NetLabel:  domain hash size = 128
[    0.298341] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.298359] NetLabel:  unlabeled traffic allowed by default
[    0.298378] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.298378] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.298378] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.301021] Switched to clocksource hpet
[    0.308576] AppArmor: AppArmor Filesystem Enabled
[    0.308631] pnp: PnP ACPI init
[    0.308650] ACPI: bus type PNP registered
[    0.309015] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff]
[    0.309099] system 00:00: [io  0x0800-0x080f] has been reserved
[    0.309103] system 00:00: [io  0x0810-0x0817] has been reserved
[    0.309106] system 00:00: [io  0x0820-0x0823] has been reserved
[    0.309109] system 00:00: [io  0x0400-0x047f] could not be reserved
[    0.309111] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.309115] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.309118] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.309121] system 00:00: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.309124] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.309127] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.309130] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.309133] system 00:00: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.309136] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.309139] system 00:00: [mem 0xff800000-0xffffffff] could not be reserved
[    0.309144] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.309156] pnp 00:01: [dma 4]
[    0.309181] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.309231] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.309334] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.309375] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.309421] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.309469] pnp 00:06: Plug and Play ACPI device, IDs SYN1913 SYN1900 SYN0002 PNP0f13 (active)
[    0.309574] pnp: PnP ACPI: found 7 devices
[    0.309576] ACPI: bus type PNP unregistered
[    0.316578] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.316583] pci 0000:02:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.316647] pci 0000:01:00.0: BAR 6: assigned [mem 0xd6220000-0xd623ffff pref]
[    0.316651] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.316654] pci 0000:00:01.0:   bridge window [io  0x6000-0x6fff]
[    0.316658] pci 0000:00:01.0:   bridge window [mem 0xd6200000-0xd62fffff]
[    0.316663] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.316669] pci 0000:02:00.0: BAR 6: assigned [mem 0xd0020000-0xd003ffff pref]
[    0.316671] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.316675] pci 0000:00:1c.0:   bridge window [io  0x4000-0x5fff]
[    0.316682] pci 0000:00:1c.0:   bridge window [mem 0xd5200000-0xd61fffff]
[    0.316687] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd10fffff 64bit pref]
[    0.316696] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.316699] pci 0000:00:1c.1:   bridge window [io  0x2000-0x3fff]
[    0.316706] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd51fffff]
[    0.316711] pci 0000:00:1c.1:   bridge window [mem 0xd1100000-0xd20fffff 64bit pref]
[    0.316720] pci 0000:00:1c.4: PCI bridge to [bus 07-08]
[    0.316723] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.316730] pci 0000:00:1c.4:   bridge window [mem 0xd3100000-0xd40fffff]
[    0.316735] pci 0000:00:1c.4:   bridge window [mem 0xd2100000-0xd30fffff 64bit pref]
[    0.316744] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.316759] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.316761] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.316764] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.316767] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.316769] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    0.316772] pci_bus 0000:01: resource 1 [mem 0xd6200000-0xd62fffff]
[    0.316774] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.316777] pci_bus 0000:02: resource 0 [io  0x4000-0x5fff]
[    0.316780] pci_bus 0000:02: resource 1 [mem 0xd5200000-0xd61fffff]
[    0.316782] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd10fffff 64bit pref]
[    0.316785] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
[    0.316787] pci_bus 0000:03: resource 1 [mem 0xd4100000-0xd51fffff]
[    0.316790] pci_bus 0000:03: resource 2 [mem 0xd1100000-0xd20fffff 64bit pref]
[    0.316793] pci_bus 0000:07: resource 0 [io  0x1000-0x1fff]
[    0.316795] pci_bus 0000:07: resource 1 [mem 0xd3100000-0xd40fffff]
[    0.316798] pci_bus 0000:07: resource 2 [mem 0xd2100000-0xd30fffff 64bit pref]
[    0.316800] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.316803] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.316805] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.316808] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.316851] NET: Registered protocol family 2
[    0.317044] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.317201] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.317387] TCP: Hash tables configured (established 32768 bind 32768)
[    0.317448] TCP: reno registered
[    0.317460] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.317495] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.317637] NET: Registered protocol family 1
[    1.916020] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.516019] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.516284] pci 0000:01:00.0: Boot video device
[    3.516302] PCI: CLS 64 bytes, default 64
[    3.516386] Trying to unpack rootfs image as initramfs...
[    3.910701] Freeing initrd memory: 18656K (ffff880035b80000 - ffff880036db8000)
[    3.910711] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    3.910714] software IO TLB [mem 0xbbd6c000-0xbfd6c000] (64MB) mapped at [ffff8800bbd6c000-ffff8800bfd6bfff]
[    3.910828] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    3.910830] Simple Boot Flag at 0x44 set to 0x1
[    3.910987] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[    3.910994] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[    3.911075] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.911077] Scanning for low memory corruption every 60 seconds
[    3.911366] Initialise system trusted keyring
[    3.911428] audit: initializing netlink socket (disabled)
[    3.911443] type=2000 audit(1401754465.904:1): initialized
[    3.943335] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.945035] zbud: loaded
[    3.945198] VFS: Disk quotas dquot_6.5.2
[    3.945256] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.945834] fuse init (API version 7.22)
[    3.945935] msgmni has been set to 7897
[    3.946003] Key type big_key registered
[    3.946476] Key type asymmetric registered
[    3.946479] Asymmetric key parser 'x509' registered
[    3.946523] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    3.946566] io scheduler noop registered
[    3.946569] io scheduler deadline registered (default)
[    3.946599] io scheduler cfq registered
[    3.946913] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    3.947137] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    3.947376] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    3.947458] pcieport 0000:00:1c.4: enabling device (0000 -> 0003)
[    3.947626] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    3.947727] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.947747] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.947798] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[    3.947800] vesafb: scrolling: redraw
[    3.947802] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.948324] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90004780000, using 3904k, total 3904k
[    4.008642] Console: switching to colour frame buffer device 144x54
[    4.068868] fb0: VESA VGA frame buffer device
[    4.068905] intel_idle: does not run on family 6 model 23
[    4.068914] ipmi message handler version 39.2
[    4.069074] ACPI: AC Adapter [ADP0] (on-line)
[    4.069208] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    4.069213] ACPI: Power Button [PWRB]
[    4.069264] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    4.070784] ACPI: Lid Switch [LID0]
[    4.070852] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.070856] ACPI: Power Button [PWRF]
[    4.070918] ACPI: Fan [FAN] (on)
[    4.071083] Monitor-Mwait will be used to enter C-1 state
[    4.071090] Monitor-Mwait will be used to enter C-2 state
[    4.071094] tsc: Marking TSC unstable due to TSC halts in idle
[    4.071099] ACPI: acpi_idle registered with cpuidle
[    4.077706] thermal LNXTHERM:00: registered as thermal_zone0
[    4.077709] ACPI: Thermal Zone [THRM] (61 C)
[    4.077748] GHES: HEST is not enabled!
[    4.077836] ACPI: Battery Slot [BAT0] (battery absent)
[    4.077879] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.080076] Linux agpgart interface v0.103
[    4.082061] brd: module loaded
[    4.083044] loop: module loaded
[    4.083537] libphy: Fixed MDIO Bus: probed
[    4.083660] tun: Universal TUN/TAP device driver, 1.6
[    4.083662] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.083729] PPP generic driver version 2.4.2
[    4.083795] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.083810] ehci-pci: EHCI PCI platform driver
[    4.084097] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    4.084105] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.084123] ehci-pci 0000:00:1a.7: debug port 1
[    4.088048] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    4.088078] ehci-pci 0000:00:1a.7: irq 19, io mem 0xd6304c00
[    4.104024] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.104089] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.104092] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.104094] usb usb1: Product: EHCI Host Controller
[    4.104097] usb usb1: Manufacturer: Linux 3.13.0-27-generic ehci_hcd
[    4.104099] usb usb1: SerialNumber: 0000:00:1a.7
[    4.104246] hub 1-0:1.0: USB hub found
[    4.104257] hub 1-0:1.0: 4 ports detected
[    4.104578] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    4.104585] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.104601] ehci-pci 0000:00:1d.7: debug port 1
[    4.108525] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    4.108547] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd6304800
[    4.120022] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.120098] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.120101] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.120104] usb usb2: Product: EHCI Host Controller
[    4.120106] usb usb2: Manufacturer: Linux 3.13.0-27-generic ehci_hcd
[    4.120109] usb usb2: SerialNumber: 0000:00:1d.7
[    4.120250] hub 2-0:1.0: USB hub found
[    4.120260] hub 2-0:1.0: 8 ports detected
[    4.120459] ehci-platform: EHCI generic platform driver
[    4.120475] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.120477] ohci-pci: OHCI PCI platform driver
[    4.120491] ohci-platform: OHCI generic platform driver
[    4.120499] uhci_hcd: USB Universal Host Controller Interface driver
[    4.120689] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.120696] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.120745] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070e0
[    4.120809] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    4.120812] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.120814] usb usb3: Product: UHCI Host Controller
[    4.120817] usb usb3: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.120819] usb usb3: SerialNumber: 0000:00:1a.0
[    4.120965] hub 3-0:1.0: USB hub found
[    4.120975] hub 3-0:1.0: 2 ports detected
[    4.121246] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.121253] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.121295] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000070c0
[    4.121360] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    4.121363] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.121365] usb usb4: Product: UHCI Host Controller
[    4.121368] usb usb4: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.121370] usb usb4: SerialNumber: 0000:00:1a.1
[    4.121512] hub 4-0:1.0: USB hub found
[    4.121521] hub 4-0:1.0: 2 ports detected
[    4.121784] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.121791] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.121824] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000070a0
[    4.121887] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    4.121890] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.121892] usb usb5: Product: UHCI Host Controller
[    4.121895] usb usb5: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.121897] usb usb5: SerialNumber: 0000:00:1d.0
[    4.122041] hub 5-0:1.0: USB hub found
[    4.122050] hub 5-0:1.0: 2 ports detected
[    4.122316] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.122322] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.122353] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00007080
[    4.122413] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    4.122416] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.122418] usb usb6: Product: UHCI Host Controller
[    4.122421] usb usb6: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.122423] usb usb6: SerialNumber: 0000:00:1d.1
[    4.122559] hub 6-0:1.0: USB hub found
[    4.122571] hub 6-0:1.0: 2 ports detected
[    4.122832] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.122839] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.122871] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00007060
[    4.122933] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    4.122936] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.122939] usb usb7: Product: UHCI Host Controller
[    4.122941] usb usb7: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.122943] usb usb7: SerialNumber: 0000:00:1d.2
[    4.123066] hub 7-0:1.0: USB hub found
[    4.123078] hub 7-0:1.0: 2 ports detected
[    4.123339] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.123345] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.123388] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00007040
[    4.123453] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    4.123456] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.123459] usb usb8: Product: UHCI Host Controller
[    4.123461] usb usb8: Manufacturer: Linux 3.13.0-27-generic uhci_hcd
[    4.123463] usb usb8: SerialNumber: 0000:00:1d.3
[    4.123587] hub 8-0:1.0: USB hub found
[    4.123597] hub 8-0:1.0: 2 ports detected
[    4.123775] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    4.150794] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.150801] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.150976] mousedev: PS/2 mouse device common for all mice
[    4.151798] rtc_cmos 00:02: RTC can wake from S4
[    4.151978] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    4.152031] rtc_cmos 00:02: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.152125] device-mapper: uevent: version 1.0.3
[    4.152217] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    4.152226] ledtrig-cpu: registered to indicate activity on CPUs
[    4.152348] TCP: cubic registered
[    4.152471] NET: Registered protocol family 10
[    4.152686] NET: Registered protocol family 17
[    4.152703] Key type dns_resolver registered
[    4.153022] Loading compiled-in X.509 certificates
[    4.154277] Loaded X.509 cert 'Magrathea: Glacier signing key: 23984ac203784325ccf7b95b51f6c119380eb933'
[    4.154296] registered taskstats version 1
[    4.157721] Key type trusted registered
[    4.160681] Key type encrypted registered
[    4.163562] AppArmor: AppArmor sha1 policy hashing enabled
[    4.163567] IMA: No TPM chip found, activating TPM-bypass!
[    4.164081] regulator-dummy: disabling
[    4.164141]   Magic number: 2:388:202
[    4.164214] acpi device:2a: hash matches
[    4.164287] rtc_cmos 00:02: setting system clock to 2014-06-03 00:14:27 UTC (1401754467)
[    4.164684] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.164687] EDD information not available.
[    4.164744] PM: Hibernation image not present or could not be loaded.
[    4.166649] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    4.166654] Write protecting the kernel read-only data: 12288k
[    4.169859] Freeing unused kernel memory: 828K (ffff880001731000 - ffff880001800000)
[    4.172346] Freeing unused kernel memory: 700K (ffff880001b51000 - ffff880001c00000)
[    4.187785] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.193156] systemd-udevd[102]: starting version 204
[    4.247141] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.247158] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.247555] r8169 0000:02:00.0: irq 44 for MSI/MSI-X
[    4.248884] r8169 0000:02:00.0 eth0: RTL8102e at 0xffffc9000063e000, 00:1e:33:de:02:0d, XID 04c00000 IRQ 44
[    4.252416] ahci 0000:00:1f.2: version 3.0
[    4.252686] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    4.252796] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.252800] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc ems sxs 
[    4.277630] scsi0 : ahci
[    4.280057] scsi1 : ahci
[    4.282534] scsi2 : ahci
[    4.286618] scsi3 : ahci
[    4.286788] scsi4 : ahci
[    4.286886] scsi5 : ahci
[    4.286943] ata1: SATA max UDMA/133 abar m2048@0xd6304000 port 0xd6304100 irq 45
[    4.286947] ata2: SATA max UDMA/133 abar m2048@0xd6304000 port 0xd6304180 irq 45
[    4.286949] ata3: DUMMY
[    4.286950] ata4: DUMMY
[    4.286954] ata5: SATA max UDMA/133 abar m2048@0xd6304000 port 0xd6304300 irq 45
[    4.286957] ata6: SATA max UDMA/133 abar m2048@0xd6304000 port 0xd6304380 irq 45
[    4.416056] usb 1-2: new high-speed USB device number 2 using ehci-pci
[    4.586888] usb 1-2: New USB device found, idVendor=04f2, idProduct=b070
[    4.586891] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    4.586894] usb 1-2: Product: CNF7051
[    4.586897] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
[    4.586899] usb 1-2: SerialNumber: SN0001
[    4.612044] ata1: SATA link down (SStatus 0 SControl 300)
[    4.616041] ata5: SATA link down (SStatus 0 SControl 300)
[    4.784630] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.792034] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.793421] ata6.00: ATAPI: MATSHITADVD-RAM UJ880AS, 1.50, max UDMA/33
[    4.795114] ata6.00: configured for UDMA/33
[    4.846071] ata2.00: ATA-8: TOSHIBA MK4055GSX, FG011M, max UDMA/100
[    4.846074] ata2.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.846840] ata2.00: configured for UDMA/100
[    4.846990] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK4055GS FG01 PQ: 0 ANSI: 5
[    4.847219] sd 1:0:0:0: [sda] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    4.847222] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    4.847299] sd 1:0:0:0: [sda] Write Protect is off
[    4.847302] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.847333] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.884057] usb 6-1: new low-speed USB device number 2 using uhci_hcd
[    4.923308]  sda: sda1 sda2 < sda5 >
[    4.923769] sd 1:0:0:0: [sda] Attached SCSI disk
[    5.065402] usb 6-1: New USB device found, idVendor=03f0, idProduct=0f0c
[    5.065406] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.065408] usb 6-1: Product: USB Multimedia Wireless Kit
[    5.065411] usb 6-1: Manufacturer: Chicony
[    5.072500] hidraw: raw HID events driver (C) Jiri Kosina
[    5.115907] usbcore: registered new interface driver usbhid
[    5.115911] usbhid: USB HID core driver
[    5.119729] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input6
[    5.119849] hid-generic 0003:03F0:0F0C.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.1-1/input0
[    5.120417] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input7
[    5.120618] hid-generic 0003:03F0:0F0C.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.1-1/input1
[    5.294655] scsi 5:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ880AS  1.50 PQ: 0 ANSI: 5
[    5.352128] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa04000/0x20000, board id: 3655, fw id: 515625
[    5.352138] psmouse serio1: synaptics: Toshiba Satellite L350 detected, limiting rate to 40pps.
[    5.424866] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    5.793370] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.793374] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.793543] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.793659] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    6.173586] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    7.603807] random: init urandom read with 126 bits of entropy available
[    7.661261] random: nonblocking pool is initialized
[   16.782250] Adding 3998716k swap on /dev/sda1.  Priority:-1 extents:1 across:3998716k FS
[   16.827830] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.969729] systemd-udevd[279]: starting version 204
[   17.193623] lp: driver loaded but no devices found
[   17.206080] ppdev: user-space parallel port driver
[   17.251892] wmi: Mapper loaded
[   17.280291] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   17.280849] input: Toshiba input device as /devices/virtual/input/input8
[   17.306655] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   17.308446] [drm] Initialized drm 1.1.0 20060810
[   17.347265] cfg80211: Calling CRDA to update world regulatory domain
[   17.425739] [drm] radeon kernel modesetting enabled.
[   17.425831] checking generic (c0000000 3d0000) vs hw (c0000000 10000000)
[   17.425834] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   17.425863] Console: switching to colour dummy device 80x25
[   17.426098] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.440546] acpi device:1a: registered as cooling_device3
[   17.440658] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:18/LNXVIDEO:00/input/input9
[   17.456153] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[   17.461687] [drm] initializing kernel modesetting (RV730 0x1002:0x9480 0x1179:0xFF22).
[   17.461720] [drm] register mmio base: 0xD6200000
[   17.461722] [drm] register mmio size: 65536
[   17.462668] ATOM BIOS: Toshiba_Inventec_Chelsea_M96M2_DDR3
[   17.462731] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   17.462734] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[   17.462737] [drm] Detected VRAM RAM=1024M, BAR=256M
[   17.462739] [drm] RAM width 128bits DDR
[   17.465943] lib80211: common routines for IEEE802.11 drivers
[   17.465948] lib80211_crypt: registered algorithm 'NULL'
[   17.469234] rtllib: module is from the staging directory, the quality is unknown, you have been warned.
[   17.481272] [TTM] Zone  kernel: Available graphics memory: 2023224 kiB
[   17.481276] [TTM] Initializing pool allocator
[   17.481282] [TTM] Initializing DMA pool allocator
[   17.481316] [drm] radeon: 1024M of VRAM memory ready
[   17.481318] [drm] radeon: 1024M of GTT memory ready.
[   17.481359] [drm] Loading RV730 Microcode
[B][   17.481535] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   17.482460] 
[   17.482460] Linux kernel driver for RTL8192E WLAN cards
[   17.482464] Copyright (c) 2007-2008, Realsil Wlan Driver
[   17.492456] Memory mapped space start: 0xd4100000
[   17.511537] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMBA 1 (20131115/utaddress-251)
[   17.511546] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.511551] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   17.511555] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.511557] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   17.511561] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.511563] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.633434] WARNING! power/level is deprecated; use power/control instead
[   17.687381] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   17.721785] SKU: Nid=0x1d sku_cfg=0x4016892d
[   17.721789] SKU: port_connectivity=0x1
[   17.721791] SKU: enable_pcbeep=0x1
[   17.721792] SKU: check_sum=0x00000006
[   17.721794] SKU: customization=0x00000089
[   17.721795] SKU: external_amp=0x5
[   17.721797] SKU: platform_type=0x1
[   17.721798] SKU: swap=0x0
[   17.721800] SKU: override=0x1
[   17.721985] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   17.721987]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.721989]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   17.721991]    mono: mono_out=0x0
[   17.721992]    inputs:
[   17.728864]      Internal Mic=0x19
[   17.728991]      Mic=0x18
[   17.728995] realtek: No valid SSID, checking pincfg 0x4016892d for NID 0x1d
[   17.728997] realtek: Enabling init ASM_ID=0x892d CODEC_ID=10ec0272
[   17.771759] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.772047] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.780545] Linux video capture interface: v2.00
[   17.862574] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)
[   17.882962] input: CNF7051 as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input12
[   17.883070] usbcore: registered new interface driver uvcvideo
[   17.883072] USB Video Class driver (1.1.1)
[   18.101464] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   18.123888] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[   18.123961] radeon 0000:01:00.0: WB enabled
[   18.123965] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8800b3302c00
[   18.123968] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff8800b3302c0c
[   18.124941] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0xffffc9000489c598
[   18.124957] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   18.124959] [drm] Driver supports precise vblank timestamp query.
[   18.124998] radeon 0000:01:00.0: irq 47 for MSI/MSI-X
[   18.125027] radeon 0000:01:00.0: radeon: using MSI.
[   18.125062] [drm] radeon: irq initialized.
[   18.171607] [drm] ring test on 0 succeeded in 1 usecs
[   18.171670] [drm] ring test on 3 succeeded in 1 usecs
[   18.296898] type=1400 audit(1401754481.630:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=371 comm="apparmor_parser"
[   18.296907] type=1400 audit(1401754481.630:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   18.296912] type=1400 audit(1401754481.630:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   18.297408] type=1400 audit(1401754481.630:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   18.297415] type=1400 audit(1401754481.630:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   18.297674] type=1400 audit(1401754481.630:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   18.302042] type=1400 audit(1401754481.634:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=434 comm="apparmor_parser"
[   18.302053] type=1400 audit(1401754481.634:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=434 comm="apparmor_parser"
[   18.302058] type=1400 audit(1401754481.634:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=434 comm="apparmor_parser"
[   18.302557] type=1400 audit(1401754481.634:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=434 comm="apparmor_parser"
[   18.358698] [drm] ring test on 5 succeeded in 1 usecs
[   18.358707] [drm] UVD initialized successfully.
[   18.359360] [drm] Enabling audio 0 support
[   18.359394] [drm] ib test on ring 0 succeeded in 0 usecs
[   18.359416] [drm] ib test on ring 3 succeeded in 0 usecs
[   18.516386] [drm] ib test on ring 5 succeeded
[   18.518475] cfg80211: World regulatory domain updated:
[   18.518481] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.518484] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.518487] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.518489] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.518491] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.518493] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.540036] [drm] radeon atom DIG backlight initialized
[   18.540044] [drm] Radeon Display Connectors
[   18.540046] [drm] Connector 0:
[   18.540049] [drm]   VGA-1
[   18.540052] [drm]   DDC: 0x7f10 0x7f10 0x7f14 0x7f14 0x7f18 0x7f18 0x7f1c 0x7f1c
[   18.540053] [drm]   Encoders:
[   18.540055] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   18.540056] [drm] Connector 1:
[   18.540058] [drm]   LVDS-1
[   18.540060] [drm]   DDC: 0x7f68 0x7f68 0x7f6c 0x7f6c 0x7f70 0x7f70 0x7f74 0x7f74
[   18.540062] [drm]   Encoders:
[   18.540063] [drm]     LCD1: INTERNAL_UNIPHY2
[   18.540065] [drm] Connector 2:
[   18.540066] [drm]   HDMI-A-1
[   18.540068] [drm]   HPD1
[   18.540070] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   18.540071] [drm]   Encoders:
[   18.540073] [drm]     DFP1: INTERNAL_UNIPHY
[   18.540074] [drm] Connector 3:
[   18.540076] [drm]   DP-1
[   18.540077] [drm]   HPD2
[   18.540080] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   18.540081] [drm]   Encoders:
[   18.540082] [drm]     DFP2: INTERNAL_UNIPHY
[   18.550567] [drm] radeon: dpm initialized
[   19.295642] init: failsafe main process (534) killed by TERM signal
[   19.405958] Bluetooth: Core ver 2.17
[   19.405995] NET: Registered protocol family 31
[   19.405997] Bluetooth: HCI device and connection manager initialized
[   19.406009] Bluetooth: HCI socket layer initialized
[   19.406013] Bluetooth: L2CAP socket layer initialized
[   19.406019] Bluetooth: SCO socket layer initialized
[   19.439577] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.439583] Bluetooth: BNEP filters: protocol multicast
[   19.439599] Bluetooth: BNEP socket layer initialized
[   19.449960] Bluetooth: RFCOMM TTY layer initialized
[   19.449977] Bluetooth: RFCOMM socket layer initialized
[   19.449987] Bluetooth: RFCOMM ver 1.11
[   19.555841] [drm] fb mappable at 0xC045E000
[   19.555846] [drm] vram apper at 0xC0000000
[   19.555848] [drm] size 5324800
[   19.555850] [drm] fb depth is 24
[   19.555852] [drm]    pitch is 5888
[   19.556302] fbcon: radeondrmfb (fb0) is primary device
[   19.578900] init: cups main process (669) killed by HUP signal
[   19.578918] init: cups main process ended, respawning
[   20.381286] r8169 0000:02:00.0 eth0: link down
[   20.381383] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.381912] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.404485] Console: switching to colour frame buffer device 180x56
[   20.408317] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   20.408319] radeon 0000:01:00.0: registered panic notifier
[   20.408383] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   20.408510] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   20.408513] hda-intel 0000:01:00.1: Using LPIB position fix
[   20.408569] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
[   20.893444] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   20.907825] HDMI ATI/AMD: no speaker allocation for ELD
[   20.907932] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   21.328276] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.328737] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.213628] init: plymouth-upstart-bridge main process ended, respawning
[   24.231546] init: plymouth-upstart-bridge main process ended, respawning
[   24.579922] Linking with TP-Link-Cyn2.4,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[   24.579936] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   24.596793] Linking with TP-Link-Cyn2.4,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[   24.597056] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   27.116041] Linking with TP-Link-Cyn2.4,channel:6, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[   27.116051] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
[   27.142494] Associated successfully
[   27.142498] normal associate
[   27.142509] Using G rates:108
[   27.142511] Successfully associated, ht enabled
[   27.142514] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[   27.142873] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.144260] RX: IEEE802.1X EAPOL frame!
[   27.159544] RX: IEEE802.1X EAPOL frame!
[   27.159764] alg name:R-CCMP
[   27.175717] rtllib_crypt_ccmp: module is from the staging directory, the quality is unknown, you have been warned.
[   27.176035] lib80211_crypt: registered algorithm 'R-CCMP'
[   27.177749] alg name:R-CCMP
[   27.372985] dm_check_edca_turbo():iot peer is atheros, bssid: f8:1a:67:a2:b9:45
[   49.987470] audit_printk_skb: 186 callbacks suppressed
[   49.987475] type=1400 audit(1401754513.316:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2044 comm="apparmor_parser"
[   49.987485] type=1400 audit(1401754513.316:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2044 comm="apparmor_parser"
[   49.987992] type=1400 audit(1401754513.316:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2044 comm="apparmor_parser"
[  125.532279] rtl819x_TxCheckStuck: QueueID=7 tcb_desc->nStuckCount=2
[  125.532289] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  126.524513] ieee->state is RTLLIB_LINKED
[  126.557945] Associated successfully
[  126.557956] Using G rates:108
[  126.557959] Successfully associated, ht enabled
[  126.557963] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  126.572912] silent reset associate
[  126.580482] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  126.682869] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  126.785274] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  126.887675] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  126.990091] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.092501] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.194865] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.297291] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.399704] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.502098] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.604503] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.706892] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.809293] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  127.911678] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.014080] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.116500] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.218903] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.321299] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.423692] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.526068] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.628487] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.730919] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.833266] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  128.935702] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  129.038082] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  166.628235] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  168.635340] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  188.737489] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  188.839863] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  188.942266] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.044668] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.147076] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.249456] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.351874] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.454294] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.556682] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.659064] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.761456] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.863899] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  189.966263] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  190.068660] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  190.171076] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  190.273464] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  190.375872] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  190.478281] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  190.580678] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  192.684359] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  192.684369] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  193.676568] ieee->state is RTLLIB_LINKED
[  193.709936] Associated successfully
[  193.709947] Using G rates:108
[  193.709950] Successfully associated, ht enabled
[  193.709955] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  193.724925] silent reset associate
[  193.755082] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  193.857495] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  193.959886] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.062312] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.164695] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.267112] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.369502] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.471887] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.574284] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.676705] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.779107] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.881510] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  194.983909] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  195.086292] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  195.188681] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  195.291108] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  195.393489] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  195.495896] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  195.598313] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  197.700280] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[  199.704350] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=3
[  201.708323] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=4
[  203.712247] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=5
[  205.716226] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=6
[  207.720238] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=7
[  207.783969] ===>tx queue is not empty:1, 63
[  207.988745] ===>tx queue is not empty:1, 63
[  208.091101] ===>tx queue is not empty:1, 63
[  208.295935] ===>tx queue is not empty:1, 63
[  208.398309] ===>tx queue is not empty:1, 63
[  208.500732] ===>tx queue is not empty:1, 63
[  208.603113] ===>tx queue is not empty:1, 63
[  208.705534] ===>tx queue is not empty:1, 63
[  208.807931] ===>tx queue is not empty:1, 63
[  209.012723] ===>tx queue is not empty:1, 63
[  209.115138] ===>tx queue is not empty:1, 63
[  209.217537] ===>tx queue is not empty:1, 63
[  209.319939] ===>tx queue is not empty:1, 63
[  209.422349] ===>tx queue is not empty:1, 63
[  209.524741] ===>tx queue is not empty:1, 63
[  209.627134] ===>tx queue is not empty:1, 63
[  209.724280] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=8
[  209.729514] ===>tx queue is not empty:1, 63
[  209.831969] ===>tx queue is not empty:1, 63
[  210.036734] ===>tx queue is not empty:1, 63
[  210.139123] ===>tx queue is not empty:1, 63
[  210.343949] ===>tx queue is not empty:1, 63
[  210.446331] ===>tx queue is not empty:1, 63
[  210.548740] ===>tx queue is not empty:1, 63
[  210.651133] ===>tx queue is not empty:1, 63
[  210.753534] ===>tx queue is not empty:1, 63
[  210.958321] ===>tx queue is not empty:1, 63
[  211.060730] ===>tx queue is not empty:1, 63
[  211.163143] ===>tx queue is not empty:1, 63
[  211.265527] ===>tx queue is not empty:1, 63
[  211.728219] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=9
[  213.732219] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=10
[  213.825529] ===>tx queue is not empty:1, 63
[  214.030327] ===>tx queue is not empty:1, 63
[  214.132758] ===>tx queue is not empty:1, 63
[  214.235144] ===>tx queue is not empty:1, 63
[  214.337545] ===>tx queue is not empty:1, 63
[  214.439969] ===>tx queue is not empty:1, 63
[  214.644741] ===>tx queue is not empty:1, 63
[  214.747151] ===>tx queue is not empty:1, 63
[  214.849544] ===>tx queue is not empty:1, 63
[  215.054363] ===>tx queue is not empty:1, 63
[  215.156752] ===>tx queue is not empty:1, 63
[  215.259149] ===>tx queue is not empty:1, 63
[  215.361555] ===>tx queue is not empty:1, 63
[  215.463971] ===>tx queue is not empty:1, 63
[  215.566346] ===>tx queue is not empty:1, 63
[  215.668756] ===>tx queue is not empty:1, 63
[  215.736255] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=11
[  215.873536] ===>tx queue is not empty:1, 63
[  215.975958] ===>tx queue is not empty:1, 63
[  216.078366] ===>tx queue is not empty:1, 63
[  216.180768] ===>tx queue is not empty:1, 63
[  216.283181] ===>tx queue is not empty:1, 63
[  216.385573] ===>tx queue is not empty:1, 63
[  216.487955] ===>tx queue is not empty:1, 63
[  216.590356] ===>tx queue is not empty:1, 63
[  216.692754] ===>tx queue is not empty:1, 63
[  216.795144] ===>tx queue is not empty:1, 63
[  216.897566] ===>tx queue is not empty:1, 63
[  216.999951] ===>tx queue is not empty:1, 63
[  217.102357] ===>tx queue is not empty:1, 63
[  217.204755] ===>tx queue is not empty:1, 63
[  217.307145] ===>tx queue is not empty:1, 63
[  217.409560] ===>tx queue is not empty:1, 63
[  217.511953] ===>tx queue is not empty:1, 63
[  217.614355] ===>tx queue is not empty:1, 63
[  217.716758] ===>tx queue is not empty:1, 63
[  217.740277] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=12
[  217.740288] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
[  218.732544] ieee->state is RTLLIB_LINKED
[  218.765925] Associated successfully
[  218.765932] Using G rates:108
[  218.765934] Successfully associated, ht enabled
[  218.765937] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:1
[  218.780895] silent reset associate
[  219.457569] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  219.559979] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  219.662368] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  219.764752] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  219.867173] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  219.969562] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  220.071983] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  220.174379] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  220.276765] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  220.379174] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  220.481586] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  220.583985] rtl819xE:No more TX desc@7, ring->idx = 0, idx = 0, skblen = 0x18 queuelen=0
[  222.760295] rtl819x_TxCheckStuck: QueueID=1 tcb_desc->nStuckCount=2
[/B]


```

I also noticed that the dmesg log does show much less of those errormessages if i keep the browser closed and do nothing else. 
The more (websites) i try to load, the more error messages appear in dmesg. 
On another sidenote: websites are loaded partially, smaller websites are loaded slow but somtimes successfully.

---

### Post by Joel_Ross on 2014-06-02
I would suggest tinkering with the options in /etc/modprobe.d/modprobe.conf by enabling(=1) and disabling(=0) them and retrying (always worth a reboot after changes are made) don't worry about the option  "options rtl8192se debug=5" as this is used to log information to log files (it cant be removed if/when fix)

At this point that's all I cant really suggest, any logs that look suspicious you should Google them and see if anyone else has had the same problems. 

**For future reference:** Consider a Dell on your next Laptop purchase as they support Ubuntu (that's if you like Dell :) ) Also see here [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/) for all other hardware that's certified for Ubuntu systems. Unfortunately unlike Windows, Linux requires extensive research when purchasing hardware.

---

### Post by killerlink23 on 2014-06-03
Hello again! I have bad and good news : D

The bad news are, i did not manage to get it to work how it was. But i have read somewhere, that people with 32Bit Variant (I had 64Bit) had no/less problems.
And those are the good news: I just downloaded Ubuntu 14.04 32Bit, installed it, and everything seems to work out of the Box!
All symptoms i had seen earlier seem to be gone, no more error messages in dmesg so far. Ill report once more after an extended testing period!

If someone wants to take a deeper look into that Problem, hey may contact me, so i can provide further information.

Thanks to everyone who helped me!

PS.: Do I need to "close" or set to "solved" the topic anyhow later?

---

### Post by Joel_Ross on 2014-06-03
Good to hear. 

If you have more then 4GB of memory make sure you  have the Ubuntu 32 Bit PAE version otherwise you'll be limited to 4GB  due the limit of 32bit OS's, but i believe all new versions of Ubuntu have  PAE enabled so you should be right. To double check run:

```
uname -r
```

and make sure it contains PAE somewhere in the output. Example : 2.6.31-22-generic-**pae**

Yeah mark it as solved in Therad Tools, once your happy. Not the best soultion, but at least it's working now for now.

---

### Post by killerlink23 on 2014-06-04
Since this Laptop has only 4GB of RAM and will never be used for gameing or something similar, it is rather irrelevant if i can use the capabilities of more than 4GB Ram and 64Bit Software or not : D
Therefore, the solution seems to be perfect! 
(Only my inner perfectionist wants to know, why the 64 Bit did not work. But I would drown myself in riddles, if I were to find out and answer all those questions my inner perfectionist asks xD )

Thanks Again, i'll set this to solved now!

Best regards!

---

