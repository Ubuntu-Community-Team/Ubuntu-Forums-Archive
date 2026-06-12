---
title: "Internet not functional on Dell Precision 3520 with Ubuntu 16.04 preinstalled"
date: 2018-01-20
forum: Networking &amp; Wireless
---

### Post by dan422 on 2018-01-20
Hello. I just got a new Dell Precision 3520. When I was customizing the laptop before buying, I opted for an Intel wireless card over the default Qualcomm one (probably a mistake in hindsight). I can scan for and "connect" to my WIFI, but the internet does not actually work. I get the same result when I connect via ethernet. I have live booted into Ubuntu 17.10, Manjaro, and Antergos and they all have the same issue. Here is the output for some terminal commands:

```
# lsmod

Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  2
ccm                    20480  2
rfcomm                 69632  0
nvram                  16384  0
msr                    16384  0
snd_hda_codec_hdmi     49152  1
cmac                   16384  2
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
btusb                  45056  0
btrtl                  16384  1 btusb
bbswitch               16384  0
bnep                   20480  2
joydev                 20480  0
hid_alps               16384  0
arc4                   16384  2
dell_led               16384  1
i2c_designware_platform    16384  0
i2c_designware_core    20480  1 i2c_designware_platform
dell_wmi               16384  0
snd_hda_codec_realtek    94208  1
mxm_wmi                16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
dell_rbtn              16384  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
intel_rapl             20480  0
dell_smm_hwmon         16384  0
iwlmvm                425984  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
mac80211              700416  1 iwlmvm
kvm_intel             172032  0
kvm                   544768  1 kvm_intel
iwlwifi               315392  1 iwlmvm
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
rtsx_pci_ms            20480  0
ghash_clmulni_intel    16384  0
memstick               20480  1 rtsx_pci_ms
cfg80211              589824  3 iwlwifi,mac80211,iwlmvm
aesni_intel           167936  6
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
snd_hda_intel          40960  6
ablk_helper            16384  1 aesni_intel
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_core           90112  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
input_leds             16384  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  23 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd
hci_uart               77824  0
mei_me                 36864  0
idma64                 20480  0
btbcm                  16384  2 btusb,hci_uart
virt_dma               16384  1 idma64
shpchp                 36864  0
mei                    98304  1 mei_me
btqca                  16384  1 hci_uart
btintel                16384  2 btusb,hci_uart
processor_thermal_device    16384  0
intel_lpss_pci         16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
bluetooth             520192  31 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
int3400_thermal        16384  0
int3403_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 processor_thermal_device,int3403_thermal
intel_hid              16384  0
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
sparse_keymap          16384  2 dell_wmi,intel_hid
dell_smo8800           16384  0
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
acpi_pad               24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
rtsx_pci_sdmmc         24576  0
i915_bpo             1306624  6
intel_ips              20480  1 i915_bpo
i2c_algo_bit           16384  1 i915_bpo
drm_kms_helper        155648  1 i915_bpo
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
e1000e                237568  0
sysimgblt              16384  1 drm_kms_helper
ptp                    20480  1 e1000e
fb_sys_fops            16384  1 drm_kms_helper
pps_core               20480  1 ptp
drm                   364544  7 i915_bpo,drm_kms_helper
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   36864  3
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  2 i2c_hid,hid_alps
pinctrl_sunrisepoint    28672  0
video                  40960  3 i915_bpo,dell_wmi,dell_laptop
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0


# rfkill list

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

# ifconfig 

enp0s31f6 Link encap:Ethernet  HWaddr 8c:ec:4b:f6:87:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:ef300000-ef320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:180632 (180.6 KB)  TX bytes:180632 (180.6 KB)

wlp2s0    Link encap:Ethernet  HWaddr 60:f6:77:f9:49:fd  
          inet6 addr: fe80::480e:78c1:9055:2c78/64 Scope:Link
          inet6 addr: fe80::4ec2:e69c:8166:77f1/64 Scope:Link
          inet6 addr: fe80::1a7f:446d:c691:c24e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62539 (62.5 KB)  TX bytes:4622 (4.6 KB)

# iwconfig

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

wlp2s0    no wireless extensions.

# route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


# GUI Connection Information:
General:
Interface:             802.11 WiFi (wlp2s0)
Hardware Address:         60:F6:77:F9:49:FD
Driver:             iwlwifi
Speed                 130 Mb/s
Security            WPA/WPA2

IPv4:
IP Address:            Unknown
Broadcast Address        Unknown
Subnet Mask:             Unknown

IPv6:
IP Address:             fe80::1a7f:446d:c691:c24e/64
```


