---
title: "Ubuntu 16.10 Can't Disable Airplane Mode on ath9k driver"
date: 2016-12-13
forum: Networking &amp; Wireless
---

### Post by jkal on 2016-12-13
Ever since I switched from Windows to Linux I've been having wifi troubles.  I just switched from another Debian based distro to Ubuntu hoping it would fix my wifi issues but it doesn't.

```


########## wireless info START ##########

Report from: 13 Dec 2016 19:45 EST -0500

Booted last: 13 Dec 2016 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

##### kernel ############################

Linux 4.8.0-30-generic #32-Ubuntu SMP Fri Dec 2 03:43:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Sony Corporation RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [104d:9077]
    Kernel driver in use: r8169

09:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card [105b:e017]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 003 Device 002: ID 0bda:0186 Realtek Semiconductor Corp. Card Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:03f5 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 276d:1119  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k,ath9k_common
ath                    32768  3 ath9k_hw,ath9k,ath9k_common
mac80211              757760  1 ath9k
cfg80211              581632  4 mac80211,ath9k,ath,ath9k_common

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 130.49.78.6  netmask 255.255.248.0  broadcast 130.49.79.255
        inet6 fe80::d986:e095:fb2e:5a7  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 12027  bytes 2245693 (2.2 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 914  bytes 111848 (111.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 6818  bytes 426986 (426.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6818  bytes 426986 (426.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp9s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp9s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         130.49.72.1     0.0.0.0         UG    100    0        0 enp2s0
130.49.72.0     0.0.0.0         255.255.248.0   U     100    0        0 enp2s0
136.142.15.13   130.49.72.1     255.255.255.255 UGH   100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search resnet.pitt.edu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       737     1  0 19:40 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       79727b3f-dd65-35ad-a28f-77fb52d734b8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   79727b3f-dd65-35ad-a28f-77fb52d734b8 | Wired connection 1
IP4.ADDRESS[1]:                         130.49.78.6/21
IP4.GATEWAY:                            130.49.72.1
IP4.ROUTE[1]:                           dst = 136.142.15.13/32, nh = 130.49.72.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             136.142.57.10
IP4.DNS[2]:                             136.142.188.73
IP4.DNS[3]:                             136.142.188.76
IP4.DNS[4]:                             136.142.15.13
IP4.DOMAIN[1]:                          resnet.pitt.edu
IP4.WINS[1]:                            136.142.57.225
IP4.WINS[2]:                            136.142.140.17
IP4.WINS[3]:                            136.142.185.225
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1481678058
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 130.49.72.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 130.49.78.6
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = resnet.pitt.edu
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       broadcast_address = 130.49.79.255
DHCP4.OPTION[21]:                       domain_name_servers = 136.142.57.10 136.142.188.73 136.142.188.76 136.142.15.13
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       dhcp_lease_time = 1800
DHCP4.OPTION[24]:                       netbios_name_servers = 136.142.57.225 136.142.140.17 136.142.185.225
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.248.0
DHCP4.OPTION[27]:                       network_number = 130.49.72.0
DHCP4.OPTION[28]:                       requested_routers = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 136.142.15.13
IP6.ADDRESS[1]:                         fe80::d986:e095:fb2e:5a7/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp9s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express) (T77H126.00 802.11bgn Wireless Half-size Mini PCIe Card)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.8.0-30-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/0000:09:00.0/net/wlp9s0
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

Region: America/New_York (based on set time zone)

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

wlp9s0    13 channels in total; available frequencies :
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

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp9s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7DD7AE5764B41812C31660E
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     C1094862B67773C0C7822B7
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D15742225CC828FEB319976
depends:        ath
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   13.659996] ath: phy0: Enable LNA combining
[   13.662412] ath: phy0: ASPM enabled: 0x42
[   13.662414] ath: EEPROM regdomain: 0x65
[   13.662414] ath: EEPROM indicates we should expect a direct regpair map
[   13.662417] ath: Country alpha2 being used: 00
[   13.662417] ath: Regpair used: 0x65
[   14.254114] ath9k 0000:09:00.0 wlp9s0: renamed from wlan0
[   27.179450] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready

########## wireless info END ############



```

