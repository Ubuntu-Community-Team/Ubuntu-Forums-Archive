---
title: "Ubuntu 14.04 wifi Realtek RTL8723BE disconnect issues,Lenovo Yoga 2 (non pro !!)"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by o0larry0o on 2014-08-30
Hi all,
I've been struggling with my wifi connection, as some knows, the lenovo Yoga 2 has some issues with the wireless (thx for the community for helping everyone with that btw)

My issues are as follow:
Before I couldn't connect properly to my wifi, even using the options "option rtl8723be fwlps=0[COLOR=#545454][FONT=arial] swlps=0" or just fwlps=0 in [/FONT][/COLOR][COLOR=#333333][FONT=monospace]/etc/modprobe.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]d/rtl8723be.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]conf[/FONT][/COLOR]

Even after a reboot, It would connect for a couple of seconds, then disconnect and never connect again sometimes even a reboot wouldn't fix anything.

Then I found this thread [http://ubuntuforums.org/showthread.php?t=2239932](http://ubuntuforums.org/showthread.php?t=2239932) and followed the instructions given. It has DRAMATICALLY improved everything, now I can connect and stay connected. Sometime it drops but i can reconnect.
But it's still not working properly, I have trouble browsing, chrome often says that the host is unreachable even if i'm connected. Sometimes a ping cannot resolve any host, until I deactivate the wireless connection (network manager) and reactivate it again.

What I did from the thread mentionned above :
-bind the MAC addr from my router
- set the region code (FR)
- set properly the config in the router but I'm not sure this step is OK, here are the option available in my router :
[[IMG]http://img4.hostingpics.net/pics/950713Screenshotfrom20140830112355.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=950713Screenshotfrom20140830112355.png")
I choose WPA2-PSK/AES,is it OK ?

Something else, the signal (dBm) seems to be very poor (see in the wireless script below) although I'm 2 meters away from my router. and I choose the less populated channel.

I did not tried swenc=1, and I've read that ips=0 could help ...

I updated to Kernel Linux larry-pc 3.15.0-031500-generic #201406131105 SMP Fri Jun 13 15:06:46 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
as the driver was updated as mentionned in : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070/comments/28)

Well ....I don't know what to do next ....

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


larry-pc 3.15.0-031500-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i3-4010U CPU @ 1.70GHz
Memory : 3873 MB
Uptime : 10:57:41 up  1:25,  2 users,  load average: 2,30, 1,75, 1,08




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b40f Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 04f3:0303 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Deuil_Coloc"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC C-01 Deuil_Coloc>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN                no            no
3: hci0: Bluetooth                   no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


snd_soc_rt5640         88063  0 
snd_soc_core          201495  1 snd_soc_rt5640
rtl8723be              87237  0 
btcoexist              55886  1 rtl8723be
rtl8723_common         23427  1 rtl8723be
rtl_pci                27257  1 rtl8723be
rtlwifi                69157  2 rtl_pci,rtl8723be
mac80211              663788  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              514187  2 mac80211,rtlwifi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (5): debug=0 | fwlps=N | ips=Y | swenc=N | swlps=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
======================o=============o===========o===========o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State     | Default | Speed     | Support      | HW Addr   
======================o=============o===========o===========o=========o===========o==============o===========
 wlan0  [Deuil_Coloc] | 802.11 WiFi | rtl8723be | connected | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    Livebox-B702:    Infra, <MAC C-03 Livebox-B702>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    FreeWifi_secure: Infra, <MAC C-02 FreeWifi_secure>, Freq 2422 MHz, Rate 54 Mb/s, Strength 100 WPA2 Enterprise
    Bbox-00FCBCF3:   Infra, <MAC C-05 Bbox-00FCBCF3>, Freq 2427 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    Livebox-DACA:    Infra, <MAC C-07 Livebox-DACA>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    SFR WiFi Mobile: Infra, <MAC C-09 SFR WiFi Mobile>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC C-12 FreeWifi_secure>, Freq 2472 MHz, Rate 54 Mb/s, Strength 60 WPA Enterprise
    freebox_CVXMVQ:  Infra, <MAC C-13 freebox_CVXMVQ>, Freq 2472 MHz, Rate 54 Mb/s, Strength 60 WPA
    LBHOME:          Infra, <MAC C-08 LBHOME>, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    NEUF_51E4:       Infra, <MAC C-10 NEUF_51E4>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    FreeWifi:        Infra, <MAC C-04 FreeWifi>, Freq 2422 MHz, Rate 54 Mb/s, Strength 100
    orange:          Infra, <MAC C-06 orange>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70
    FreeWifi:        Infra, <MAC C-14 FreeWifi>, Freq 2472 MHz, Rate 54 Mb/s, Strength 57
    SFR WiFi FON:    Infra, <MAC C-11 SFR WiFi FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    *Deuil_Coloc:    Infra, <MAC C-01 Deuil_Coloc>, Freq 2422 MHz, Rate 54 Mb/s, Strength 98 WPA2


    Address:         192.168.150.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.150.254
    DNS:             192.168.150.254
----------------------+-------------+-----------+-----------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC eth0>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


Deuil_Coloc          : ssid=Deuil_Coloc | bssid=<MAC C-01 Deuil_Coloc> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.150.254 0.0.0.0         UG    0      0        0 wlan0
192.168.150.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.150.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.741/1.246/1.751/0.505 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.019/0.023/0.028/0.006 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : fr_FR.UTF-8)
country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.422 GHz (Channel 3)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Deuil_Coloc>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"Deuil_Coloc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000834d43425f
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 FreeWifi_secure>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000834d3cf4bf
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC C-03 Livebox-B702>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Livebox-B702"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005abbf73163
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 FreeWifi>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000834d3d6d99
                    Extra: Last beacon: 20ms ago
          Cell 05 - Address: <MAC C-05 Bbox-00FCBCF3>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Bbox-00FCBCF3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7f409bbff
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 orange>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"orange"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=320000eeb03b962d
                    Extra: Last beacon: 20ms ago
          Cell 07 - Address: <MAC C-07 Livebox-DACA>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Livebox-DACA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eeb03b85fc
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 LBHOME>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"LBHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012978402404
                    Extra: Last beacon: 25020ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 SFR WiFi Mobile>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001725f39a0c2
                    Extra: Last beacon: 724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC C-10 NEUF_51E4>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"NEUF_51E4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001725f39a75e
                    Extra: Last beacon: 728ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 SFR WiFi FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001725f39be21
                    Extra: Last beacon: 724ms ago
          Cell 12 - Address: <MAC C-12 FreeWifi_secure>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-12 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004922ba507e
                    Extra: Last beacon: 24164ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC C-13 freebox_CVXMVQ>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"freebox_CVXMVQ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000049242b209e
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 FreeWifi>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-12 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004922ba40d1
                    Extra: Last beacon: 24164ms ago




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[snd_soc_rt5640]
filename:       /lib/modules/3.15.0-031500-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
srcversion:     0C9709ADDA21C3834088646
depends:        snd-soc-core


