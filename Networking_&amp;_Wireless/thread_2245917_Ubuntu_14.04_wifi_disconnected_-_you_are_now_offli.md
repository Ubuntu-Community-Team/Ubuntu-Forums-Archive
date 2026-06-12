---
title: "Ubuntu 14.04 wifi disconnected - you are now offline"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by Bregham_Dalgliesh on 2014-09-27
Hi,

I know there are many posts on this subject, but I have been through many of them and followed their instructions, but without success. The best looking thread I could find was this one: [http://ubuntuforums.org/showthread.php?t=2238805](http://ubuntuforums.org/showthread.php?t=2238805), which I followed through to the end but without success.

I am also not an advanced user, but a very loyal one, so please provide detailed step-by-step instructions if you are able to help.

Problem: since upgrading to Ubuntu 14.04 I cannot connect to wifi. The bubble "Wifi disconnected - you are now offline" appears.

I am using an ASUS K53E laptop with an Atheros 9 wifi driver.

Weird related issues: 1. I can connect to wifi if I use my LAN connection, and when I unplug the LAN cable I stay connected. 2. There is not a problem with my wifi driver as it connects without a problem when I switch into Windows 7. 3. There is a problem that shows up in the menu bar "Error: BrokenCount>0", which I cannot seem to resolve, but I do not know if it is linked to the wifi problem

Any help would be greatly appreciated, thanks!

---

### Post by varunendra on 2014-09-27
Welcome to the forums Bregham_Dalgliesh!

Please try a driver parameter commonly used with ath9k driver. Following are the steps to use it -

Open a terminal from menu or with shortcut key 'Ctrl-Alt-T', then enter this command in it (you may copy-paste it using your mouse cursor to avoid typo) -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot and check connectivity.

If it doesn't seem to help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Bregham_Dalgliesh on 2014-09-28
Dear Varun,

Thanks for getting back to me, I really appreciate it.

I tried the first suggestion concerning the Atheros driver, then rebooted but without success. I am attaching the screenshot with the results.

I have just followed your instructions for the "wireless_script" and it generated the results as requested. However, I cannot find "how to use code tags" ... sorry for being so amateur, so I am attaching the file instead. I am also cutting and pasting it below, hopefully it will be "clean" like you requested.

Just a further point. I connected to my PDaNet Hot Spot on my iPhone today, even though it was very slow loading a page. That might suggest my wifi router is at fault, but all other devices connect to it without a problem, including my laptop when I initially connect it via the LAN cable as mentioned in the first post. I did try changing the channels on the router from automatic to 1, 11, 3 etc but that didn't help either. Last point, I live in Tokyo so fiddling with the wifi router isn't that easy and, as I said, it works perfectly otherwise.

Thanks!


[COLOR=#000000]```
[/COLOR]
    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Bregham-Asus 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory : 3811 MB
Uptime : 18:41:27 up 7 min,  2 users,  load average: 0.91, 0.94, 0.49




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5120 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"MyPlaceKitamachi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 MyPlaceKitamachi>   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:84   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
0: phy0: Wireless LAN           no            no
1: asus-wlan: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


asus_nb_wmi            16862  0 
asus_wmi               23495  1 asus_nb_wmi
sparse_keymap          13708  1 asus_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
video                  18903  2 i915,asus_wmi
wmi                    18673  1 asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
===========================o=============o========  o=============o=========o===========o=============  =o===========
 Interface & ID            | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
===========================o=============o========  o=============o=========o===========o=============  =o===========
 eth0                      | Wired       | atl1c  | unavailable | no      | 100 Mb/s  |              | <MAC eth0>
---------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [MyPlaceKitamachi] | 802.11 WiFi | ath9k  | connected   | yes     | 65 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    FON_FREE_EAP:    Infra, <MAC C-03 FON_FREE_EAP>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA Enterprise
    WARPSTAR-C03A33: Infra, <MAC C-05 WARPSTAR-C03A33>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    F660T-bCgM-G:    Infra, <MAC C-06 F660T-bCgM-G>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    aterm-5332d9-g:  Infra, <MAC C-07 aterm-5332d9-g>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    WARPSTAR-C03A33-W: Infra, <MAC C-04 WARPSTAR-C03A33-W>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WEP
    aterm-5332d9-gw: Infra, <MAC C-08 aterm-5332d9-gw>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WEP
    Kitamachi:       Infra, <MAC C-02 Kitamachi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89
    *MyPlaceKitamachi: Infra, <MAC C-01 MyPlaceKitamachi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA2
    4CE676AEB41D-1:  Infra, <MAC C-NA 4CE676AEB41D-1 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA
    4CE676AEB41D:    Infra, <MAC C-NA 4CE676AEB41D 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    0024A514F2FF:    Infra, <MAC C-NA 0024A514F2FF 1>, Freq 2457 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2


    Address:         192.168.10.158
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1
    DNS:             192.168.10.1
---------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


0001softbank         : ssid=0001softbank | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
001D7346D5EA         : ssid=001D7346D5EA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
0024A5B0DFF0         : ssid=0024A5B0DFF0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
106F3F09C129         : ssid=106F3F09C129 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
4CE6765AA3EA-1       : ssid=4CE6765AA3EA-1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Airport Free Wi-Fi   : ssid=Airport Free Wi-Fi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AirPort_Hotspot      : ssid=AirPort_Hotspot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AIRPORT-WiFi-FREE    : ssid=AIRPORT-WiFi-FREE | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Apple Network 83df15 : ssid=Apple Network 83df15 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
at_STARBUCKS_Wi2     : ssid=at_STARBUCKS_Wi2 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AUCKLAND CITY WI-FI  : ssid=AUCKLAND CITY WI-FI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auckland Wi-Fi @ Tomizone : ssid=Auckland Wi-Fi @ Tomizone | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AVOCATS_WIFI         : ssid=AVOCATS_WIFI | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
awmn-4097-AP         : ssid=awmn-4097-AP | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Barabra              : ssid=Barabra | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Bluediamond_F3B      : ssid=Bluediamond_F3B | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Boingo Hotspot       : ssid=Boingo Hotspot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Boingo_Hotspot       : ssid=Boingo_Hotspot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
$ Cheap Internet HOTSPOT : ssid=$ Cheap Internet HOTSPOT | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Cheap Internet HOTSPOT : ssid=Cheap Internet HOTSPOT | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ChinaNet             : ssid=ChinaNet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
CHUO-GRAD            : ssid=CHUO-GRAD | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CHUO-U               : ssid=CHUO-U | mac-address=<MAC wlan0> | ipv4=auto 
Copthorne Conference Wireless : ssid=Copthorne Conference Wireless | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Copthorne Lobby Wireless : ssid=Copthorne Lobby Wireless | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Copthorne Wireless   : ssid=Copthorne Wireless | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
docomo               : ssid=docomo | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Doubleduke2          : ssid=Doubleduke2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Esalen 6             : ssid=Esalen 6 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Esalen 7             : ssid=Esalen 7 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FON                  : ssid=FON | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FON_FREE_EAP         : ssid=FON_FREE_EAP | mac-address=<MAC wlan0> | ipv4=auto 
FON_FREE_INTERNET    : ssid=FON_FREE_INTERNET | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
freebox_POZBEB       : ssid=freebox_POZBEB | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Free Internet by DIA : ssid=Free Internet by DIA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FreeWifi             : ssid=FreeWifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FreeWiFi-NARITA      : ssid=FreeWiFi-NARITA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
guestwifi            : ssid=guestwifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
HANEDA-FREE-WIFI     : ssid=HANEDA-FREE-WIFI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Herald_Solana        : ssid=Herald_Solana | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Herald Suites Boardroom : ssid=Herald Suites Boardroom | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Hope                 : ssid=Hope | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hotel St Charles     : ssid=Hotel St Charles | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Hss_5th_Floor_Center : ssid=Hss_5th_Floor_Center | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hss_5th_Floor_Elevator : ssid=Hss_5th_Floor_Elevator | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hss_6th_Floor_Elevator : ssid=Hss_6th_Floor_Elevator | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
iMac gael            : ssid=iMac gael | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Invites-Telecom      : ssid=Invites-Telecom | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Jal Wireless         : ssid=Jal Wireless | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Kitamachi            : ssid=Kitamachi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Livebox-087a         : ssid=Livebox-087a | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MegaNet-FreeWifi     : ssid=MegaNet-FreeWifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
MegaNet-NoiBai       : ssid=MegaNet-NoiBai | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
mobilepoint          : ssid=mobilepoint | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlace              : ssid=MyPlace | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlace_2D6BF4       : ssid=MyPlace_2D6BF4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlaceKitamachi     : ssid=MyPlaceKitamachi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlace Kitamachi    : ssid=MyPlace Kitamachi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
narita-airport-free-mifi : ssid=narita-airport-free-mifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
narita-airport-free-wifi : ssid=narita-airport-free-wifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
NETGEAR              : ssid=NETGEAR | bssid=<MAC ID removed> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Nozawa               : ssid=Nozawa | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NSAH                 : ssid=NSAH | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
OTEDFEBE0            : ssid=OTEDFEBE0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
OTEe447a7            : ssid=OTEe447a7 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
PdaNet HotSpot       : ssid=PdaNet | autoconnect=false HotSpot | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto 
PdaNet HotSpot 1     : ssid=PdaNet HotSpot | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Qtel My-Fi a82b      : ssid=Qtel My-Fi a82b | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Salad Buri@outdoor2  : ssid=Salad Buri@outdoor2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SpetSof              : ssid=SpetSof | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SUTD_Guest           : ssid=SUTD_Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
SWS1day              : ssid=SWS1day | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
t1fg                 : ssid=t1fg | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TDPJ                 : ssid=TDPJ | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Telecom-ParisTech    : ssid=Telecom-ParisTech | mac-address=<MAC wlan0> | ipv4=auto 
TP-LINK_D0F0E4       : ssid=TP-LINK_D0F0E4 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TRM1                 : ssid=TRM1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
@TRUEWIFI            : ssid=@TRUEWIFI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
UQ_Wi-Fi             : ssid=UQ_Wi-Fi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
utroam               : ssid=utroam | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WARPSTAR-C03A33      : ssid=WARPSTAR-C03A33 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WARPSTAR-C03A33-W    : ssid=WARPSTAR-C03A33-W | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
#WiFi@Changi         : ssid=#WiFi@Changi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
swifi haadsalad from  room : ssid=swifi haadsalad from  room | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Wifi@TheElizabeth    : ssid=Wifi@TheElizabeth | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WiMasT@ JJ2          : ssid=WiMasT@ JJ2 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WINNING              : ssid=WINNING | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WLANNET              : ssid=WLANNET | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


auto lo
iface lo inet loopback




resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search lan




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 wlan0
192.168.10.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.469/1.489/1.509/0.020 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.044/0.050/0.056/0.006 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_GB.UTF-8")
country JP:
    (2402 - 2482 @ 40), (N/A, 20)
    (2474 - 2494 @ 20), (N/A, 20), NO-OFDM
    (4910 - 4990 @ 40), (N/A, 23)
    (5030 - 5090 @ 40), (N/A, 23)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 23), DFS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          Current Frequency=2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 MyPlaceKitamachi>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"MyPlaceKitamachi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017005861f6
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Kitamachi>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"Kitamachi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000170fb47abb
                    Extra: Last beacon: 148ms ago
          Cell 03 - Address: <MAC C-03 FON_FREE_EAP>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"FON_FREE_EAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000170fb481ed
                    Extra: Last beacon: 144ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC C-04 WARPSTAR-C03A33-W>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"WARPSTAR-C03A33-W"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000190bb2af728
                    Extra: Last beacon: 0ms ago
          Cell 05 - Address: <MAC C-05 WARPSTAR-C03A33>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WARPSTAR-C03A33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000190bb2ae81c
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 F660T-bCgM-G>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"F660T-bCgM-G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000227c13412b9
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 aterm-5332d9-g>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"aterm-5332d9-g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004120b4abeac
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 aterm-5332d9-gw>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"aterm-5332d9-gw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004120b4b9640
                    Extra: Last beacon: 0ms ago




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist r8169




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[asus_nb_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[video]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/acpi/video.ko
srcversion:     3D537E78F15014033076CAC
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/rc.local]
exit 0
echo 1 > /sys/class/backlight/intel_backlight/brightness


[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/sleep.d/wakenet.sh] [executable]
#!/bin/bash
case "$1" in
thaw|resume)
nmcli nm sleep false
pkill -f wpa_supplicant
;;
*)
;;
esac
exit $?




