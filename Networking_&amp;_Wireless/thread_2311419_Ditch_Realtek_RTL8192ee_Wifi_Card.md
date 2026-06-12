---
title: "Ditch Realtek RTL8192ee Wifi Card?"
date: 2016-01-27
forum: Networking &amp; Wireless
---

### Post by fishski13 on 2016-01-27
Hello,
Newish Ubuntu user here with a low-level Linux skill set. As the title suggests, I'm having a difficult time with the rtl8192ee. I've spent a fair amount of time of researching and troubleshooting but to no avail. The wifi will work for a brief period upon start up and after disconnecting from a wired ethernet connection, but then slows down and will stop all together despite the fact that I'm showing connection to local access/router.

Running Lenovo L440 laptop and Mate 14.04.3 LTS as a single OS, here's what I've done so far without luck:

```

sudo apt-get install git build-essential
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install 

```

and **sudo lshw -C network **returns after reboot:

```

st-hc@sthc-ThinkPad-L440:~$  sudo lshw -C network
[sudo] password for st-hc: 
  *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 3c:97:0e:ee:26:4f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.13-3 ip=192.168.1.253 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f2500000-f251ffff memory:f253f000-f253ffff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: RTL8192EE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 34:23:87:45:67:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8192ee driverversion=3.16.0-59-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 ioport:5000(size=256) memory:f2400000-f2403fff

```

and [B]lsmod

[/B]```
st-hc@sthc-ThinkPad-L440:~$ lsmod
Module                  Size  Used by
uas                    27255  0 
usb_storage            66545  2 uas
hid_generic            12559  0 
usbhid                 52616  0 
snd_usb_audio         166338  2 
hid                   110426  2 hid_generic,usbhid
snd_usbmidi_lib        29828  1 snd_usb_audio
ctr                    13049  3 
ccm                    17773  3 
bnep                   19624  2 
rfcomm                 69509  12 
arc4                   12608  2 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77561  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
intel_rapl             18783  0 
r8192ee               582544  0 
thinkpad_acpi          81027  1 
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
snd_hwdep              17698  2 snd_usb_audio,snd_hda_codec
nvram                  14411  1 thinkpad_acpi
mac80211              652777  1 r8192ee
snd_pcm               104112  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
coretemp               13441  0 
snd_rawmidi            30876  2 snd_usbmidi_lib,snd_seq_midi
btusb                  32497  0 
rtsx_pci_ms            18168  0 
bluetooth             446409  22 bnep,btusb,rfcomm
i915                  906182  5 
cfg80211              498458  2 mac80211,r8192ee
kvm                   456292  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
6lowpan_iphc           18702  1 bluetooth
memstick               16966  1 rtsx_pci_ms
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
joydev                 17393  0 
serio_raw              13483  0 
cryptd                 20359  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         61574  1 i915
drm                   311018  4 i915,drm_kms_helper
mei_me                 19696  0 
snd_timer              29562  2 snd_pcm,snd_seq
i2c_algo_bit           13413  1 i915
mei                    87875  1 mei_me
video                  20128  1 i915
snd                    79468  27 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
wmi                    19193  0 
shpchp                 37047  0 
soundcore              15047  2 snd,snd_hda_codec
lpc_ich                21093  0 
mac_hid                13227  0 
nls_iso8859_1          12713  1 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23043  0 
psmouse               106767  0 
ahci                   34142  3 
e1000e                226396  0 
libahci                32424  1 ahci
rtsx_pci               46259  2 rtsx_pci_ms,rtsx_pci_sdmmc
ptp                    19395  1 e1000e
pps_core               19382  1 ptp

```

It appears that the correct driver is loaded? 

[B]wireless info script