[snd_soc_core]
filename:       /lib/modules/3.15.0-031500-generic/kernel/sound/soc/snd-soc-core.ko
srcversion:     9209B5B3EC23B94DA94259D
depends:        snd-pcm,snd,snd-compress
parm:           pmdown_time:DAPM stream powerdown time (msecs) (int)


[rtl8723be]
filename:       /lib/modules/3.15.0-031500-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     6C73102E40E54982621AB13
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           debug:Set debug level (0-5) (default 0) (int)


[btcoexist]
filename:       /lib/modules/3.15.0-031500-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     5B71A133DD8D59B03434E70
depends:        


[rtl8723_common]
filename:       /lib/modules/3.15.0-031500-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
srcversion:     7410431A59C24B1BC33226E
depends:        


[rtl_pci]
filename:       /lib/modules/3.15.0-031500-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     3B7DA1A27B0F29790698794
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.15.0-031500-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     8867161389A32ADC4DB474A
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.15.0-031500-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D94FBA2D64C6B1E13B783B1
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.15.0-031500-generic/kernel/net/wireless/cfg80211.ko
srcversion:     BDA7AFAD5D9F6CD8ED8A92E
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rtl8723be.conf    : options rtl8723be fwlps=0




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.15.0-031500-generic root=UUID=95d5dd30-14c8-4136-b326-a45f0da31844 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.039854] Initializing cgroup subsys net_cls
[    0.039859] Initializing cgroup subsys net_prio
[    1.244375] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.244849] audit: initializing netlink subsys (disabled)
[    6.250098] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    6.250769] rtl8723be 0000:01:00.0: irq 63 for MSI/MSI-X
[    6.276525] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    6.276973] rtlwifi: wireless switch is on
[   10.911365] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  156.286431] asix 2-1.4:1.0 eth0: register 'asix' at usb-0000:00:14.0-1.4, ASIX AX88772 USB 2.0 Ethernet, <MAC eth0>
[ 4012.118337] asix 2-1.4:1.0 eth0: unregister 'asix' usb-0000:00:14.0-1.4, ASIX AX88772 USB 2.0 Ethernet
[ 4018.824685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4019.760081] wlan0: authenticate with <MAC C-01 Deuil_Coloc>
[ 4019.770254] wlan0: send auth to <MAC C-01 Deuil_Coloc> (try 1/3)
[ 4019.771975] wlan0: authenticated
[ 4019.776023] wlan0: associate with <MAC C-01 Deuil_Coloc> (try 1/3)
[ 4019.779116] wlan0: RX AssocResp from <MAC C-01 Deuil_Coloc> (capab=0x411 status=0 aid=2)
[ 4019.779187] wlan0: associated
[ 4019.779222] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4481.937608] wlan0: deauthenticating from <MAC C-01 Deuil_Coloc> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4488.370400] wlan0: authenticate with <MAC C-01 Deuil_Coloc>
[ 4488.844172] wlan0: send auth to <MAC C-01 Deuil_Coloc> (try 1/3)
[ 4488.845726] wlan0: authenticated
[ 4488.849128] wlan0: associate with <MAC C-01 Deuil_Coloc> (try 1/3)
[ 4488.852410] wlan0: RX AssocResp from <MAC C-01 Deuil_Coloc> (capab=0x411 status=0 aid=2)
[ 4488.852468] wlan0: associated
[ 4638.417685] asix 2-1.4:1.0 eth0: register 'asix' at usb-0000:00:14.0-1.4, ASIX AX88772 USB 2.0 Ethernet, <MAC eth0>
[ 4699.366842] wlan0: deauthenticating from <MAC C-01 Deuil_Coloc> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4769.227144] asix 2-1.4:1.0 eth0: unregister 'asix' usb-0000:00:14.0-1.4, ASIX AX88772 USB 2.0 Ethernet
[ 4773.382415] asix 2-1.4:1.0 eth0: register 'asix' at usb-0000:00:14.0-1.4, ASIX AX88772 USB 2.0 Ethernet, <MAC eth0>
[ 5134.411052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5135.812517] asix 2-1.4:1.0 eth0: unregister 'asix' usb-0000:00:14.0-1.4, ASIX AX88772 USB 2.0 Ethernet
[ 5136.112365] wlan0: authenticate with <MAC C-01 Deuil_Coloc>
[ 5136.132132] wlan0: send auth to <MAC C-01 Deuil_Coloc> (try 1/3)
[ 5136.135629] wlan0: authenticated
[ 5136.139729] wlan0: associate with <MAC C-01 Deuil_Coloc> (try 1/3)
[ 5136.143181] wlan0: RX AssocResp from <MAC C-01 Deuil_Coloc> (capab=0x411 status=0 aid=2)
[ 5136.143251] wlan0: associated
[ 5136.143287] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5136.154669] wlan0: deauthenticating from <MAC C-01 Deuil_Coloc> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 5136.186044] wlan0: authenticate with <MAC C-01 Deuil_Coloc>
[ 5136.199928] wlan0: send auth to <MAC C-01 Deuil_Coloc> (try 1/3)
[ 5136.201448] wlan0: authenticated
[ 5136.203883] wlan0: associate with <MAC C-01 Deuil_Coloc> (try 1/3)
[ 5136.208475] wlan0: RX AssocResp from <MAC C-01 Deuil_Coloc> (capab=0x411 status=0 aid=2)
[ 5136.208598] wlan0: associated


    ======== Done ========