[/etc/pm/sleep.d/wakenet.sh~] [executable]




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=7df40251-48fe-4d9a-836f-081d230b2465 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.842957] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.843317] audit: initializing netlink socket (disabled)
[    2.281392] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   22.858857] wmi: Mapper loaded
[   23.114094] ath: phy0: Enable LNA combining
[   23.115929] ath: EEPROM regdomain: 0x60
[   23.115932] ath: EEPROM indicates we should expect a direct regpair map
[   23.115935] ath: Country alpha2 being used: 00
[   23.115936] ath: Regpair used: 0x60
[   23.189792] asus_wmi: ASUS WMI generic driver loaded
[   23.195914] asus_wmi: Initialization: 0x1
[   23.195955] asus_wmi: BIOS WMI version: 7.6
[   23.196019] asus_wmi: SFUN value: 0x1a0877
[   23.196964] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   23.291820] asus_wmi: Backlight controlled by ACPI video driver
[   25.253656] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.255106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.259943] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.348081] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   30.364961] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   30.566989] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 2/3)
[   30.770897] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 3/3)
[   30.974778] wlan0: authentication with <MAC C-01 MyPlaceKitamachi> timed out
[   32.062792] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   32.085085] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   32.286161] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 2/3)
[   32.490021] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 3/3)
[   32.693977] wlan0: authentication with <MAC C-01 MyPlaceKitamachi> timed out
[   34.189913] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   34.212180] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   34.413069] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 2/3)
[   34.616983] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 3/3)
[   34.820911] wlan0: authentication with <MAC C-01 MyPlaceKitamachi> timed out
[   36.796198] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   36.818894] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   37.019691] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 2/3)
[   37.223615] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 3/3)
[   37.427519] wlan0: authentication with <MAC C-01 MyPlaceKitamachi> timed out
[   49.361946] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   49.384167] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   49.585319] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 2/3)
[   49.789228] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 3/3)
[   49.993027] wlan0: authentication with <MAC C-01 MyPlaceKitamachi> timed out
[   58.286301] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   58.303319] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   58.504755] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 2/3)
[   58.708591] wlan0: direct probe to <MAC C-01 MyPlaceKitamachi> (try 3/3)
[   58.912541] wlan0: authentication with <MAC C-01 MyPlaceKitamachi> timed out
[   69.899466] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   69.921724] wlan0: send auth to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   69.923685] wlan0: authenticated
[   69.926867] wlan0: associate with <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   69.932690] wlan0: RX AssocResp from <MAC C-01 MyPlaceKitamachi> (capab=0xc11 status=0 aid=2)
[   69.932740] wlan0: associated
[   69.932748] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.935427] ath: EEPROM regdomain: 0x8188
[   69.935429] ath: EEPROM indicates we should expect a country code
[   69.935431] ath: doing EEPROM country->regdmn map search
[   69.935432] ath: country maps to regdmn code: 0x40
[   69.935433] ath: Country alpha2 being used: JP
[   69.935434] ath: Regpair used: 0x40
[   69.935435] ath: regdomain 0x8188 dynamically updated by country IE
[   88.443048] wlan0: deauthenticating from <MAC C-01 MyPlaceKitamachi> by local choice (reason=3)
[   89.661770] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   89.684183] wlan0: send auth to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   89.686285] wlan0: authenticated
[   89.689269] wlan0: associate with <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   89.693513] wlan0: RX AssocResp from <MAC C-01 MyPlaceKitamachi> (capab=0xc11 status=0 aid=2)
[   89.693587] wlan0: associated
[   89.695818] ath: EEPROM regdomain: 0x8188
[   89.695821] ath: EEPROM indicates we should expect a country code
[   89.695822] ath: doing EEPROM country->regdmn map search
[   89.695823] ath: country maps to regdmn code: 0x40
[   89.695824] ath: Country alpha2 being used: JP
[   89.695825] ath: Regpair used: 0x40
[   89.695827] ath: regdomain 0x8188 dynamically updated by country IE
[   90.274713] wlan0: deauthenticating from <MAC C-01 MyPlaceKitamachi> by local choice (reason=2)
[   90.285747] wlan0: authenticate with <MAC C-01 MyPlaceKitamachi>
[   90.301918] wlan0: send auth to <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   90.303980] wlan0: authenticated
[   90.305277] wlan0: associate with <MAC C-01 MyPlaceKitamachi> (try 1/3)
[   90.309515] wlan0: RX AssocResp from <MAC C-01 MyPlaceKitamachi> (capab=0xc11 status=0 aid=2)
[   90.309572] wlan0: associated
[   90.311697] ath: EEPROM regdomain: 0x8188
[   90.311700] ath: EEPROM indicates we should expect a country code
[   90.311701] ath: doing EEPROM country->regdmn map search
[   90.311702] ath: country maps to regdmn code: 0x40
[   90.311703] ath: Country alpha2 being used: JP
[   90.311704] ath: Regpair used: 0x40
[   90.311706] ath: regdomain 0x8188 dynamically updated by country IE


    ======== Done ========

