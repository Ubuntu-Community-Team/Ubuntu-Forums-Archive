---
title: "No Wireless Connection"
date: 2017-02-26
forum: Networking &amp; Wireless
---

### Post by dshah on 2017-02-26
I am using Ubuntu 14.04 on a laptop which was running fine WiFi before two days, Now I can't see the wireless connections at all, Here are the commands I tried:

```
$ iwconfig 
lo        no wireless extensions.


eth0      no wireless extensions.


$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	Subsystem: Dell Device [1028:05be]
	Kernel driver in use: e1000e
$ rfkill unblock all
$ rfkill list all
$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.

```

Any help? Thanks

More info:
```

me@dell:/var/pp$  cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
Linux dell 4.4.0-64-generic #85~14.04.1-Ubuntu SMP Mon Feb 20 12:10:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
me@dell:/var/pp$  lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
    Subsystem: Dell Device [1028:05be]
    Kernel driver in use: e1000e
me@dell:/var/pp$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2984 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 002: ID 1c4f:0040 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
me@dell:/var/pp$ dmesg | grep iwl
[15359.087768] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[15359.087771] iwl3945: Copyright(c) 2003-2011 Intel Corporation
me@dell:/var/pp$  iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


me@dell:/var/pp$  rfkill list all
me@dell:/var/pp$  lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     53248  1 
amdkfd                131072  1 
amd_iommu_v2           20480  1 amdkfd
radeon               1503232  1 
i915                 1208320  5 
intel_rapl             20480  0 
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       16384  0 
coretemp               16384  0 
uvcvideo               90112  0 
kvm_intel             167936  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              180224  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
kvm                   536576  1 kvm_intel
ttm                    94208  1 radeon
media                  24576  2 uvcvideo,videodev
drm_kms_helper        151552  2 i915,radeon
mei_me                 36864  0 
mei                    98304  1 mei_me
snd_soc_rt5640        114688  0 
snd_hda_codec_realtek    86016  1 
drm                   360448  9 ttm,i915,drm_kms_helper,radeon
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0 
dcdbas                 16384  1 dell_laptop
dell_smm_hwmon         16384  0 
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  7 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  1 snd_soc_rt5640
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
ghash_clmulni_intel    16384  0 
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
i2c_algo_bit           16384  2 i915,radeon
snd_pcm_dmaengine      16384  1 snd_soc_core
fb_sys_fops            16384  1 drm_kms_helper
snd_hda_core           73728  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
bnep                   20480  2 
snd_hwdep              16384  1 snd_hda_codec
rfcomm                 69632  0 
lpc_ich                24576  0 
sysimgblt              16384  1 drm_kms_helper
aesni_intel           167936  0 
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
bluetooth             516096  10 bnep,rfcomm
ie31200_edac           16384  0 
edac_core              53248  1 ie31200_edac
shpchp                 36864  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 20480  0 
input_leds             16384  0 
serio_raw              16384  0 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
wmi                    20480  1 dell_wmi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
8250_fintek            16384  0 
dell_smo8800           16384  0 
snd                    81920  26 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
elan_i2c               36864  0 
i2c_hid                20480  0 
dw_dmac                16384  0 
soundcore              16384  1 snd
video                  40960  3 i915,dell_wmi,dell_laptop
dw_dmac_core           24576  1 dw_dmac
parport_pc             36864  0 
snd_soc_sst_acpi       16384  0 
i2c_designware_platform    16384  0 
spi_pxa2xx_platform    24576  0 
i2c_designware_core    20480  1 i2c_designware_platform
ppdev                  20480  0 
8250_dw                16384  0 
dell_rbtn              16384  1 
mac_hid                16384  0 
lp                     20480  0 
parport                49152  3 lp,ppdev,parport_pc
binfmt_misc            20480  1 
hid_generic            16384  0 
usbhid                 49152  0 
hid                   118784  3 i2c_hid,hid_generic,usbhid
e1000e                233472  0 
psmouse               126976  0 
ahci                   36864  2 
ptp                    20480  1 e1000e
libahci                32768  1 ahci
sdhci_pci              28672  0 
pps_core               20480  1 ptp
sdhci_acpi             16384  0 
sdhci                  45056  2 sdhci_acpi,sdhci_pci
fjes                   28672  0 
me@dell:/var/pp$ 

```

