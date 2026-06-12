---
title: "Installed new network adapter in laptop, unsure of specific issue. &quot;network disabled&quot;"
date: 2016-02-21
forum: Networking &amp; Wireless
---

### Post by Coaltrain on 2016-02-21
Hello, I recently replaced the realtek wifi card that was causing me issues with a new intel 5100agn wireless card.  The realtek card had serious driver issues, and I heard that intel had better support, so i decided to upgrade.  I replaced the card, but am having issues.  When I first boot my computer, I am able to see a list of networks to connect to via wifi, but can't actually access the internet.  Most of the time it doesn't show that it connects, the icon just goes in circles then disconnects.  If I try to connect again, I frequently get the error 

*"(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/2' failed in libnm-glib."*

After which, all of the networks that were visible previously disappear.  There are several possibilities in my mind, but I'm not particularly well versed in linux.  First, the new network adapter has two leads for wifi antennas, but there was only one lead available in my laptop. I don't think this is truly the issue though, since the previous card also had two possible leads, but was only connected to a single antenna.  Also, the list of networks shows up, so it's clearly able to connect with them on some level.  

When I run sudo lshw -c network, it outputs 

```
*-network DISABLED      
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 00:24:d6:2e:aa:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-27-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:93 memory:d0700000-d0701fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: enp3s0f2
       version: 06
       serial: 08:62:66:6f:f6:ef
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8402-1_0.0.1 10/26/11 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:90 ioport:e000(size=256) memory:d0614000-d0614fff memory:d0610000-d0613fff


```

Seeing that the network is disabled, some solutions I've seen said to use "rfkill list all" to show soft blocks and hard blocks. However, when I run the command, it outputs

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

I'm really not sure what could be the issue here, any suggestions?  here's the output from a few other commands, thank you for the help in advance.


```
iwconfig
wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

enp3s0f2  no wireless extensions.


```

```
lspci
00:00.0 Host bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
00:13.0 SATA controller: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB xHCI (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine (rev 0e)
00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 (rev 0e)
00:1c.3 PCI bridge: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 4 (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation Atom Processor E3800 Series SMBus Controller (rev 0e)
02:00.0 Network controller: Intel Corporation WiFi Link 5100
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5286 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 06)


```

---

### Post by Bucky Ball on 2016-02-21
Welcome. You don't mention the make and model of your laptop nor the release you are using, but just wondering if you have a wireless switch on the laptop itself. Control+F2 or something? Thought we'd better check before going any further. Things actually look ok apart from the fact your card is 'Disabled'. 

If not, please see the 'wireless info script' link in my signature and post the output of that here (using code tags, also linked in my sig).

PS: You only have one contact for the two leads for the wireless card? Never heard of that before and may be more significant than you're thinking. New one on me. :-k

---

### Post by Coaltrain on 2016-02-22
Here is the output of the script.  Also, I've investigated what you said about there only being one lead, but haven't come up with anyone else running into a similar situation.  For reference, I am using an ASUS x200MA, and the previous network card was a Realtek RTL8188EE

