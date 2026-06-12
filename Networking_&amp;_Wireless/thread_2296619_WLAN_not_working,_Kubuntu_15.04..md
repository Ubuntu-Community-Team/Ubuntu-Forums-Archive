---
title: "WLAN not working, Kubuntu 15.04."
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by Lovebrrt on 2015-09-27
Hi!

I just installed kubuntu, but i cant seem to get my WLAN up and running. I have searched around the forums and tried installing ath9k drivers but it still does not work. I also followed all the steps in the sticky. The following text is from the script.

```

########## wireless info START ##########

Report from: 27 Sep 2015 15:57 CEST +0200

Booted last: 27 Sep 2015 15:15 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-28-generic #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7, acpi=off

##### desktop ###########################

Plasma

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0662]

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5286] (rev 01)

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04ca:3010 Lite-On Technology Corp. 
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                  98304  0 
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              655360  1 ath9k
cfg80211              544768  4 ath,ath9k_common,ath9k,mac80211
compat                 24576  4 cfg80211,ath9k_common,ath9k,mac80211
ath3k                  20480  0 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9682411 (9.6 MB)  TX bytes:901737 (901.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       607     1  0 15:16 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.2/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       c127f602-7474-4a4d-8863-e5d2bc727152
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c127f602-7474-4a4d-8863-e5d2bc727152 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.1.138/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.138
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1443446933
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = love-X553MA
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth0' [IF]>/64, gw = ::

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WiMAXEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Ulrikas Wi-Fi-network]] (600 root)
[connection] id=Ulrikas Wi-Fi-network | type=wifi
[wifi] ssid=Ulrikas Wi-Fi-network
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v4.2-rc1-0-gd770e55) using backports v4.2-rc1-1-0-g83a2518
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     2E72229B6C412F5CF05D433
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v4.2-rc1-0-gd770e55) using backports v4.2-rc1-1-0-g83a2518
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     A74E731B7BC6CD66D4D716C
depends:        compat,ath9k_hw,cfg80211,ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     113481A06C666B99D1DF20A
depends:        ath
vermagic:       3.19.0-28-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/3.19.0-28-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     728F9FA9D17C407477851D2
depends:        cfg80211
vermagic:       3.19.0-28-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.2-rc1-0-gd770e55) using backports v4.2-rc1-1-0-g83a2518
srcversion:     B652F2B4D96683F7D24D167
depends:        cfg80211,compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.2-rc1-0-gd770e55) using backports v4.2-rc1-1-0-g83a2518
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     37A2898EFA46715DA49F3A5
depends:        compat
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        99:11:2E:F1:A6:BA:85:BE:99:25:82:E9:FE:F3:A2:3F:1A:88:81:75
sig_hashalgo:   sha512

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    4.397042] ath9k 0000:02:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    4.397118] genirq: Flags mismatch irq 0. 00000080 (ath9k) vs. 00015a00 (timer)
[    4.397123] ath9k 0000:02:00.0: request_irq failed
[    4.397153] ath9k: probe of 0000:02:00.0 failed with error -16
[  500.044601] wl: module license 'MIXED/Proprietary' taints kernel.
[  500.056074] wl: disagrees about version of symbol wiphy_new_nm
[  500.056077] wl: Unknown symbol wiphy_new_nm (err -22)
[  500.056113] wl: disagrees about version of symbol wiphy_register
[  500.056115] wl: Unknown symbol wiphy_register (err -22)
[  500.056254] wl: disagrees about version of symbol wiphy_unregister
[  500.056256] wl: Unknown symbol wiphy_unregister (err -22)
[  500.056296] wl: disagrees about version of symbol __ieee80211_get_channel
[  500.056299] wl: Unknown symbol __ieee80211_get_channel (err -22)
[  500.056385] wl: disagrees about version of symbol wiphy_free
[  500.056387] wl: Unknown symbol wiphy_free (err -22)

########## wireless info END ############


```


Any help is greatly appreciated!

Thanks.

---

### Post by praseodym on 2015-09-27
> ```
[    4.397042] ath9k 0000:02:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
```
Before we go deep in your system, check the slot of the card.

---

### Post by Lovebrrt on 2015-09-27
How do i do that? It is a laptop so i cant open it up, sadly.

---

### Post by praseodym on 2015-09-27
Ok, then the hard way:
```

sudo cp /etc/default/grub /etc/default/grub.bak
kdesudo kate /etc/default/grub
```
Search the line:
```
GRUB_CMDLINE_LINUX=""
```
and change it to
```
GRUB_CMDLINE_LINUX="pci=biosirq"
```
Proof-read it, save, close the editor and run
```

sudo update-grub
```
Reboot and check:

```
dmesg | grep ath
iwconfig
rfkill list
lsmod
```

---

### Post by Lovebrrt on 2015-09-28
I followed your steps, these are the outputs i receive when running.

dmesg | grep ath
iwconfig
rfkill list
lsmod

