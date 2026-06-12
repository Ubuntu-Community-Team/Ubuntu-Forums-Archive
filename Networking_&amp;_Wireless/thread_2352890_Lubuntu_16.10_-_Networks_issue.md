---
title: "Lubuntu 16.10 - Networks issue"
date: 2017-02-16
forum: Networking &amp; Wireless
---

### Post by abeloki on 2017-02-16
Hello this is my first post in these forums and so I hope you don't mind me pushing myself in.

I have just installed Lubuntu 16.10 on my Compaq Presario CQ56 and I can't seem to connect to my homeWifi. During installation, it detected my network hardware correctly showing both:
enp3s0 Realtek PCI/Ethernet & wlo1 Ralink RT5390 wireless.

 I chose the last one and connected sucesfully to the internet. It downloaded packages during installation no probs and I EVEN got to browse for a while with Firefox before I restarted my laptop as Lubuntu had updates for me to install. (Note that on the first boot after installation I somehow was plugged in to my Wifi although "Device not ready" was still persistent). I'm not very Linux savy so I hope I'm making myself clear.

After this, the same old problem, Network Manager find both my ethernet and wifi "not ready" and I can't connect or scan for more. The Network Connections Tab somehow still has my homeWifi on it, I suppose the one used during installation.

@wildmanne39

Here are my results:

```
abel1@LUBUNTU1:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
Linux LUBUNTU1 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:25:32 UTC 2017 i686 i686 i686 GNU/Linux
```

```
abel1@LUBUNTU1:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    DeviceName: plug in device WLAN
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
--
03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136]  (rev 02)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1605]
    Kernel driver in use: r8169
    Kernel modules: r8169

```

```
abel1@LUBUNTU1:~$ lsusb
Bus 002 Device 002: ID 0bda:58e0 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
abel1@LUBUNTU1:~$ iwconfig
lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:"vodafoneE765"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 68:F9:56:29:E7:66   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:320   Missed beacon:0

enp3s0    no wireless extensions.

```
```
abel1@LUBUNTU1:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
abel1@LUBUNTU1:~$ lsmod
Module                  Size  Used by
ccm                    20480  1
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
gpio_ich               16384  0
uvcvideo               77824  0
videobuf2_vmalloc      16384  1 uvcvideo
arc4                   16384  2
videobuf2_memops       16384  1 videobuf2_vmalloc
rt2800pci              16384  0
videobuf2_v4l2         24576  1 uvcvideo
rt2800mmio             16384  1 rt2800pci
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_hda_codec_realtek    77824  1
rt2800lib              90112  2 rt2800mmio,rt2800pci
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
videodev              159744  3 uvcvideo,videobuf2_core,videobuf2_v4l2
rt2x00pci              16384  1 rt2800pci
snd_hda_intel          32768  3
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              49152  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
media                  36864  2 uvcvideo,videodev
snd_hda_codec         118784  3 snd_hda_intel,snd_hda_codec_generic,snd_hda_codec_realtek
mac80211              679936  3 rt2800lib,rt2x00pci,rt2x00lib
snd_hda_core           69632  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
cfg80211              512000  2 rt2x00lib,mac80211
snd_pcm                94208  3 snd_hda_intel,snd_hda_codec,snd_hda_core
eeprom_93cx6           16384  1 rt2800pci
snd_timer              32768  1 snd_pcm
snd                     69632  13  snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_generic,snd_hda_codec_realtek,snd_pcm
joydev                 20480  0
input_leds             16384  0
coretemp               16384  0
soundcore              16384  1 snd
serio_raw              16384  0
lpc_ich                20480  0
shpchp                 32768  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              20480  0
x_tables               24576  1 ip_tables
autofs4                40960  2
i915                 1245184  2
psmouse               122880  0
ahci                   36864  2
libahci                32768  1 ahci
r8169                  77824  0
i2c_algo_bit           16384  1 i915
mii                    16384  1 r8169
drm_kms_helper        147456  1 i915
syscopyarea            16384  1 drm_kms_helper
wmi                    16384  1 hp_wmi
sysfillrect            16384  1 drm_kms_helper
video                  36864  1 i915
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   311296  4 i915,drm_kms_helper
fjes                   28672  0
```




Thank you in advance.

---

### Post by wildmanne39 on 2017-02-16
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

### Post by abeloki on 2017-02-16
This is what I got:

```

########## wireless info START ##########

Report from: 16 Feb 2017 21:39 CET +0100

Booted last: 16 Feb 2017 00:00 CET +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

##### kernel ############################

Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:25:32 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    DeviceName: plug in device WLAN
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1605]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 0bda:58e0 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib              90112  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              49152  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              679936  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              512000  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  1 hp_wmi

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto wlo1
iface wlo1 inet dhcp
    wpa-ssid vodafoneE765
    wpa-psk  53AF9D53ABE692

##### ifconfig ##########################

enp3s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 161  bytes 11889 (11.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 161  bytes 11889 (11.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 13  bytes 1569 (1.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 34  bytes 5463 (5.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:"vodafoneE765"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'vodafoneE765' [AC2]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:59   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 192.168.0.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       791     1  0 21:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe (U98Z077.00 Half-size Mini PCIe Card)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               0.40
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/vodafoneE765]] (600 root)
[connection] id=vodafoneE765 | type=802-11-wireless
[802-11-wireless] ssid=vodafoneE765
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlo1      14 channels in total; available frequencies :
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
          Current Frequency=2.452 GHz (Channel 9)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.452 GHz (Channel 9)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'MOVISTAR_4E75' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_4E75"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000df78a7a17c
                    Extra: Last beacon: 3348ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'vodafoneE765' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"vodafoneE765"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008b618e368
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4D2CAAE95D28B3DF4F72A52
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DBE617B0243C0FEB62786D4
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 

[rt2800lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 

[rt2x00pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D84965563CC7530CFFD2269
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 

[rt2x00mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     02CA9DA77FC2C7FCCC58176
depends:        rt2x00lib
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 

[rt2x00lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF930122B7900096FC259FA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   12.920689] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   12.924708] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   14.054336] rt2800pci 0000:02:00.0 wlo1: renamed from wlan0
[   15.685061] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   16.100963] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.40
[   16.260604] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   17.820516] wlo1: authenticate with <MAC 'vodafoneE765' [AC2]>
[   17.844947] wlo1: send auth to <MAC 'vodafoneE765' [AC2]> (try 1/3)
[   17.846561] wlo1: authenticated
[   17.848082] wlo1: associate with <MAC 'vodafoneE765' [AC2]> (try 1/3)
[   17.851432] wlo1: RX AssocResp from <MAC 'vodafoneE765' [AC2]> (capab=0x411 status=0 aid=2)
[   17.851525] wlo1: associated
[   17.851537] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready

########## wireless info END ############



```

Thanks.

---

### Post by wildmanne39 on 2017-02-16
First I am not sure that this driver is working well with Ubuntu 16.10 so this is going to be an experiment, Please do:
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
This file:
> /etc/network/interfaces
should only have this in it unless you are not using network manager, which is installed so please store this file to defaut:
```
auto lo
iface lo inet loopback 
```
We need to set your country code for your router:
```
sudo iw reg set ES
```
Make it permanent:
```
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
```
Best to set the channel on 1, 11 or 6 in your router but not on auto.

---

### Post by abeloki on 2017-02-17
Well it seems that was a sucessfull experiment wildmanne39 :D. I'm currently posting this on my laptop with no problem at all, although before finishing I've got some minor details to ask you.

So, I did all the commands you wrote, edited the interfaces file and restarted. Now my Network Manager is finally showing available wifis and connecting to my own.

My 'interfaces' file was showing this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlo1
iface wlo1 inet dhcp
    wpa-ssid vodafoneE765
    wpa-psk  MYPASSWORD
```

And you said it should be showing only this two lines (auto lo | iface lo inet loopback) and so I did. I've got two minor questions: Is the source /etc/network.../* line necessary? Should I put it back? Inet is working fine to be honest. And last one, is this tunning with this 'experimental' driver something to be afraid of? I mean if this solution is something reliable.

Finally I can't thank you enough for your help wildmanne39, I've been working hard here for the last few days and I appreciate it. I really do.

---

### Post by wildmanne39 on 2017-02-17
This is everything in my /etc/network/interfaces file:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

``` 
if you notice the first line has a #at the beginning of it which means it is a comment or advice to the user so it does not effect the working of your wifi but I leave that line there myself.

I am running 16.04 and if this line source /etc/network/interfaces.d/* is in that file that is new it has never been there before to my knowledge, it is a reference to the source file file so please leave it their.

This file /etc/network/interfaces.d/* has always been in ubuntu just not referenced in that file.

The solution is permanent, however sometime updates break things so if it does come back and start a new thread.  Please use thread tools at the top of the page to mark this one solved.

Glad it is working enjoy!

---

### Post by wildmanne39 on 2017-02-17
I just saw your edit, there is always a chance that an update can break your wifi but it is not likely, I update every time there is one for security and bug fixes it is important, there not an easy way to roll back an update but it helps if you know what was installed.

---

### Post by abeloki on 2017-02-17
Ok I will put that line back on the file and hope for the best ;). Everything still going strong but I've got a doubt. Now that I've  finally got inet, I'm being asked for a lot software updates.

 Most of  them are Javascript, Webcontent libraries and so on but I noticed a  Network Connections update with the following: GObject based client  library for NM, library for wireless and mobile dialogs and NM  framework. Should I update this? I'm scared that they might dismantle  what we've achieved so far. If I end up updating, do I have some option  to rollback? Thanks.

___
PD: I was just about to edit my previous post with this update thingy just when I noticed your reply. I just wanted to have that as our last chittychat before I marked this SOLVED. Thx!
PD2: Hahaha ok i'll stop editing this is going out of control. I guess I'll update and hope for the best that they don't cause me any more trouble.
___

**                                                                                                                 [SIZE=5]SOLVED[/SIZE]**

---

### Post by wildmanne39 on 2017-02-17
I thought you left that line in if you took it out just leave it out.

---

