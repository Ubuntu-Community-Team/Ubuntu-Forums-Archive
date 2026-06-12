---
title: "RTL8190 Issues with NDISWrapper (Terminal)"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by skeletor89 on 2020-02-04
Good evening,

I'm new to Ubuntu and I am trying to get my WiFi working, currently dualbooting with W10. I've followed all instructions on setting up NDISWrapper and I see that the NDISWrapper module is loaded in "lsmod", I have installed 2 drivers that have claims to work for the RTL8190, net8190p.inf AND net819xp.inf. Both seem to be installed and working with my device according to "ndiswrapper -l".
lsmod results;
```
kyle@Kyle-PC:~$ lsmod
Module                  Size  Used by
wl                   6451200  0
cfg80211              704512  1 wl
nls_iso8859_1          16384  1
intel_powerclamp       20480  0
coretemp               20480  0
kvm_intel             241664  0
kvm                   651264  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  1
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
crc32_pclmul           16384  0
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_codec_hdmi     57344  1
ghash_clmulni_intel    16384  0
snd_hda_intel          49152  10
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
aesni_intel           372736  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
snd_seq_midi           20480  0
glue_helper            16384  1 aesni_intel
intel_cstate           20480  0
serio_raw              20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
radeon               1454080  27
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
ttm                   102400  1 radeon
drm_kms_helper        180224  1 radeon
input_leds             16384  0
joydev                 28672  0
drm                   483328  18 drm_kms_helper,radeon,ttm
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
i2c_algo_bit           16384  1 radeon
fb_sys_fops            16384  1 drm_kms_helper
ndiswrapper           286720  0
syscopyarea            16384  1 drm_kms_helper
snd_timer              36864  2 snd_seq,snd_pcm
lpc_ich                24576  0
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
snd                    86016  31 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
soundcore              16384  1 snd
mei                   102400  1 mei_me
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
uas                    24576  0
usb_storage            73728  2 uas
hid_generic            16384  0
usbhid                 53248  0
hid                   131072  2 usbhid,hid_generic
pata_jmicron           16384  0
pata_acpi              16384  0
r8168                 540672  0

```
And my NDISWrapper -l results;
```
kyle@Kyle-PC:~$ ndiswrapper -l
net8190p : driver installed
    device (10EC:8190) present
net819xp : driver installed
    device (10EC:8190) present

```
That is the proper device id according to lspci -nn
```
kyle@Kyle-PC:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0041] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3b] (rev 06)
00:1a.1 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3e] (rev 06)
00:1a.2 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3f] (rev 06)
00:1a.7 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b36] (rev 06)
00:1d.1 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b37] (rev 06)
00:1d.2 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b38] (rev 06)
00:1d.7 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation H55 Chipset LPC Interface Controller [8086:3b06] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Juniper XT [Radeon HD 6770] [1002:68ba]
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
03:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
05:02.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c61] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved [8086:2d13] (rev 02)

```

As I understand after I run ```
sudo modprobe ndiswrapper
``` the wlan0 should initialize and I should be able to configure it through iwconfig but nothing is showing up there.

```
kyle@Kyle-PC:~$ iwconfig
enp4s0    no wireless extensions.

lo        no wireless extensions.

```

So at the moment not sure what I should do. I have read a thread on these forums that stated to run the wireless-info...script? I have done so and came back with these results.
```

########## wireless info START ##########

Report from: 04 Feb 2020 18:21 AST -0400

Booted last: 04 Feb 2020 00:00 AST -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8168

05:02.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
    Kernel modules: ndiswrapper

##### lsusb #############################

Bus 002 Device 002: ID 0781:55a1 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1b1c:1b06 Corsair 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1b1c:1b13 Corsair 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

wl                   6451200  0
cfg80211              704512  1 wl
ndiswrapper           286720  0

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp4s0' [IF1]> brd <MAC address>
    inet 192.168.0.2/24 brd 192.168.0.255 scope global dynamic noprefixroute enp4s0
       valid_lft 604139sec preferred_lft 604139sec
    inet6 fe80::9022:966a:7f7d:2e31/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp4s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp4s0 proto dhcp metric 100 
169.254.0.0/16 dev enp4s0 scope link metric 1000 
192.168.0.0/24 dev enp4s0 proto kernel scope link src 192.168.0.2 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       818     1  0 18:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Onboard Ethernet)
GENERAL.DRIVER:                         r8168
GENERAL.DRIVER-VERSION:                 8.048.00-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Profile 1
GENERAL.CON-UUID:                       4f1e8cdb-95cb-494e-9265-522b91551444
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.2/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_ntp_servers = 1
DHCP4.OPTION[3]:                        requested_domain_search = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        expiry = 1581459019
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       requested_wpad = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       dhcp_lease_time = 604800
DHCP4.OPTION[15]:                       ip_address = 192.168.0.2
DHCP4.OPTION[16]:                       requested_subnet_mask = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       host_name = Kyle-PC
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       domain_name_servers = 8.8.8.8
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       routers = 192.168.0.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::9022:966a:7f7d:2e31/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4f1e8cdb-95cb-494e-9265-522b91551444 | Profile 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Halifax (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp4s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp4s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/5.3.0-28-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.3.0-28-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/5.3.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A4BDDDDFBDE4DDDB63AAE3
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/5.3.0-28-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.60
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     15A1648753C4CE0F5FB00AA
depends:        
retpoline:      Y
name:           ndiswrapper
vermagic:       5.3.0-28-generic SMP mod_unload 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000007AAd00000044sv*sd*bc*sc*i* ndiswrapper
alias pci:v000007AAd00000046sv*sd*bc*sc*i* ndiswrapper
alias pci:v000007AAd00000047sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv00003304sd00001186bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv0000C12Dsd00001259bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000005Esd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00006896sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00007160sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000E01Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000E01Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    9.779077] enp4s0: 0xffffa8b200029000, <MAC 'enp4s0' [IF1]>, IRQ 28
[   12.930390] r8168: enp4s0: link up
[   12.930528] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready

########## wireless info END ############

```

Not sure what is going on, hopefully I have done enough so anyone can give me a hand :)

---

### Post by skeletor89 on 2020-02-04
Also, forgot to mention. For some reason the ndisgtk doesnt run for me, so I've had to do the whole setup through the Terminal. Which I don't mind just unsure why nothing would load after countless attempts at installing ndisgtk.

---

### Post by jeremy31 on 2020-02-04
Ndiswrapper has been no more than a bandaid for a broken bone for a while.  You may want to replace the internal card with one supported by the Linux kernel like the Intel 7260

---

### Post by skeletor89 on 2020-02-05
That's kind of what I've been thinking at doing. Looking at both PCI and USB options, I'd rather just replace the RTL8190 with something better but not break the bank. Any suggestions for a Canadian buyer? I was looking at a TP-Link TL-WN722N from The Source for $15.99 but I'd have to have it ordered to the store near me, however I don't want to have a USB WiFi adapter with a curious 4 y/o in the house :) I guess something for under $25 CAD if possible.

---

