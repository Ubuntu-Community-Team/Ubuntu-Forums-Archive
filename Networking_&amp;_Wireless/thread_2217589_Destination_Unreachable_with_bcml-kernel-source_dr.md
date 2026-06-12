---
title: "Destination Unreachable with bcml-kernel-source driver"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by 98cwitr on 2014-04-18
Worked fine with the bcmwl driver (bcmwl-kernel-source) on 12.04, even used it for the upgrade. Very strange with what it's doing though, it will see other networks, connect to my network, pull an IP, but I cannot ping the router (destination unreachable). Network is working with other devices around the house, and the wired connection works. Unfortunately there doesn't seem to be another prop. driver available. Thinking about trying ndiswrapper, but I was hoping in this day and age it wouldn't be necessary. Any help is much appreciated :)

---

### Post by 98cwitr on 2014-04-18
Maybe some more useful info :) I have eth0 in so I can have internet access obviously.

:~$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
05:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel driver in use: wl
:~$ lsmod
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22896  0 
vboxnetadp             25636  0 
vboxnetflt             27291  0 
vboxdrv               299807  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13213  3 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
hid_generic            12492  0 
gpio_ich               13229  0 
lib80211_crypt_tkip    17456  0 
usbhid                 47035  0 
kvm_intel             132549  0 
hid                    87604  2 hid_generic,usbhid
wl                   3999690  0 
kvm                   388083  1 kvm_intel
snd_hda_codec_realtek    51029  1 
snd_hda_intel          42730  2 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
psmouse                91033  0 
snd_hwdep              13272  1 snd_hda_codec
serio_raw              13230  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
lpc_ich                16864  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  14 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
nvidia               9648068  49 
parport_pc             31981  1 
ppdev                  17391  0 
it87                   33161  0 
hwmon_vid              12687  1 it87
mac_hid                13037  0 
drm                   243792  2 nvidia
coretemp               13195  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
r8169                  61562  0 
mii                    13654  1 r8169
pata_jmicron           12662  0 
:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


wlan1     IEEE 802.11abg  ESSID:"net"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 28:C6:8E:AE:12:76   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
:~$ dmesg | grep ipw
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:95:48:67
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe95:492c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:712259 (712.2 KB)  TX bytes:140121 (140.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26217 (26.2 KB)  TX bytes:26217 (26.2 KB)


wlan1     Link encap:Ethernet  HWaddr 2c:b0:5d:1f:17:c1 
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2eb0:5dff:fe1f:81e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:30511
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4488 (4.4 KB)  TX bytes:11518 (11.5 KB)
          Interrupt:20 


:~$

---

### Post by 98cwitr on 2014-04-18
I find the following quite interesting

:~$ dmesg | grep wl
[    2.284122] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    2.355724] wlan0: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[    2.558157] systemd-udevd[307]: renamed network interface wlan0 to wlan1
[  206.777234] ERROR @wl_dev_intvar_get : error (-1)
[  206.777238] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  358.858822] ERROR @wl_dev_intvar_get : error (-1)
[  358.858826] ERROR @wl_cfg80211_get_tx_power : error (-1)

---

### Post by 98cwitr on 2014-04-19
just tried turning off all encryption...no difference :(

---

### Post by 98cwitr on 2014-04-19
Switched over to the b43 driver and still the exact same behavior

> 
  *-network
       description: Wireless interface
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.5 latency=32 multicast=yes wireless=IEEE 802.11abg
       resources: irq:20 memory:fb000000-fb003fff


---

### Post by 98cwitr on 2014-04-25
*bump

---

### Post by 98cwitr on 2014-04-29
emailed broadcom :/

I ran the script in the sticky...here's what I've got



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux user 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux


##### lspci #####


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 01)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169
05:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
	Kernel driver in use: wl