```

########## wireless info START ##########

Report from: 21 Feb 2016 23:55 CST -0600

Booted last: 21 Feb 2016 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 04f2:b409 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0457:1028 Silicon Integrated Systems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
iwldvm                233472  0
mac80211              733184  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              548864  3 iwlwifi,mac80211,iwldvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

auto wlp2s0
iface wlp2s0 dhcp

##### ifconfig ##########################

enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF]>  
          inet addr:129.93.207.151  Bcast:129.93.207.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0f2' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6900857 (6.9 MB)  TX bytes:976177 (976.1 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0f2  no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.93.207.254  0.0.0.0         UG    100    0        0 enp3s0f2
129.93.6.144    129.93.207.254  255.255.255.255 UGH   100    0        0 enp3s0f2
129.93.207.0    0.0.0.0         255.255.255.0   U     100    0        0 enp3s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0f2

##### resolv.conf #######################

nameserver 127.0.1.1
search unl.edu

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       538     1  0 23:47 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
GENERAL.IP-IFACE:                       enp3s0f2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0782fb9a-a17b-4300-8454-bb8638ba3553
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0782fb9a-a17b-4300-8454-bb8638ba3553 | Wired connection 1
IP4.ADDRESS[1]:                         129.93.207.151/24
IP4.GATEWAY:                            129.93.207.254
IP4.ROUTE[1]:                           dst = 129.93.6.144/32, nh = 129.93.207.254, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             129.93.6.144
IP4.DNS[2]:                             129.93.6.92
IP4.DOMAIN[1]:                          unl.edu
DHCP4.OPTION[1]:                        network_number = 129.93.207.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1456122103
DHCP4.OPTION[9]:                        domain_name = unl.edu
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 129.93.207.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 129.93.207.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 1800
DHCP4.OPTION[16]:                       ip_address = 129.93.207.151
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 129.93.6.144 129.93.6.92
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 129.93.6.144
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0f2' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        WiFi Link 5100 (AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-27-generic
GENERAL.FIRMWARE-VERSION:               8.83.5.1 build 33692
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/UNL-AIR]] (600 root)
[connection] id=UNL-AIR | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=UNL-AIR
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

enp3s0f2  no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

wlp2s0    Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp3s0f2  Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     B715639CA9F6E3BA25A93FD
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FBF6EA073A00B4F3836226E
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     75997E53B9CC3BD2CA79F3B
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
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

[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   62.188624] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[   63.964586] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[   63.964644] iwlwifi 0000:02:00.0: Unable to initialize device.
[   63.964923] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x0
[   74.894120] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[   74.962469] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   80.595489] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[   80.595500] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[   82.371516] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[   82.371624] iwlwifi 0000:02:00.0: Unable to initialize device.
[  216.930863] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  216.999127] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  222.631040] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  222.631069] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  224.406254] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  224.406384] iwlwifi 0000:02:00.0: Unable to initialize device.
[  244.261944] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  244.330458] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  249.965244] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  249.965268] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  251.742442] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  251.742571] iwlwifi 0000:02:00.0: Unable to initialize device.
[  251.929491] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  251.997833] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  257.631262] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  257.631289] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  259.407442] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  259.407579] iwlwifi 0000:02:00.0: Unable to initialize device.
[  259.413172] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  259.481500] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  265.113530] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  265.113558] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  266.891036] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  266.891126] iwlwifi 0000:02:00.0: Unable to initialize device.
[  266.907768] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  276.491763] r8169 0000:03:00.2 enp3s0f2: link up
[  276.491803] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0f2: link becomes ready

########## wireless info END ############


```

---

### Post by Bucky Ball on 2016-02-22
Ok. You have Network Manager and Wicd installed. Remove Wicd as that has nothing to do with this. 

Network Manager and Wicd will not play together and that may be the only thing that is preventing your card from connecting. 

Remove Wicd, reboot, plug the dongle in, tell us exactly what happens and perhaps post the wireless info again.

(Also, please confirm: You are in America/Chicago?)

Have you also investigated whether the machine has a wireless on/off key/button? When you reboot the machine after doing the above, is the wireless light on the machine on or off?

---

### Post by Coaltrain on 2016-02-22
I removed Wicd, rebooted, and the wireless light flashed during boot up, as well as when I got to my desktop and tried to connect to a visible network.  In fact, it still is flickering intermittently.  As for the wireless on/off key, It appears to have a FN + f2 wireless toggle, but I'm not sure if it is working, and I have tried connecting after the key combination as well as before.  I am still able to view networks, so I don't believe that the on/off key has an effect. I am in America, Lincoln NE if it is important to know.  Here is the output of the script now

