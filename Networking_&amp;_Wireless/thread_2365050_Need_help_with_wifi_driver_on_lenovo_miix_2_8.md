---
title: "Need help with wifi driver on lenovo miix 2 8"
date: 2017-07-01
forum: Networking &amp; Wireless
---

### Post by login721 on 2017-07-01
Hello .
I'm new to ubuntu . I just installed xubuntu on lenovo miix2-8 .But wifi not work ,wifi card is not showed in  lspci and lsusb .In windows the wificard is Broadcom 802.11abgn Wireless SDIO , [COLOR=#252525][FONT=sans-serif]VID_02D0&PID_4324&FN_1.

this is result of lspci:

[/FONT][/COLOR]```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI [8086:0f35] (rev 09)
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 09)
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 09)

```[COLOR=#252525][FONT=sans-serif]

lsusb:
[/FONT][/COLOR]```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0fce:7197 Sony Ericsson Mobile Communications AB 
Bus 001 Device 004: ID 056e:6022 Elecom Co., Ltd 
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```[COLOR=#252525][FONT=sans-serif]

wireless-info.txt
[/FONT][/COLOR]```

########## wireless info START ##########

Report from: 01 Jul 2017 15:22 UTC +0000

Booted last: 01 Jul 2017 00:00 UTC +0000

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/preseed/xubuntu.seed, boot=casper, nomodeset, ---

##### desktop ###########################

Xubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0fce:7197 Sony Ericsson Mobile Communications AB 
Bus 001 Device 004: ID 056e:6022 Elecom Co., Ltd 
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: LNV4752:00: GPS
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

snd_soc_sst_bytcr_rt5640    20480  0
brcmfmac              303104  0
brcmutil               16384  1 brcmfmac
cfg80211              581632  1 brcmfmac
snd_soc_rt5645        147456  0
snd_soc_rt5640        118784  2 snd_soc_sst_bytcr_rt5640
snd_soc_rl6231         16384  2 snd_soc_rt5640,snd_soc_rt5645
snd_soc_sst_match      16384  2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_core          233472  4 snd_soc_sst_bytcr_rt5640,snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform
snd_pcm               110592  6 snd_soc_sst_bytcr_rt5640,snd_pcm_dmaengine,snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform,snd_soc_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s20u2u4 Link encap:Ethernet  HWaddr <MAC 'enp0s20u2u4' [IF1]>  
          inet addr:192.168.42.108  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::3253:f547:8a76:43a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2143344 (2.1 MB)  TX bytes:332930 (332.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:150699 (150.6 KB)  TX bytes:150699 (150.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20u2u4  no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20u2u4
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20u2u4
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20u2u4

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1361     1  0 15:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u2u4
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Sony
GENERAL.PRODUCT:                        C5503
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u2u4' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.0/net/enp0s20u2u4
GENERAL.IP-IFACE:                       enp0s20u2u4
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       fec96e74-f485-3758-884a-6a96f46e5e3c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   fec96e74-f485-3758-884a-6a96f46e5e3c | Wired connection 1
IP4.ADDRESS[1]:                         192.168.42.108/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.108
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1498925739
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = xubuntu
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::3253:f547:8a76:43a1/64
IP6.GATEWAY:                            

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

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

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

enp0s20u2u4  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s20u2u4  Interface doesn't support scanning.

##### module infos ######################

[brcmfmac]
filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365c-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     268EF37D0EAA7FC577A8EC8
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:Do not use internal roaming engine (int)

[brcmutil]
filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     389318E018771B5453D0B02
depends:        
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 

[cfg80211]
filename:       /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]

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

##### udev rules ########################

##### dmesg #############################

[  360.143369] rndis_host 1-2.4:1.0 enp0s20u2u4: renamed from usb0
[  360.180963] IPv6: ADDRCONF(NETDEV_UP): enp0s20u2u4: link is not ready

########## wireless info END ############
```[COLOR=#252525][FONT=sans-serif]

Thanks in advance !
Sorry for my bad English![/FONT][/COLOR]

---

### Post by praseodym on 2017-07-01
Looks like a SDIO card, driver **brcmfmac** is loaded.

```
cat /sys/bus/sdio/devices/*
cat /sys/bus/sdio/devices/*/uevent
```

---

### Post by login721 on 2017-07-01
Thank for reply!.
this is output'

cat /sys/bus/sdio/devices/*
```
cat: '/sys/bus/sdio/devices/mmc0:0001:1': Is a directory
cat: '/sys/bus/sdio/devices/mmc0:0001:2': Is a directory

```

cat /sys/bus/sdio/devices/*/uevent
```
SDIO_CLASS=00
SDIO_ID=02D0:4324
MODALIAS=sdio:c00v02D0d4324
DRIVER=brcmfmac
SDIO_CLASS=00
SDIO_ID=02D0:4324
MODALIAS=sdio:c00v02D0d4324

```

---

### Post by praseodym on 2017-07-01
Okay, lets check
```

dmesg | egrep 'brcm|SDIO|4324|fail'
```
and
```

modinfo brcmfmac
```

---

### Post by login721 on 2017-07-01
dmesg | egrep 'brcm|SDIO|4324|fail'
```

[    0.233723] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.233764] acpi PNP0A08:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[   17.531487] mmc0: new ultra high speed DDR50 SDIO card at address 0001
[   39.431654] i2c i2c-0: i2c read failed
[   39.520091] thermal thermal_zone6: failed to read out thermal zone (-5)
[   39.551803] i2c i2c-0: i2c read failed
[   39.752226] i2c i2c-0: i2c read failed
[   39.827807] i2c i2c-0: i2c read failed
[   39.991687] i2c i2c-0: i2c read failed
[   40.095647] i2c i2c-0: i2c read failed
[   41.019685] i2c i2c-0: i2c read failed
[   41.415279] usbcore: registered new interface driver brcmfmac
[   41.524724] brcmfmac mmc0:0001:1: Direct firmware load for brcm/brcmfmac43241b4-sdio.txt failed with error -2
[   42.547902] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[   43.556111] brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50

```


modinfo brcmfmac
```

filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365c-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     268EF37D0EAA7FC577A8EC8
alias:          usb:v0A5Cp0BDCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep3101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD1Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5CpBD1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          pci:v000014E4d0000440Dsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043C5sv*sd*bc02sc80i*
alias:          pci:v000014E4d000043C4sv*sd*bc02sc80i*
alias:          pci:v000014E4d000043C3sv*sd*bc02sc80i*
alias:          pci:v000014E4d00004365sv000014E4sd00004365bc02sc80i*
alias:          pci:v000014E4d000043CCsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043CBsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043CAsv*sd*bc02sc80i*
alias:          pci:v000014E4d0000AA52sv*sd*bc02sc80i*
alias:          pci:v000014E4d000043BCsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043BBsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043BAsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043EFsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043E9sv*sd*bc02sc80i*
alias:          pci:v000014E4d000043D9sv*sd*bc02sc80i*
alias:          pci:v000014E4d000043D3sv*sd*bc02sc80i*
alias:          pci:v000014E4d000043ECsv*sd*bc02sc80i*
alias:          pci:v000014E4d000043A3sv*sd*bc02sc80i*
alias:          sdio:c*v02D0d4356*
alias:          sdio:c*v02D0d4354*
alias:          sdio:c*v02D0d4345*
alias:          sdio:c*v02D0dA9A6*
alias:          sdio:c*v02D0d4335*
alias:          sdio:c*v02D0dA962*
alias:          sdio:c*v02D0dA94D*
alias:          sdio:c*v02D0dA94C*
alias:          sdio:c*v02D0d4334*
alias:          sdio:c*v02D0d4330*
alias:          sdio:c*v02D0d4329*
alias:          sdio:c*v02D0d4324*
alias:          sdio:c*v02D0dA887*
depends:        brcmutil,cfg80211
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:Do not use internal roaming engine (int)

```

i just search for [COLOR=#000000][FONT=&amp]brcmfmac43241b4-sdio.txt , but its nowhere to be found .Some not networking related problem is , ubuntu not [/FONT][/COLOR]recognize [COLOR=#000000][FONT=&amp]the battery and i can't adjust screen brightness.[/FONT][/COLOR]

---

### Post by login721 on 2017-07-02
update : i made file [COLOR=#000000]brcmfmac43241b4-sdio.txt[/COLOR]  in [COLOR=#000000]/lib/firmware/brcm/ and paste the content of [/COLOR]https://github.com/jfwells/linux-asus-t100ta/blob/master/nvram/lib/firmware/brcm/brcmfmac43241b4-sdio.txt
replace the mac addr with the card's mac , reboot and wifi works.But bluetooth ,battery ,screen brightness are not.

---

### Post by praseodym on 2017-07-02
Ok, if wireless works the thread can be closed here. Please open new threads for the other problems

---