##### lsusb #####


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c22a Logitech, Inc. Gaming Keyboard G110
Bus 001 Device 004: ID 046d:c22b Logitech, Inc. Gaming Keyboard G110 G-keys
Bus 001 Device 003: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


auto lo
iface lo inet loopback


##### iwconfig #####


wlan1     IEEE 802.11abg  ESSID:"myssid"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         <network>1     0.0.0.0         UG    0      0        0 eth0
<network>0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
<network>0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan1  [myssid] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  myssid:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           130 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ANTHONY's Wi-Fi Network: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    CenturyLink3472: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    NETGEAR62:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Rudy:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Pmartinez:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    *myssid:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2
    TG862G22:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2


  IPv4 Settings:
    Address:         <network>5
    Prefix:          24 (255.255.255.0)
    Gateway:         <network>1


    DNS:             <network>1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  myssid:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         <network>8
    Prefix:          24 (255.255.255.0)
    Gateway:         <network>1


    DNS:             <network>1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2D0003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332D0003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"myssid"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 736600ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2D0003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332D0003FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink3472"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000F43656E747572794C696E6B33343732
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040036127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DDA50050F204104A0001101044000102103B00010310470010BC329E001DD811B28601B2B2DCFCCC08102100175A7958454C20546563686E6F6C6F67792C20436F72702E1023001B5A7958454C20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F2040001101100095A7958454C2041505310080002210C103C0001011049000600372A000120
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR62"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 00094E4554474541523632
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3406001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010427974EECF6C52788C94000000000000102100046E6F6E65102300046E6F6E65102400046E6F6E651042001253657269616C204E756D62657220486572651054000800060050F204000110110016574E5232303030763428576972656C65737320415029100800022008103C0001011049000600372A000120
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ANTHONY's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0017414E54484F4E5927732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
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
                    IE: Unknown: DD0700039301780320
                    IE: Unknown: DD0E0017F20700010106881FA134749B
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46050200010000
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"judyandjim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000A6A756479616E646A696D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010DF3AB0AF26EDB0631AB7808A5C09F5321021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Pmartinez"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0009506D617274696E657A
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601B2B2DCFE009C103C0001011049000600372A000120
                    IE: Unknown: 0505000100A001
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601B2B2DCFE009C103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05060008127A
                    IE: Unknown: DD07000C4300000000


##### iwlist channel #####


wlan1     32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Current Frequency=2.437 GHz (Channel 6)


##### lsmod #####


wl                   3999690  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              409394  1 wl
ndiswrapper           192915  0 


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


filename:       /lib/modules/3.13.0-24-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     C101C962263FFF26465A483
depends:        
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (myssid: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (myssid: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (myssid: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (myssid: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### modules #####


lp


coretemp
it87


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### udev rules #####


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    2.454011] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   99.324094] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   99.394468] wlan1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   99.402798] systemd-udevd[2202]: renamed network interface wlan0 to wlan1
[  840.490711] ERROR @wl_dev_intvar_get : error (-1)
[  840.490717] ERROR @wl_cfg80211_get_tx_power : error (-1)


########## wireless info END ############

---

### Post by 98cwitr on 2014-04-30
Same issue in Mint (live usb) as well. Kernel 3.11 there.

---

### Post by 98cwitr on 2014-05-04
no word back from broadcom...hope my email wasn't "lost"

---

