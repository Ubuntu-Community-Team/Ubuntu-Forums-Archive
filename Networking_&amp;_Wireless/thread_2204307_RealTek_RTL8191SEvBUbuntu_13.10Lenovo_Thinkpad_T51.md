---
title: "RealTek RTL8191SEvB/Ubuntu 13.10/Lenovo Thinkpad T510i Poor Wireless Performance"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by M3ta7h3ad on 2014-02-07
I'm experiencing very poor wireless performance. Downloads slow to a crawl/0k/s speeds and while the connection doesn't appear to drop, it does slow to a point where browsing the web simply results in page timeouts.

Browsing the local network also results in the same thing, with the wireless routers page being just as difficult to get to.

Meanwhile, phones and ipads connect just fine to the internet.

Reading that my driver in question had some issues with N back on 12.* I have also made my router force G only connectivity rather than bgn.

I am situated smack next door to the router with the network on a channel which is not occupied by neighbouring stations. Signal strength is great but I do get a hell of a lot of "Invalid Misc" errors showing up in iwconfig. Just doing a watch on it shows it increasing by approximately 80 - 100 packets within the 2 second time it takes watch to refresh.

In terms of speed hit, when the web is "browsable" speeds are approximately 30 to 70KB/s in comparison to my phone which just did a speedtest and got 1.7MB/s down.

Would appreciate any help you can give, i've read through the sticky here so the information requested in that sticky is located below and I have searched all evening for solutions but have had no success.

Details as per the sticky "HOWTO post a Wireless Issue".

```

Lenovo Thinkpad T510i

Ubuntu Version:
root@ubunut:~# lsb_release -d
Description:	Ubuntu 13.10

Kernel Architecture:
root@ubunut:~# uname -mr
3.11.0-15-generic x86_64

```
lspci:
```

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

```
ifconfig:
```

wlan0     Link encap:Ethernet  HWaddr 50:63:13:cb:f0:90  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5263:13ff:fecb:f090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100515753 (100.5 MB)  TX bytes:3304951 (3.3 MB)

```
iwconfig:
```

root@ubunut:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Aircrack-ngFTW"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: A0:F3:C1:73:4D:6A   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4366   Missed beacon:0

```
lsmod:
```

root@ubunut:~# lsmod | grep -i rtl
rtl8192se              63196  0 
rtl_pci                26641  1 rtl8192se
rtlwifi                63229  2 rtl_pci,rtl8192se
mac80211              597268  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              480503  2 mac80211,rtlwifi

```
dmesg:
```

root@ubunut:~# dmesg | grep -i rtl
[   31.931988] rtl8192se: FW Power Save off (module option)
[   31.932038] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   31.932038] Loading firmware rtlwifi/rtl8192sefw.bin
[   32.313167] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[16227.632029] rtl8192se: FW Power Save off (module option)
[16227.632083] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[16227.632083] Loading firmware rtlwifi/rtl8192sefw.bin
[16227.685957] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'

```
lshw:
```

root@ubunut:~# lshw -C network
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 50:63:13:cb:f0:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.11.0-15-generic firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f2400000-f2403fff

```
iwlist scan:
```

root@ubunut:~# iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: A0:F3:C1:73:4D:6A
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Aircrack-ngFTW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000470e7786
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 000E416972637261636B2D6E67465457
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 02 - Address: 28:10:7B:F5:FC:FE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:on
                    ESSID:"WEBBY-WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00001308ef433ae6
                    Extra: Last beacon: 136ms ago
                    IE: Unknown: 000A57454242592D57494649
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001086B0E5038B1132816BA928107BF5FCFF10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 03 - Address: C0:3F:0E:D4:F9:DA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:on
                    ESSID:"TurboVacXL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b4e713359a
                    Extra: Last beacon: 2436ms ago
                    IE: Unknown: 000A547572626F566163584C
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16060F1600000000000000000000000000000000000000
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B00010310470010AF4C39CE45CB8908DC5ED8A4B05534D51021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F1600000000000000000000000000000000000000
          Cell 04 - Address: 00:01:E3:EF:08:38
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:on
                    ESSID:"OrangeEF0836"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003a96b1230
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000C4F72616E6765454630383336
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

```

