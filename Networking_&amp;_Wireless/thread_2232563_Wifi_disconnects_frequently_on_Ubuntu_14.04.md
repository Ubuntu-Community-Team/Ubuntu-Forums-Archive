---
title: "Wifi disconnects frequently on Ubuntu 14.04"
date: 2014-07-02
forum: Networking &amp; Wireless
---

### Post by iPhantom on 2014-07-02
I've tried applying the commands such as 

```
[COLOR=#666666][FONT=Consolas]sudo sh -c 'echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf'[/FONT][/COLOR]
```

but no good.

Here's my syslog from boot to the first diconnect:

[http://pastie.org/private/hmwlrbm1aijlskf4rsamzq]("http://pastie.org/private/scyuvzaxmcrsxgzvhdtqtw")

Edit: I use a TP-Link wireless dongle but I didn't have such problems with 12.02. This was a clean install into 14.04 as well.

---

### Post by varunendra on 2014-07-06
If you are still having the problem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by iPhantom on 2014-07-24
> **varunendra said:**
> If you are still having the problem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

Sorry for being so late but here it is:

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


glend-ubuntu-home 3.13.0-32-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i3-4130 CPU @ 3.40GHz
Memory : 7924 MB
Uptime : 04:16:17 up 10 min,  3 users,  load average: 0,56, 0,58, 0,35




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
	Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 003 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 002: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Tring-Wireless-03283"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC C-01 Tring-Wireless-03283>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:133   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
ath9k_htc              95963  0 
ath9k_common           13551  1 ath9k_htc
ath9k_hw              453856  2 ath9k_common,ath9k_htc
ath                    28698  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              630653  1 ath9k_htc
cfg80211              484040  3 ath,mac80211,ath9k_htc
video                  19476  1 asus_wmi
wmi                    19177  1 asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


ath9k_htc     (3): btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
===============================o=============o====  =======o=============o=========o===========o======  ========o===========
 Interface & ID                | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
===============================o=============o====  =======o=============o=========o===========o======  ========o===========
 eth0                          | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
-------------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [Tring-Wireless-03283] | 802.11 WiFi | ath9k_htc | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    *Tring-Wireless-03283: Infra, <MAC C-01 Tring-Wireless-03283>, Freq 2427 MHz, Rate 54 Mb/s, Strength 59 WPA
    Gena:            Infra, <MAC C-02 Gena>, Freq 2427 MHz, Rate 54 Mb/s, Strength 22 WPA
    Tring-01578:     Infra, <MAC C-NA Tring-01578 1>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA
    lata:            Infra, <MAC C-04 lata>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    Topnet 4:        Infra, <MAC C-06 Topnet 4>, Freq 2462 MHz, Rate 11 Mb/s, Strength 20
    Neli:            Infra, <MAC C-05 Neli>, Freq 2457 MHz, Rate 54 Mb/s, Strength 14 WPA
    DRITAN _SHEHU:   Infra, <MAC C-03 DRITAN _SHEHU>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2


    Address:         192.168.1.59
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
-------------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


Tring-Wireless-03283 : ssid=Tring-Wireless-03283 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search lan




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.796/2.063/2.331/0.271 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.035/0.035/0.036/0.006 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : sq_AL.UTF-8)
country GR:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.427 GHz (Channel 4)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Tring-Wireless-03283>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Tring-Wireless-03283"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003271ebd80c
                    Extra: Last beacon: 168ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Gena>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Gena"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e730ad3d8
                    Extra: Last beacon: 208ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 DRITAN _SHEHU>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"DRITAN _SHEHU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003275ebcf89
                    Extra: Last beacon: 6468ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 lata>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"lata"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003275b31076
                    Extra: Last beacon: 6480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Neli>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Neli"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000326e8111e9
                    Extra: Last beacon: 1616ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Topnet 4>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Topnet 4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000009c9a3c181
                    Extra: Last beacon: 1128ms ago




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[eeepc_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/eeepc-wmi.ko
srcversion:     B54CE86332FC282F9684B45
depends:        asus-wmi
parm:           hotplug_wireless:Enable hotplug for wireless device. If your laptop needs that, please report to acpi4asus-user@lists.sourceforge.net. (bool)


[asus_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[ath9k_htc]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
srcversion:     76D0CC269ACAA11EA825B93
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (ath9k_htc)
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
                    options iwlwifi 11n_disable=1
                    options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=98a959c9-8c16-4ec0-9a42-71821172e17b ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.395745] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.395933] audit: initializing netlink socket (disabled)