```

---

### Post by varunendra on 2014-09-28
> **Bregham_Dalgliesh said:**
> ..I cannot find "how to use code tags" ...

It has been shown with screenshots here : [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Please take a look at it, and edit your post above to wrap the output part within the 'code' tags pair. Basically, all you have to do in the edit is to type **[COLOR="#0000FF"][noparse]```
[/noparse][/COLOR]** in the beginning and **[COLOR="#0000FF"][noparse]
```[/noparse][/COLOR]** at the end of the part that you want to keep within the 'Code' box.

Regarding the problem, I can't see any obvious issue, but please try updating your system first. I think the current kernel version is 3.13.0-36, while you are using ...35, so an update may fix it automatically if it is a driver issue.

To do the update, you can do it via GUI 'Update Manager', or with -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
..in the terminal. After updating the system as suggested above, confirm the kernel version with -
```
uname -r
```

Apart from that, please try this in a terminal -
```
sudo iwconfig wlan0 txpower 20
```
Then check -
```
iwconfig
```
Does it now show "Tx-Power=**20** dBm"? This trick doesn't work on all cards, but is useful where it does. Japan's regdomain settings allow Transmission Power upto 20 dBm it seems, so unless it is a limitation on the card itself, it should be 20 dBm.

Also, maybe not related, but the custom entry in your '/etc/rc.local' file is placed in a wrong way. The "exit 0" line should ALWAYS be the LAST line in that file, while it is the custom entry that is the last line in your file. Please run the following commands to correct this discrepancy -
```
sudo sed -i '/^exit 0/ d' /etc/rc.local
echo "exit 0" | sudo tee -a /etc/rc.loacl
```

And delete an unnecessary file from your sudo rm '/etc/pm/sleep.d/' directory -
```
sudo rm /etc/pm/sleep.d/wakenet.sh~
```
It is a backup file that is created automatically when you edit any text file using your GUI text editor. It may not be harmful, but I don't want to leave any doubts. By the way, when did you create that file (the original, not the backup one above)? Were you having a Network Manager problem after suspend/resume cycle? Did it solve it?

One more thing, shouldn't be a problem with connection, but *sometimes* may cause slow browsing speed problems - Please set "IPv6" in Network Manager to "Ignore" (under "IPv6 Settings" tab > "Method"), since you don't seem to be using it.

Let us know if these changes make any difference. If not, we have a few more things to try.

---

### Post by Bregham_Dalgliesh on 2014-09-29
Dear Varun,

Thanks for the "stupid users' guide" to code tags, I hope I reedited the post correctly!

Strange thing just happened, I turned on the laptop within 1-1.5 metres of the wifi router and it connected automatically! To check, I sat on the other side of the room where I usually work from - only about 3-7 metres from the wifi router - and it didn't connect, so I walked over to the router and it has just connected again from a metre or so away. So it seems like a possible problem linked to distance ... but as I said before, all our other devices connect as normal from much greater distances, including an iPhone 4 & 5 and an Android tablet.

I ran the instructions you gave me in a terminal and below are the results. It doesn't seem to have updated 3.13.0-36?

```