[/B]```


                        ########## wireless info START ##########

Report from: 27 Jan 2016 01:01 CST -0600

Booted last: 26 Jan 2016 23:55 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-59-generic #79~14.04.1-Ubuntu SMP Mon Jan 18 15:41:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: Lenovo Device [17aa:501e]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:001b]
    Kernel driver in use: r8192ee

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 13fd:1340 Initio Corporation Hi-Speed USB to SATA Bridge
Bus 003 Device 003: ID 0d8c:0319 C-Media Electronics, Inc. 
Bus 003 Device 002: ID 0bda:8761 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

r8192ee               582544  0 
mac80211              652777  1 r8192ee
cfg80211              498458  2 mac80211,r8192ee
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.253  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9305673 (9.3 MB)  TX bytes:2599215 (2.5 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:907315 (907.3 KB)  TX bytes:12299 (12.2 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Hal3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Hal3' [AC1]>   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-16 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       938     1  0 Jan26 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Hal3] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8192ee
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    trj2:            Infra, <MAC 'trj2' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 67 WPA2
    trj2:            Infra, <MAC 'trj2' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2
    *Hal3:           Infra, <MAC 'Hal3' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Bieno:           Infra, <MAC 'Bieno' [AC6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 74 WPA2
    TMGI:            Infra, <MAC 'TMGI' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    HPM1217-880D8F:  Ad-Hoc, <MAC 'HPM1217-880D8F' [AC8]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 44
    JNet:            Infra, <MAC 'JNet' [AN7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Comcast-TMGI:    Infra, <MAC 'Comcast-TMGI' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.253
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Hal3]] (600 root)
[connection] id=Hal3 | type=802-11-wireless
[802-11-wireless] ssid=Hal3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Hal3' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"Hal3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000047c7f562
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TMGI' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TMGI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8fe165192
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'trj2' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"trj2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003eae23bc9e
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'trj2' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"trj2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010e57edc380
                    Extra: Last beacon: 3540ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '########' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000384527885ae
                    Extra: Last beacon: 672ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Bieno' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Bieno"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000222616a1c96
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '######################' [AC7]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005890da03a
                    Extra: Last beacon: 2192ms ago
          Cell 08 - Address: <MAC 'HPM1217-880D8F' [AC8]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"HPM1217-880D8F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc

##### module infos ######################

[r8192ee]
filename:       /lib/modules/3.16.0-59-generic/kernel/drivers/staging/rtl8192ee/r8192ee.ko
firmware:       rtlwifi/rtl8192eefw.bin
description:    Realtek 8192E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     046553152F8274C9D21FCAC
depends:        mac80211,cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DB:81:2A:9E:DB:ED:CE:CB:54:FC:9F:D8:2A:4B:24:B6:A8:9B:4E:9D
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[mac80211]
filename:       /lib/modules/3.16.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     477882071593B10E01388C8
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DB:81:2A:9E:DB:ED:CE:CB:54:FC:9F:D8:2A:4B:24:B6:A8:9B:4E:9D
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        DB:81:2A:9E:DB:ED:CE:CB:54:FC:9F:D8:2A:4B:24:B6:A8:9B:4E:9D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[r8192ee]
debug: 1
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x818b (r8192ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.744545] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.498912] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.524330] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   16.524335] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   16.524580] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.701958] wlan0: authenticate with <MAC 'Hal3' [AC1]>
[   19.405603] wlan0: send auth to <MAC 'Hal3' [AC1]> (try 1/3)
[   19.433962] wlan0: authenticated
[   19.436187] wlan0: associate with <MAC 'Hal3' [AC1]> (try 1/3)
[   19.441223] wlan0: RX AssocResp from <MAC 'Hal3' [AC1]> (capab=0x411 status=0 aid=7)
[   19.451858] wlan0: associated
[   19.451867] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2696.963685] wlan0: Connection to AP <MAC 'Hal3' [AC1]> lost
[ 2698.020986] wlan0: authenticate with <MAC 'Hal3' [AC1]>
[ 2698.054080] wlan0: send auth to <MAC 'Hal3' [AC1]> (try 1/3)
[ 2698.057799] wlan0: authenticated
[ 2698.060477] wlan0: associate with <MAC 'Hal3' [AC1]> (try 1/3)
[ 2698.064505] wlan0: RX AssocResp from <MAC 'Hal3' [AC1]> (capab=0x411 status=0 aid=2)
[ 2698.075131] wlan0: associated
[ 2857.704326] wlan0: deauthenticated from <MAC 'Hal3' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 2857.747717] wlan0: authenticate with <MAC 'Hal3' [AC1]>
[ 2857.764468] wlan0: send auth to <MAC 'Hal3' [AC1]> (try 1/3)
[ 2857.766730] wlan0: authenticated
[ 2857.771261] wlan0: associate with <MAC 'Hal3' [AC1]> (try 1/3)
[ 2857.774770] wlan0: RX AssocResp from <MAC 'Hal3' [AC1]> (capab=0x411 status=0 aid=6)
[ 2857.785292] wlan0: associated

########## wireless info END ############
 
```

Router is configured to WPA2-personal, Auto wireless mode between N and Legacy, channel 1, and IPv6 disabled. I've considered disabling 802.11n but am unsure how to do this.

I'm willing to purchase a new PCI card/USB adapter that would would offer compatibility if I'm unable to get the rtl8192ee to work with the Lenovo. If so, are there any recommendations? Here's a link to a pic of the Realtek, and the key slot inside the laptop is a M.2 Type A: [URL="http://ecx.images-amazon.com/images/I/71I92b5YJlL._SX425_.jpg"]http://ecx.images-amazon.com/images/I/71I92b5YJlL._SX425_.jpg 

[/URL]

---