Find attachment with full logs scrip from [this thread script]("https://ubuntuforums.org/showthread.php?t=370108")
```



########## wireless info START ##########


Report from: 26 Feb 2017 15:10 EET +0200


Booted last: 26 Feb 2017 10:29 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 4.4.0-64-generic #85~14.04.1-Ubuntu SMP Mon Feb 20 12:10:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	Subsystem: Dell Device [1028:05be]
	Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2984 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 002: ID 1c4f:0040 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


iwlwifi               196608  0 
iwl3945                69632  0 
iwlegacy              102400  1 iwl3945
mac80211              733184  2 iwl3945,iwlegacy
brcmfmac              286720  0 
brcmutil               16384  1 brcmfmac
cfg80211              561152  5 iwl3945,iwlwifi,brcmfmac,iwlegacy,mac80211
snd_soc_rt5640        114688  0 
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0 
dcdbas                 16384  1 dell_laptop
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  1 snd_soc_rt5640
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  1 dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1618831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:964757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2260834907 (2.2 GB)  TX bytes:91832745 (91.8 MB)
          Interrupt:20 Memory:f7c00000-f7c20000 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root     20594     1  0 14:52 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.7
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


no-auto-default=<MAC 'eth0' [IF1]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/CYTA545333]] (600 root)
[connection] id=CYTA545333 | type=802-11-wireless
[802-11-wireless] ssid=CYTA545333 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OTEd86fe8]] (600 root)
[connection] id=OTEd86fe8 | type=802-11-wireless
[802-11-wireless] ssid=OTEd86fe8 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Thomson52323C]] (600 root)
[connection] id=Thomson52323C | type=802-11-wireless
[802-11-wireless] ssid=Thomson52323C | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Christina]] (600 root)
[connection] id=Christina | type=802-11-wireless
[802-11-wireless] ssid=Christina | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/tipo]] (600 root)
[connection] id=tipo | type=802-11-wireless
[802-11-wireless] ssid=tipo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CLERMONT LTD]] (600 root)
[connection] id=CLERMONT LTD | type=802-11-wireless
[802-11-wireless] ssid=CLERMONT LTD | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Mikel Guest Internet]] (600 root)
[connection] id=Mikel Guest Internet | type=802-11-wireless
[802-11-wireless] ssid=Mikel Guest Internet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Dimitris]] (600 root)
[connection] id=Dimitris | type=802-11-wireless
[802-11-wireless] ssid=Dimitris | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Forthnet-E628AF]] (600 root)
[connection] id=Forthnet-E628AF | type=802-11-wireless
[802-11-wireless] ssid=Forthnet-E628AF | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wind WiFi CC8304]] (600 root)
[connection] id=Wind WiFi CC8304 | type=802-11-wireless
[802-11-wireless] ssid=Wind WiFi CC8304 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OTEc5d5c8]] (600 root)
[connection] id=OTEc5d5c8 | type=802-11-wireless
[802-11-wireless] ssid=OTEc5d5c8 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Beny's]] (600 root)
[connection] id=Beny's | type=802-11-wireless
[802-11-wireless] ssid=Beny's | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OTEc3a6c0]] (600 root)
[connection] id=OTEc3a6c0 | type=802-11-wireless
[802-11-wireless] ssid=OTEc3a6c0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Forthnet-806E0]] (600 root)
[connection] id=Forthnet-806E0 | type=802-11-wireless
[802-11-wireless] ssid=Forthnet-806E0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CYTA 922]] (600 root)
[connection] id=CYTA 922 | type=802-11-wireless
[802-11-wireless] ssid=CYTA 922 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/wii2]] (600 root)
[connection] id=wii2 | type=802-11-wireless
[802-11-wireless] ssid=wii2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Forthnet-5k6G9]] (600 root)
[connection] id=Forthnet-5k6G9 | type=802-11-wireless
[802-11-wireless] ssid=Forthnet-5k6G9 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/VODAFONE_WIFI_108]] (600 root)
[connection] id=VODAFONE_WIFI_108 | type=802-11-wireless
[802-11-wireless] ssid=VODAFONE_WIFI_108 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wind WiFi 36hS21]] (600 root)
[connection] id=Wind WiFi 36hS21 | type=802-11-wireless
[802-11-wireless] ssid=Wind WiFi 36hS21 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Fastcapital-wifi]] (600 root)
[connection] id=Fastcapital-wifi | type=802-11-wireless
[802-11-wireless] ssid=Fastcapital-wifi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/STUDIO GARDEN]] (600 root)
[connection] id=STUDIO GARDEN | type=802-11-wireless
[802-11-wireless] ssid=STUDIO GARDEN | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OTE6141A4]] (600 root)
[connection] id=OTE6141A4 | type=802-11-wireless
[802-11-wireless] ssid=OTE6141A4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/conn-x420CE7]] (600 root)
[connection] id=conn-x420CE7 | type=802-11-wireless
[802-11-wireless] ssid=conn-x420CE7 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wind WiFi 28BA80]] (600 root)
[connection] id=Wind WiFi 28BA80 | type=802-11-wireless
[802-11-wireless] ssid=Wind WiFi 28BA80 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOL_ZTE_4]] (600 root)
[connection] id=HOL_ZTE_4 | type=802-11-wireless
[802-11-wireless] ssid=HOL_ZTE_4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/A.SOFRA]] (600 root)
[connection] id=A.SOFRA | type=802-11-wireless
[802-11-wireless] ssid=A.SOFRA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NetFasteR IAD 2 (PSTN)]] (600 root)
[connection] id=NetFasteR IAD 2 (PSTN) | type=802-11-wireless
[802-11-wireless] ssid=NetFasteR IAD 2 (PSTN) | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOL_ZTE_6]] (600 root)
[connection] id=HOL_ZTE_6 | type=802-11-wireless
[802-11-wireless] ssid=HOL_ZTE_6 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CYTADBC0]] (600 root)
[connection] id=CYTADBC0 | type=802-11-wireless
[802-11-wireless] ssid=CYTADBC0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/conn-x905f54]] (600 root)
[connection] id=conn-x905f54 | type=802-11-wireless
[802-11-wireless] ssid=conn-x905f54 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CYTA 65D3]] (600 root)
[connection] id=CYTA 65D3 | type=802-11-wireless
[802-11-wireless] ssid=CYTA 65D3 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EASY-WASH]] (600 root)
[connection] id=EASY-WASH | type=802-11-wireless
[802-11-wireless] ssid=EASY-WASH | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/gz-xalkodemon]] (600 root)
[connection] id=gz-xalkodemon | type=802-11-wireless
[802-11-wireless] ssid=gz-xalkodemon | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Christina 1]] (600 root)
[connection] id=Christina 1 | type=802-11-wireless
[802-11-wireless] ssid=Christina | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CBOUKOU]] (600 root)
[connection] id=CBOUKOU | type=802-11-wireless
[802-11-wireless] ssid=CBOUKOU | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FastCapital]] (600 root)
[connection] id=FastCapital | type=802-11-wireless
[802-11-wireless] ssid=FastCapital | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RazaLabs]] (600 root)
[connection] id=RazaLabs | type=802-11-wireless
[802-11-wireless] ssid=RazaLabs | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Thomson8B5659]] (600 root)
[connection] id=Thomson8B5659 | type=802-11-wireless
[802-11-wireless] ssid=Thomson8B5659 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Thomson8B5659 1]] (600 root)
[connection] id=Thomson8B5659 1 | type=802-11-wireless
[802-11-wireless] ssid=Thomson8B5659 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Athens (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


[iwlwifi]
filename:       /lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     4116E844336D79483D28F6F
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[iwl3945]
filename:       /lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     CF9C1C17889D3ECA8E5B735
depends:        iwlegacy,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)


[iwlegacy]
filename:       /lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     464AE65E4E6FD2825462A97
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


[mac80211]
filename:       /lib/modules/4.4.0-64-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     59E6C095E163EDB3ECF327B
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[brcmfmac]
filename:       /lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4354-sdio.txt
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.txt
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.txt
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.txt
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.txt
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.txt
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.txt
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.txt
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.txt
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.txt
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.txt
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.txt
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.txt
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.txt
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.txt
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.txt
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.txt
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.txt
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.txt
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.txt
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.txt
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.txt
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     5CF9C69FE8B5583500A165A
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 
parm:           txglomsz:maximum tx packet chain size [SDIO] (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:string
parm:           debug:level of debug output (int)
parm:           p2pon:enable legacy p2p management functionality (int)
parm:           fcmode:mode of firmware signalled flow control (int)
parm:           roamoff:do not use internal roaming engine (int)


[brcmutil]
filename:       /lib/modules/4.4.0-64-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 


[cfg80211]
filename:       /lib/modules/4.4.0-64-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A7DC879B6551813C20004F1
depends:        
intree:         Y
vermagic:       4.4.0-64-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y


[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1


[iwlegacy]
bt_coex_active: Y
led_mode: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/fcmode: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]


[cfg80211]
bss_entries_limit: 1000
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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x153a (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x088e (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #############################


########## wireless info END ############

```