[    0.515425] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   13.584245] wmi: Mapper loaded
[   13.651701] usb 3-7: ath9k_htc: Firmware htc_9271.fw requested
[   13.651750] usbcore: registered new interface driver ath9k_htc
[   13.724699] asus_wmi: ASUS WMI generic driver loaded
[   13.725790] asus_wmi: Initialization: 0x0
[   13.725802] asus_wmi: BIOS WMI version: 0.9
[   13.725822] asus_wmi: SFUN value: 0x0
[   13.725995] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input12
[   13.732715] asus_wmi: Disabling ACPI video driver
[   14.154651] usb 3-7: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   14.392172] ath9k_htc 3-7:1.0: ath9k_htc: HTC initialized with 33 credits
[   14.658909] ath9k_htc 3-7:1.0: ath9k_htc: FW Version: 1.3
[   14.658911] ath: EEPROM regdomain: 0x809c
[   14.658912] ath: EEPROM indicates we should expect a country code
[   14.658912] ath: doing EEPROM country->regdmn map search
[   14.658913] ath: country maps to regdmn code: 0x52
[   14.658914] ath: Country alpha2 being used: CN
[   14.658914] ath: Regpair used: 0x52
[   15.861370] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.718795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.718974] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.295069] wlan0: authenticate with <MAC C-01 Tring-Wireless-03283>
[   18.706130] wlan0: send auth to <MAC C-01 Tring-Wireless-03283> (try 1/3)
[   18.708376] wlan0: authenticated
[   18.708456] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[   18.708459] ath9k_htc 3-7:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   18.712309] wlan0: associate with <MAC C-01 Tring-Wireless-03283> (try 1/3)
[   18.716300] wlan0: RX AssocResp from <MAC C-01 Tring-Wireless-03283> (capab=0x431 status=0 aid=13)
[   18.725867] wlan0: associated
[   18.725874] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


	======== Done ========

```

---

### Post by praseodym on 2014-07-25
You are using an Atheros stick with the same driver like me:
```

sudo rm /etc/modprobe.d/iwlwifi.conf
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```
Replug the stick and change to WPA2 encryption instead of WPA.

---

### Post by varunendra on 2014-07-25
There are many things that can be and should be optimized to improve the connectivity.

Starting from what praseodym already suggested - create the conf file with the commands he provided, and change the encryption type _in your router_ to WPA2-PSK with AES (CCMP). The current encryption type WPA(1) uses TKIP which can have adverse effect on speed and connection quality.

Apart from that, again in the router itself, please try changing the channel from 4 (or 'auto') to channel 1 or 11. They usually offer better signal quality.

Also look for a feature called "WMM" - usually it is located under 'QoS' settings. Is it enabled? If yes, make sure to disable it. It seems the driver is not liking its settings. Reboot the router after saving any changes.

There should also be a setting regarding channel bandwidth (20 MHz vs 20/40 MHz auto mode). Some drivers work better with 20 MHz fixed mode (against 20/40 MHz auto mode), but try the above changes first. Play with this setting only if the above ones don't seem to help.

One more thing to confirm in the router - does it have the option to change the country/regional settings? If yes, or even if it only 'shows' its current country setting (some routers don't let you change that) - is it set to the country in which you are in?

Which country you are in by the way? It seems your wireless card was originally manufactured for China (hence by default it tries to apply Chinese regdomain settings, thanks to the external mechanism that forces it to the regional settings defined by you/the router). And then your language settings are for Albania, while the selected RegDomain settings for the wifi are for Greece. While the wifi stack is designed to tolerate this kind of confusion to some extent, it may be one of the reasons for unstable connection. So we better make sure the RegDomain setting is the same as on your Router.

---

### Post by iPhantom on 2014-07-28
I will try the above and report back, thank you. One thing to consider, I just bought a new HP laptop and installed Ubuntu 14.04 on it and I got the same problem, it must be like you say about the router creating a confusion.

I used these commands from another thread you answered (for the new laptop). Seems to be working so far.

```

