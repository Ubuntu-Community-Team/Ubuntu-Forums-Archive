---
title: "Realtek RTL8723AE PCIe keeps disconnecting and low signal (Ubuntu 13.10)"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by dipiscingelit on 2013-09-30
I'm having some problems on my toshiba satellite c850 and my wireless card, when i try to connect to a wireless network it takes a lots of time to connect and when it does the connection losts or even can't access the internet.. it's realy anyoing. i've already tryed to install the wireless drivers following [this]("http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized") link but when i do "make" command it just gaves me this error:

```
$ sudo makemake -C /lib/modules/3.8.0-31-generic/build M=/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-3.8.0-31-generic'
  CC [M]  /home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
In file included from /home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:39:0:
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/pci.h:245:15: erro: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: Na função &#8216;_rtl_init_mac80211&#8217;:
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: erro: &#8216;IEEE80211_HW_BEACON_FILTER&#8217; undeclared (first use in this function)
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: nota: each undeclared identifier is reported only once for each function it appears in
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: Na função &#8216;rtl_action_proc&#8217;:
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:870:25: erro: &#8216;RX_FLAG_MACTIME_MPDU&#8217; undeclared (first use in this function)
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: Na função &#8216;rtl_send_smps_action&#8217;:
/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1432:16: erro: &#8216;struct <anónimo>&#8217; has no member named &#8216;sta&#8217;
make[2]: ** [/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Erro 1
make[1]: ** [_module_/home/daniel/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-3.8.0-31-generic'
make: ** [all] Erro 2
```

i've tryed [this]("http://forums.opensuse.org/english/get-technical-help-here/wireless/477285-rtl8723ae-realtek-wirless-driver-hell-3.html#post2494079") solution too and it didn't work neither... i don't know, i don't want to make the problem worse so i found a link to a "Wireless Script" and this is what i've got:

```


*************** info trace ***************


***** uname -a *****


Linux daniel-portatil 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring


***** lspci *****


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
    Kernel driver in use: rtl8723ae
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:fb37]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 062a:6301 Creative Labs Trust Wireless Optical Mouse MI-4150K
Bus 003 Device 003: ID 0930:021d Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 083a:4505 Accton Technology Corp. SMCWUSB-G 802.11bg
Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd 


***** PCMCIA Card Info *****




***** iwconfig *****


wlan1     IEEE 802.11bg  ESSID:"SAPO-ABE0EB7"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=49/100  Signal level=49/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:131   Missed beacon:0


wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Power Management: off
          


***** rfkill *****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  2 rtlwifi,zd1211rw
cfg80211              511019  3 mac80211,rtlwifi,zd1211rw


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan1  [SAPO-ABE0EB7 1] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            zd1211rw
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ThomsonB5CF5B:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 23 WPA WPA2
    ZON-26D0:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    ZON-CB40:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 18 WPA WPA2
    MEO-566D2B:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 6
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    *SAPO-ABE0EB7:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 6


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    ThomsonB5CF5B:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    ZON-CB40:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    MEO-566D2B:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 18 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/100  Signal level=47/100  
                    Encryption key: on
                    ESSID:"SAPO-ABE0EB7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c03a7c5e6
                    Extra: Last beacon: 25652ms ago
                    IE: Unknown: 000C5341504F2D41424530454237
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAA0050F204104A00011010440001021041000100103B0001031047001000000000000000010003DC0B1A0E0EB710210013506972656C6C6920436F72706F726174696F6E1023000B502E44472041313030304710240019302E39392E323562312D50545F54523036395F416E6E65784D1042000D323439303259303036323435391054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706505420010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/100  Signal level=26/100  
                    Encryption key: on
                    ESSID:"ThomsonB5CF5B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ca152959b
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000D54686F6D736F6E423543463542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010D1186E35805457A3B849094ECBBDFAFD1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420010383265626637643335303339653161331054000800060050F20400011011000D54686F6D736F6E205447373834100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=8/100  Signal level=8/100  
                    Encryption key: on
                    ESSID:"ZON-26D0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018e03cc161
                    Extra: Last beacon: 1988ms ago
                    IE: Unknown: 00085A4F4E2D32364430
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32048C98B060
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88068B6FC8F26D8103C000101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A8C0116FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000C127A
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=4/100  Signal level=4/100  
                    Encryption key: on
                    ESSID:"MEO-566D2B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c9f65a18c
                    Extra: Last beacon: 26764ms ago
                    IE: Unknown: 000A4D454F2D353636443242
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/100  Signal level=47/100  
                    Encryption key: on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c0527911a
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706505420010D10
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=16/100  Signal level=16/100  
                    Encryption key: off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c9ea68014
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
          Cell 07 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/100  Signal level=13/100  
                    Encryption key: on
                    ESSID:"ZON-CB40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c9ea6791b
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00085A4F4E2D43423430
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A88000265B01CB481021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key: on
                    ESSID:"ThomsonB5CF5B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ca1757fc5
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D54686F6D736F6E423543463542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD8D0050F204104A0001101044000102103B00010310470010D1186E35805457A3B849094ECBBDFAFD1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383410420010383265626637643335303339653161331054000800060050F20400011011000D54686F6D736F6E205447373834100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180201000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key: on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c053d70a2
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706505420010D10
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key: on
                    ESSID:"MEO-566D2B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003ca109e9e7
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A4D454F2D353636443242
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010AC32E09F69815B29ABC9604B6DAD85001021000754484F4D534F4E1023000A54686F6D736F6E205447102400043738346E10420010353161346639346264613339643031661054000800060050F20400011011000E54686F6D736F6E2054473738346E100800020004103C0001011049000600372A000120
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key: on
                    ESSID:"ZON-CB40"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c9ebb5175
                    Extra: Last beacon: 240ms ago
                    IE: Unknown: 00085A4F4E2D43423430
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A88000265B01CB481021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key: off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c9ebe7ab3
                    Extra: Last beacon: 32ms ago
                    IE: Unknown: 0015464F4E5F5A4F4E5F465245455F494E5445524E4554
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8C0117FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** modinfo *****


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1197043093752E03A00CA5B
alias:          pci:v000010ECd00008723sv*sd*bc*sc*i*
depends:        rtlwifi
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     FA8C819FC50E5EFF6562FED
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.8.0-31-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x083a:0x4505 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


***** dmesg *****


[   18.788926] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   19.062897] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   19.063127] rtlwifi: wireless switch is on
[   22.793270] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.793914] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.038887] wlan0: authenticate with <MAC address removed>
[   58.066897] wlan0: send auth to <MAC address removed> (try 1/3)
[   58.073032] wlan0: authenticated
[   58.073291] rtl8723ae 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   58.073300] rtl8723ae 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   58.073315] rtl8723ae 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   58.077209] wlan0: associate with <MAC address removed> (try 1/3)
[   58.108180] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   58.108337] wlan0: associated
[   58.108354] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.845209] type=1400 audit(1380588123.939:29): apparmor="DENIED" operation="open" parent=1715 profile="/sbin/dhclient" name="/var/lib/NetworkManager/dhclient6-wlan0.conf" pid=3337 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  156.319134] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  170.957871] zd1211rw 1-1.2:1.0: firmware version 4725
[  171.111572] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  171.112393] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  202.152654] wlan1: authenticate with <MAC address removed>
[  202.241712] wlan1: send auth to <MAC address removed> (try 1/3)
[  202.243636] wlan1: authenticated
[  202.243931] zd1211rw 1-1.2:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  202.243936] zd1211rw 1-1.2:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[  202.243940] zd1211rw 1-1.2:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[  202.246892] wlan1: associate with <MAC address removed> (try 1/3)
[  202.274593] wlan1: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  202.274908] wlan1: associated
[  202.274991] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  205.688173] type=1400 audit(1380588268.786:30): apparmor="DENIED" operation="open" parent=1715 profile="/sbin/dhclient" name="/var/lib/NetworkManager/dhclient6-wlan1.conf" pid=3932 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0


****************** done ******************



```

I hope you guys could help me, i would be very appreciated. Thanks in advance ;)

oh, i almost forgot.. i'm using an d-link pen to get connected, so maybe is wlan1 or something..

---

### Post by MIJ-VI on 2013-10-01
A possible solution given that other Realtek WiFi chips and Linux 3.8.x won't work together:

Post #7

[ubuntu] Realtek RTL8192CU Driver issues under 13.04 
[http://ubuntuforums.org/showthread.php?t=2148130](http://ubuntuforums.org/showthread.php?t=2148130)

---

### Post by varunendra on 2013-10-02
Before trying the proprietary driver right away, please try something with the native driver first.
> **broas000 said:**
> ```

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz ([COLOR="#FF0000"]Channel 6[/COLOR])
                    ....
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]

```
Please try changing the channel to 1 or 11, as well as encryption type to WPA2-PSK with AES (no TKIP !) in the router. After saving the settings, reboot the router to be sure that the settings take effect.

With the above changes (or without them, if it's a problem), please try the following with the driver in Ubuntu -
```
sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae swenc=1 ips=0 fwlps=0
```
See if this helps improving the connectivity. If not ONLY THEN try the proprietary driver with some patching as suggested in [post=12770984]this post[/post] , and let us know the result.

---

### Post by jerico.dev on 2013-10-19
> **varunendra said:**
> 
```
sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae swenc=1 ips=0 fwlps=0
```


Got the same chipset and the same problem. This didn't help in my case.

---

### Post by varunendra on 2013-10-19
> **jerico.dev said:**
> Got the same chipset and the same problem. This didn't help in my case.

I'd suggest to post your case in a different thread with a detailed description of your problem, solutions you have tried so far, and the report generated by wireless_script (follow the link in my signature below).

Feel free to post a link to it here so we can follow.

---

