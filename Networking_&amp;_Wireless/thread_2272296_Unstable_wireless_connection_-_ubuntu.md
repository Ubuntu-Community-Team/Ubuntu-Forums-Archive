---
title: "Unstable wireless connection - ubuntu"
date: 2015-04-05
forum: Networking &amp; Wireless
---

### Post by Birdy_Black on 2015-04-05
hello everybody,


First i'm french so excuse my english if it's not really good. I didn't find any answer on the french website that why i would ask you a question :(. I just install Ubuntu on my computer (dual boot with windows 7) yesterday. But the broblem is that the wireless connection is very unstable and i'm disconnected every 5, 10 or 15 min if i'm lucky. I tried many solution, then i instaled wicd, it work at the beging but after few hours the same problem of disconnection arrived. So i unstaled wicd and i have instaled network-manager again. So now it's still not working and i need your help guys :(.

I'm not on a laptop but on a deskop computer, with a netgear wireless key (<- hope you understand ^^'). The only solution wich is working is to disconnet and reconnect. I'm doing that every 10 min :(. 

Here some informations, it's could be usefull :



```



>>    cat /etc/lsb-release 


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"


>>    lsusb 


Bus 002 Device 004: ID 192f:0416 Avago Technologies, Pte. ADNS-5700 Optical Mouse Controller (3-button)
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f9:01f4 Brother Industries, Ltd MFC-5890CN
Bus 003 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


>>    lspci -k -nn | grep -A 3 -i net 


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169
04:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 03)


>>    sudo lshw -C network 


  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: eth0
       version: 06
       numéro de série: 10:bf:48:85:a6:99
       taille: 10Mbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       ressources: irq:43 portE/S:d000(taille=256) mémoire:f0004000-f0004fff mémoire:f0000000-f0003fff
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 2
       information bus: usb@3:3
       nom logique: wlan0
       numéro de série: 4c:60:de:5d:7d:ff
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.16.0-33-generic firmware=N/A ip=192.168.0.16 link=yes multicast=yes wireless=IEEE 802.11bgn


>>    lsmod 


Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39837  1 
usblp                  22901  0 
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
snd_hda_codec_hdmi     47548  1 
arc4                   12608  2 
rtl8192cu              67741  0 
joydev                 17393  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                64255  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
hid_generic            12559  0 
mac80211              652718  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              494362  2 mac80211,rtlwifi
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68937  1 snd_hda_codec_realtek
snd_hda_intel          30469  5 
snd_hda_controller     31056  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
parport_pc             32741  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
ppdev                  17671  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
lp                     17759  0 
snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
parport                42348  3 lp,ppdev,parport_pc
radeon               1412941  4 
eeepc_wmi              13151  0 
asus_wmi               24094  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm                   452043  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              13483  0 
ttm                    93588  1 radeon
drm_kms_helper         61574  1 radeon
lpc_ich                21093  0 
drm                   311018  7 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
mei                    87875  1 mei_me
shpchp                 37047  0 
video                  20128  1 asus_wmi
mac_hid                13227  0 
wmi                    19193  1 asus_wmi
uas                    23159  0 
usb_storage            66545  1 uas
psmouse               106561  0 
ahci                   34062  3 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169

```
```



>>    iwconfig 


wlan0     IEEE 802.11bgn  ESSID:"freebox_nadiap"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 6A:12:F8:A9:B9:50   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0




>>    ifconfig -a 


eth0      Link encap:Ethernet  HWaddr 10:bf:48:85:a6:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)


lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:2350 erreurs:0 :0 overruns:0 frame:0
          TX packets:2350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:204631 (204.6 KB) Octets transmis:204631 (204.6 KB)


wlan0     Link encap:Ethernet  HWaddr 4c:60:de:5d:7d:ff  
          inet adr:192.168.0.16  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::4e60:deff:fe5d:7dff/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:13832 erreurs:0 :0 overruns:0 frame:0
          TX packets:10934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:15725587 (15.7 MB) Octets transmis:1214501 (1.2 MB)




>>    sudo iwlist scan 


wlan0     Scan completed :
          Cell 01 - Address: 6A:12:F8:A9:B9:50
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"freebox_nadiap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055bf30d4
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000E66726565626F785F6E6164696170
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
          Cell 02 - Address: 6A:12:F8:A9:B9:51
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055be0a52
                    Extra: Last beacon: 104ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050065127A
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4300000000
          Cell 03 - Address: 6A:12:F8:A9:B9:52
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055bf3b2b
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 00084672656557696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
          Cell 04 - Address: 6A:12:F8:A9:B9:53
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055bf448d
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 000F46726565576966695F736563757265
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C336E1017FFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000




>>    uname -r -m 


3.16.0-33-generic x86_64


>>    cat /etc/network/interfaces 


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


>>    nm-tool 




NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        10:BF:48:85:A6:99


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [freebox_nadiap] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        4C:60:DE:5D:7D:FF


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    FreeWifi_secure: Infra, 6A:12:F8:A9:B9:53, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA Enterprise
    FreeWifi:        Infra, 6A:12:F8:A9:B9:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 87
    *freebox_nadiap: Infra, 6A:12:F8:A9:B9:50, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WEP


  IPv4 Settings:
    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             212.27.40.241
    DNS:             212.27.40.240






>>    sudo rfkill list 


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by jeremy31 on 2015-04-05
See the answer from chili555 [http://ubuntuforums.org/showthread.php?t=2251402&p=13159739#post13159739](http://ubuntuforums.org/showthread.php?t=2251402&p=13159739#post13159739)

---

### Post by Birdy_Black on 2015-04-09
Thanks you so much ! it's work !!

---

### Post by jeremy31 on 2015-04-09
Thank chili555 and use Thread tools at the top of the page to "Mark as Solved"

---

