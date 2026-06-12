---
title: "WiFi Networks device not ready - no internet access"
date: 2017-01-19
forum: Networking &amp; Wireless
---

### Post by skeletonxf on 2017-01-19
I'm dualbooting Windows 10 and Ubuntu 16 LTS on my Lenovo Yoga 710. I had a tricky installation with many boots not reaching the login screen and difficulty even getting to the installer from my live usb. I later fixed this issue via following the advice here: [https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/Special_Interest_Linux/thread-id/7958/page/3](https://forums.lenovo.com/t5/forums/v3_1/forumtopicpage/board-id/Special_Interest_Linux/thread-id/7958/page/3) and blacklisting ***modprobe.blacklist=i2c_hid*** when booting. I now have no issues trying to boot and get to the login screen every time. Unfortunately, some time in between many failed attempts at booting my laptop it now always says "Wifi Networks device not ready" when I try to look at the wifi icon and I have no Internet access from Ubuntu (Windows 10 still uses wifi without problems). This was not the case when I actually used the installer as the Internet worked fine then.

My laptop does not have an ethernet cable so I am very stuck. I have ran some terminal commands that other people with similar issues seemed to run.

```

skeletonxf@skeletonxf-Lenovo-YOGA-710-14IKB:~$ iwconfig
lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
skeletonxf@skeletonxf-Lenovo-YOGA-710-14IKB:~$ lsmod
Module                  Size  Used by
rfcomm                 69632  0
arc4                   16384  2
bnep                   20480  2
hid_multitouch         20480  0
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
8250_dw                16384  0
nls_iso8859_1          16384  1
x86_pkg_temp_thermal    16384  0
coretemp               16384  0
kvm_intel             172032  0
kvm                   536576  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
ath                    32768  1 ath10k_core
joydev                 20480  0
input_leds             16384  0
mac80211              737280  1 ath10k_core
serio_raw              16384  0
rtsx_pci_ms            20480  0
memstick               20480  1 rtsx_pci_ms
cfg80211              565248  3 ath,mac80211,ath10k_core
hci_uart               77824  0
btqca                  16384  1 hci_uart
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
idma64                 20480  0
virt_dma               16384  1 idma64
intel_lpss_acpi        16384  0
intel_lpss_pci         16384  0
mei_me                 36864  0
mei                    98304  1 mei_me
shpchp                 36864  0
tpm_crb                16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  2 btusb,hci_uart
btintel                16384  2 btusb,hci_uart
bluetooth             520192  31 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
acpi_pad               20480  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
rtsx_pci_sdmmc         24576  0
i915_bpo             1261568  3
psmouse               126976  0
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
drm_kms_helper        147456  1 i915_bpo
ahci                   36864  3
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
libahci                32768  1 ahci
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  5 i915_bpo,drm_kms_helper
wmi                    20480  1 ideapad_laptop
i2c_hid                20480  0
hid                   118784  2 i2c_hid,hid_multitouch
pinctrl_sunrisepoint    28672  0
pinctrl_intel          20480  2 pinctrl_sunrisepoint
video                  40960  2 i915_bpo,ideapad_laptop
fjes                   28672  0
skeletonxf@skeletonxf-Lenovo-YOGA-710-14IKB:~$ iwlist scan
lo        Interface doesn't support scanning.

wlp1s0    Failed to read scan data : Network is down

skeletonxf@skeletonxf-Lenovo-YOGA-710-14IKB:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
skeletonxf@skeletonxf-Lenovo-YOGA-710-14IKB:~$ sudo lshw -C network
[sudo] password for skeletonxf: 
  *-network DISABLED      
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 32
       serial: 94:e9:79:fa:af:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-31-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:279 memory:b1000000-b11fffff
skeletonxf@skeletonxf-Lenovo-YOGA-710-14IKB:~$ 


```

---

### Post by ajgreeny on 2017-01-19
See the Wireless-Info link in my signature to run the wifi-info script and post back here the results from that.  Users more expert in wifi than I will be able to help you more from that.

---

### Post by skeletonxf on 2017-01-20
Thanks

I have followed the info for the without internet access method 2

```


########## wireless info START ##########

Report from: 20 Jan 2017 11:09 GMT +0000

Booted last: 20 Jan 2017 00:00 GMT +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, modprobe.blacklist=hid_sensor_hub, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Lenovo QCA6174 802.11ac Wireless Network Adapter [17aa:0827]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 002: ID 0bda:57f8 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 1221:3234 Unknown manufacturer Disk (Thumb drive)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915_bpo,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF1]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2535     1  1 11:07 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlp1s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[    2.039065] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.286879] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    2.287109] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    2.287111] ath10k_pci 0000:01:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    2.355189] ath10k_pci 0000:01:00.0: failed to fetch board data for ath10k/QCA6174/hw3.0 from bus=pci,vendor=168c,device=003e,subsystem-vendor=17aa,subsystem-device=0827/board-2.bin
[    4.560803] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 17aa:0827) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.560807] ath10k_pci 0000:01:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    7.557690] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[    7.634943] ath: EEPROM regdomain: 0x6c
[    7.634946] ath: EEPROM indicates we should expect a direct regpair map
[    7.634947] ath: Country alpha2 being used: 00
[    7.634948] ath: Regpair used: 0x6c
[    7.640760] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[    7.661038] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   12.945864] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   18.945997] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   24.302118] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   30.302257] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   35.662363] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   41.662498] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   57.294875] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   63.294541] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   68.659089] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   74.659234] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   90.291573] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[   96.291756] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  101.651822] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  107.651539] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  123.291901] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  129.291961] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[  134.652132] ath10k_pci 0000:01:00.0: failed to enable dynamic BW: -11
[  140.652696] ath10k_pci 0000:01:00.0: could not suspend target (-11)

########## wireless info END ############


```

---

### Post by jeremy31 on 2017-01-20
I would download [http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.6_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157.6_all.deb)
Transfer it to the Ubuntu desktop, then in terminal
```
cd Desktop
sudo dpkg -i linux-firmware_1.157.6_all.deb
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Reboot

---

### Post by skeletonxf on 2017-01-20
Thank you very much the laptop wifi works now.

---

### Post by ajgreeny on 2017-01-20
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