bregham@Bregham-Asus:~$ sudo apt-get update
[sudo] password for bregham: 
Sorry, try again.
[sudo] password for bregham: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release.gpg                                    
Ign http://jp.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable Release                                        
Ign http://jp.archive.ubuntu.com trusty-updates InRelease                      
Ign http://jp.archive.ubuntu.com trusty-backports InRelease                    
Hit http://jp.archive.ubuntu.com trusty Release.gpg                            
Hit http://dl.google.com stable Release                                        
Get:1 http://jp.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:2 http://jp.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://archive.canonical.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://jp.archive.ubuntu.com trusty Release                                
Get:3 http://jp.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable/main i386 Packages                             
Get:4 http://jp.archive.ubuntu.com trusty-backports Release [59.7 kB]          
Hit http://archive.canonical.com trusty Release.gpg                            
Get:5 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://jp.archive.ubuntu.com trusty/main Sources                           
Hit http://jp.archive.ubuntu.com trusty/restricted Sources                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://jp.archive.ubuntu.com trusty/universe Sources                       
Hit http://jp.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://archive.canonical.com trusty Release                                
Hit http://jp.archive.ubuntu.com trusty/main i386 Packages                     
Get:6 http://security.ubuntu.com trusty-security Release [59.7 kB]             
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://jp.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://jp.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://jp.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://jp.archive.ubuntu.com trusty/main Translation-en_GB                 
Hit http://jp.archive.ubuntu.com trusty/main Translation-en                    
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://jp.archive.ubuntu.com trusty/multiverse Translation-en_GB           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://jp.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://jp.archive.ubuntu.com trusty/restricted Translation-en_GB           
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://jp.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://jp.archive.ubuntu.com trusty/universe Translation-en_GB             
Hit http://jp.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty Release                                    
Get:7 http://jp.archive.ubuntu.com trusty-updates/main Sources [121 kB]        
Get:8 http://security.ubuntu.com trusty-security/main Sources [45.3 kB]        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release                                    
Get:9 http://jp.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B] 
Ign http://dl.google.com stable/main Translation-en_GB                         
Get:10 http://jp.archive.ubuntu.com trusty-updates/universe Sources [85.1 kB]  
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Get:11 http://jp.archive.ubuntu.com trusty-updates/multiverse Sources [3,527 B]
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:12 http://jp.archive.ubuntu.com trusty-updates/main i386 Packages [318 kB] 
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Get:13 http://security.ubuntu.com trusty-security/restricted Sources [14 B]    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:14 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]   
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:15 http://jp.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:16 http://jp.archive.ubuntu.com trusty-updates/universe i386 Packages [206 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:17 http://security.ubuntu.com trusty-security/multiverse Sources [700 B]   
Get:18 http://jp.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,545 B]
Hit http://jp.archive.ubuntu.com trusty-updates/main Translation-en            
Get:19 http://security.ubuntu.com trusty-security/main i386 Packages [136 kB]  
Hit http://jp.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://jp.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://jp.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:20 http://jp.archive.ubuntu.com trusty-backports/main Sources [4,760 B]    
Get:21 http://jp.archive.ubuntu.com trusty-backports/restricted Sources [14 B] 
Get:22 http://jp.archive.ubuntu.com trusty-backports/universe Sources [13.7 kB]
Get:23 http://jp.archive.ubuntu.com trusty-backports/multiverse Sources [1,315 B]
Get:24 http://jp.archive.ubuntu.com trusty-backports/main i386 Packages [6,379 B]
Get:25 http://jp.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:26 http://jp.archive.ubuntu.com trusty-backports/universe i386 Packages [16.8 kB]
Get:27 http://jp.archive.ubuntu.com trusty-backports/multiverse i386 Packages [945 B]
Hit http://jp.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://jp.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://jp.archive.ubuntu.com trusty-backports/restricted Translation-en    
Get:28 http://jp.archive.ubuntu.com trusty-backports/universe Translation-en [14.3 kB]
Get:29 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:30 http://security.ubuntu.com trusty-security/universe i386 Packages [48.8 kB]
Get:31 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Ign http://jp.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://jp.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://jp.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://jp.archive.ubuntu.com trusty/universe Translation-en_US             
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Fetched 1,234 kB in 7s (155 kB/s)                                              
Reading package lists... Done
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
bregham@Bregham-Asus:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.6.3) but it is not installed
 libreoffice-ogltrans : Depends: libreoffice-common but it is not installed
E: Unmet dependencies. Try using -f.
bregham@Bregham-Asus:~$ uname -r
3.13.0-35-generic
bregham@Bregham-Asus:~$ sudo sed -i '/^exit 0/ d' /etc/rc.local
bregham@Bregham-Asus:~$ echo "exit 0" | sudo tee -a /etc/rc.loacl
exit 0
bregham@Bregham-Asus:~$ sudo rm /etc/pm/sleep.d/wakenet.sh~
bregham@Bregham-Asus:~$ 

```

So I seem to have a workable solution as long as I'm near the wifi router, but it would be nice to sort out the problem properly. I'll take the laptop into work tomorrow and connect to other wifi networks to check it isn't anything to do with my wifi router at home. I'll post back with the results.

Thanks again for all your help, the time and patience you devote is amazing!

Just one thing I forgot, which is to do with the 20dBm. I ran that test as well and here are the results (with "leaking memory" result that keeps cropping up...?)

```

bregham@Bregham-Asus:~$ sudo iwconfig wlan0 txpower 20
[sudo] password for bregham: 
Sorry, try again.
[sudo] password for bregham: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
bregham@Bregham-Asus:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"MyPlaceKitamachi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:71:30:2D:6B:F4   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:147   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.

