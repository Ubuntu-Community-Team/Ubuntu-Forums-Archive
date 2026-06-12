---
title: "USB Wifi card TL-WN823N in Ubuntu 14.04.2 no working"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by mario49 on 2015-02-24
Hi every one!
I hope you be fine. I´m newbie on Ubuntu. I´ve installed Ubuntu 14.04.2 in old Sony Vaio Laptop (MODEL PCG-5J2L or VGN-SZ79SN/C, i´m not sure). It has a builtin wifi interfacem but it´s not working (when it had Win XP it didn´t work too). I decided to use an USB wifi card TL-WN823N. It didn´t work. I´ve read about solutions for it and i found this one:

[B][https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)

[/B]It didn´t worked. 

The builtin NIC doesn´t work nor switched on nor switched off. I discover the builtin wifi NIC is wlan1 and my new USB wifi NIC is wlan0. 

Playing with sudo ifconfig wlan0 up i could my USB wifi NIC to start to blink.

I'd really appreciate someone may help me.

I launched some commands line for troubleshooting:

$ sudo lshw -C network
```

 *-network DESACTIVADO   
       **descripción: Interfaz inalámbrica**
       **producto: PRO/Wireless 4965 AG or AGN [Kedron] Network Connectio**n
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:02:00.0
       **nombre lógico: wlan1**
       versión: 61
       serie: 00:13:e8:bd:4f:ab
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=iwl4965 driverversion=3.13.0-45-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       recursos: irq:46 memoria:f6000000-f6001fff
  *-network
       descripción: Ethernet interface
       producto: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:06:00.0
       nombre lógico: eth0
       versión: 01
       serie: 00:1a:80:3e:5a:e9
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.133 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:43 ioport:4000(size=256) memoria:fa000000-fa000fff memoria:f4000000-f401ffff
  *-network
       **descripción: Interfaz inalámbrica**
       id físico: 1
       información del bus: usb@2:3
       **nombre lógico: wlan0**
       serie: 14:cc:20:13:69:df
       capacidades: ethernet physical wireless
       configuración: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated

```
$ rfkill list wifi
```

0: phy0: Wireless LAN
    Soft blocked: no
    **Hard blocked: yes**

```
wlan 0 ???

$ sudo rfkill unblock 0
$ rfkill list wifi
```

0: phy0: Wireless LAN
    Soft blocked: no
   ** Hard blocked: yes**

```
wlan0 keeps blocked????

~$ sudo lsusb
```

**Bus 002 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 005 Device 003: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 005 Device 002: ID 192f:0616 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (5-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
$ sudo lsmod
```

Module                  Size  Used by
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
hid_generic            12492  0 
arc4                   12536  2 
pcmcia                 51828  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
usbhid                 47070  0 
videobuf2_core         39258  1 uvcvideo
hid                    87604  2 hid_generic,usbhid
videodev              108503  2 uvcvideo,videobuf2_core
coretemp               13195  0 
[B]iwl4965               106859  0 
iwlegacy               88016  1 iwl4965[/B]
joydev                 17101  0 
yenta_socket           40201  0 
**mac80211              546067  2 iwl4965,iwlegacy**
i915                  710013  3 
pcmcia_rsrc            18319  1 yenta_socket
tifm_7xx1              13163  0 
lpc_ich                16864  0 
serio_raw              13230  0 
parport_pc             31981  0 
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm_kms_helper         48868  1 i915
tifm_core              15133  1 tifm_7xx1
ppdev                  17391  0 
**cfg80211              409394  3 iwl4965,iwlegacy,mac80211**
snd_hda_codec_realtek    59259  1 
snd_hda_intel          42794  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
drm                   244037  4 i915,drm_kms_helper
shpchp                 32128  0 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
video                  18903  1 i915
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
**8192cu                572775  0 **
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91357  0 
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  61562  0 
pata_acpi              12886  0 
mii                    13654  1 r8169

```
$ sudo iwconfig 
```

**wlan0 **    unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
```
$ sudo iwlist wlan1 scanning
```

wlan1     Interface doesn't support scanning : Network is down

```
$ sudo iwlist **wlan0** scanning   --> It scans channels !!!
```