```
 [FONT=monospace][COLOR=#000000]love@love-X553MA:~$ dmesg | grep ath [/COLOR]
[    0.864584] Loaded X.509 cert 'Magr[COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]ea: Glacier signing key: 99112ef1a6ba85be992582e9fef[/COLOR]
3a23f1a888175' 
[    4.365744] [COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]9k 0000:02:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq [/COLOR]
[    4.365824] genirq: Flags mismatch irq 0. 00000080 ([COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]9k) vs. 00015a00 (timer) [/COLOR]
[    4.365829] [COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]9k 0000:02:00.0: request_irq failed [/COLOR]
[    4.365857] [COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]9k: probe of 0000:02:00.0 failed with error -16 [/COLOR]
[    4.373829] usbcore: registered new interface driver [COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]3k [/COLOR]
[    5.217227] audit: type=1400 audit(1443470637.857:6): apparmor="STATUS" operation="profile
_load" profile="unconfined" name="/usr/lib/telep[COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]y/mission-control-5" pid=442 comm="apparmo[/COLOR]
r_parser" 
[    5.217244] audit: type=1400 audit(1443470637.857:7): apparmor="STATUS" operation="profile
_load" profile="unconfined" name="/usr/lib/telep[COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]y/telep[/COLOR][COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]y-*" pid=442 comm="apparmor_pars[/COLOR]
er" 
[    5.217274] audit: type=1400 audit(1443470637.857:10): apparmor="STATUS" operation="profil
e_load" profile="unconfined" name="/usr/lib/telep[COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]y/telep[/COLOR][COLOR=#ff5454]**ath**[/COLOR][COLOR=#000000]y-ofono" pid=442 comm="apparmor[/COLOR]
_parser" 
love@love-X553MA:~$ iwconfig 
eth0      no wireless extensions. 

lo        no wireless extensions. 

love@love-X553MA:~$ rfkill list 
0: hci0: Bluetooth 
        Soft blocked: no 
        Hard blocked: no 
love@love-X553MA:~$ lsmod 
Module                  Size  Used by 
rfcomm                 69632  8  
bnep                   20480  2  
nls_iso8859_1          16384  1  
snd_hda_codec_hdmi     53248  1  
snd_hda_codec_realtek    86016  1  
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek 
snd_hda_intel          36864  3  
snd_hda_controller     32768  1 snd_hda_intel 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generi
c,snd_hda_intel,snd_hda_controller 
snd_hwdep              20480  1 snd_hda_codec 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_contro
ller                                                                                          
intel_rapl             20480  0                                                               
intel_powerclamp       20480  0                                                               
coretemp               16384  0                                                               
snd_seq_midi           16384  0                                                               
snd_seq_midi_event     16384  1 snd_seq_midi                                                  
kvm_intel             151552  0                                                               
snd_rawmidi            32768  1 snd_seq_midi                                                  
kvm                   483328  1 kvm_intel                                                     
crct10dif_pclmul       16384  0  
crc32_pclmul           16384  0  
ghash_clmulni_intel    16384  0  
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi 
uvcvideo               90112  0  
cryptd                 20480  1 ghash_clmulni_intel 
videobuf2_vmalloc      16384  1 uvcvideo 
ath9k                  98304  0  
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi 
ath9k_common           36864  1 ath9k 
videobuf2_memops       16384  1 videobuf2_vmalloc 
snd_timer              32768  2 snd_pcm,snd_seq 
ath9k_hw              458752  2 ath9k_common,ath9k 
joydev                 20480  0  
ath                    32768  3 ath9k_common,ath9k,ath9k_hw 
mac_hid                16384  0  
videobuf2_core         49152  1 uvcvideo 
mac80211              655360  1 ath9k 
serio_raw              16384  0  
v4l2_common            16384  1 videobuf2_core 
snd                    90112  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi
,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device 
ath3k                  20480  0  
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core 
media                  24576  2 uvcvideo,videodev 
btusb                  40960  0  
rtsx_pci_ms            20480  0  
mei_txe                20480  0  
cfg80211              544768  4 ath,ath9k_common,ath9k,mac80211 
memstick               20480  1 rtsx_pci_ms 
lpc_ich                24576  0  
compat                 24576  4 cfg80211,ath9k_common,ath9k,mac80211 
mei                    90112  1 mei_txe 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm 
shpchp                 40960  0  
soundcore              16384  2 snd,snd_hda_codec 
iosf_mbi               16384  1 intel_rapl 
parport_pc             32768  0  
ppdev                  20480  0  
lp                     20480  0  
parport                45056  3 lp,ppdev,parport_pc 
autofs4                40960  2  
rtsx_pci_sdmmc         24576  0  
i915                 1060864  6  
video                  20480  1 i915 
psmouse               118784  0  
i2c_algo_bit           16384  1 i915 
ahci                   36864  3  
r8169                  81920  0  
mii                    16384  1 r8169 
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc 
drm_kms_helper        131072  1 i915 
drm                   348160  8 i915,drm_kms_helper 
libahci                32768  1 ahci

[/FONT]

```

---

### Post by praseodym on 2015-09-29
Tried resetting the BIOS to default? Please do not do it if it is a (U)EFI!

---

### Post by praseodym on 2015-09-29
Try these bootparameters one after another in the same way as described above where it is reading:


*Kein Fehler "ath5k 0000:00:06.0: can't find IRQ for PCI INT A;"*

[http://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507](http://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507)

Do not forget to run
```

sudo update-grub
```before rebooting

---