```

---

### Post by slickymaster on 2014-09-29
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Bregham_Dalgliesh on 2014-09-29
Thanks, but the problem isn't yet solved and I'm hoping to have a reply to get a proper fix. I hope that's okay.

---

### Post by varunendra on 2014-09-29
The 'memory leakage' error seems to be 'samba' related, doesn't seem to harm anything other than some network sharing features. Can possibly be fixed with -
```
sudo pam-auth-update
```
See this bug report and possible fixes so far : [https://bugs.launchpad.net/bugs/1257186](https://bugs.launchpad.net/bugs/1257186)
You should add yourself to the "Affects Me" list of the bug report above.

The update failed because you seem to have held-back old packages problem. Please try as the outputs suggested -
```
sudo apt-get -f install
```
Watch for errors, post a new thread if you still get any. The usual and easier fix is to simply remove the offending package, and it seems to be related with 'libreoffice', which is an important, but not system-critical package. So should get fixed easily (even if it means removing everything 'libreoffice' related. We can install that again later).

The request for marking as [solved] in slickymaster's post is part of his signature, not the part of his post, so don't worry about it. :)

I'd be curious to see the report of your connection attempts at office. Be sure to generate a wireless_script report there too, whether the connection succeeds or fails. A comparison may help sometimes.

---

### Post by Bregham_Dalgliesh on 2014-09-29
Thanks Varun, I tried the fixes but there were still one or two bugs/errors. Here are the results:

```

bregham@Bregham-Asus:~$ sudo pam-auth-update
[sudo] password for bregham: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
bregham@Bregham-Asus:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-human libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-style-tango
The following NEW packages will be installed
  libreoffice-common