wlan0     Scan completed :
          Cell 01 - Address: CA:D7:19:E9:59:60
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Quality=20/100  Signal level=100/100  
          Cell 02 - Address: C8:D7:19:E9:59:6E
                    ESSID:"tokito"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD940050F204104A0001101044000102103B00010310470010EB606877966F6240CA6804FEA3F2B41E10210013436973636F2053797374656D732C20496E632E1023000E4C696E6B737973204541363530301024000645413635303010420008247B7365726E6F7D1054000800060050F204000110110009746F6B69746F204150100800022008103C0001031049000600372A000120
                    Quality=36/100  Signal level=100/100  
          Cell 03 - Address: 00:26:ED:AC:C0:7D
                    ESSID:"Movistar"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=36/100  Signal level=88/100

```

$ dmesg | grep 8192
```

[    0.004163] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.004168] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.197842] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.197865] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.197902] TCP: Hash tables configured (established 8192 bind 8192)
[    0.986056] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[   14.694863] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   14.700513] rtl8192cu driver version=v4.0.2_9000.20130911
[   14.700653] CHIP TYPE: RTL8188C_8192C
[   14.701776] ====> ReadAdapterInfo8192C
[   15.011936] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   15.011939] <==== ReadAdapterInfo8192C in 308 ms
[   15.013325] usbcore: registered new interface driver rtl8192cu
[   21.078192] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  326.652431] rtl8192cu_hal_init in 572ms