---

### Post by praseodym on 2014-02-08
Change the encryption mode to WPA2-AES (CCMP), check the router manual.

Checked a driver update?
```

sudo apt-get install git linux-headers-generic build-essential
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
```
Reboot.

---

### Post by M3ta7h3ad on 2014-02-08
already is WPA2-AES (note the essid... im a pentester in my day job :)). Is there something that suggests otherwise?

Thanks for the commands to check drivers will give it a go and report back.

---

### Post by praseodym on 2014-02-08
It looks like a weired mixed mode WPA/WPA2:
```

                    IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1
                        Group Cipher : [COLOR="#FF0000"]CCMP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="#FF0000"]CCMP[/COLOR]
                        Authentication Suites (1) : PSK
```
Deactivate WPA as fallback mode and/or check the router settings.

---

### Post by M3ta7h3ad on 2014-02-08
[COLOR="#D3D3D3"]yeah thats a limitation in my router unfortunately. Only WPA/WPA2 available, can't hard set it to WPA2. Given the devices connected to my network are hard set to WPA2 however it shouldn't be an issue.[/COLOR] - Updated router firmware, new option. Sorted the WPA/WPA2 mixed mode issue now.

Anyway, driver installation instructions followed. Invalid Miscs are ramping up as per usual and same problem as before.

---

### Post by praseodym on 2014-02-08
Lets check now:
```

iwconfig
ifconfig -a
iwlist chan
sudo iwlist scan
lsmod
cat /etc/resolv.conf
```
Maybe you try Wicd instead of the NWM:
```

sudo apt-get install wicd
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose there **wlan0** as interface name and **wext** as driver

---

### Post by M3ta7h3ad on 2014-02-08
Haven't tried Wicd just yet but will give it a bash if you think it'll help.

latest output as follows:

IWCONFIG:
```

wlan0     IEEE 802.11bgn  ESSID:"Aircrack-ngFTW"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: A0:F3:C1:73:4D:6A   
          Bit Rate=18 Mb/s   Tx-Power=33 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26153   Missed beacon:0


```
IFCONFIG:
```

eth0      Link encap:Ethernet  HWaddr 00:26:2d:fc:6d:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1171395 (1.1 MB)  TX bytes:1171395 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 50:63:13:cb:f0:90  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5263:13ff:fecb:f090/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1265088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1870168002 (1.8 GB)  TX bytes:42647962 (42.6 MB)


```
IWLIST CHAN:
```

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.422 GHz (Channel 3)


```
IWLIST SCAN:
```

wlan0     Scan completed :
          Cell 01 - Address: A0:F3:C1:73:4D:6A
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Aircrack-ngFTW"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000dc2b638e
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000E416972637261636B2D6E67465457
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 02 - Address: 28:10:7B:F5:FC:FE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"WEBBY-WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000013164174e366
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000A57454242592D57494649
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000014127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001086B0E5038B1132816BA928107BF5FCFF10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086
          Cell 03 - Address: 00:01:E3:EF:08:38
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"OrangeEF0836"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f28a10a9
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000C4F72616E6765454630383336
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: CC:33:BB:6E:99:D0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"BTHub4-8FWZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bce28e207
                    Extra: Last beacon: 768ms ago
                    IE: Unknown: 000B4254487562342D3846575A
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706474220010D12
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010BEF4543683D65A97A34AAD923E400482103C000101
          Cell 05 - Address: CC:33:BB:6E:99:D3
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007bce2917a2
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000F4254576966692D776974682D464F4E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0706474220010D12
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C001EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD050009860100


```
LSMOD:
```