0 to upgrade, 1 to newly install, 0 to remove and 44 not to upgrade.
8 not fully installed or removed.
Need to get 0 B/19.9 MB of archives.
After this operation, 76.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 222403 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a4.2.6.3-0ubuntu1_all.deb ...
Unpacking libreoffice-common (1:4.2.6.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.2.6.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.1-9775
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.2.6.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bregham@Bregham-Asus:~$ 

```

If Libreoffice is playing up, I have no problem removing it if you advise. I use Apache OOO.

Will post the wifi results from my office connectivity tomorrow.

Many thanks!

---

### Post by varunendra on 2014-09-29
Is the 'memory leakage' error gone? Just curious.

The package error troubleshooting go longer than anticipated, so as originally suggested, please start a new thread for it. PM me its link so I can follow, possibly troubleshoot it if no one else picks it up.

The fact that Tx Power can be set to 20 is a good progress. If the newer kernel doesn't fix the remaining problem, I would probably try a newer driver from the backports, but for the procedure to go smoothly, you need to fix the package error first.

---

### Post by Bregham_Dalgliesh on 2014-10-01
Hi Varun

So the wifi connection at my office is working normally! I tried two different networks and the connection is established quickly as you would expect. As requested I'm posting the wireless_script report:

```

    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Bregham-Asus 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory : 3811 MB
Uptime : 14:47:58 up 56 min,  2 users,  load average: 0.92, 1.37, 0.70




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5120 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"wpa.c"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 wpa.c>   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
0: phy0: Wireless LAN           no            no
1: asus-wlan: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


asus_nb_wmi            16862  0 
asus_wmi               23495  1 asus_nb_wmi
sparse_keymap          13708  1 asus_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
video                  18903  2 i915,asus_wmi
wmi                    18673  1 asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
================o=============o========o==========  ===o=========o===========o==============o=========  ==
 Interface & ID | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=============o========o==========  ===o=========o===========o==============o=========  ==
 eth0           | Wired       | atl1c  | unavailable | no      |           |              | <MAC eth0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [wpa.c] | 802.11 WiFi | ath9k  | connected   | yes     | 58 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    4CE676FA0CAE_G:  Infra, <MAC C-05 4CE676FA0CAE_G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    breghamiMac:     Infra, <MAC C-30 breghamiMac>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    106F3F377803:    Infra, <MAC C-04 106F3F377803>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Buffalo-G-0F1A:  Infra, <MAC C-07 Buffalo-G-0F1A>, Freq 2422 MHz, Rate 54 Mb/s, Strength 52 WPA2
    komaba-guest:    Infra, <MAC C-14 komaba-guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    utroam-1x:       Infra, <MAC C-11 utroam-1x>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    106F3F88ADE2_G:  Infra, <MAC C-06 106F3F88ADE2_G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    eduroam:         Infra, <MAC C-13 eduroam>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    utroam:          Infra, <MAC C-10 utroam>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    utroam:          Infra, <MAC C-31 utroam>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    utroam:          Infra, <MAC C-17 utroam>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    utroam-1x:       Infra, <MAC C-19 utroam-1x>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    eduroam:         Infra, <MAC C-20 eduroam>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    utroam:          Infra, <MAC C-21 utroam>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    eduroam:         Infra, <MAC C-NA eduroam 4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    utroam-1x:       Infra, <MAC C-NA utroam-1x 3>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    LISOffice:       Infra, <MAC C-27 LISOffice>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WEP
    SWS1day:         Infra, <MAC C-34 SWS1day>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    0001softbank:    Infra, <MAC C-02 0001softbank>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    SWS1day:         Infra, <MAC C-03 SWS1day>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    wpa.c:           Infra, <MAC C-NA wpa.c 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    komaba-guest:    Infra, <MAC C-08 komaba-guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    wpa.c:           Infra, <MAC C-18 wpa.c>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    eduroam:         Infra, <MAC C-33 eduroam>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    aterm-986b4a-gw: Infra, <MAC C-24 aterm-986b4a-gw>, Freq 2447 MHz, Rate 54 Mb/s, Strength 35 WEP
    0001softbank:    Infra, <MAC C-23 0001softbank>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    0001softbank:    Infra, <MAC C-35 0001softbank>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29
    SWS1day:         Infra, <MAC C-16 SWS1day>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19
    wpa.c:           Infra, <MAC C-15 wpa.c>, Freq 2437 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    komaba-guest:    Infra, <MAC C-28 komaba-guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    CDR Guests:      Infra, <MAC C-09 CDR Guests>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    aterm-986b4a-g:  Infra, <MAC C-NA aterm-986b4a-g 1>, Freq 2447 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    komaba-guest:    Infra, <MAC C-NA komaba-guest 4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    wpa.c:           Infra, <MAC C-NA wpa.c 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    utroam:          Infra, <MAC C-NA utroam 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    18jimu-wifi:     Infra, <MAC C-NA 18jimu-wifi 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    eduroam:         Infra, <MAC C-NA eduroam 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
    komaba-guest:    Infra, <MAC C-NA komaba-guest 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    utroam-1x:       Infra, <MAC C-NA utroam-1x 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
    SWS1day:         Infra, <MAC C-22 SWS1day>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    0001softbank:    Infra, <MAC C-NA 0001softbank 3>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    SWS1day:         Infra, <MAC C-NA SWS1day 2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    *wpa.c:          Infra, <MAC C-01 wpa.c>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2


    Address:         10.10.0.51
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.0.1
    DNS:             157.82.35.235
    DNS:             157.82.35.35
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


0001softbank         : ssid=0001softbank | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
001D7346D5EA         : ssid=001D7346D5EA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
0024A5B0DFF0         : ssid=0024A5B0DFF0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
106F3F09C129         : ssid=106F3F09C129 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
4CE6765AA3EA-1       : ssid=4CE6765AA3EA-1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Airport Free Wi-Fi   : ssid=Airport Free Wi-Fi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AirPort_Hotspot      : ssid=AirPort_Hotspot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AIRPORT-WiFi-FREE    : ssid=AIRPORT-WiFi-FREE | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Apple Network 83df15 : ssid=Apple Network 83df15 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
at_STARBUCKS_Wi2     : ssid=at_STARBUCKS_Wi2 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AUCKLAND CITY WI-FI  : ssid=AUCKLAND CITY WI-FI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auckland Wi-Fi @ Tomizone : ssid=Auckland Wi-Fi @ Tomizone | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
AVOCATS_WIFI         : ssid=AVOCATS_WIFI | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
awmn-4097-AP         : ssid=awmn-4097-AP | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Barabra              : ssid=Barabra | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Bluediamond_F3B      : ssid=Bluediamond_F3B | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Boingo Hotspot       : ssid=Boingo Hotspot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Boingo_Hotspot       : ssid=Boingo_Hotspot | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
breghamiMac          : ssid=breghamiMac | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
$ Cheap Internet HOTSPOT : ssid=$ Cheap Internet HOTSPOT | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Cheap Internet HOTSPOT : ssid=Cheap Internet HOTSPOT | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
ChinaNet             : ssid=ChinaNet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
CHUO-GRAD            : ssid=CHUO-GRAD | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
CHUO-U               : ssid=CHUO-U | mac-address=<MAC wlan0> | ipv4=auto 
Copthorne Conference Wireless : ssid=Copthorne Conference Wireless | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Copthorne Lobby Wireless : ssid=Copthorne Lobby Wireless | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Copthorne Wireless   : ssid=Copthorne Wireless | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
docomo               : ssid=docomo | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Doubleduke2          : ssid=Doubleduke2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Esalen 6             : ssid=Esalen 6 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Esalen 7             : ssid=Esalen 7 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FON                  : ssid=FON | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FON_FREE_EAP         : ssid=FON_FREE_EAP | mac-address=<MAC wlan0> | ipv4=auto 
FON_FREE_INTERNET    : ssid=FON_FREE_INTERNET | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
freebox_POZBEB       : ssid=freebox_POZBEB | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Free Internet by DIA : ssid=Free Internet by DIA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FreeWifi             : ssid=FreeWifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
FreeWiFi-NARITA      : ssid=FreeWiFi-NARITA | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
guestwifi            : ssid=guestwifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
HANEDA-FREE-WIFI     : ssid=HANEDA-FREE-WIFI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Herald_Solana        : ssid=Herald_Solana | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Herald Suites Boardroom : ssid=Herald Suites Boardroom | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Hope                 : ssid=Hope | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hotel St Charles     : ssid=Hotel St Charles | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Hss_5th_Floor_Center : ssid=Hss_5th_Floor_Center | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hss_5th_Floor_Elevator : ssid=Hss_5th_Floor_Elevator | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hss_6th_Floor_Elevator : ssid=Hss_6th_Floor_Elevator | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
iMac gael            : ssid=iMac gael | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Invites-Telecom      : ssid=Invites-Telecom | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Jal Wireless         : ssid=Jal Wireless | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Kitamachi            : ssid=Kitamachi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Livebox-087a         : ssid=Livebox-087a | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MegaNet-FreeWifi     : ssid=MegaNet-FreeWifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
MegaNet-NoiBai       : ssid=MegaNet-NoiBai | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
mobilepoint          : ssid=mobilepoint | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlace              : ssid=MyPlace | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlace_2D6BF4       : ssid=MyPlace_2D6BF4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MyPlaceKitamachi     : ssid=MyPlaceKitamachi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 
MyPlace Kitamachi    : ssid=MyPlace Kitamachi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 
narita-airport-free-mifi : ssid=narita-airport-free-mifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
narita-airport-free-wifi : ssid=narita-airport-free-wifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
NETGEAR              : ssid=NETGEAR | bssid=<MAC ID removed> | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Nozawa               : ssid=Nozawa | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NSAH                 : ssid=NSAH | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
OTEDFEBE0            : ssid=OTEDFEBE0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
OTEe447a7            : ssid=OTEe447a7 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
PdaNet HotSpot       : ssid=PdaNet | autoconnect=false HotSpot | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto 
PdaNet HotSpot 1     : ssid=PdaNet HotSpot | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Qtel My-Fi a82b      : ssid=Qtel My-Fi a82b | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Salad Buri@outdoor2  : ssid=Salad Buri@outdoor2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SpetSof              : ssid=SpetSof | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SUTD_Guest           : ssid=SUTD_Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
SWS1day              : ssid=SWS1day | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
t1fg                 : ssid=t1fg | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TDPJ                 : ssid=TDPJ | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Telecom-ParisTech    : ssid=Telecom-ParisTech | mac-address=<MAC wlan0> | ipv4=auto 
TP-LINK_D0F0E4       : ssid=TP-LINK_D0F0E4 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TRM1                 : ssid=TRM1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
@TRUEWIFI            : ssid=@TRUEWIFI | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
UQ_Wi-Fi             : ssid=UQ_Wi-Fi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
utroam               : ssid=utroam | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WARPSTAR-C03A33      : ssid=WARPSTAR-C03A33 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
WARPSTAR-C03A33-W    : ssid=WARPSTAR-C03A33-W | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
#WiFi@Changi         : ssid=#WiFi@Changi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
swifi haadsalad from  room : ssid=swifi haadsalad from  room | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Wifi@TheElizabeth    : ssid=Wifi@TheElizabeth | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WiMasT@ JJ2          : ssid=WiMasT@ JJ2 | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WINNING              : ssid=WINNING | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WLANNET              : ssid=WLANNET | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
wpa.c                : ssid=wpa.c | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


auto lo
iface lo inet loopback




resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search c.u-tokyo.ac.jp




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.0.1       0.0.0.0         UG    0      0        0 wlan0
10.10.0.0       0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 10.10.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 5.907/8.177/10.448/2.272 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.026/0.034/0.043/0.010 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_GB.UTF-8")
country JP:
    (2402 - 2482 @ 40), (N/A, 20)
    (2474 - 2494 @ 20), (N/A, 20), NO-OFDM
    (4910 - 4990 @ 40), (N/A, 23)
    (5030 - 5090 @ 40), (N/A, 23)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 23), DFS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          Current Frequency=2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 wpa.c>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"wpa.c"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a472f502499
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 0001softbank>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"0001softbank"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a47325d401a
                    Extra: Last beacon: 260ms ago
          Cell 03 - Address: <MAC C-03 SWS1day>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"SWS1day"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a47325d6580
                    Extra: Last beacon: 240ms ago
          Cell 04 - Address: <MAC C-04 106F3F377803>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"106F3F377803"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000e7027ecb8b4
                    Extra: Last beacon: 260ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 4CE676FA0CAE_G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"4CE676FA0CAE_G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000016db7161cf34
                    Extra: Last beacon: 880ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 106F3F88ADE2_G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"106F3F88ADE2_G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000f901711dde9
                    Extra: Last beacon: 532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 Buffalo-G-0F1A>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Buffalo-G-0F1A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003d750352ddd
                    Extra: Last beacon: 2240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 komaba-guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"komaba-guest"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a47325ee580
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 CDR Guests>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"CDR Guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000043ea0f40180
                    Extra: Last beacon: 540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 utroam>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"utroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a47325eeeb8
                    Extra: Last beacon: 192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 utroam-1x>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"utroam-1x"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a47325eed80
                    Extra: Last beacon: 180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC C-12 CDR>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"CDR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000043ea0fa4180
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 eduroam>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a47325ee980
                    Extra: Last beacon: 168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC C-14 komaba-guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"komaba-guest"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3e00000ae4b9cbcc
                    Extra: Last beacon: 1892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 wpa.c>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"wpa.c"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ae4b9974c
                    Extra: Last beacon: 1908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 SWS1day>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"SWS1day"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=25000a4730c2379d
                    Extra: Last beacon: 5780ms ago
          Cell 17 - Address: <MAC C-17 utroam>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"utroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=5700000ae4616ac9
                    Extra: Last beacon: 5780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC C-18 wpa.c>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"wpa.c"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a4730c20c93
                    Extra: Last beacon: 5780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC C-19 utroam-1x>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"utroam-1x"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=4b00000ae46170ae
                    Extra: Last beacon: 5780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 20 - Address: <MAC C-20 eduroam>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3200000ae461739c
                    Extra: Last beacon: 1928ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC C-21 utroam>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"utroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=57000a4730c2176f
                    Extra: Last beacon: 5780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC C-22 SWS1day>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"SWS1day"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=2500000ae4b9bc68
                    Extra: Last beacon: 1896ms ago
          Cell 23 - Address: <MAC C-23 0001softbank>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"0001softbank"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=1900000ae4b9c3ce
                    Extra: Last beacon: 1892ms ago
          Cell 24 - Address: <MAC C-24 aterm-986b4a-gw>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"aterm-986b4a-gw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000069e0a894180
                    Extra: Last beacon: 7372ms ago
          Cell 25 - Address: <MAC C-25 FON_FREE_INTERNET>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"FON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000751ec9cb21
                    Extra: Last beacon: 7100ms ago
          Cell 26 - Address: <MAC C-26 Buffalo-G-7AC8>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Buffalo-G-7AC8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000dd3868316a3
                    Extra: Last beacon: 7024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC C-27 LISOffice>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"LISOffice"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000dd386db0ee2
                    Extra: Last beacon: 1256ms ago
          Cell 28 - Address: <MAC C-28 komaba-guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"komaba-guest"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=19000a4734bbf383
                    Extra: Last beacon: 5780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC C-29 0024A5B9ECDF-1>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"0024A5B9ECDF-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000016dbce734180
                    Extra: Last beacon: 6780ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC C-30 breghamiMac>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"breghamiMac"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000059d010af2
                    Extra: Last beacon: 352ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC C-31 utroam>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"utroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=57000a4734bba1c9
                    Extra: Last beacon: 1020ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC C-32 utroam-1x>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"utroam-1x"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=4b000a4734bbaac0
                    Extra: Last beacon: 1008ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 33 - Address: <MAC C-33 eduroam>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3e000a4734bbb220
                    Extra: Last beacon: 5780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 34 - Address: <MAC C-34 SWS1day>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"SWS1day"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=25000a4734bbc556
                    Extra: Last beacon: 972ms ago
          Cell 35 - Address: <MAC C-35 0001softbank>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"0001softbank"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=32000a4734bbd34c
                    Extra: Last beacon: 5780ms ago
          Cell 36 - Address: <MAC C-36 523>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"523"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000c92954e2456
                    Extra: Last beacon: 1564ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 37 - Address: <MAC C-37 0024A5B9ECDF>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"0024A5B9ECDF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000016dbcecacd80
                    Extra: Last beacon: 1016ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 38 - Address: <MAC C-38 106F3F7FD464_G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"106F3F7FD464_G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist r8169




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[asus_nb_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[video]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/acpi/video.ko
srcversion:     3D537E78F15014033076CAC
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/rc.local]
echo 1 > /sys/class/backlight/intel_backlight/brightness