```

More details: I´ve executed the known wireless script with this outputs:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

mario-VAIO 3.13.0-45-generic i686,  Ubuntu 14.04.2 LTS, trusty

CPU    : Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
Memory : 1499 MB
Uptime : 22:26:11 up  2:19,  2 users,  load average: 0,16, 0,27, 0,23


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100]
    Kernel driver in use: iwl4965
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Sony Corporation Device [104d:9015]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 005 Device 003: ID 03eb:0902 Atmel Corp. 4-Port Hub
Bus 005 Device 002: ID 192f:0616 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (5-button)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1839 Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwl4965               106859  0 
iwlegacy               88016  1 iwl4965
mac80211              546067  2 iwl4965,iwlegacy
cfg80211              409394  3 iwl4965,iwlegacy,mac80211
8192cu                572775  0 


module parameters ~~~~~~~~~~~~~~~~~~

8192cu       (37): if2name=wlan0 | ifname=wlan0 | rtw_80211d=0 | rtw_ampdu_amsdu=0 | rtw_ampdu_enable=1 | rtw_antdiv_cfg=2 | rtw_busy_thresh=40 | rtw_cbw40_enable=3 | rtw_channel=1 | rtw_channel_plan=65 | rtw_chip_version=0 | rtw_enusbss=0 | rtw_force_iol=N | rtw_ht_enable=1 | rtw_hwpdn_mode=2 | rtw_hwpwrp_detect=0 | rtw_hw_wps_pbc=1 | rtw_initmac=(null) | rtw_ips_mode=1 | rtw_lbkmode=0 | rtw_low_power=0 | rtw_lowrate_two_xmit=1 | rtw_mac_phy_mode=0 | rtw_max_roaming_times=2 | rtw_mc2u_disable=0 | rtw_mp_mode=0 | rtw_network_mode=0 | rtw_notch_filter=0 | rtw_power_mgnt=0 | rtw_rf_config=5 | rtw_rfintfs=2 | rtw_rx_stbc=1 | rtw_special_rf_path=0 | rtw_vcs_type=1 | rtw_vrtl_carrier_sense=2 | rtw_wifi_spec=0 | rtw_wmm_enable=1
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwl4965       (5): 11n_disable=0 | amsdu_size_8K=1 | fw_restart=1 | queues_num=0 | swcrypto=0
iwlegacy      (2): bt_coex_active=Y | led_mode=0
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID              | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=============================o=============o===========o=============o=========o===========o==============o===========
 wlan0                       | 802.11 WiFi | rtl8192cu | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0  [Conexión cableada 1]| Wired       | r8169     | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.133
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.2
    DNS:             192.168.1.2
-----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan1                       | 802.11 WiFi | iwl4965   | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan1>
-----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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
managed=true


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.855/5.486/6.118/0.635 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.055/0.056/0.058/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "es_CL.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.412 GHz (Channel 1)
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
wlan1     24 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rtl8192cu
blacklist iwl3945

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwl4965]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko
firmware:       iwlwifi-4965-2.ucode
version:        in-tree:
srcversion:     0C07ED8F3D47BC4C25E124D
depends:        iwlegacy,cfg80211,mac80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     A847A747E4E6066D74E1D6A
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[8192cu]
filename:       /lib/modules/3.13.0-45-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     98913FB8609F2F16E0996C2
depends:        
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_special_rf_path:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_mc2u_disable:int
parm:           rtw_mac_phy_mode:int
parm:           rtw_80211d:int
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x4229 (iwl4965)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
8192cu
8192cu

[/etc/modprobe.d]
8192cu-disable-power-management.conf: options 8192cu rtw_power_mgnt=0 rtw_enusbss=0
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=4a6ded17-9e05-4e97-b872-0477cbd3ed02 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.777971] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.778464] audit: initializing netlink socket (disabled)
[    1.435039] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   14.607467] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   14.609648] rtl8192cu driver version=v4.0.2_9000.20130911
[   14.609811] register rtw_netdev_ops to netdev_ops
[   14.786532] _rtw_drv_register_netdev, MAC Address (if1) = <MAC wlan0>
[   15.266631] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   15.266637] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   15.266709] iwl4965 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   15.266939] iwl4965 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   15.310060] iwl4965 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5
[   15.310820] iwl4965 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.310949] iwl4965 0000:02:00.0: irq 45 for MSI/MSI-X
[   15.687544] iwl4965 0000:02:00.0: loaded firmware version 228.61.2.24
[   15.699352] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   19.001422] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.934267] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   19.953254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

Please help me. I´m a little bit tired.

Thanx in advance,
MR
-----------------------------------------------------------------------------------
Hi guys!
Nobody help me?

Yesterday i made

$ sudo apt-get update 
$ sudo apt-get dist-upgrade

Nothing works yet !!!

Please, someone help me.

Regards,
MR

---

### Post by mario49 on 2015-03-01
Hi everybody !!!
Finally i solved my problem by my own. Nobody help me in this forum. That's not cool 

Well, i told you what i did.

1.- I followed:

[https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)

2.- $ lsusb
Bus 002 Device 008: ID **0bda:8178** Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter

3.- $ lsmod | grep 8192
8192cu                572775  0

Original module wasn´t loaded at startup (it was at blacklist.conf files according to step 1).

4.- I think  i linked my NIC with right module at startup. If someone knows what it means this commands, please explain it here:

echo '8192cu' | sudo tee -a /etc/modules
echo "**0bda 8178**" | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id

5.- I checked at etc/rc.local says

echo "**0bda 8178**" | tee /sys/bus/usb/drivers/rtl8192cu/new_id
exit 0

I guess i wrote manually in this file.

6.- Nothing worked. 

7.- I read:
[http://askubuntu.com/questions/146076/network-is-not-working-anymore-ubuntu-12-04](http://askubuntu.com/questions/146076/network-is-not-working-anymore-ubuntu-12-04)

So, network manager was suspicious.

I reinstalled. Nothing worked.

8.- I installed wicd network manager and wifi worked. A different network manager. So the problem was the preinstalled network manager. Now my wifi NIC USB TL-WN823N is working in Ubuntu 14.04.2.

It´s not an elegant solution, but it´s working.

I hope someone may help this solution.

Regards,
MR

---

### Post by Rex_Sunny on 2015-03-07
Hi Mario,

Great to see your work around! I am desperate about the wi-fi fix too. I have one NIC TP-LINK TL-WN781ND 150Mbps Wireless PCI Express Network Nic. I am getting very low signal since I used in Ubuntu 14.04.2

Please see my output for the following commands

**sudo lshw -C network**

*-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan2
       version: 01
       serial: e8:de:27:8e:85:dd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.16.0-31-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fea80000-feafffff memory:fea70000-fea7ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: c0
       serial: 54:04:a6:d8:a9:1d
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fe9c0000-fe9fffff ioport:dc00(size=128)

**rfkill list wifi**

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no





[B]dmesg | grep 8192

[/B][    0.000000] total RAM covered: 8192M
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021fc00000 s82304 r8192 d24192 u524288
[    0.000000] pcpu-alloc: s82304 r8192 d24192 u524288 alloc=1*2097152

[B]lsmod |grep ath9k

[/B]ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652718  1 ath9k
cfg80211              494330  4 ath,ath9k_common,ath9k,mac80211

Please suggest me what should I do next! I really need your help bro.

Thanks
Rex

---

### Post by Rex_Sunny on 2015-03-19
Nobody cares to reply or don know the fix????

---

### Post by howefield on 2015-03-19
Give yourself a break and don't post a question in a thread marked solved. Try your own thread if you are serious about wanting assistance.

---