```

Many thx for your help
Ludo

EDIT : I've just read somewhere, that a guy using Arch, was upgraded to kernel 3.16 and now it work perfectly ... any thoughts ?

---

### Post by chili555 on 2014-08-30
> I choose WPA2-PSK/AES,is it OK ?Exactly correct.> Something else, the signal (dBm) seems to be very poor (see in the wireless script below) although I'm 2 meters away from my router. and I choose the less populated channel.I don't see that at all:> *Deuil_Coloc:    Infra, <MAC C-01 Deuil_Coloc>, Freq 2422 MHz, Rate 54 Mb/s, [COLOR="#FF0000"]Strength 98 [/COLOR]WPA2As well:> wlan0     IEEE 802.11bgn  ESSID:"Deuil_Coloc"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC C-01 Deuil_Coloc>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          [COLOR="#FF0000"]Link Quality=58/70 [/COLOR] Signal level=-52 dBm  I don't know how signal strength ever got to be xx/70, but it is. 58 ÷ 70 = 82.8; it is a bit different from the 98 reported above but, in either case, not what I'd call very poor.

After you change to WPA2-AES, please test. Then change the /etc/modprobe.d/rtl8723be.conf file to read:```
option[COLOR="#FF0000"]s[/COLOR] rtl8723be swenc=1
```Test again.

I might also try the router on channel 13.

We may try the backported drivers from 3.16 next.

---

### Post by o0larry0o on 2014-08-31
Well i've added the swenc options and it didn't change a thing ...

I've noted 2 things anyway
first in dmesg :

```