```

########## wireless info START ##########

Report from: 22 Feb 2016 00:16 CST -0600

Booted last: 22 Feb 2016 00:00 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:49:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 04f2:b409 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0457:1028 Silicon Integrated Systems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
iwldvm                233472  0
mac80211              733184  1 iwldvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
iwlwifi               200704  1 iwldvm
cfg80211              548864  3 iwlwifi,mac80211,iwldvm
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

auto wlp2s0
iface wlp2s0 dhcp

##### ifconfig ##########################

enp3s0f2  Link encap:Ethernet  HWaddr <MAC 'enp3s0f2' [IF]>  
          inet addr:129.93.207.21  Bcast:129.93.207.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp3s0f2' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:726845 (726.8 KB)  TX bytes:85654 (85.6 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0f2  no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.93.207.254  0.0.0.0         UG    100    0        0 enp3s0f2
129.93.6.144    129.93.207.254  255.255.255.255 UGH   100    0        0 enp3s0f2
129.93.207.0    0.0.0.0         255.255.255.0   U     100    0        0 enp3s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0f2

##### resolv.conf #######################

nameserver 127.0.1.1
search unl.edu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       524     1  6 00:14 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp3s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/enp3s0f2
GENERAL.IP-IFACE:                       enp3s0f2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c2e42fef-97a1-4f0c-b42d-32baf40aa453
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c2e42fef-97a1-4f0c-b42d-32baf40aa453 | Wired connection 1
IP4.ADDRESS[1]:                         129.93.207.21/24
IP4.GATEWAY:                            129.93.207.254
IP4.ROUTE[1]:                           dst = 129.93.6.144/32, nh = 129.93.207.254, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             129.93.6.144
IP4.DNS[2]:                             129.93.6.92
IP4.DOMAIN[1]:                          unl.edu
DHCP4.OPTION[1]:                        network_number = 129.93.207.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1456123501
DHCP4.OPTION[9]:                        domain_name = unl.edu
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 129.93.207.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 129.93.207.254
DHCP4.OPTION[15]:                       dhcp_lease_time = 1800
DHCP4.OPTION[16]:                       ip_address = 129.93.207.21
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 129.93.6.144 129.93.6.92
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 129.93.6.144
IP6.ADDRESS[1]:                         fe80::<IP6 'enp3s0f2' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        WiFi Link 5100 (AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-27-generic
GENERAL.FIRMWARE-VERSION:               8.83.5.1 build 33692
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   80b18f8a-3519-4808-8859-e9597236593f | UNL-AIR

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN5]>  Infra  56    5280 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN6]>  Infra  153   5765 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2 802.1X  no        
--                               <MAC '--' [AN8]>  Infra  36    5180 MHz  0 Mbit/s   69      &#9602;&#9604;&#9606;_  WEP          no        
--                               <MAC '--' [AN9]>  Infra  165   5825 MHz  0 Mbit/s   52      &#9602;&#9604;__  WEP          no        
UNL-AIR                          <MAC 'UNL-AIR' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN12]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN14]>  Infra  161   5805 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN16]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN17]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN18]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN19]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN20]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN21]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN22]>  Infra  40    5200 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN23]>  Infra  153   5765 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN24]>  Infra  153   5765 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN25]>  Infra  153   5765 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN26]>  Infra  40    5200 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN27]>  Infra  153   5765 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN28]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN29]>  Infra  44    5220 MHz  54 Mbit/s  27      &#9602;___  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN30]>  Infra  44    5220 MHz  54 Mbit/s  25      &#9602;___  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN31]>  Infra  11    2462 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN32]>  Infra  161   5805 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2 802.1X  no        
CellSpot_2.4GHz_80A0             <MAC 'CellSpot_2.4GHz_80A0' [AN33]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN34]>  Infra  161   5805 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN35]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN36]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN37]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN38]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-Conference                   <MAC 'UNL-Conference' [AN39]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN40]>  Infra  56    5280 MHz  54 Mbit/s  49      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN41]>  Infra  161   5805 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN42]>  Infra  161   5805 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN43]>  Infra  161   5805 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN44]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN45]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN46]>  Infra  1     2412 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN47]>  Infra  40    5200 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN48]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN49]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN50]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN51]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
HP-Print-5D-Officejet Pro 8610   <MAC 'HP-Print-5D-Officejet Pro 8610' [AN52]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN53]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN54]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA2 802.1X  no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN55]>  Infra  161   5805 MHz  54 Mbit/s  54      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN56]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN57]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN58]>  Infra  161   5805 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN59]>  Infra  161   5805 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN60]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN61]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN62]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN63]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN64]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN65]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN66]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN67]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN68]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN69]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN70]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN71]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN72]>  Infra  40    5200 MHz  54 Mbit/s  22      &#9602;___  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN73]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
DIRECT-54-HP ENVY 5660 series    <MAC 'DIRECT-54-HP ENVY 5660 series' [AN74]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN75]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN76]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN77]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR                          <MAC 'UNL-AIR' [AN78]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN79]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN80]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN81]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN82]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN83]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN84]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN85]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --           no        
HP-Print-79-Officejet 4630       <MAC 'HP-Print-79-Officejet 4630' [AN86]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN87]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN88]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN89]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN90]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN91]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN92]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  --           no        
DIRECT-9E-HP ENVY 7640 series    <MAC 'DIRECT-9E-HP ENVY 7640 series' [AN93]>  Infra  6     2437 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2         no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN94]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
UNL-Guest                        <MAC 'UNL-Guest' [AN95]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN96]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN97]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN98]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN99]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN100]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN101]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN102]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN103]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN104]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN105]>  Infra  1     2412 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN106]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN107]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN108]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN109]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN110]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN111]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN112]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN113]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN114]>  Infra  11    2462 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN115]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN116]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-Guest                        <MAC 'UNL-Guest' [AN117]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN118]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN119]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN120]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN121]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN122]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN123]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN124]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN125]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN126]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN127]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN128]>  Infra  40    5200 MHz  54 Mbit/s  30      &#9602;___  WPA2 802.1X  no        
HP-Print-D1-Deskjet 2540 series  <MAC 'HP-Print-D1-Deskjet 2540 series' [AN129]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2         no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN130]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-Conference                   <MAC 'UNL-Conference' [AN131]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN132]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN133]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN134]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN135]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN136]>  Infra  40    5200 MHz  54 Mbit/s  29      &#9602;___  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN137]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN138]>  Infra  11    2462 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN139]>  Infra  11    2462 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN140]>  Infra  11    2462 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN141]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN142]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN143]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN144]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN145]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN146]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN147]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN148]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-Guest                        <MAC 'UNL-Guest' [AN149]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN150]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN151]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN152]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN153]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN154]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN155]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN156]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN157]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN158]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN159]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN160]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN161]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN162]>  Infra  64    5320 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X  no        
UNL-Guest                        <MAC 'UNL-Guest' [AN163]>  Infra  64    5320 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN164]>  Infra  64    5320 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Wireless-Registration        <MAC 'UNL-Wireless-Registration' [AN165]>  Infra  64    5320 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN166]>  Infra  64    5320 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN167]>  Infra  48    5240 MHz  54 Mbit/s  22      &#9602;___  --           no        
UNL-AIR-E                        <MAC 'UNL-AIR-E' [AN168]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2 802.1X  no        
UNL-AIR                          <MAC 'UNL-AIR' [AN169]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN170]>  Infra  56    5280 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
UNL-Guest                        <MAC 'UNL-Guest' [AN171]>  Infra  56    5280 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN172]>  Infra  44    5220 MHz  54 Mbit/s  24      &#9602;___  --           no        
UNL-Conference                   <MAC 'UNL-Conference' [AN173]>  Infra  44    5220 MHz  54 Mbit/s  24      &#9602;___  --           no        
--                               <MAC '--' [AN174]>  Infra  157   5785 MHz  0 Mbit/s   17      &#9602;___  WEP          no        
UNL-AIR                          <MAC 'UNL-AIR' [AN175]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
UNL-AIR                          <MAC 'UNL-AIR' [AN176]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        

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

[[/etc/NetworkManager/system-connections/UNL-AIR]] (600 root)
[connection] id=UNL-AIR | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=UNL-AIR
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

enp3s0f2  no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

wlp2s0    Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp3s0f2  Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     B715639CA9F6E3BA25A93FD
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     FBF6EA073A00B4F3836226E
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     75997E53B9CC3BD2CA79F3B
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
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

[cfg80211]
filename:       /lib/modules/4.2.0-27-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-27-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        94:21:CE:78:F7:DD:69:32:D7:A7:1D:3B:AB:89:BB:03:6A:FA:29:EB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  127.070119] iwlwifi 0000:02:00.0: Log capacity -1515870811 is bogus, limit to 256 entries
[  127.070123] iwlwifi 0000:02:00.0: Log write index -1515870811 is bogus, limit to 256
[  127.070127] iwlwifi 0000:02:00.0: Start IWL Event Log Dump: display last 20 entries
[  128.864798] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  128.933192] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  134.569874] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  134.569897] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  136.346703] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  136.346782] iwlwifi 0000:02:00.0: Unable to initialize device.
[  136.347143] wlp2s0:  Failed check-sdata-in-driver check, flags: 0x4
[  136.349919] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  136.418259] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  142.051121] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  142.051133] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  143.829105] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  143.829244] iwlwifi 0000:02:00.0: Unable to initialize device.
[  143.849863] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  143.882664] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[  143.956586] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  149.597275] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  149.597303] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  151.373837] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  151.373970] iwlwifi 0000:02:00.0: Unable to initialize device.
[  151.378472] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

########## wireless info END ############


```