Module                  Size  Used by
btrfs                 826233  0 
raid6_pq               97812  1 btrfs
zlib_deflate           26914  1 btrfs
xor                    21411  1 btrfs
ufs                    74892  0 
qnx4                   13317  0 
hfsplus               102763  0 
hfs                    54677  0 
minix                  36140  0 
ntfs                   97369  0 
msdos                  17332  0 
jfs                   181201  0 
xfs                   884515  0 
libcrc32c              12644  2 xfs,btrfs
reiserfs              246744  0 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               320455  3 vboxnetadp,vboxnetflt,vboxpci
dm_crypt               22832  1 
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rfcomm                 69130  0 
bluetooth             372041  10 bnep,rfcomm
binfmt_misc            17468  1 
ext2                   72949  1 
joydev                 17377  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
ip6t_REJECT            12939  1 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18938  7 
nf_defrag_ipv6         34645  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17718  10 
xt_limit               12711  13 
xt_tcpudp              12884  18 
xt_addrtype            12635  4 
nf_conntrack_ipv4      15012  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_conntrack           12760  14 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12770  0 
nf_nat                 26711  1 nf_nat_ftp
nf_conntrack_ftp       18638  1 nf_nat_ftp
nf_conntrack           91940  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27239  1 iptable_filter
x_tables               34059  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
arc4                   12608  2 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_conexant    56990  1 
rtl8192se              94062  0 
rtlwifi               110108  1 rtl8192se
microcode              23576  0 
psmouse                97655  0 
serio_raw              13413  0 
intel_ips              18470  0 
mac80211              597268  2 rtlwifi,rtl8192se
thinkpad_acpi          80730  0 
lpc_ich                21080  0 
nvram                  14362  1 thinkpad_acpi
cfg80211              480503  2 mac80211,rtlwifi
firewire_ohci          40327  0 
snd_seq_midi           13324  0 
snd_hda_intel          48171  3 
firewire_core          64534  1 firewire_ohci
e1000e                254604  0 
snd_seq_midi_event     14899  1 snd_seq_midi
crc_itu_t              12707  1 firewire_core
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_rawmidi            30095  1 snd_seq_midi
sdhci_pci              19014  0 
sdhci                  42898  1 sdhci_pci
snd_hwdep              13602  1 snd_hda_codec
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ptp                    18580  1 e1000e
pps_core               19057  1 ptp
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  2 snd_pcm,snd_seq
mei_me                 18421  0 
mei                    77782  1 mei_me
snd                    69141  18 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
tpm_tis                19123  0 
mac_hid                13205  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
mxm_wmi                13021  0 
i915                  661261  9 
i2c_algo_bit           13413  1 i915
drm_kms_helper         52710  1 i915
drm                   297056  5 i915,drm_kms_helper
wmi                    19070  1 mxm_wmi
video                  19318  1 i915

```
RESOLV.CONF
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```

---

### Post by praseodym on 2014-02-08
```
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
Looks better now. Deactivate IPv6 in the NM applet ("Ignore") and reconnect. Did you activate the package filter (aka "firewall")? Deactivation via:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by M3ta7h3ad on 2014-02-08
yeah firewall is configured as my laptop travels somewhat.

didn't realise ufw and gufw shoved a crapton of "invisible" rules in there. Dumped the two and just have iptables running on start up now with: 

```

richard@ubunut:~$ sudo iptables -t filter -n -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2066  177K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 369K  548M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
   15   971 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 83435 packets, 5144K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

in it.

That said I don't believe that was the issue as im still bombing out when downloading large files (thats when the problem is most evident)

---

### Post by praseodym on 2014-02-08
Check the Google-public-nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by M3ta7h3ad on 2014-02-08
actually may have solved it. Still getting increasing counts of invalid misc.

Switched router to N only. Now speedtest is giving me decent results.

[[IMG]http://www.speedtest.net/result/3291887255.png[/IMG]](http://www.speedtest.net/my-result/3291887255)

Will keep an eye on it over the next few days (normally when im doing an apt-get dist-upgrade is the worst) and report back if its solved or not.

Thanks for the help, no idea what may have solved it in the end. Could be the driver, could have been the router firmware, the WPA/WPA2 mixed mode setting or the G/N thing.

Won't consider it solved though at least until I do a few more downloads and checks with it.

---

### Post by M3ta7h3ad on 2014-02-19
This appears to now be fixed. No idea what of the above fixed it but I certainly have improved wireless performance.

Thank you to everyone involved.

---

### Post by mac1929 on 2015-02-05
Same problem with Ubuntu 14.04 LTS, 14.10 and Linux Mint 17.1

Finally I spent 8 euros at ebay to get an intel Wireless Card and now my T410 works perfectly.

---

