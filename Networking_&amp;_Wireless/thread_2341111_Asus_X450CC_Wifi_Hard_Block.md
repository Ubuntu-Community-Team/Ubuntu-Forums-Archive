---
title: "Asus X450CC Wifi Hard Block"
date: 2016-10-25
forum: Networking &amp; Wireless
---

### Post by kuramot on 2016-10-25
Asus X450CC wifi has been hard blocked. Tested on other Linux distros and result is the same. Wifi cannot be turned on and remains hard blocked. Current Linux distro in use is Xubuntu 16.0.1 and is dual booted to Windows 10. The wifi works fine on Windows 10. Laptop has no physical wifi switch.

[https://ubuntuforums.org/showthread.php?t=2181558](https://ubuntuforums.org/showthread.php?t=2181558) did not work for me.

```
cat /sys/class/dmi/id/product_name
X450CC
```

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

```
lsmod | grep -e asus -e wmi
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mxm_wmi                16384  1 nouveau
video                  40960  3 i915,nouveau,asus_wmi
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
```

Wireless info script result:
```


########## wireless info START ##########


Report from: 25 Oct 2016 12:31 PHT +0800


Booted last: 25 Oct 2016 00:00 PHT +0800


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Xubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Foxconn International, Inc. RT3290 Wireless 802.11n 1T/1R PCIe [105b:e055]
    Kernel driver in use: rt2800pci


04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5188 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 0781:5581 SanDisk Corp. Ultra
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
asus_nb_wmi            24576  0
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
mxm_wmi                16384  1 nouveau
video                  40960  3 i915,nouveau,asus_wmi
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0f2  Link encap:Ethernet  HWaddr <MAC 'enp4s0f2' [IF1]>  
          inet addr:192.168.254.4  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::993d:47e8:ebb6:eda0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1060754 (1.0 MB)  TX bytes:117708 (117.7 KB)


wlp3s0f0  Link encap:Ethernet  HWaddr <MAC 'wlp3s0f0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0f2  no wireless extensions.


wlp3s0f0  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    100    0        0 enp4s0f2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0f2
192.168.254.0   0.0.0.0         255.255.255.0   U     100    0        0 enp4s0f2


##### resolv.conf #######################


nameserver 127.0.1.1
search domain.name


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2392     1  0 12:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp4s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.2/net/enp4s0f2
GENERAL.IP-IFACE:                       enp4s0f2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b941e87c-8280-42a8-a97b-44bc70eb6738
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b941e87c-8280-42a8-a97b-44bc70eb6738 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.254.4/24
IP4.GATEWAY:                            192.168.254.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.254.254
IP4.DOMAIN[1]:                          domain.name
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1477513840
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.254.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.254.4
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = domain.name
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.254.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.254.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.254.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.254.254
IP6.ADDRESS[1]:                         fe80::993d:47e8:ebb6:eda0/64
IP6.GATEWAY:                            fe80::9261:cff:fe1e:c3d9
IP6.ROUTE[1]:                           dst = fe80::9261:cff:fe1e:c3d9/128, nh = ::, mt = 100


GENERAL.DEVICE:                         wlp3s0f0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0f0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0f0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


Region: Asia/Manila (based on set time zone)


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


enp4s0f2  no frequency information.


wlp3s0f0  14 channels in total; available frequencies :
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


lo        Interface doesn't support scanning.


wlp3s0f0  Interface doesn't support scanning : Network is down


enp4s0f2  Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
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


[    9.891666] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0013 detected
[    9.900031] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   10.079979] rt2800pci 0000:03:00.0 wlp3s0f0: renamed from wlan0
[   23.554708] IPv6: ADDRCONF(NETDEV_UP): wlp3s0f0: link is not ready
[   23.558897] IPv6: ADDRCONF(NETDEV_UP): enp4s0f2: link is not ready
[   23.843911] r8169 0000:04:00.2 enp4s0f2: link down
[   23.843977] IPv6: ADDRCONF(NETDEV_UP): enp4s0f2: link is not ready
[  513.229924] r8169 0000:04:00.2 enp4s0f2: link up
[  513.229951] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0f2: link becomes ready


########## wireless info END ############



```

---

### Post by chili555 on 2016-10-25
As far as I know, there are only a few things that can be done. The first is the asus-nb-wmi parameter. From the terminal:

```
sudo -i
echo "options asus-nb-wmi wapf=0"  >  /etc/modprobe.d/asus-nb-wmi.conf
exit
```

Reboot and test the Fn+F2 button. If this is ineffective, try a different parameter:

```
sudo -i
echo "options asus-nb-wmi wapf=1"  >  /etc/modprobe.d/asus-nb-wmi.conf
exit

```
Or else:

```
sudo -i
echo "options asus-nb-wmi wapf=4"  >  /etc/modprobe.d/asus-nb-wmi.conf
exit
```

In all cases, reboot.  I recommend that you disregard the wireless light or LED. Check by pressing the Fn+F2 key combination and check:

```
rfkill list all
```

Press the Fn+F2 combination again and check:

```
rfkill list all
```

Another option is to remove the module completely:

```
sudo modprobe -r asus-wmi
sudo rfkill unblock all
rfkill list all

```
Please let us know the result of these steps.

---

### Post by kuramot on 2016-10-30
Changing tha wapf value does nothing for me. I checked this by pressing the Fn+F2 combination.
I also tried removing the asus-nb-wmi module and unblocking all. When I checked the list again, only the phy0 Wireless LAN was left and it was still hard blocked.

---