---

### Post by jeremy31 on 2017-02-26
It looks like you have been manually loading drivers hoping to get it working.  You might want to check in BIOS to see if it is disabled.  If it isn't disabled or there is no setting for WLAN in BIOS, you may want to power the computer down and see if it is easy to remove the wireless card and reinstall it as it may be a connection issue.  From the script results in the UDEV rules it appears that you have an Intel 7260 card but unless it shows up in ```
lspci -nnk | grep -iA2 net
```
Results, it may never work

---

### Post by dshah on 2017-02-26
I checked in BIOS its enabled, I have dell E6540 laptop. Its not easy for me to remove the wireless card from laptop. This is the output of above command:
```

$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	Subsystem: Dell Device [1028:05be]
	Kernel driver in use: e1000e

```

---

### Post by jeremy31 on 2017-02-26
Disconnect the ethernet cable and see if the results change for ```
lspci -nnk | grep -iA2 net
```

There was a comment on a page that said some Dell's disable the wifi when there is an ethernet cable attached

---

### Post by dshah on 2017-02-26
I removed ethernet cable and ran command after few seconds, its the same output as above
```

$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
	Subsystem: Dell Device [1028:05be]
	Kernel driver in use: e1000e

```

---

### Post by jeremy31 on 2017-02-26
You might need to check the connection on the wireless card.  For your model see [http://www.myfixguide.com/manual/dell-latitude-e6540-disassembly/](http://www.myfixguide.com/manual/dell-latitude-e6540-disassembly/)
It isn't as bad as my Dell as it involves removing ribbon cables, keyboard..I did it once and I don't plan on doing it again

---

### Post by dshah on 2017-02-26
Ok, I will try that tomorrow, I have assembled many towers, laptop would be first. I will update thread later with progress,
 Thanks again for help.

---

### Post by dshah on 2017-03-02
alright, I just removed the LAN and put back again, Now I can see Wifi in network list but it display "Wifi is diabled by Hardswitch"
I checked in bios its enabled.

I ran this:
```

sudo rfkill unblock all
rfkill list all
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


```
any idea?
Thanks

---

### Post by jeremy31 on 2017-03-02
Does the switch on the right side change the rfkill status?

---

### Post by dshah on 2017-03-03
Ah I slide the switch and it started to work, Thanks a lot for the help 
 :popcorn:

---