Other devices connect to my router just fine. Should I return the laptop and order it again with the default WIFI card, or is it a simple fix? Thanks in advance for any help.

---

### Post by jeremy31 on 2018-01-20
*Thread moved to **Networking & Wireless**.*
Please see the wireless script link in my signature and post results

---

### Post by dan422 on 2018-01-20
Here is the results of the script:
```

########## wireless info START ##########

Report from: 20 Jan 2018 09:51 CST -0600

Booted last: 20 Jan 2018 00:00 CST -0600

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, locale=en_US, acpi_rev_override, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (5) I219-LM [8086:15e3] (rev 31)
    Subsystem: Dell Ethernet Connection (5) I219-LM [1028:07a9]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:0050]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 011: ID 23a9:ef18  
Bus 001 Device 003: ID 1bcf:2b96 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
mxm_wmi                16384  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
iwlmvm                425984  0
mac80211              700416  1 iwlmvm
iwlwifi               315392  1 iwlmvm
cfg80211              589824  3 iwlwifi,mac80211,iwlmvm
compat                 16384  4 cfg80211,iwlwifi,mac80211,iwlmvm
wmi                    20480  3 dell_led,dell_wmi,mxm_wmi
sparse_keymap          16384  2 dell_wmi,intel_hid
video                  40960  3 i915_bpo,dell_wmi,dell_laptop

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:ef300000-ef320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:16496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1223800 (1.2 MB)  TX bytes:1223800 (1.2 MB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet6 addr: fe80::4ec2:e69c:8166:77f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421495 (421.4 KB)  TX bytes:23614 (23.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

wlp2s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       886     1  0 08:07 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Sunrise Point-H PCI Express Root Port
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-83-generic
GENERAL.FIRMWARE-VERSION:               22.361476.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ISSFI
GENERAL.CON-UUID:                       8ee0cd0a-ae8e-4342-ac69-879698f9a928
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     86 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   8ee0cd0a-ae8e-4342-ac69-879698f9a928 | ISSFI
IP6.ADDRESS[1]:                         fe80::4ec2:e69c:8166:77f1/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (5) I219-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                   <MAC '--' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       no        
ISSFI                <MAC 'ISSFI' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
Kodak_Verite55:1013  <MAC 'Kodak_Verite55:1013' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  --         no        
2WIRE947             <MAC '2WIRE947' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1       no        
ATT6STF4Bx           <MAC 'ATT6STF4Bx' [AN5]>  Infra  7     2442 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
ISSFI                <MAC 'ISSFI' [AN6]>  Infra  36    5180 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
FBISurveillanceVan   <MAC 'FBISurveillanceVan' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
ATTMjZX84I           <MAC 'ATTMjZX84I' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
ATT3B3YpH9           <MAC 'ATT3B3YpH9' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
ATTUvec222           <MAC 'ATTUvec222' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
ATT8YVf94c           <MAC 'ATT8YVf94c' [AN11]>  Infra  4     2427 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
2WIRE769             <MAC '2WIRE769' [AN12]>  Infra  5     2432 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
Benson AP            <MAC 'Benson AP' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
ATTZWj4PtA           <MAC 'ATTZWj4PtA' [AN14]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/ISSFI]] (600 root)
[connection] id=ISSFI | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ISSFI
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s31f6  no frequency information.

wlp2s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

wlp2s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-83-generic/updates/dkms/iwlmvm.ko
version:        iwlwifi-stack-public:release/LinuxCore19:5364:f6ebfe04
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     171131C63930364D4EE527F
depends:        iwlwifi,mac80211,compat,cfg80211
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-83-generic/updates/dkms/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        iwlwifi-stack-public:release/LinuxCore19:5364:f6ebfe04
srcversion:     29989DDC149D2A8F67CFD48
depends:        cfg80211,compat
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-83-generic/updates/dkms/iwlwifi.ko
version:        iwlwifi-stack-public:release/LinuxCore19:5364:f6ebfe04
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-7265D-16.ucode
firmware:       iwlwifi-7265-16.ucode
firmware:       iwlwifi-3168-20.ucode
firmware:       iwlwifi-3160-16.ucode
firmware:       iwlwifi-7260-16.ucode
firmware:       iwlwifi-8265-20.ucode
firmware:       iwlwifi-8000-16.ucode
firmware:       iwlwifi-9000--16.ucode
srcversion:     D0BA6FAA170FAA795DA7F49
depends:        compat,cfg80211
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           debug:debug output mask (uint)
parm:           xvt_default_mode:xVT is the default operation mode (default: false) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0:4K 1:8K 2:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: N) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-83-generic/updates/dkms/cfg80211.ko
version:        iwlwifi-stack-public:release/LinuxCore19:5364:f6ebfe04
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C54F85E78C61F75A83A5D8D
depends:        compat
vermagic:       4.4.0-83-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: N
d0i3_timeout: 1000
debug: 0
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3
xvt_default_mode: N

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############

```

