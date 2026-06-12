---
title: "Authentication failure (pwloop)"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by byuri on 2014-09-17
I've recently set up Xubuntu on my laptop. During the set up I used an ethernet cable, I didn't connect to the wifi until I had most of the packages and apps I wanted. So, later I connect to the wifi with seemingly no trouble, and authenticate myself successfully. The next day, I am unable to connect to the wifi, and I get caught in an authenticate loop. I've gotten out of the loop with the command ```
sudo modprobe iwl395 disable_hw_scan=0
``` (At least I believe this was the reason, I found it on a forum post) But now I'm unable to connect to my wifi at all. There's no response whatsoever. Below is some code output that may be helpful, if more is needed, please let me know what I can do to help you help me.
Thanks

lspci

```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe



```

iwconfig wlan0

```
wlan0     IEEE 802.11bgn  ESSID:"NSA Surveillance Van"            Mode:Managed  Frequency:2.437 GHz  Access Point: AC:22:0B:D0:49:F8   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0



```

dmesg

```
[   54.922718] wlan0: authenticate with ac:22:0b:d0:49:f8[   54.938130] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[   54.939654] wlan0: authenticated
[   54.942001] wlan0: associate with ac:22:0b:d0:49:f8 (try 1/3)
[   54.947219] wlan0: RX AssocResp from ac:22:0b:d0:49:f8 (capab=0x411 status=0 aid=2)
[   54.947300] wlan0: associated
[   54.947344] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.041035] wlan0: deauthenticated from ac:22:0b:d0:49:f8 (Reason: 15)
[   63.058081] cfg80211: Calling CRDA to update world regulatory domain
[   63.062957] cfg80211: World regulatory domain updated:
[   63.062962] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   63.062965] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   63.062968] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   63.062971] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   63.062973] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   63.062975] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1183.975147] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 1183.990655] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 1183.992179] wlan0: authenticated
[ 1183.994356] wlan0: associate with ac:22:0b:d0:49:f8 (try 1/3)
[ 1183.997889] wlan0: RX AssocResp from ac:22:0b:d0:49:f8 (capab=0x411 status=0 aid=2)
[ 1183.997982] wlan0: associated
[ 1192.091270] wlan0: deauthenticated from ac:22:0b:d0:49:f8 (Reason: 15)
[ 1192.110377] cfg80211: Calling CRDA to update world regulatory domain
[ 1192.118020] cfg80211: World regulatory domain updated:
[ 1192.118025] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1192.118029] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1192.118031] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1192.118034] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1192.118036] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1192.118038] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1192.638483] systemd-hostnamed[2761]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1957.480476] cfg80211: Calling CRDA to update world regulatory domain
[ 1957.489620] cfg80211: World regulatory domain updated:
[ 1957.489629] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1957.489634] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1957.489640] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1957.489644] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1957.489649] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1957.489653] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1957.516062] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[ 1957.519672] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[ 1957.519909] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 1957.525451] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[ 1957.525499] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[ 1957.585410] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1957.586209] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1977.649371] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 1977.656512] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 1977.658026] wlan0: authenticated
[ 1982.677116] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 1992.793399] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 1992.799077] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 1992.800599] wlan0: authenticated
[ 1994.398232] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2012.235977] r8169 0000:01:00.0 eth0: link down
[ 2016.624171] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2030.434491] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2030.439170] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2030.440666] wlan0: authenticated
[ 2035.463969] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2045.984446] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2045.990187] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2045.991705] wlan0: authenticated
[ 2050.997317] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2081.428808] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2081.436127] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2081.437637] wlan0: authenticated
[ 2086.457030] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2156.450087] r8169 0000:01:00.0 eth0: link down
[ 2180.958789] r8169 0000:01:00.0 eth0: link up
[ 2180.958809] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2332.837244] cfg80211: Calling CRDA to update world regulatory domain
[ 2332.843987] cfg80211: World regulatory domain updated:
[ 2332.843993] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2332.843996] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2332.843998] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2332.844001] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2332.844003] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2332.844005] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2332.870634] rt2800pci: unknown parameter '11n_disable' ignored
[ 2332.871058] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[ 2332.874687] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[ 2332.874919] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 2332.880768] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[ 2332.880829] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[ 2332.941785] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2332.942367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2530.950756] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2530.958308] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2530.959810] wlan0: authenticated
[ 2535.966248] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2581.837473] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2581.843225] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2581.844926] wlan0: authenticated
[ 2586.864009] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2589.147809] systemd-hostnamed[3434]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2597.380208] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2597.386103] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2597.387638] wlan0: authenticated
[ 2599.853949] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)
[ 2954.836146] wlan0: authenticate with ac:22:0b:d0:49:f8
[ 2954.841051] wlan0: send auth to ac:22:0b:d0:49:f8 (try 1/3)
[ 2954.843337] wlan0: authenticated
[ 2959.862135] wlan0: deauthenticating from ac:22:0b:d0:49:f8 by local choice (reason=3)



```
(I installed libnss-myhostname as suggested, with no effect)

iwlist scan

```
wlan0     Scan completed :          Cell 01 - Address: AC:22:0B:D0:49:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"NSA Surveillance Van"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001d86c3d0f8
                    Extra: Last beacon: 4728ms ago
                    IE: Unknown: 00144E5341205375727665696C6C616E63652056616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050200160000
                    IE: Unknown: 2D1ABD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F03010008
                    IE: Unknown: DDA90050F204104A0001101044000102103B000103104700108367D259E416F39EC332E8C1173B584F102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000852542D41433636551042000C4341494141323030303030311054000800060050F20400011011000852542D4143363655100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00



```

---

### Post by byuri on 2014-09-17
[ATTACH]256493[/ATTACH]
Here's my wireless info also.

---

### Post by byuri on 2014-09-17
Update : I installed drivers for my Wireless card (Ralink RT3290) and ran the wireless.txt script again. This time the results came out quite different, and I am still at a loss of what to do after searching the forum even more. If anyone could pitch in, I'd be grateful.[ATTACH]256499[/ATTACH]

---

