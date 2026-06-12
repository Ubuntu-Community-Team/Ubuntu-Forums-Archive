---
title: "Sony Vaio with Intel PRO/wireless 4956 AG keeps dropping network"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by 2 legit 2 quit on 2013-10-22
My Sony Viao keeps dropping wireless network. I have tried a lot of the solutions posted on this forum, but I usually get temporary network before it starts dropping again. 

I have run the commands from the "How to  post a wireless question" and here are the results:

SONY VIAO VGN-FZ345D


 06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)i


eth0      Link encap:Ethernet  HWaddr 00:1a:80:4b:50:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:608053 (608.0 KB)  TX bytes:608053 (608.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:47:0f:c3  
          inet addr:192.168.2.12  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe47:fc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24823321 (24.8 MB)  TX bytes:7377348 (7.3 MB)


iwl4965               117406  0 


[   12.703066] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   12.703070] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   12.703170] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.703207] iwl4965 0000:06:00.0: setting latency timer to 64
[   12.703270] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   12.746209] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   12.746227] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.746359] iwl4965 0000:06:00.0: irq 47 for MSI/MSI-X
[   14.118764] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[   65.983753] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 2
[   71.745490] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 1
[   77.045130] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = 2c:39:96:46:7f:ca tid = 0
[  212.583749] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 7
[  222.598616] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 0
[  278.407847] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 1
[  285.968637] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 10
[  321.340112] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = 2c:39:96:46:7f:ca tid = 0
[ 2673.148803] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 8
[ 2677.648048] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = 2c:39:96:46:7f:ca tid = 0
[ 5002.930580] iwl4965 0000:06:00.0: Aggregation not enabled for tid 6 because load = 2
[12599.828160] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = 2c:39:96:46:7f:ca tid = 6


*-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:47:0f:c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-55-generic-pae firmware=228.61.2.24 ip=192.168.2.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:fa000000-fa001fff
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 16
       serial: 00:1a:80:4b:50:3b
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fc200000-fc203fff ioport:5000(size=256)


Description:    Ubuntu 12.04.3 LTS


3.2.0-55-generic-pae i686


stop: Unknown instance: 
networking stop/waiting

---

### Post by learst on 2013-10-23
I starting to think one of the updates a few weeks ago caused this. I'm having a similar issue to yours a few weeks ago. The only solution I can find is to disconnect and reconnect,which gets really annoying.

---

### Post by varunendra on 2013-10-24
First of all, Welcome to the forums ! :)

The card you have -
> **2 legit 2 quit said:**
>  06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)i
..is a legacy one and uses the same legacy type driver. Its working smoothly is 'usually' a matter of hit and miss.

Anyway, as a temporary test, please try this -
```
sudo modprobe -rv iwl4965
sudo modprobe -v iwl_legacy bt_coex_active=N
sudo modprobe -v iwl4965
```
Then start using wifi and see if it helps stabilizing the connection. This is a temporary change that will be lost at next boot, so don't reboot after running the command. If it helps, we'll make it permanent.

However, if it doesn't, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

@ learst
Are you sure your card is also the same? (Intel Corporation PRO/Wireless 4965 AG)
If it is a different card, post your problem in a different thread and give me its link. If it is indeed the same one, please try what I suggested above.

---

### Post by 2 legit 2 quit on 2013-10-31
Thanks for responding. I did not check for responses over the last few days till today. I have tried the temporary fix. I will let you know if it works for me, so you can help me with making it permanent as you said. Thanks for the advice on how to post outputs!

---

### Post by tgalati4 on 2013-10-31
I would also check for loose antenna connections.  Open the bottom door and see if the wireless card is accessable.  Try reseating the card and the antenna connections.

Also, install *wifi-radar* and check how many wireless routers are near you.  If you have 4 or 5, moderate strength transmitters near you, you will be dropping connections like it's Hammer Time.

---

### Post by 2 legit 2 quit on 2013-11-11
I am still having problems with wifi. I used the script varunendra recommended and this is the output:

```


*************** info trace ***************

***** uname -a *****

Linux ron-VGN-FZ345D 3.2.0-56-generic-pae #86-Ubuntu SMP Wed Oct 23 17:51:27 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
    Kernel driver in use: iwl4965
--
08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 16)
    Subsystem: Sony Corporation Device [104d:9005]
    Kernel driver in use: sky2

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 007 Device 024: ID 044e:3011 Alps Electric Co., Ltd 
Bus 007 Device 025: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 007 Device 026: ID 044e:3013 Alps Electric Co., Ltd 
Bus 007 Device 027: ID 044e:3012 Alps Electric Co., Ltd 

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11abgn  ESSID:"BELL644"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC address removed>   
          Bit Rate=52 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15266  Invalid misc:997   Missed beacon:0


***** rfkill *****

2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

iwl4965               117406  0 
iwl_legacy             71334  1 iwl4965
mac80211              436493  2 iwl4965,iwl_legacy
cfg80211              178877  3 iwl4965,iwl_legacy,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [BELL644] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *BELL644:        Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WPA2
    clodog:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WEP
    dLink 21:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    BELL898:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    6MountainPark:   Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BELL964:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    nofree4u:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    wifi:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



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

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"BELL644"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d2863a13e
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 000742454C4C363434
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1016FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1603050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030006127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706434120010B10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A8802C3996467FCA1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"BELL964"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015de34eb159
                    Extra: Last beacon: 14916ms ago
                    IE: Unknown: 000742454C4C393634
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706434120010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8804C17EBD2BB8D103C000101
                    IE: Unknown: 050400010008
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1016FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000F127A
                    IE: Unknown: DD07000C4300000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BELL898"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000198f87d9181
                    Extra: Last beacon: 2868ms ago
                    IE: Unknown: 000742454C4C383938
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"dLink 21"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c40f40d80
                    Extra: Last beacon: 2904ms ago
                    IE: Unknown: 0008644C696E6B203231
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555349010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406071900000000000000000000000000000000000000
                    IE: Unknown: 3D1606071900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700100000000000001000000000265AD25B8610210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363031104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363031100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"nofree4u"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000198fb224353
                    Extra: Last beacon: 14332ms ago
                    IE: Unknown: 00086E6F667265653475
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"6MountainPark"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000141d62b7bd
                    Extra: Last beacon: 2672ms ago
                    IE: Unknown: 000D364D6F756E7461696E5061726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021400
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD0B0017F20100010100000007
                    IE: Unknown: DD0700039301770320
                    IE: Unknown: DD0E0017F207000101069072401D7523
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BELL441"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000141c5a4c93
                    Extra: Last beacon: 3312ms ago
                    IE: Unknown: 000742454C4C343431
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1016FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500000C127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706434120010B10
                    IE: Unknown: DD9D0050F204104A0001101044000102103B000103104700102880288028801880A8804C17EBE137051021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B415053100800020084103C000101
          Cell 08 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"clodog"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000198fb0525ac
                    Extra: Last beacon: 2676ms ago
                    IE: Unknown: 0006636C6F646F67
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050010180105


***** resolv.conf *****

nameserver 127.0.0.1
search home

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

filename:       /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi 4965 driver for Linux
srcversion:     57713622A8E7F662803C701
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwl-legacy,cfg80211,mac80211
intree:         Y
vermagic:       3.2.0-56-generic-pae SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.2.0-56-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl-legacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     E722FD105B84D0374546E93
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-56-generic-pae SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


***** udev rules *****

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.4/0000:08:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   26.326727] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   26.326731] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   26.326818] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.326848] iwl4965 0000:06:00.0: setting latency timer to 64
[   26.326905] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   26.369575] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   26.373080] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.373223] iwl4965 0000:06:00.0: irq 47 for MSI/MSI-X
[   27.010406] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[   27.015542] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   27.275186] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.275746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.959512] wlan0: authenticate with <MAC address removed> (try 1)
[   31.961325] wlan0: authenticated
[   31.980194] wlan0: associate with <MAC address removed> (try 1)
[   31.984146] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=6)
[   31.984151] wlan0: associated
[   32.027226] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.519466] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = <MAC address removed> tid = 0
[   42.624059] wlan0: no IPv6 routers present
[ 2701.667628] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 2701.668226] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.668236] iwl4965 0000:06:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5
[ 2701.668281] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.668289] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[ 2701.668309] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.668316] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 2701.668323] iwl4965 0000:06:00.0: Error setting RXON_ASSOC (-5)
[ 2701.668330] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.668336] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[ 2701.668345] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.668352] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 2701.668359] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 2701.668366] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.668372] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 2701.668382] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2701.704180] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.704192] iwl4965 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[ 2701.704202] iwl4965 0000:06:00.0: Error removing station <MAC address removed>
[ 2701.708515] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.708519] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 2701.708548] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.708551] iwl4965 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[ 2701.708556] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.708559] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 2701.708562] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 2701.720077] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 2701.720082] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 2701.720086] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 2701.724045] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[ 2701.724045] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[ 2701.724045] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[ 2701.724045] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[ 2702.124685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2915.546043] iwl4965 0000:06:00.0: PCI INT A disabled
[ 2969.534273] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[ 2969.534277] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[ 2969.534365] iwl4965 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2969.534405] iwl4965 0000:06:00.0: setting latency timer to 64
[ 2969.534462] iwl4965 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[ 2969.577183] iwl4965 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[ 2969.577375] iwl4965 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 2969.577610] iwl4965 0000:06:00.0: irq 47 for MSI/MSI-X
[ 2969.637887] iwl4965 0000:06:00.0: loaded firmware version 228.61.2.24
[ 2969.638432] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[ 2969.762754] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3100.046581] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[ 3100.046586] iwl4965 0000:06:00.0: On demand firmware reload
[ 3100.292078] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3105.016181] wlan0: authenticate with <MAC address removed> (try 1)
[ 3105.018055] wlan0: authenticated
[ 3105.037170] wlan0: associate with <MAC address removed> (try 1)
[ 3105.041208] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=6)
[ 3105.041218] wlan0: associated
[ 3105.084099] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3111.552053] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = <MAC address removed> tid = 0
[ 3116.032030] wlan0: no IPv6 routers present
[ 3473.027511] iwl4965 0000:06:00.0: Aggregation not enabled for tid 6 because load = 1
[ 9615.863277] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[ 9615.863622] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.863627] iwl4965 0000:06:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5
[ 9615.863647] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.863650] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[ 9615.863726] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.863760] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 9615.863764] iwl4965 0000:06:00.0: Error setting RXON_ASSOC (-5)
[ 9615.863766] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.863769] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[ 9615.863772] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.863775] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 9615.863778] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 9615.863780] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.863783] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 9615.863787] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9615.876310] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.876321] iwl4965 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[ 9615.876331] iwl4965 0000:06:00.0: Error removing station <MAC address removed>
[ 9615.876949] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.876953] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[ 9615.876980] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.876983] iwl4965 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[ 9615.876989] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.876991] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 9615.876994] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 9615.880083] iwl4965 0000:06:00.0: Not sending command - RF KILL
[ 9615.880089] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 9615.880094] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[ 9615.884058] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[ 9615.884058] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[ 9615.884058] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[ 9615.884058] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[ 9616.447150] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[ 9616.447155] iwl4965 0000:06:00.0: On demand firmware reload
[ 9633.311464] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9634.350175] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9636.450990] wlan0: authenticate with <MAC address removed> (try 1)
[ 9636.467210] wlan0: authenticated
[ 9636.467399] wlan0: associate with <MAC address removed> (try 1)
[ 9636.471382] wlan0: RX ReassocResp from <MAC address removed> (capab=0xc11 status=0 aid=6)
[ 9636.471389] wlan0: associated
[ 9636.510750] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9641.860773] iwl4965 0000:06:00.0: Aggregation not enabled for tid 0 because load = 6
[ 9648.864031] wlan0: no IPv6 routers present
[ 9655.828980] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = <MAC address removed> tid = 0
[ 9659.318264] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = <MAC address removed> tid = 0
[27602.664846] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[27602.665145] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.665154] iwl4965 0000:06:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5
[27602.665199] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.665206] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[27602.665223] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.665230] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[27602.665237] iwl4965 0000:06:00.0: Error setting RXON_ASSOC (-5)
[27602.665244] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.665250] iwl4965 0000:06:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5
[27602.665259] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.665266] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[27602.665273] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[27602.665279] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.665286] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[27602.665296] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[27602.688115] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.688123] iwl4965 0000:06:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5
[27602.688130] iwl4965 0000:06:00.0: Error removing station <MAC address removed>
[27602.696785] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.696790] iwl4965 0000:06:00.0: Error sending REPLY_RXON_ASSOC: enqueue_hcmd failed: -5
[27602.696819] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.696822] iwl4965 0000:06:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5
[27602.696828] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.696831] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[27602.696834] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[27602.712063] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27602.712069] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[27602.712073] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[27602.716022] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[27602.716022] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[27602.716022] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[27602.716022] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[27607.444126] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27648.800568] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[27648.800579] iwl4965 0000:06:00.0: On demand firmware reload
[27649.041516] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27651.070100] iwl4965 0000:06:00.0: RF_KILL bit toggled to disable radio.
[27651.088054] iwl4965 0000:06:00.0: Not sending command - RF KILL
[27651.088059] iwl4965 0000:06:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[27651.088063] iwl4965 0000:06:00.0: Error setting new RXON (-5)
[27651.092026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 1 [0xa5a5a5a2]
[27651.092026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 3 [0xa5a5a5a2]
[27651.092026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 4 [0xa5a5a5a2]
[27651.092026] iwl4965 0000:06:00.0: Failing on timeout while stopping DMA channel 6 [0xa5a5a5a2]
[27651.588099] iwl4965 0000:06:00.0: RF_KILL bit toggled to enable radio.
[27651.588104] iwl4965 0000:06:00.0: On demand firmware reload
[27651.831673] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27656.433665] wlan0: authenticate with <MAC address removed> (try 1)
[27656.448413] wlan0: authenticated
[27656.448896] wlan0: associate with <MAC address removed> (try 1)
[27656.452822] wlan0: RX AssocResp from <MAC address removed> (capab=0xc11 status=0 aid=6)
[27656.452827] wlan0: associated
[27656.493339] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[27668.456057] wlan0: no IPv6 routers present
[27671.136096] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = <MAC address removed> tid = 0
[30861.346588] iwl4965 0000:06:00.0: Aggregation not enabled for tid 6 because load = 0
[36958.290482] iwl4965 0000:06:00.0: Aggregation not enabled for tid 6 because load = 1
[38718.182551] iwl4965 0000:06:00.0: Aggregation not enabled for tid 6 because load = 1
[39325.474695] iwl4965 0000:06:00.0: iwl4965_tx_agg_start on ra = <MAC address removed> tid = 6

****************** done ******************

```

I tried the temporary fix but it also was dropping although it was much better during that session than usual.

Thanks!

---

### Post by mörgæs on 2013-11-27
I saw you posted another thread, so I guess this is still a problem. 

Are you sure the network card is the problem and not the router? Have you tried on different networks?

---

### Post by 2 legit 2 quit on 2014-03-22
sorry i never got back to your question. I do not think its a router issue because i had my isp upgrade my router to the latest router model they have and I notice that this is not a problem on windows laptops. Just this one with ubuntu.

---

### Post by chili555 on 2014-03-22
[CENTER]Doc Chili's Handy Dandy Intel Wireless troubleshooter[/CENTER]

I own and use successfully two Intel wireless devices. I have honed a few techniques in years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit0, add the line:```
iw reg set IS
```Proofread, save and close gedit. If these changes do not help, please try:```
sudo modprobe -r iwl4964
sudo modprobe iwl4965 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwl4965 11n_disable=1"  >>  /etc/modprobe.d/iwl4965.conf
exit
```Finally, if all these steps are not helpful, try the compat driver suite:```
sudo apt-get install linux-backports-modules-cw-3.6-generic
```Reboot and let us have your report.

---