---

### Post by Hadaka on 2018-01-21
Hi, looks like you have the shiney new intel pci-id..
Network controller [0280]: Intel Corporation Device [**[COLOR=#ff0000]8086:24fd[/COLOR]**] (rev 78)
lets see if there is an alias for it in the kernel.
Please post the output OR state No output- i suspect it will be 'no output'
Please Copy and Paste.
```
modinfo iwlwifi | grep $(lspci -n | awk '/0280/{print toupper($3)}'| cut -c 6-)
```
Thanks.

---

### Post by dan422 on 2018-01-22
Update: My card works with WIFI networks that are not my home WIFI. Is my card just not backwards compatible with my old router? Here is the output of the command:
```

alias:          pci:v00008086d000024FDsv*sd00000012bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00001012bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00003E01bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00003E02bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00001014bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000850bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000950bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000930bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000910bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00008130bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00009110bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000810bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00008010bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00008050bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00008110bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00009010bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000150bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000050bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd000010D0bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00001010bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000130bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00001130bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00001110bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000110bc*sc*i*
alias:          pci:v00008086d000024FDsv*sd00000010bc*sc*i*

```

---

### Post by chili555 on 2018-01-22
My friend Hadaka appears to be away for a bit. We are interested in this:> My card works with WIFI networks that are not my home WIFI. Let's see what is unique about your home wifi. Please run and post: ```
sudo iwlist scan
```Just show us your access points (routers) and redact the MAC addresses like this:```
 wlp3s0    Scan completed :
          Cell 01 - [COLOR="#FF0000"]Address: xx:2B:B0:DC:45:zz[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"GBR5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001063af09824
                    Extra: Last beacon: 784ms ago
                    IE: Unknown: <snip>
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```Hadaka should be right along soon.

---

### Post by dan422 on 2018-01-22
```

  Cell 01 - Address: # Redacted unless y'all need it
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID: #Redacted
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 00054953534649
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : # Redacted unless y'all need it
                        Pairwise Ciphers (1) : # Redacted unless y'all need it
                        Authentication Suites (1) : # Redacted unless y'all need it
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : # Redacted unless y'all need it
                        Pairwise Ciphers (1) : # Redacted unless y'all need it



```

---

### Post by chili555 on 2018-01-22
> IE: WPA Version 1
                        Group Cipher : # Redacted unless y'all need it
                        Pairwise Ciphers (1) : # Redacted unless y'all need it
                        Authentication Suites (1) : # Redacted unless y'all need it
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : # Redacted unless y'all need it
                        Pairwise Ciphers (1) : # Redacted unless y'all need itWe certainly do, because that is what we suspect is the problem.

Go ahead, you can say it, TKIP. We already know.

---

### Post by chili555 on 2018-01-22
Doc Chili's Handy Dandy Intel Wireless troubleshooter

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor. Reboot.

---

### Post by dan422 on 2018-01-22
You would be wrong: 
```


 Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

---

### Post by Hadaka on 2018-01-22
Hi ..as the good Doctor says..."Ubuntu and ole chili555...HATE TKIP"
we also noted you are flying mixed wpa1 and wpa2...this also is very likely
an "issue" we suggest you correct both those items, by configuring the router
to ..wpa2 aes..NO tkip and just to make life
easy for you.. Copy and Paste to set your unset country code.
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
*Note~NOT applicable if you reside in the country of Iceland.
Thanks.

---

### Post by dan422 on 2018-01-27
Got I new router and the issue is solved.

---

### Post by Hadaka on 2018-01-27
Thanks for marking the thread Solved.

---

