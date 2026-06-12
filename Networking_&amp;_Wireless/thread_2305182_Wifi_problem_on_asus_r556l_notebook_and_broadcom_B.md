---
title: "Wifi problem on asus r556l notebook and broadcom BCM43142 integrated card"
date: 2015-12-03
forum: Networking &amp; Wireless
---

### Post by bubu3 on 2015-12-03
Though similar problem appears quite many times I could not found the solution.
Kubuntu 15.10, the BCM43142 integrated wifi device. The signal strength is relatively poor, the maximum connection speed reported is 72Mb/s, but often goes much lower, the connection drops from time to time. After moving with the laptop more than a couple of meters connection dies completely.
For this wifi card the appropriate driver bcmwl-kernel-source is used.
Similar problem experienced on Linux Mint 14.04, I also tried with USB dongle (tp-link it was I think, don't remember the model id) - exactly the same issue.
At home there are many devices (mobile phones and laptops) working fine with the router so I don't think it is the router problem which works stably. Just know there's second Dell laptop which reports (on Win7) 300Mb/s connectivity. This laptop also connects without problems in the most remote room in home, while with the Asus laptop there's no connection, at all there. There aren't any other wifi hotspots in the nearest area.
The wireless-info.txt content below:
```

########## wireless info START ##########

Report from: 03 Dec 2015 17:58 CET +0100

Booted last: 03 Dec 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 15.10
Release:        15.10
Codename:       wily

##### kernel ############################

Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
        Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
        Subsystem: Lite-On Communications Inc Device [11ad:6675]
        Kernel driver in use: wl

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04ca:2006 Lite-On Technology Corp. Broadcom BCM43142A0 Bluetooth Device
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: asus-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
wl                   6365184  0
cfg80211              548864  1 wl
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
mxm_wmi                16384  1 nouveau
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  36864  3 i915,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp3s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24724 errors:0 dropped:0 overruns:0 frame:103773
          TX packets:18080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23073219 (23.0 MB)  TX bytes:3280296 (3.2 MB)
          Interrupt:19 

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abg  ESSID:"dudki"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'dudki' [AC1]>   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

        NetworkManager

Running:

root       727     1  0 14:52 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     dudki
GENERAL.CON-UUID:                       f767d950-4a4f-47f7-87ef-fdfaae78881d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f767d950-4a4f-47f7-87ef-fdfaae78881d | dudki
IP4.ADDRESS[1]:                         192.168.2.101/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        expiry = 1449245520
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.2.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.2.101
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.2.1 192.168.2.1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       network_number = 192.168.2.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp3s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
dudki  <MAC 'dudki' [AC1]>  Infra  3     2422 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/dudki]] (600 root)
[connection] id=dudki | type=wifi | permissions=user:narya:;
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=dudki
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Warsaw (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'dudki' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"dudki"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.2.0-19-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 8391.128152] CPU: 0 PID: 440 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-19-generic #23-Ubuntu
[ 8391.128256]  [<ffffffffc0837965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 8391.128299]  [<ffffffffc0836fa4>] wl_event_handler+0x64/0x1e0 [wl]
[ 8391.128341]  [<ffffffffc0836f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[ 8400.043481] CPU: 0 PID: 440 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-19-generic #23-Ubuntu
[ 8400.043604]  [<ffffffffc0837965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 8400.043655]  [<ffffffffc0836fa4>] wl_event_handler+0x64/0x1e0 [wl]
[ 8400.043704]  [<ffffffffc0836f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[ 9127.671877] CPU: 0 PID: 440 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-19-generic #23-Ubuntu
[ 9127.671952]  [<ffffffffc0837965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 9127.671983]  [<ffffffffc0836fa4>] wl_event_handler+0x64/0x1e0 [wl]
[ 9127.672013]  [<ffffffffc0836f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[10862.092717] CPU: 0 PID: 440 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-19-generic #23-Ubuntu
[10862.092792]  [<ffffffffc0837965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[10862.092823]  [<ffffffffc0836fa4>] wl_event_handler+0x64/0x1e0 [wl]
[10862.092854]  [<ffffffffc0836f40>] ? wl_notify_scan_status+0x320/0x320 [wl]

########## wireless info END ############

```

The dmesg also shows something like this (I suppose this is when disconnecting from the network):
```

[ 9127.671778] ------------[ cut here ]------------
[ 9127.671804] WARNING: CPU: 0 PID: 440 at /build/linux-26_gwp/linux-4.2.0/net/wireless/sme.c:850 cfg80211_roamed+0x86/0xa0 [cfg80211]()
[ 9127.671806] Modules linked in: binfmt_misc rfcomm bnep rtsx_usb_ms memstick asus_nb_wmi asus_wmi sparse_keymap intel_rapl x86_pkg_temp_thermal uvcvideo intel_powerclamp coretemp snd_soc_rt5640 videobuf2_vmalloc videobuf2_memops snd_soc_rl6231 kvm_intel videobuf2_core nls_iso8859_1 v4l2_common btusb btrtl kvm videodev btbcm btintel bluetooth snd_soc_core wl(POE) media crct10dif_pclmul crc32_pclmul snd_compress ac97_bus snd_pcm_dmaengine aesni_intel snd_seq_midi snd_seq_midi_event snd_hda_codec_hdmi aes_x86_64 lrw gf128mul glue_helper snd_hda_codec_realtek ablk_helper cryptd snd_rawmidi snd_hda_codec_generic joydev input_leds snd_hda_intel serio_raw snd_hda_codec cfg80211 snd_hda_core snd_hwdep lpc_ich snd_pcm snd_seq mei_me snd_seq_device mei snd_timer shpchp snd dw_dmac dw_dmac_core processor_thermal_device
[ 9127.671851]  int3402_thermal snd_soc_sst_acpi int340x_thermal_zone intel_soc_dts_iosf soundcore iosf_mbi int3400_thermal mac_hid i2c_designware_platform spi_pxa2xx_platform 8250_dw i2c_designware_core acpi_thermal_rel parport_pc ppdev lp parport autofs4 rtsx_usb_sdmmc rtsx_usb psmouse nouveau r8169 i915 mxm_wmi ttm i2c_algo_bit mii drm_kms_helper ahci drm libahci wmi sdhci_acpi video sdhci i2c_hid hid
[ 9127.671877] CPU: 0 PID: 440 Comm: wl_event_handle Tainted: P        W  OE   4.2.0-19-generic #23-Ubuntu
[ 9127.671879] Hardware name: ASUSTeK COMPUTER INC. X555LD/X555LD, BIOS X555LD.310 08/14/2014
[ 9127.671881]  0000000000000000 00000000723af857 ffff8802242f7da8 ffffffff817e93f9
[ 9127.671884]  0000000000000000 0000000000000000 ffff8802242f7de8 ffffffff8107b3d6
[ 9127.671886]  ffff8800c88bd478 ffff880221cf3000 ffff8800ae3a2f00 0000000000000099
[ 9127.671889] Call Trace:
[ 9127.671895]  [<ffffffff817e93f9>] dump_stack+0x45/0x57
[ 9127.671900]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
[ 9127.671903]  [<ffffffff8107b50a>] warn_slowpath_null+0x1a/0x20
[ 9127.671914]  [<ffffffffc05675d6>] cfg80211_roamed+0x86/0xa0 [cfg80211]
[ 9127.671952]  [<ffffffffc0837965>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 9127.671983]  [<ffffffffc0836fa4>] wl_event_handler+0x64/0x1e0 [wl]
[ 9127.672013]  [<ffffffffc0836f40>] ? wl_notify_scan_status+0x320/0x320 [wl]
[ 9127.672017]  [<ffffffff8109a7e8>] kthread+0xd8/0xf0
[ 9127.672019]  [<ffffffff8109a710>] ? kthread_create_on_node+0x1f0/0x1f0
[ 9127.672022]  [<ffffffff817f061f>] ret_from_fork+0x3f/0x70
[ 9127.672025]  [<ffffffff8109a710>] ? kthread_create_on_node+0x1f0/0x1f0
[ 9127.672026] ---[ end trace baa2c6af9c7bfa9b ]---

```

I'll appreciate for any hints how to get the wifi working - it's my wife's laptop, just to set the appropriate priority for the problem ;)

Thanks in advance,
Bubu

---

