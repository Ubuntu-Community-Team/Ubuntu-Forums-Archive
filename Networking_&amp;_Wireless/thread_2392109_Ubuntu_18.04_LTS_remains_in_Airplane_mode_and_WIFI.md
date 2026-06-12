---
title: "Ubuntu 18.04 LTS remains in Airplane mode and WIFI not works"
date: 2018-05-16
forum: Networking &amp; Wireless
---

### Post by eliecersr on 2018-05-16
I have a Notebook ASUS X501A, and de WIFI controller is a Ralink RT5390. The Airplane mode is activated by default and de Fn+F2 combination not works. I can not unblock the WIFI.
I have instaled Windows 10 as dual boot and the wireless works fine and the Fn + F2 works perfectly and the PC change without problems to Airplane mode.
[ATTACH=CONFIG]279726[/ATTACH][ATTACH=CONFIG]279726[/ATTACH]

This is the outpup of some commands:

```
ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# rfkill 
ID TYPE DEVICE      SOFT    HARD
 0 wlan phy0   unblocked blocked
root@ubuntu:/home/ubuntu# rfkill unblock wlan
root@ubuntu:/home/ubuntu# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@ubuntu:/home/ubuntu# lsmod
Module                  Size  Used by
rndis_host             16384  0
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
nls_utf8               16384  0
isofs                  45056  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_codec_hdmi     49152  1
kvm_intel             204800  0
snd_hda_codec_realtek   102400  1
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
kvm                   593920  1 kvm_intel
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
rt2800lib             114688  2 rt2800mmio,rt2800pci
snd_hda_intel          40960  3
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  3 rt2800lib,rt2x00pci,rt2x00lib
irqbypass              16384  1 kvm
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
crct10dif_pclmul       16384  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
uvcvideo               86016  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
intel_cstate           20480  0
intel_rapl_perf        16384  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_rawmidi            32768  1 snd_seq_midi
videodev              184320  3 uvcvideo,videobuf2_core,videobuf2_v4l2
asus_nb_wmi            28672  0
joydev                 24576  0
media                  40960  2 uvcvideo,videodev
input_leds             16384  0
asus_wmi               28672  1 asus_nb_wmi
cfg80211              622592  2 rt2x00lib,mac80211
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
sparse_keymap          16384  1 asus_wmi
serio_raw              16384  0
rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
eeprom_93cx6           16384  1 rt2800pci
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
mei_me                 40960  0
snd                    81920  17 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
lpc_ich                24576  0
mei                    90112  1 mei_me
asus_wireless          16384  0
mac_hid                16384  0
soundcore              16384  1 snd
shpchp                 36864  0
sch_fq_codel           20480  3
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
overlay                77824  1
nls_iso8859_1          16384  1
dm_mirror              24576  0
dm_region_hash         20480  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
uas                    24576  0
usb_storage            69632  2 uas
i915                 1617920  11
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  0
r8169                  86016  0
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
drm                   401408  5 i915,drm_kms_helper
libahci                32768  1 ahci
mii                    16384  2 r8169,usbnet
wmi                    24576  1 asus_wmi
psmouse               147456  0
video                  40960  2 asus_wmi,i915
root@ubuntu:/home/ubuntu# 
```

```
root@ubuntu:/home/ubuntu# lspci -v
....................................................
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
    Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7d00000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-36-d0-22-8e-3e-08
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci
....................................

root@ubuntu:/home/ubuntu# 
```

And this is the output of wireless-info script:

```


########## wireless info START ##########

Report from: 16 May 2018 19:10 UTC +0000

Booted last: 16 May 2018 00:00 UTC +0000

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/preseed/ubuntu.seed, boot=casper, quiet, splash, ---

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe [105b:e054]
    Kernel driver in use: rt2800pci

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:14f7]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:5705 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 125f:db8a A-DATA Technology Co., Ltd. 
Bus 003 Device 006: ID 12d1:1050 Huawei Technologies Co., Ltd. 
Bus 003 Device 004: ID 15d9:0a4f Trust International B.V. Optical Mouse
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

rt2800pci              16384  0
rt2800mmio             16384  1 rt2800pci
rt2800lib             114688  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              778240  3 rt2800lib,rt2x00pci,rt2x00lib
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
cfg80211              622592  2 rt2x00lib,mac80211
sparse_keymap          16384  1 asus_wmi
eeprom_93cx6           16384  1 rt2800pci
wmi                    24576  1 asus_wmi
video                  40960  2 asus_wmi,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0f2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0f2' [IF1]> brd <MAC address>
3: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>
4: enp0s20u1u4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20u1u4' [IF3]> brd <MAC address>
    inet 192.168.42.153/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s20u1u4
       valid_lft 2076sec preferred_lft 2076sec
    inet6 fe80::959a:9875:f94d:4cd1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp3s0f2  no wireless extensions.

enp0s20u1u4  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.42.129 dev enp0s20u1u4 proto dhcp metric 20100 
169.254.0.0/16 dev enp0s20u1u4 scope link metric 1000 
192.168.42.0/24 dev enp0s20u1u4 proto kernel scope link src 192.168.42.153 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1187     1  0 18:42 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u1u4
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         HUAWEI
GENERAL.PRODUCT:                        ALE-L02
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u1u4' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.0/net/enp0s20u1u4
GENERAL.IP-IFACE:                       enp0s20u1u4
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       36df98f2-3891-3ba1-bb02-28c51d23d5b2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.153/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 20100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.153
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1526499917
DHCP4.OPTION[20]:                       host_name = ubuntu
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::959a:9875:f94d:4cd1/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   36df98f2-3891-3ba1-bb02-28c51d23d5b2 | Wired connection 2

GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.15.0-20-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp3s0f2  no frequency information.

enp0s20u1u4  no frequency information.

lo        no frequency information.

wlp2s0    14 channels in total; available frequencies :
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

##### iwlist scan #######################

wlp2s0    Interface doesn't support scanning : Network is down

enp3s0f2  Interface doesn't support scanning.

enp0s20u1u4  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9B5C2765C235C863C24FDE0
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2AF67DBF566ACB443136786
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2800lib]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     E3426613D56538B49359106
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00pci]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     EF62F1ED5B94FD33F012351
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00mmio]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DE3F68ABAA885403D3E251A
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rt2x00lib]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     61C3C15FFF5FD57ADC4DEB0
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   21.551311] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   21.555663] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   21.943310] rt2800pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   22.905760] IPv6: ADDRCONF(NETDEV_UP): enp3s0f2: link is not ready
[   22.995059] r8169 0000:03:00.2 enp3s0f2: link down
[   22.996188] IPv6: ADDRCONF(NETDEV_UP): enp3s0f2: link is not ready
[   23.002201] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  159.091117] rndis_host 3-1.4:1.0 enp0s20u1u4: renamed from usb0
[  159.123686] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1u4: link is not ready

########## wireless info END ############
```

---

### Post by chili555 on 2018-05-17
Please try:

```
sudo modprobe -rv asus_nb_wmi
sudo modprobe asus_nb_wmi wapf=4
```Wait a few moments for the system to notice and use the change.

Now does the Fn+F2 key combination work? If so, we can make the change persistent.

---

### Post by eliecersr on 2018-05-17
I tried the commands and the output was this:


```
[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ [/FONT][/COLOR]sudo modprobe -rv asus_nb_wmi
rmod asus_nb_wmi
rmod asus_wmi
rmod wmi
rmod sparse_keymap
[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ sudo [/FONT][/COLOR]modprobe asus_nb_wmi wapf = 4
[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$[/FONT][/COLOR]

```

But the Fn + F2 combination still does not work, and the Airplane mode remains the same.

The WIFI worked without problems until version 14.04 of Ubuntu, until with an update of the operating system stopped working.
After that I started using Windows 10 and in this operating system everything works without problems, the combination Fn + F2 activates and deactivates the Airplane mode without problems and the WIFI works correctly.
So I guess the problem is some change in the kernel after the initial version of Ubuntu 14.04 and that persists until now.

---

### Post by chili555 on 2018-05-17
Please repeat the experiment with 0, 1, 2 and 3 in succession and check again.

---

### Post by eliecersr on 2018-05-17
I tested with the combinations from 0 to 9 and the Fn + F2 still does not work. Airplane mode continues activated.

---

### Post by chili555 on 2018-05-17
From the .c file:

> /*
 * WAPF defines the behavior of the Fn+Fx wlan key
 * The significance of values is yet to be found, but
 * most of the time:
 * Bit | Bluetooth | WLAN
 *  0  | Hardware  | Hardware
 *  1  | Hardware  | Software
 *  4  | Software  | Software
 */
Please try 4 again and follow with:```
sudo rfkill unblock all
rfkill list all
```Any improvement? Don't make me break out the plasma cutter!!!

---

### Post by eliecersr on 2018-05-17
I try , and this is the output:
```

0:  phy0: Wireless LAN
                Softt blocked:  no
                Hard blocked:  yes

```

The Fn+F2 not works and Airplane mode remains.

---

### Post by chili555 on 2018-05-17
In Windows, do the key presses enable wireless on, bluetooth off and then wireless on and bluetooth on and then wireless off and bluetooth on and finally both off?

If you press the Fn+F2 repeatedly and, after each press, check:```
rfkill list all
```Is there any change whatever? Or is there any bluetooth device included at all?

---

### Post by eliecersr on 2018-05-17
I test the different combinations by activating and deactivating the WIFI from Windows, and the Airplane mode and it still does not work. The output of the rfkill is the same, after repeating the operation Fn + F2 several times.
The Notebook does not have Bluetooh, only WIFI.
From Ubuntu all combinations Fn + F1 ... F9 work well, except Fn + F2. In Windows if all work without any problem and the WIFI is activated and connected correctly.

---

### Post by praseodym on 2018-05-18
Try it again with "wapf=1"

---

### Post by jeremy31 on 2018-05-18
I would reboot the Live ISO and when the grub menu appears press e to edit, scroll down to the line that starts with linux and ends with quiet splash ---
add ```
asus_nb_wmi.wapf=4
```
So the end of the line is
```
quiet splash asus_nb_wmi.wapf=4 ---
```
Then I think you press F10 to boot

---

### Post by eliecersr on 2018-05-18
I try whith asus_nb_wmi.wapf=4 and wapf=1 but the problem remains. The Airplane mode is on and Fn+F2 don't work and WIFI is off.

---

### Post by eliecersr on 2018-05-18
I try whith wapf=1 but the problem remains. The Airplane mode is on and Fn+F2 don't work and WIFI is off.

---

### Post by praseodym on 2018-05-19
Lets try

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Reboot and show
```

rfkill list
lsmod
iwconfig
```

---

### Post by praseodym on 2018-05-20
Another option: Press the key(s) permanently or repeatedly during boot-up

---

### Post by eliecersr on 2018-05-20
I tried this option but it still does not work. Pressing (s) during start-up does not produce any change either. This is the output of the commands.