[87674.356357] cfg80211: Calling CRDA to update world regulatory domain
[87674.359913] cfg80211: World regulatory domain updated:
[87674.359918] cfg80211:  DFS Master region: unset
[87674.359919] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[87674.359922] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[87674.359924] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[87674.359926] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[87674.359928] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[87674.359930] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[87674.359950] cfg80211: Calling CRDA for country: FR
[87674.363376] cfg80211: Regulatory domain changed to country: FR
[87674.363381] cfg80211:  DFS Master region: unset
[87674.363382] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[87674.363385] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[87674.363387] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[87674.363389] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[87674.363391] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[87674.363393] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[87675.801370] wlan0: authenticate with 00:24:d4:51:ef:90
[87675.820413] wlan0: send auth to 00:24:d4:51:ef:90 (try 1/3)
[87675.824771] wlan0: authenticated
**[COLOR=#ff0000][87675.824940] wlan0: AP has invalid WMM params (ECWmin/max=8/1 for ACI 2), disabling WMM[/COLOR]**
**[COLOR=#ff0000][87675.824946] wlan0: associating with AP with corrupt beacon and probe response[/COLOR]**
[87675.828207] wlan0: associate with 00:24:d4:51:ef:90 (try 1/3)
[87675.832360] wlan0: RX AssocResp from 00:24:d4:51:ef:90 (capab=0x411 status=0 aid=2)
[87675.832491] wlan0: associated

```

But i've registered my country region as you explained in the other thread,
and what about this WMM parameters?

And then in the networkmanager logs :

```

Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Activation (wlan0/wireless): connection 'Deuil_Coloc' has security, and secrets exist.  No new secrets needed.Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Config: added 'ssid' value 'Deuil_Coloc'
Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Config: added 'scan_ssid' value '1'
Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Config: added 'bssid' value '00:24:d4:51:ef:90'
Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Config: added 'psk' value '<omitted>'
Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 31 19:27:25 larry-pc NetworkManager[810]: <info> Config: set interface ap_scan to 1
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: authenticating -> associating
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Deuil_Coloc'.
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> dhclient started with pid 17845
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info>   address 192.168.150.7
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info>   prefix 24 (255.255.255.0)
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info>   gateway 192.168.150.254
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info>   nameserver '192.168.150.254'
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 31 19:27:26 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> Policy set 'Deuil_Coloc' (wlan0) as default for IPv4 routing and DNS.
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> Writing DNS information to /sbin/resolvconf
Aug 31 19:27:27 larry-pc NetworkManager[810]: <info> Activation (wlan0) successful, device activated.
**[COLOR=#ff0000]Aug 31 19:28:13 larry-pc NetworkManager[810]: <info> (wlan0): roamed from BSSID 00:24:D4:51:EF:90 (Deuil_Coloc) to (none) ((none))[/COLOR]**
Aug 31 19:28:13 larry-pc NetworkManager[810]: <warn> Connection disconnected (reason -4)
Aug 31 19:28:13 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: completed -> disconnected
Aug 31 19:28:13 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 31 19:28:15 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 31 19:28:15 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: authenticating -> associating
Aug 31 19:28:15 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Aug 31 19:28:15 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
[COLOR=#ff0000]**Aug 31 19:28:15 larry-pc NetworkManager[810]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:24:D4:51:EF:90 (Deuil_Colo#012)**[/COLOR]
[COLOR=#ff0000]**Aug 31 19:28:36 larry-pc NetworkManager[810]: <info> (wlan0): roamed from BSSID 00:24:D4:51:EF:90 (Deuil_Colo#012) to (none) ((none))**[/COLOR]
Aug 31 19:28:36 larry-pc NetworkManager[810]: <warn> Connection disconnected (reason -4)
Aug 31 19:28:36 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: completed -> disconnected
Aug 31 19:28:37 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 31 19:28:38 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 31 19:28:38 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: authenticating -> associating
Aug 31 19:28:38 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Aug 31 19:28:38 larry-pc NetworkManager[810]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
**[COLOR=#ff0000]Aug 31 19:28:38 larry-pc NetworkManager[810]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:24:D4:51:EF:90 (Deuil_Colo#012)[/COLOR]**

```

It keeps roaming from BSSID, although I've binded the MAC addr of my router in the networkmanager GUI

I've read that some people had the same roaming issue over the years, and one solution was to replace networkmanager with another one, hqt do you think ?

thx

---

### Post by chili555 on 2014-09-01
> [87675.824940] wlan0: AP has invalid WMM params (ECWmin/max=8/1 for ACI 2), disabling WMMPlease see: [https://en.wikipedia.org/wiki/Wireless_Multimedia_Extensions](https://en.wikipedia.org/wiki/Wireless_Multimedia_Extensions) In many cases, WMM is a user-selectable option in the router. Can you please try with the option turned off in the router?> It keeps roaming from BSSID, although I've binded the MAC addr of my router in the networkmanager GUIWould you please let us have a peek at the settings? If you wish, please disguise the MAC address something like attached. Change it back after you do a screenshot or write down the details, etc.

---

### Post by o0larry0o on 2014-09-02
um ok, i'll check, I know I can tweak some parameters in the router.

here is the config GUI window
[[IMG]http://img4.hostingpics.net/pics/558769wifi.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=558769wifi.png")

And i've set the ipv6 to "ignore"

---

### Post by o0larry0o on 2014-09-05
I tried several tweaks present in my router, but i can't disable the WWM.
It has improved ... not sure if I did something good or if it's IT magic :p

Anyway, I tried without succes to replace NM with Wicd, which seems to solve many problems according to a lot of users.

I'm kinda out of option here ....

One question though ... about your advices to limit the channel to 20mhz. Doing this cancel the inner fonction of 802.11n right ?

---

### Post by chili555 on 2014-09-05
> about your advices to limit the channel to 20mhz. Doing this cancel the inner fonction of 802.11n right ?It will still be able to connect at N speeds, although it may be a bit slower: [http://www.connect802.com/80211n_channels.htm](http://www.connect802.com/80211n_channels.htm)> The use of 40 MHz channels with 802.11n gives you just a little bit better than twice the throughput capacity of 20 MHz channel systems.I originally got the suggestion here: [http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed](http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed)> If you are changing the Channel Width or mode from the default 20 MHz to the 40 MHz (or "Auto 20/40" mode in some routers) channel-bonding mode, you could be reducing, not increasing your throughput.

The Channel-bonding trick can provide a 10 to 20 Mbps throughput increase, but usually works best under strong signal conditions. As signal levels drop, using channel bonding becomes much less effective in providing a throughput boost.I checked and my own router was set to 'Auto 20/40.' When I changed it to 20 Mhz only, I noticed no change in speeds but a big improvement in stability. I suspect that the improvement in stability is related, not to the use of 40 Mhz, but to the automatic switching between the bands. I haven't the means to prove it either way.

In short, if I can connect at a zillion Mb/s but it's unstable and drops the connection, what good is it? If I connect like this, and it's as solid as a rock, then I'm happy!```
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx   
          [COLOR="#FF0000"]Bit Rate=115.6 Mb/s [/COLOR]  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  

```

---

### Post by o0larry0o on 2014-09-05
that's why it has improved since I changed to 20mhz,
but it's still not able to maintain it forever ..... meaning more than 10 min :p

I guess I'll give another try to Wicd ....

thx

---

### Post by chili555 on 2014-09-05
Is power management on or off?```
iwconfig
```> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx   
          Bit Rate=115.6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:on[/COLOR]
          Link Quality=61/70  Signal level=-49 dBmDoes it help if you turn it off?```
sudo iwconfig power off
```

---

### Post by o0larry0o on 2014-09-10
The power mgmt was already off ...;

Something I discovered today is that I am properly connected to the network, but I don't have any DNS resolv, I can ping my router but I cannot resolv URI .... I have to disconnect and connect several times before it works, and then it's very slow .... I don't get it :)

---

### Post by varunendra on 2014-09-14
Can you please try "ips=N" parameter now as suggested [post=13119513]here[/post]? The description of your problem still seems to be power management related, and you said you didn't try this one.

I got a success confirmation just this morning in above linked post. Maybe it could prove to be a reliable solution for this driver? Please do let us know the outcome if you try this.

---

### Post by phillbo2 on 2015-05-08
Perfect - worked with the ath9k on the more recent Yoga2 (non-pro) as well.

---

### Post by darek334 on 2016-03-31
Hi this helps me  with rtl8723be :
[http://ubuntuforums.greatknow.com/showthread.php?t=2219917&page=3](http://ubuntuforums.greatknow.com/showthread.php?t=2219917&page=3)

---