---

### Post by Bucky Ball on 2016-02-22
Try this:

```
ifconfig wlp2s0 up
```

Let us know if you connect or it spits an error. Your output looks healthier and you appear to have the correct driver installed and Network Manager only. Progress. ;)

The card still seems to be disabled so it looks like it is not switching on at boot for some reason. If we can get it 'abled' it may be working fine and that is your issue.

---

### Post by Coaltrain on 2016-02-22
After running that using sudo, I got the output of.  Still unable to connect
```
[COLOR=#333333][FONT=sans-serif]SIOCSIFFLAGS: Connection timed out[/FONT][/COLOR]
```

---

### Post by Coaltrain on 2016-02-24
Does anyone have any ideas what could be going on?

---

### Post by chili555 on 2016-02-24
> **Coaltrain said:**
> Does anyone have any ideas what could be going on?Probably. Please see:> [  149.597275] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[  149.597303] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[  151.373837] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[  151.373970] iwlwifi 0000:02:00.0: Unable to initialize device.
[  151.378472] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not readyIt seems to load the -8 firmware here:> driver=iwlwifi driverversion=4.2.0-27-generic firmware=[COLOR="#FF0000"]8[/COLOR].83.5.1 build 33692 This is, as far as Google and I can find, the latest.

The second thing I suggest you check is related to this:>  I replaced the card, but am having issues. I wonder if either the card is not seated correctly in its slot or if it was received by you as defective.

I'd hate to call out any of our fine, upstanding resellers, but it is not unknown for dodgy, twitchy electronics to be sold on line.

---