### Post by 98cwitr on 2014-07-02
still no response :( Hoping an update would come down and fix this issue but nothing so far.

Found this in syslog over the course of a few reboots

> 
Jul  2 00:06:46 user kernel: [    2.131550] wl: module verification failed: signature and/or  required key missing - tainting kernel
Jul  2 00:13:56 user kernel: [    2.081672] wl: module verification failed: signature and/or  required key missing - tainting kernel
Jul  2 00:19:00 user kernel: [    2.101878] wl: module verification failed: signature and/or  required key missing - tainting kernel


> 
Jul  2 00:06:46 user kernel: [    2.131550] wl: module verification failed: signature and/or  required key missing - tainting kernel
Jul  2 00:13:56 user kernel: [    2.081672] wl: module verification failed: signature and/or  required key missing - tainting kernel
Jul  2 00:19:00 user kernel: [    2.101878] wl: module verification failed: signature and/or  required key missing - tainting kernel



Jul  2 00:06:46 user kernel: [    2.083701] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 00:06:46 user kernel: [    2.094724] lib80211: common routines for IEEE802.11 drivers
Jul  2 00:06:46 user kernel: [    2.094727] lib80211_crypt: registered algorithm 'NULL'
Jul  2 00:06:46 user kernel: [    2.232414] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul  2 00:06:46 user kernel: [    2.249417] lib80211_crypt: registered algorithm 'TKIP'
Jul  2 00:06:46 user kernel: [    2.786527] cfg80211: World regulatory domain updated:
Jul  2 00:06:46 user kernel: [    2.786528] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 00:06:46 user kernel: [    2.786530] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:06:46 user kernel: [    2.786531] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:06:46 user kernel: [    2.786532] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:06:46 user kernel: [    2.786533] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:06:46 user kernel: [    2.786534] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:06:46 user NetworkManager[845]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/ieee80211/phy0/rfkill0) (driver wl)
Jul  2 00:06:46 user NetworkManager[845]: <info> (wlan1): using nl80211 for WiFi device control
Jul  2 00:13:56 user kernel: [    2.061909] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 00:13:56 user kernel: [    2.066189] lib80211: common routines for IEEE802.11 drivers
Jul  2 00:13:56 user kernel: [    2.066192] lib80211_crypt: registered algorithm 'NULL'
Jul  2 00:13:56 user kernel: [    2.163848] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul  2 00:13:56 user kernel: [    2.181125] lib80211_crypt: registered algorithm 'TKIP'
Jul  2 00:13:56 user kernel: [    2.965728] cfg80211: World regulatory domain updated:
Jul  2 00:13:56 user kernel: [    2.965732] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 00:13:56 user kernel: [    2.965734] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:13:56 user kernel: [    2.965736] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:13:56 user kernel: [    2.965738] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:13:56 user kernel: [    2.965740] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:13:56 user kernel: [    2.965741] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:13:56 user NetworkManager[782]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/ieee80211/phy0/rfkill0) (driver wl)
Jul  2 00:13:56 user NetworkManager[782]: <info> (wlan1): using nl80211 for WiFi device control
Jul  2 00:19:00 user kernel: [    2.080696] cfg80211: Calling CRDA to update world regulatory domain
Jul  2 00:19:00 user kernel: [    2.087906] lib80211: common routines for IEEE802.11 drivers
Jul  2 00:19:00 user kernel: [    2.087910] lib80211_crypt: registered algorithm 'NULL'
Jul  2 00:19:00 user kernel: [    2.183797] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul  2 00:19:00 user kernel: [    2.193076] lib80211_crypt: registered algorithm 'TKIP'
Jul  2 00:19:00 user kernel: [    2.978803] cfg80211: World regulatory domain updated:
Jul  2 00:19:00 user kernel: [    2.978806] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  2 00:19:00 user kernel: [    2.978808] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:19:00 user kernel: [    2.978810] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:19:00 user kernel: [    2.978812] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:19:00 user kernel: [    2.978814] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:19:00 user kernel: [    2.978815] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  2 00:19:00 user NetworkManager[821]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/ieee80211/phy0/rfkill0) (driver wl)
Jul  2 00:19:00 user NetworkManager[821]: <info> (wlan1): using nl80211 for WiFi device control

---

### Post by 98cwitr on 2014-10-21
Updated to 6.30.223.248 and same issue. Had a time getting the driver installed since it kept wanting to hold onto the old one. I finally overwrote the wl.ko file under /lib/modules/<kernelVer>/updates and it worked. Update was from 10/15 too...kinda weird.

---