Some things i've tried are reseting BIOS, reinstalling different linux distros, rfkill unblock all, sudo modprobe ath9k, sudo modprobe ath9k nohwcrypt, among some other common fixes I found across different forums.  But no matter what I try the hard block remains on my wifi.  And before you mention it, there is no key combo for wifi and the physical switch for wifi on my laptop doesn't make a difference when I flip it.  

Here is my computer model if that helps:
```

holby@holby:~$ sudo dmidecode | grep -A3 '^System Information'
System Information
    Manufacturer: Sony Corporation
    Product Name: VPCEE31FX
    Version: C104X2ZG

```

---

### Post by chili555 on 2016-12-13
May we also see:```
lsmod | grep -e sony -e wmi
```Thanks.

---

### Post by jkal on 2016-12-13
> **chili555 said:**
> May we also see:```
lsmod | grep -e sony -e wmi
```Thanks.

Absolutely!

```

holby@holby:~$ lsmod | grep -e sony -e wmi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    86016  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
sony_laptop            61440  0
video                  40960  1 sony_laptop

```

---

### Post by jkal on 2016-12-13
Just a thought..  Is there some kind of substitute driver I could try instead of ath9k for my Atheros AR9285?  Could a different driver be a solution?

---

### Post by chili555 on 2016-12-13
> **jkal said:**
> Just a thought..  Is there some kind of substitute driver I could try instead of ath9k for my Atheros AR9285?  Could a different driver be a solution?It isn't the driver for the wireless card; i.e. ath9k. It is the little helper module that translates key presses into action; in your case, flipping the wireless switch should (but does not) turn on the wireless, removing this:> 0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]Let's try an experiment:```
sudo modprobe -r sony-laptop
```Now flip the switch to the assumed ON position and check:```
rfkill list all
```Any signs of life? If so, we'll blacklist the module.

Please also let us see:```
cat /var/log/syslog | grep -i sony | tail -n20
```

---

### Post by jkal on 2016-12-13
> **chili555 said:**
> It isn't the driver for the wireless card; i.e. ath9k. It is the little helper module that translates key presses into action; in your case, flipping the wireless switch should (but does not) turn on the wireless, removing this:Let's try an experiment:```
sudo modprobe -r sony-laptop
```Now flip the switch to the assumed ON position and check:```
rfkill list all
```Any signs of life? If so, we'll blacklist the module.

Please also let us see:```
cat /var/log/syslog | grep -i sony | tail -n20
```

No signs of life, nothing changed.  Thanks for clarifying my other through too by the way!

Here's my output:

```

holby@holby:~$ sudo modprobe -r sony-laptop
[sudo] password for holby: 
holby@holby:~$ rfkill list
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
holby@holby:~$ cat /var/log/syslog | grep -i sony | tail -n20
Dec 13 20:34:31 holby NetworkManager[754]: <info>  [1481679271.4921] rfkill0: found WiFi radio killswitch (at /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0) (platform driver Sony Notebook Control Driver)
Dec 13 23:11:50 holby kernel: [    0.000000] DMI: Sony Corporation VPCEE31FX/VAIO, BIOS R0200Z5 12/09/2010
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: RSDP 0x00000000000FE020 000024 (v02 Sony  )
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: XSDT 0x00000000DFEF6120 00005C (v01 Sony   VAIO     20101209      01000013)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: FACP 0x00000000DFEF5000 0000F4 (v04 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: DSDT 0x00000000DFEE7000 00A52B (v01 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: HPET 0x00000000DFEF4000 000038 (v01 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: APIC 0x00000000DFEF3000 000084 (v02 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: MCFG 0x00000000DFEF2000 00003C (v01 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: BOOT 0x00000000DFEE6000 000028 (v01 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: SLIC 0x00000000DFEE5000 000176 (v01 Sony   VAIO     20101209 INTL 20061109)
Dec 13 23:11:50 holby kernel: [    0.000000] ACPI: SSDT 0x00000000DFEE4000 000386 (v01 Sony   VAIO     20101209 AMD  20061109)
Dec 13 23:11:50 holby NetworkManager[761]: <info>  [1481688709.9243] rfkill0: found WiFi radio killswitch (at /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0) (platform driver Sony Notebook Control Driver)
Dec 13 23:11:50 holby kernel: [    2.528335] ATOM BIOS: Sony_NE7
Dec 13 23:11:50 holby kernel: [    2.762005] usb 2-3: Product: Sony Visual Communication Camera
Dec 13 23:11:50 holby kernel: [   24.017934] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/input/input8
Dec 13 23:11:50 holby kernel: [   24.018045] input: Sony Vaio Jogdial as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/input/input9
Dec 13 23:11:50 holby kernel: [   24.081911] sony_laptop: SNC setup done.
Dec 13 23:11:50 holby kernel: [   26.303425] uvcvideo: Found UVC 1.00 device Sony Visual Communication Camera (0408:03f5)
Dec 13 23:11:50 holby kernel: [   26.312349] input: Sony Visual Communication Camer as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input13



```