[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/sleep.d/wakenet.sh] [executable]
#!/bin/bash
case "$1" in
thaw|resume)
nmcli nm sleep false
pkill -f wpa_supplicant
;;
*)
;;
esac
exit $?






Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=7df40251-48fe-4d9a-836f-081d230b2465 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.842776] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.843132] audit: initializing netlink socket (disabled)
[    2.281373] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   22.513859] wmi: Mapper loaded
[   22.748544] ath: phy0: Enable LNA combining
[   22.750164] ath: EEPROM regdomain: 0x60
[   22.750165] ath: EEPROM indicates we should expect a direct regpair map
[   22.750167] ath: Country alpha2 being used: 00
[   22.750168] ath: Regpair used: 0x60
[   23.070710] asus_wmi: ASUS WMI generic driver loaded
[   23.075549] asus_wmi: Initialization: 0x1
[   23.075589] asus_wmi: BIOS WMI version: 7.6
[   23.075651] asus_wmi: SFUN value: 0x1a0877
[   23.076441] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input12
[   23.171964] asus_wmi: Backlight controlled by ACPI video driver
[   25.474029] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.386432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.391270] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.448128] wlan0: authenticate with <MAC C-03 SWS1day>
[   30.465132] wlan0: send auth to <MAC C-03 SWS1day> (try 1/3)
[   30.467252] wlan0: authenticated
[   30.470970] wlan0: associate with <MAC C-03 SWS1day> (try 1/3)
[   30.474650] wlan0: RX AssocResp from <MAC C-03 SWS1day> (capab=0x421 status=0 aid=1)
[   30.474738] wlan0: associated
[   30.474745] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  198.632370] wlan0: deauthenticating from <MAC C-03 SWS1day> by local choice (reason=3)
[  199.763607] wlan0: authenticate with <MAC C-10 utroam>
[  199.784000] wlan0: direct probe to <MAC C-10 utroam> (try 1/3)
[  199.984299] wlan0: send auth to <MAC C-10 utroam> (try 2/3)
[  199.986556] wlan0: authenticated
[  199.988266] wlan0: associate with <MAC C-10 utroam> (try 1/3)
[  199.992411] wlan0: RX AssocResp from <MAC C-10 utroam> (capab=0x431 status=0 aid=1)
[  199.992517] wlan0: associated
[  388.170762] wlan0: deauthenticating from <MAC C-10 utroam> by local choice (reason=3)
[  393.600498] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  395.646685] wlan0: authenticate with <MAC C-NA wpa.c 1>
[  395.668146] wlan0: direct probe to <MAC C-NA wpa.c 1> (try 1/3)
[  395.868219] wlan0: direct probe to <MAC C-NA wpa.c 1> (try 2/3)
[  396.071993] wlan0: direct probe to <MAC C-NA wpa.c 1> (try 3/3)
[  396.275883] wlan0: authentication with <MAC C-NA wpa.c 1> timed out
[  396.306235] wlan0: authenticate with <MAC C-15 wpa.c>
[  396.322768] wlan0: send auth to <MAC C-15 wpa.c> (try 1/3)
[  396.324780] wlan0: authenticated
[  396.327812] wlan0: associate with <MAC C-15 wpa.c> (try 1/3)
[  396.331093] wlan0: RX AssocResp from <MAC C-15 wpa.c> (capab=0x431 status=0 aid=2)
[  396.331148] wlan0: associated
[  396.331177] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  396.338285] ath: EEPROM regdomain: 0x8188
[  396.338293] ath: EEPROM indicates we should expect a country code
[  396.338297] ath: doing EEPROM country->regdmn map search
[  396.338301] ath: country maps to regdmn code: 0x40
[  396.338304] ath: Country alpha2 being used: JP
[  396.338308] ath: Regpair used: 0x40
[  396.338320] ath: regdomain 0x8188 dynamically updated by country IE
[  419.598356] wlan0: authenticate with <MAC C-01 wpa.c>
[  419.614726] wlan0: send auth to <MAC C-01 wpa.c> (try 1/3)
[  419.618445] wlan0: authenticated
[  419.620188] wlan0: associate with <MAC C-01 wpa.c> (try 1/3)
[  419.625312] wlan0: RX AssocResp from <MAC C-01 wpa.c> (capab=0x431 status=0 aid=2)
[  419.625368] wlan0: associated
[  419.627970] ath: EEPROM regdomain: 0x8188
[  419.627974] ath: EEPROM indicates we should expect a country code
[  419.627975] ath: doing EEPROM country->regdmn map search
[  419.627976] ath: country maps to regdmn code: 0x40
[  419.627977] ath: Country alpha2 being used: JP
[  419.627978] ath: Regpair used: 0x40
[  419.627980] ath: regdomain 0x8188 dynamically updated by country IE


    ======== Done ========