```
eliecer@asus-pc:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```[HR][/HR]```


eliecer@asus-pc:~$ lsmod
Module                  Size  Used by
xfrm_user              36864  2
xfrm4_tunnel           16384  0
tunnel4                16384  1 xfrm4_tunnel
ipcomp                 16384  0
xfrm_ipcomp            16384  1 ipcomp
esp4                   20480  0
ah4                    20480  0
af_key                 36864  0
xfrm_algo              16384  5 xfrm_user,esp4,ah4,af_key,xfrm_ipcomp
rt5390sta            1404928  0
iTCO_wdt               16384  0
iTCO_vendor_support    16384  1 iTCO_wdt
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
crct10dif_pclmul       16384  0
rndis_host             16384  0
videobuf2_memops       16384  1 videobuf2_vmalloc
cdc_ether              16384  1 rndis_host
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
usbnet                 45056  2 rndis_host,cdc_ether
media                  40960  2 uvcvideo,videodev
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_cstate           16384  0
intel_uncore          118784  0
intel_rapl_perf        16384  0
snd_hda_codec_hdmi     49152  1
rtsx_pci_ms            20480  0
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
memstick               20480  1 rtsx_pci_ms
snd_hda_intel          36864  3
joydev                 20480  0
pcspkr                 16384  0
serio_raw              16384  0
snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
sg                     32768  0
mei_me                 40960  0
acpi_cpufreq           20480  0
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_timer              32768  1 snd_pcm
snd                    86016  14 snd_hda_intel,snd_hwdep,snd_hda_codec,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
mei                   102400  1 mei_me
lpc_ich                24576  0
battery                20480  0
evdev                  24576  27
asus_wireless          16384  0
ac                     16384  0
shpchp                 36864  0
fuse                   98304  11
arc4                   16384  2
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              53248  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
eeprom_93cx6           16384  1 rt2800pci
mac80211              679936  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              598016  2 rt2x00lib,mac80211
crc_ccitt              16384  1 rt2800lib
rfkill                 24576  3 asus_wmi,cfg80211
parport_pc             28672  0
binfmt_misc            20480  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               36864  1 ip_tables
autofs4                40960  2
ext4                  589824  2
crc16                  16384  1 ext4
jbd2                  110592  1 ext4
fscrypto               28672  1 ext4
ecb                    16384  0
glue_helper            16384  0
lrw                    16384  0
gf128mul               16384  1 lrw
ablk_helper            16384  0
cryptd                 24576  2 ablk_helper,ghash_clmulni_intel
aes_x86_64             20480  0
mbcache                16384  3 ext4
btrfs                1048576  0
raid10                 49152  0
raid456               102400  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_xor,async_pq,raid456,async_memcpy,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              110592  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  1 raid456
crc32c_generic         16384  0
raid1                  36864  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
md_mod                131072  6 raid1,raid10,multipath,linear,raid0,raid456
sd_mod                 49152  6
hid_generic            16384  0
usbhid                 53248  0
hid                   122880  2 hid_generic,usbhid
i915                 1232896  28
rtsx_pci_sdmmc         24576  0
mmc_core              147456  1 rtsx_pci_sdmmc
ahci                   36864  5
libahci                32768  1 ahci
crc32c_intel           24576  6
i2c_i801               24576  0
i2c_smbus              16384  1 i2c_i801
psmouse               135168  0
libata                249856  2 ahci,libahci
scsi_mod              225280  3 sd_mod,libata,sg
ehci_pci               16384  0
ehci_hcd               81920  1 ehci_pci
i2c_algo_bit           16384  1 i915
xhci_pci               16384  0
drm_kms_helper        155648  1 i915
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
r8169                  81920  0
xhci_hcd              188416  1 xhci_pci
mii                    16384  2 r8169,usbnet
mfd_core               16384  2 lpc_ich,rtsx_pci
usbcore               249856  9 rndis_host,usbnet,uvcvideo,usbhid,ehci_hcd,cdc_ether,xhci_pci,xhci_hcd,ehci_pci
drm                   360448  13 i915,drm_kms_helper
usb_common             16384  1 usbcore
thermal                20480  0
wmi                    16384  1 asus_wmi
video                  40960  2 asus_wmi,i915
button                 16384  1 i915

```


[HR][/HR]```


eliecer@asus-pc:~$ iwconfig 
enp0s20u1  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


enp3s0f2  no wireless extensions.

```

---

### Post by jeremy31 on 2018-05-20
Try [https://ubuntuforums.org/showthread.php?t=2392109&p=13768167#post13768167](https://ubuntuforums.org/showthread.php?t=2392109&p=13768167#post13768167) again and post the results for ```
rfkill; grep [[:alnum:]] /sys/module/asus_nb_wmi/parameters/*
```

---

### Post by eliecersr on 2018-05-20
This is the output, after edit grub:
```

0:   phy0:   Wireless LAN
                   Soft blocked:  no
                   Hard blocked:  yes
4

```

---

### Post by praseodym on 2018-05-21
Try

```
echo 1 | sudo tee /sys/devices/platform/asus_laptop/wlan 
```
It loads two drivers: rt5390sta and rt2800pci. Tried to install rt5390sta?

---

### Post by eliecersr on 2018-05-24
Sorry that I delayed answering, I was on vacation and had no Internet connection. Searching in this forum I found a thread that indicated that they tried to install the rt5390sta driver, but it did not work either. The address you give me does not exist, that is, neither the directories nor the files exist.


This is the output of an ls:
```
eliecer@asus-pc:~$ ls  /sys/devices/platform/asus-nb-wmi/
cpufv   driver_override  input  lid_resume  power      uevent
driver  hwmon            leds   modalias    subsystem

```
The closest thing I found was:

```

eliecer@asus-pc:~$ ls  /sys/devices/platform/asus-nb-wmi/leds/asus\:\:wlan/
brightness  device  max_brightness  power  subsystem  trigger  uevent

```

---

### Post by gobbie2 on 2018-09-14
Did you find a resolution to this?  I have the exact same issue

---