sudo modprobe -r iwldvm #otherwise iwlwifi refuses to stop
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
sudo modprobe iwldvm

```

---

### Post by praseodym on 2014-07-29
You can make it permanent via:

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by iPhantom on 2014-07-30
I did the above however at work my laptop wireless is working poorly and sometimes disconnect and asks for password even though I had saved it before. I ran the wireless script here, please take a look:

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


glend-HP-15-Notebook-PC 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Pentium(R) CPU  N3530  @ 2.16GHz
Memory : 7873 MB
Uptime : 17:16:21 up 38 min,  2 users,  load average: 0,68, 0,85, 0,85




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:2213]
	Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b40e Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 18d1:4ee1 Google Inc. Nexus 4
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Aledia"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Aledia>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-4 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rtl8188ee              89677  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              630653  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 hp_wmi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8188ee     (6): debug=0 | fwlps=Y | ips=Y | msi=N | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=================o=============o===========o=============o=========o===========o==============o===========
 eth0            | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [Aledia] | 802.11 WiFi | rtl8188ee | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    NETGEAR:         Infra, <MAC C-04 NETGEAR>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
    Qelbanx:         Infra, <MAC C-05 Qelbanx>, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    Thom_D006620:    Infra, <MAC C-07 Thom_D006620>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Topnet 3:        Infra, <MAC C-03 Topnet 3>, Freq 2437 MHz, Rate 11 Mb/s, Strength 84
    *Aledia:         Infra, <MAC C-01 Aledia>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    ArchEB_Studio:   Infra, <MAC C-NA ArchEB_Studio 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    DION:            Infra, <MAC C-NA DION 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Anjeza Gjuzi:    Infra, <MAC C-NA Anjeza Gjuzi 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    AndroidAP:       Infra, <MAC C-02 AndroidAP>, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA2
    MULTISERVICE-Tirana: Infra, <MAC C-NA MULTISERVICE-Tirana 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2
    Kush Te Vuri Kujdestar: Infra, <MAC C-NA Kush Te Vuri Kujdestar 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
    ZTE:             Infra, <MAC C-NA ZTE 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA
    Topnet 4:        Infra, <MAC C-NA Topnet 4 2>, Freq 2462 MHz, Rate 11 Mb/s, Strength 80


    Address:         192.168.10.245
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1
    DNS:             192.168.10.1
-----------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


Aledia               : ssid=Aledia | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Tring-Wireless-03283 : ssid=Tring-Wireless-03283 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
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
rtt min/avg/max/mdev = 3.326/6.495/9.664/3.169 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.066/0.080/0.095/0.017 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : sq_AL.UTF-8)
country AL:
	(2402 - 2482 @ 20), (N/A, 20)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Aledia>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=8 dBm  
                    Encryption key:on
                    ESSID:"Aledia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f3f8ac43
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 AndroidAP>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"AndroidAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000bcb7324
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Topnet 3>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"Topnet 3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000005c571181
                    Extra: Last beacon: 2992ms ago
          Cell 04 - Address: <MAC C-04 NETGEAR>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a1391e181
                    Extra: Last beacon: 232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Qelbanx>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Qelbanx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006f796700a
                    Extra: Last beacon: 1952ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 SitecomA8C910>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"SitecomA8C910"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001904adab
                    Extra: Last beacon: 520ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 Thom_D006620>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Thom_D006620"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ee7bf9ad0
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[hp_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap


[rtl8188ee]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
srcversion:     FA356D8EFD887B567263405
depends:        rtlwifi,rtl_pci,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=743e1a2c-43f7-4f0f-95a5-4281766f9429 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.640317] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.640840] audit: initializing netlink socket (disabled)
[    1.875328] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.171744] wmi: Mapper loaded
[   11.288049] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   11.447752] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.448084] rtlwifi: wireless switch is on
[   17.089294] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.353557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.354005] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.085878] wlan0: authenticate with <MAC C-01 Aledia>
[   21.105381] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[   21.118386] wlan0: authenticated
[   21.121214] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[   21.134854] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[   21.134967] wlan0: associated
[   21.134982] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.964450] wlan0: deauthenticating from <MAC C-01 Aledia> by local choice (reason=2)
[   21.996016] wlan0: authenticate with <MAC C-01 Aledia>
[   22.006132] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[   22.008775] wlan0: authenticated
[   22.009975] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[   22.018597] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[   22.018709] wlan0: associated
[  306.212291] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  307.575186] wlan0: authenticate with <MAC C-01 Aledia>
[  307.594482] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  307.696621] wlan0: authenticated
[  307.698012] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  307.764871] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  307.765035] wlan0: associated
[  360.888372] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  362.263308] wlan0: authenticate with <MAC C-01 Aledia>
[  362.282834] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  362.299431] wlan0: authenticated
[  362.302526] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  362.332547] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  362.332707] wlan0: associated
[  598.089455] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  599.459538] wlan0: authenticate with <MAC C-01 Aledia>
[  599.472281] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  599.476310] wlan0: authenticated
[  599.479258] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  599.486550] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  599.486699] wlan0: associated
[  612.657294] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  614.017887] wlan0: authenticate with <MAC C-01 Aledia>
[  614.035866] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  614.105847] wlan0: authenticated
[  614.107081] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  614.110554] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  614.110726] wlan0: associated
[  761.598424] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  762.973286] wlan0: authenticate with <MAC C-01 Aledia>
[  762.990222] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  763.013139] wlan0: authenticated
[  763.016234] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  763.020906] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  763.021023] wlan0: associated
[  769.397720] wlan0: deauthenticated from <MAC C-01 Aledia> (Reason: 15)
[  770.739481] wlan0: authenticate with <MAC C-01 Aledia>
[  770.758860] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  770.762615] wlan0: authenticated
[  770.766435] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  770.771007] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  770.771149] wlan0: associated
[  795.974287] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  797.334018] wlan0: authenticate with <MAC C-01 Aledia>
[  797.348557] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  797.349756] wlan0: authenticated
[  797.352011] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  797.354100] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  797.354231] wlan0: associated
[  800.633512] wlan0: deauthenticated from <MAC C-01 Aledia> (Reason: 15)
[  806.182175] wlan0: authenticate with <MAC C-01 Aledia>
[  806.199703] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  806.200953] wlan0: authenticated
[  806.203200] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  806.208446] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  806.208596] wlan0: associated
[  857.488094] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  858.838777] wlan0: authenticate with <MAC C-01 Aledia>
[  858.858488] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  858.859801] wlan0: authenticated
[  858.862062] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  858.864895] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  858.865083] wlan0: associated
[  896.107472] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  897.478961] wlan0: authenticate with <MAC C-01 Aledia>
[  897.497757] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  897.508654] wlan0: authenticated
[  897.509428] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  897.519123] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=11)
[  897.519277] wlan0: associated
[  946.781611] wlan0: Connection to AP <MAC C-01 Aledia> lost
[  948.157632] wlan0: authenticate with <MAC C-01 Aledia>
[  948.175242] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[  948.196758] wlan0: authenticated
[  948.198638] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[  948.215065] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[  948.215191] wlan0: associated
[  999.467641] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1000.827897] wlan0: authenticate with <MAC C-01 Aledia>
[ 1000.845828] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1000.848907] wlan0: authenticated
[ 1000.853428] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1000.856342] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1000.856470] wlan0: associated
[ 1034.087656] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1035.455969] wlan0: authenticate with <MAC C-01 Aledia>
[ 1035.470235] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1035.474312] wlan0: authenticated
[ 1035.478226] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1035.484775] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1035.484916] wlan0: associated
[ 1044.644130] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1046.020836] wlan0: authenticate with <MAC C-01 Aledia>
[ 1046.031023] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1046.048748] wlan0: authenticated
[ 1046.050162] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1046.059522] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1046.059710] wlan0: associated
[ 1125.402019] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1126.764822] wlan0: authenticate with <MAC C-01 Aledia>
[ 1126.784136] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1126.853687] wlan0: authenticated
[ 1126.856068] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1126.859213] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1126.859394] wlan0: associated
[ 1133.144264] wlan0: deauthenticated from <MAC C-01 Aledia> (Reason: 15)
[ 1134.479658] wlan0: authenticate with <MAC C-01 Aledia>
[ 1134.498763] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1134.509165] wlan0: authenticated
[ 1134.510138] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1134.516169] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1134.516293] wlan0: associated
[ 1155.706819] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1157.072226] wlan0: authenticate with <MAC C-01 Aledia>
[ 1157.089007] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1157.192614] wlan0: send auth to <MAC C-01 Aledia> (try 2/3)
[ 1157.296735] wlan0: send auth to <MAC C-01 Aledia> (try 3/3)
[ 1157.363327] wlan0: authenticated
[ 1157.364879] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1157.369123] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1157.369325] wlan0: associated
[ 1163.700098] wlan0: deauthenticated from <MAC C-01 Aledia> (Reason: 15)
[ 1165.042378] wlan0: authenticate with <MAC C-01 Aledia>
[ 1165.059699] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1165.163116] wlan0: send auth to <MAC C-01 Aledia> (try 2/3)
[ 1165.193803] wlan0: authenticated
[ 1165.195094] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1165.296089] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1165.296271] wlan0: associated
[ 1168.789104] wlan0: deauthenticated from <MAC C-01 Aledia> (Reason: 15)
[ 1177.611898] wlan0: authenticate with <MAC C-01 Aledia>
[ 1177.622124] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1177.627467] wlan0: authenticated
[ 1177.629122] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1177.631789] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1177.631907] wlan0: associated
[ 1184.786449] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1186.142835] wlan0: authenticate with <MAC C-01 Aledia>
[ 1186.153095] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1186.215801] wlan0: authenticated
[ 1186.220285] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1186.222656] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1186.222835] wlan0: associated
[ 1193.325122] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1194.690294] wlan0: authenticate with <MAC C-01 Aledia>
[ 1194.708612] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1194.798362] wlan0: authenticated
[ 1194.803487] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1194.821751] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1194.821943] wlan0: associated
[ 1252.016793] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1253.382109] wlan0: authenticate with <MAC C-01 Aledia>
[ 1253.399241] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1253.410607] wlan0: authenticated
[ 1253.418792] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1253.435477] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1253.435650] wlan0: associated
[ 1300.680775] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1302.047283] wlan0: authenticate with <MAC C-01 Aledia>
[ 1302.063012] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1302.067611] wlan0: authenticated
[ 1302.070443] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1302.079563] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1302.079725] wlan0: associated
[ 1319.259500] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1320.600686] wlan0: authenticate with <MAC C-01 Aledia>
[ 1320.618051] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1320.721745] wlan0: send auth to <MAC C-01 Aledia> (try 2/3)
[ 1320.752104] wlan0: authenticated
[ 1320.753502] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1320.761660] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1320.761860] wlan0: associated
[ 1324.083582] wlan0: deauthenticated from <MAC C-01 Aledia> (Reason: 15)
[ 1330.687488] wlan0: authenticate with <MAC C-01 Aledia>
[ 1330.706025] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1330.710443] wlan0: authenticated
[ 1330.713526] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1330.715662] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=10)
[ 1330.715819] wlan0: associated
[ 1572.533373] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 1573.899473] wlan0: authenticate with <MAC C-01 Aledia>
[ 1573.917398] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 1573.920986] wlan0: authenticated
[ 1573.927225] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 1573.930688] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=3)
[ 1573.930828] wlan0: associated
[ 2186.788847] wlan0: Connection to AP <MAC C-01 Aledia> lost
[ 2188.158904] wlan0: authenticate with <MAC C-01 Aledia>
[ 2188.174777] wlan0: send auth to <MAC C-01 Aledia> (try 1/3)
[ 2188.180598] wlan0: authenticated
[ 2188.182564] wlan0: associate with <MAC C-01 Aledia> (try 1/3)
[ 2188.198121] wlan0: RX AssocResp from <MAC C-01 Aledia> (capab=0xc11 status=0 aid=3)
[ 2188.198245] wlan0: associated


	======== Done ========

```

---

### Post by praseodym on 2014-07-30
Try pure WPA2-AES (CCMP) enctryption instead of mixed mode WPA/WPA2. Check thr router manual

---

### Post by varunendra on 2014-07-31
How many laptops do you want to troubleshoot in a single thread? They only confuse the problem and the helpers (at least a small head like me).

Different hardware = different problem = different thread, no matter how similar the symptoms are, even with everything else (on the network) being the same.

Just a humble advice. :)

---