```

My Sherlock Holmes' instinct leads me to think it is therefore a problem after all with my FON wifi router at home ... I can post a screenshot of its wifi settings later, if that would help?

The "memory leakage" isn't gone, as far as I know, I don't know how to fix it after all?

Thanks!

---

### Post by varunendra on 2014-10-01
> **Bregham_Dalgliesh said:**
> ... I can post a screenshot of its wifi settings later, if that would help?..

Yes that may be helpful. Just blur or obscure the security key and MAC addresses in the screenshots from security's point of view.

A general list of recommended settings is -

- Keep channel fixed to 1 or 11 or any other not-too-crowded channel. Default may be 'auto' which may cause problems sometimes.
- Similarly, try channel bandwidth 20 MHz if it is set to 20/40 mixed mode or 'auto'.
- Sometimes a feature called 'WMM' (usually located under 'QoS' settings) may cause troubles. Try disabling it if your router has it and is set to 'Enabled'.
- If the router supports 2.4/5 GHz dual band, try them separately. 2.4 GHz is usual band and is supported by ALL wireless devices. 5 GHz is relatively newer and some devices/drivers may not support it (be assured that it is supported nicely by the ath9k driver).

Apart from these, the screenshots may give us some more ideas.

---

### Post by Bregham_Dalgliesh on 2014-10-01
[ATTACH=CONFIG]256853[/ATTACH][ATTACH=CONFIG]256854[/ATTACH][ATTACH=CONFIG]256855[/ATTACH][ATTACH=CONFIG]256856[/ATTACH]
As advised, here are the screenshots. Like two days ago, I cannot connect when 3-5 metres from the wifi router, but when I walk towards it there is a connection when about 1-2 metres away, which is then maintained when I return to the other side of the room!

---

### Post by varunendra on 2014-10-01
The only 'usual' suspect is the channel setting. Try changing it to a fixed one, preferably 1 or 11, instead of "Automatic".

If this doesn't help, please solve your package update problem > update the system/kernel and post back if the problem persists after the update.

---

### Post by Bregham_Dalgliesh on 2014-10-04
Hi Varun

This is possibly the last post, although I only have a "pragmatic" solution of simply being physically next to the wifi router to get a connection, but not really a "technical" solution that "fixes" the problem and lets me connect from anywhere within the range of the router!

Anyway, for the record I changed the channel setting from Automatic to a fixed one as you suggested, but whereas before I could connect to the wifi router by being next to it, after the change there was no connection at all, so I've changed it back to Automatic (and can once again connect by approaching the router).

I also updated the system/kernel to "3.14.0-031400-generic" ... not knowing exactly what I was doing, I followed the instructions of this post ([http://ubuntuhandbook.org/index.php/2014/04/installupgrade-to-linux-kernel-3-14-in-ubuntu-or-linux-mint/](http://ubuntuhandbook.org/index.php/2014/04/installupgrade-to-linux-kernel-3-14-in-ubuntu-or-linux-mint/)) and the installation worked, but the wifi problem and its solution as described above persists.

I am not sure where to go from here? If you have any advice or suggestions please let me know.

Many thanks for all your help!

---

### Post by Creatorr on 2015-02-14
[HTML]gh[/HTML]

---