This line stands out to me:
```

Dec 13 23:11:50 holby NetworkManager[761]: <info>  [1481688709.9243] rfkill0: found WiFi radio killswitch (at /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0) (platform driver Sony Notebook Control Driver)

```

---

### Post by chili555 on 2016-12-14
Is there any clues when you watch the log and move the switch?```
tail -f /var/log/syslog
```Now move the switch and tell us if there are any messages that appear. Record them any way you can and report.

Get out of 'tail' with Ctrl+c.

I am a bit worried because the .c code for sony-laptop contains many, many references to rfkill: [http://lxr.free-electrons.com/source/drivers/platform/x86/sony-laptop.c](http://lxr.free-electrons.com/source/drivers/platform/x86/sony-laptop.c)

However, the available, manipulable parameters do not include rfkill:```
$ modinfo sony-laptop 
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/platform/x86/sony-laptop.ko
license:        GPL
description:    Sony laptop extras driver (SPIC and SNC ACPI device)
author:         Stelian Pop, Mattia Dongili
srcversion:     0996BC44AF72BECE47D4B69
alias:          acpi*:SNY6001:*
alias:          acpi*:SNY5001:*
depends:        video
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
[COLOR="#FF0000"]parm:           debug:set this to 1 (and RTFM) if you want to help the development of this driver (int)
parm:           no_spic:set this if you don't want to enable the SPIC device (int)
parm:           compat:set this if you want to enable backward compatibility mode (int)
parm:           mask:set this to the mask of event you want to enable (see doc) (ulong)
parm:           camera:set this to 1 to enable Motion Eye camera controls (only use it if you have a C1VE or C1VN model) (int)
parm:           minor:minor number of the misc device for the SPIC compatibility code, default is -1 (automatic) (int)
parm:           kbd_backlight:set this to 0 to disable keyboard backlight, 1 to enable it with automatic control and 2 to have it always on (default: no change from current value) (int)
parm:           kbd_backlight_timeout:meaningful values vary from 0 to 3 and their meaning depends on the model (default: no change from current value) (int)[/COLOR]

```

---

### Post by jkal on 2016-12-14
A little update..  I navigated to that folder in my previous post and found that there are two files, called soft and hard.  They correspond to the soft and hard block on my wifi.  Reading them showed a 0 for soft, and a 1 for hard, which corresponds to my rfkill.  It wouldn't let me simply change my 1 to a 0 for my hard block, but maybe there is something I need to do in this folder to fix my issue?

Here is my terminal:
```

holby@holby:~$ cd /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0
holby@holby:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0$ ls
device  index  persistent  soft   subsystem  uevent
hard    name   power       state  type
holby@holby:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0$ cat hard
1
holby@holby:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0$ cat soft
0

```

---

### Post by jkal on 2016-12-14
> **chili555 said:**
> Is there any clues when you watch the log and move the switch?```
tail -f /var/log/syslog
```Now move the switch and tell us if there are any messages that appear. Record them any way you can and report.

Get out of 'tail' with Ctrl+c.

I am a bit worried because the .c code for sony-laptop contains many, many references to rfkill: [http://lxr.free-electrons.com/source/drivers/platform/x86/sony-laptop.c](http://lxr.free-electrons.com/source/drivers/platform/x86/sony-laptop.c)

However, the available, manipulable parameters do not include rfkill:```
$ modinfo sony-laptop 
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/platform/x86/sony-laptop.ko
license:        GPL
description:    Sony laptop extras driver (SPIC and SNC ACPI device)
author:         Stelian Pop, Mattia Dongili
srcversion:     0996BC44AF72BECE47D4B69
alias:          acpi*:SNY6001:*
alias:          acpi*:SNY5001:*
depends:        video
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
[COLOR=#FF0000]parm:           debug:set this to 1 (and RTFM) if you want to help the development of this driver (int)
parm:           no_spic:set this if you don't want to enable the SPIC device (int)
parm:           compat:set this if you want to enable backward compatibility mode (int)
parm:           mask:set this to the mask of event you want to enable (see doc) (ulong)
parm:           camera:set this to 1 to enable Motion Eye camera controls (only use it if you have a C1VE or C1VN model) (int)
parm:           minor:minor number of the misc device for the SPIC compatibility code, default is -1 (automatic) (int)
parm:           kbd_backlight:set this to 0 to disable keyboard backlight, 1 to enable it with automatic control and 2 to have it always on (default: no change from current value) (int)
parm:           kbd_backlight_timeout:meaningful values vary from 0 to 3 and their meaning depends on the model (default: no change from current value) (int)[/COLOR]

```
No luck watching the log and flipping the switch.  If this helps, when I was running a different debian based distro and had this problem I was able to fix my wifi issue for a few days before the problem came back up.  Since then I've tried the old fix multiple times and it didn't work.

The fix was:

```

sudo modprobe ath9k nohwcrypt

```

Maybe that would help?

---

### Post by chili555 on 2016-12-14
>  It wouldn't let me simply change my 1 to a 0 for my hard block,How, exactly, did you try it? I suggest:
```
sudo -i
echo 0  >   /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard
rfkill list all
exit
```> sudo modprobe ath9k nohwcryptI doubt that it will help, but it is a bit more complex:```
sudo modprobe -r ath9k
sudo modprobe ath9k hohwcrypt=1
```Try it and let us know.

The encryption method, whether it is done in software or hardware is unrelated to rfkill. However, I have learned to never be surprised when the unworkable magically works!

---

### Post by jkal on 2016-12-14
> **chili555 said:**
> How, exactly, did you try it? I suggest:
```
sudo -i
echo 0  >   /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard
rfkill list all
exit
```I doubt that it will help, but it is a bit more complex:```
sudo modprobe -r ath9k
sudo modprobe ath9k hohwcrypt=1
```Try it and let us know.

The encryption method, whether it is done in software or hardware is unrelated to rfkill. However, I have learned to never be surprised when the unworkable magically works!
I tried the ath9k nohwcrypt=1 and there was no change.  And when I tried your first snippet I got permission denied.

```

holby@holby:~$ sudo -i
[sudo] password for holby: 
root@holby:~# echo 0  >   /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard
-bash: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard: Permission denied

```

---

### Post by chili555 on 2016-12-14
> -bash: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard: Permission deniedI fear that it means that we are reporting what the state of the switch is, turned to off. We can't change the state; that is, flip the switch, with a terminal command. Arrghhh!

Is the result the same with the sony-laptop module present of removed?

---

### Post by jkal on 2016-12-14
> **chili555 said:**
> I fear that it means that we are reporting what the state of the switch is, turned to off. We can't change the state; that is, flip the switch, with a terminal command. Arrghhh!

Is the result the same with the sony-laptop module present of removed?

Very frustrating haha, but again no luck.

```

holby@holby:~$ sudo modprobe -r sony-laptop
[sudo] password for holby: 
holby@holby:~$ sudo -i
root@holby:~# echo 0  >   /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard
-bash: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard: No such file or directory

```

This time it says there is no file in directory.  I'm starting to get nervous that my wireless will never work again :(

Here's some more info if it helps.  When I said I had this problem in a different distro, the fix was 'sudo modprobe ath9k nowhcrypt' and it started working instantly.  I was able to use my hardware switch as normal and everything worked.  Then just the other day, I accidentally switched the switch off and when I switched it back on, nothing happened.  I tried rebooting and using the old fix but nothing would re activate it.  Then I switched to ubuntu hoping that would fix it but no.  Just wanted to throw the history of this problem out in case it helps?

If anyone can fix it, it's you cause I'm out of ideas!

---

### Post by chili555 on 2016-12-14
> -bash: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2b/SNY5001:00/rfkill/rfkill0/hard: No such file or directoryI think that means that the "hard" file is now somewhere else. You may have to look around in /sys/devices to find it.

Studying...lunch and a beer might help. Later.

---

### Post by jkal on 2016-12-14
> **chili555 said:**
> I think that means that the "hard" file is now somewhere else. You may have to look around in /sys/devices to find it.

Studying...lunch and a beer might help. Later.
I'm studying too, finals week is killer.  I found the hard file.  It's located in 'sys/devices/pci0000:00/0000:00:07.0/0000:09:00.0/ieee80211/phy0/rfkill0'.  

I ran the commands you posted earlier with this new location and again go permission denied.

```

holby@holby:~$ sudo modprobe -r sony-laptop
[sudo] password for holby: 
holby@holby:~$ sudo -i
root@holby:~# echo 0 >   /sys/devices/pci0000:00/0000:00:07.0/0000:09:00.0/ieee80211/phy0/rfkill0/hard 
-bash: /sys/devices/pci0000:00/0000:00:07.0/0000:09:00.0/ieee80211/phy0/rfkill0/hard: Permission denied


```

Enjoy your lunch and your beer, hope to hear from you soon!

---

### Post by chili555 on 2016-12-14
Aside from filing a bug report against sony-laptop and getting a different device, I regret that I haven't any other suggestions.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

The rfkill will also block any other wireless device, usually even USB. I therefore suggest a wireless-ethernet bridge or else a powerline ethernet adapter.

I wish I had a better solution.

---

### Post by jeremy31 on 2016-12-14
You may want to see this youtube video [https://www.youtube.com/watch?v=yzAKcmlaH1M&t=6s](https://www.youtube.com/watch?v=yzAKcmlaH1M&t=6s)
A small piece of electrical tape on the right pin of the wireless card may allow you to use it

---

### Post by jkal on 2016-12-14
> **chili555 said:**
> Aside from filing a bug report against sony-laptop and getting a different device, I regret that I haven't any other suggestions.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

The rfkill will also block any other wireless device, usually even USB. I therefore suggest a wireless-ethernet bridge or else a powerline ethernet adapter.

I wish I had a better solution.Which pin should I mask for my laptop?  I tried researching it but I can't find a clear answer.  It's a Sony Vaio E-series.
```

System Information
    Manufacturer: Sony Corporation
    Product Name: VPCEE31FX
    Version: C104X2ZG

```

---

### Post by jkal on 2016-12-14
> **chili555 said:**
> Aside from filing a bug report against sony-laptop and getting a different device, I regret that I haven't any other suggestions.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

The rfkill will also block any other wireless device, usually even USB. I therefore suggest a wireless-ethernet bridge or else a powerline ethernet adapter.

I wish I had a better solution.
That's disappointing to hear but I guess I'm out of options.

---

### Post by jkal on 2016-12-14
Is there some kind of replacement driver I should try for my Atheros AR9285?

---

