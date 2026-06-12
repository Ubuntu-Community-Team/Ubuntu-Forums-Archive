---
title: "My Toshiba C50D-B-132 is new to Ubuntu - teething problems!!"
date: 2017-06-26
forum: Networking &amp; Wireless
---

### Post by fluffyslippers on 2017-06-26
Hi everyone,

I've got a new computer.  It came with Win8, so I got rid of it and installed trusty tahr.  It works fine except:

- can only boot in CSM
- ethernet works fine but not wifi
- connections icon shows networks and wifi greyed out and marked as disabled
- system settings has wireless greyed out and cannot unlock switch to "on"

Very frustrating as I've installed Ubuntu on everyone's computers over the years without many problems!

If anyone has any clues as to what's going on??

ps. when I press antenna switch on keyboard this simply disconnects the ethernet.
I am working with a qca9565 card 

Please help me!! Stressed out!

---

### Post by howefield on 2017-06-26
Thread seems centred on networking issues so moved to the "*Networking & Wireless*" for a better fit.

---

### Post by fluffyslippers on 2017-06-26
Thankyou howefield - I jumped in without looking at the forums headers - sorry :)

---

### Post by chili555 on 2017-06-26
Let's start with a full diagnostic work-up. Please check here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by fluffyslippers on 2017-06-28
Thanks Chili - I'm reinstalling pangolin (perhaps an older version will better capture the wifi??) right now so I'll see how that goes, and then I'll follow that thread you sent ;) x

---

### Post by chili555 on 2017-06-28
I wouldn't go as far back as Pangolin, aka 12.04, as it has reached end-of-life and doesn't receive security updates. [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

I recommend 16.04 LTS. We have made a lot of progress in wireless drivers in four years!

---

### Post by fluffyslippers on 2017-06-29
Thanks Chili!
I've installed 16.04 and it boots fine (only from CSM if that means anything to you)
It works fine - when it's connected to cable
Wifi networks greyed out, and still no wifi possible - what have I done??

---

### Post by Autodave on 2017-06-29
Let's try the old favorite. Shut down the laptop. Disconnect the power cord and then remove the battery. Wait 10 minutes. Install battery and power cable. Boot computer. Does switch and wifi work now?

---

### Post by fluffyslippers on 2017-06-29
Hi Autodave, I'll do that right now - see you in 10!
Thanks

---

### Post by chili555 on 2017-06-29
> **fluffyslippers said:**
> Thanks Chili!
I've installed 16.04 and it boots fine (only from CSM if that means anything to you)
It works fine - when it's connected to cable
Wifi networks greyed out, and still no wifi possible - what have I done??Please see my post #4 above. We can't guess what you've done without details.

---

### Post by fluffyslippers on 2017-06-29
ok Auto, I'm back online via the cable.  When I click on "enable wi-fi" on the dropdown list, nothing happens.

---

### Post by fluffyslippers on 2017-06-29
Chili - I've done the distro update upgrade thingy.

---

### Post by fluffyslippers on 2017-06-29
ok, and here's the gi-normous wireless info text with all my dirty secrets revealed!


```
Report from: 29 Jun 2017 17:08 CEST +0200

Booted last: 29 Jun 2017 00:00 CEST +0200

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-56-generic #61~16.04.1-Ubuntu SMP Wed Jun 14 11:58:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1179:f91b]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: XAVi Technologies Corp. QCA9565 / AR9565 Wireless Network Adapter [1b9a:28a2]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 001 Device 005: ID 0930:0227 Toshiba Corp. 
Bus 001 Device 006: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath3k                  20480  0
bluetooth             557056  32 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k,ath9k_common
ath                    32768  3 ath9k_hw,ath9k,ath9k_common
mac80211              761856  1 ath9k
cfg80211              581632  4 mac80211,ath9k,ath,ath9k_common
wmi                    16384  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.1.48  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::910a:22b:5ece:f2b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2857697 (2.8 MB)  TX bytes:332601 (332.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:89990 (89.9 KB)  TX bytes:89990 (89.9 KB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       763     1  0 16:57 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       7f43423d-bd9c-38ca-ada1-efe4923c7c5b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7f43423d-bd9c-38ca-ada1-efe4923c7c5b | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.48/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1498834758
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.48
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::910a:22b:5ece:f2b5/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.8.0-56-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:03:00.0/net/wlp3s0
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

Region: Europe/Paris (based on set time zone)

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

enp2s0    no frequency information.

wlp3s0    13 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

wlp3s0    Interface doesn't support scanning : Network is down

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[ath3k]
filename:       /lib/modules/4.8.0-56-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     822A166EB22C0577CB2ED55
depends:        bluetooth
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 

[ath9k]
filename:       /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     507D3C35184BD6869DFF77B
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     19485B6EE09E2C6B7C1E9F7
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     59EAA28A511241D6DC5991C
depends:        ath
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.8.0-56-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-56-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-56-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-56-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   14.925230] ath: phy0: WB335 2-ANT card detected
[   14.925234] ath: phy0: Set BT/WLAN RX diversity capability
[   14.932143] ath: phy0: Enable LNA combining
[   14.933251] ath: phy0: ASPM enabled: 0x42
[   14.933255] ath: EEPROM regdomain: 0x6a
[   14.933257] ath: EEPROM indicates we should expect a direct regpair map
[   14.933260] ath: Country alpha2 being used: 00
[   14.933262] ath: Regpair used: 0x6a
[   17.234901] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[   27.669167] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   27.707853] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   27.957345] r8169 0000:02:00.0 enp2s0: link down
[   27.957537] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  140.918046] r8169 0000:02:00.0 enp2s0: link up
[  140.918071] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-06-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

All sensitive information is masked so none of your important secrets are showing.

---

### Post by fluffyslippers on 2017-06-29
*blush* thankyou Wildmanne - sorry to post that big slab (I'm still a newbie in many ways...)

---

### Post by wildmanne39 on 2017-06-29
No worries we all learned the same way!:)

---

### Post by chili555 on 2017-06-29
```
##### rfkill ############################

0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Is there a switch on the laptop to enable and disable wireless? It appears to be set to disable wireless.

---

### Post by fluffyslippers on 2017-07-01
Thanks Chili - yes there's a button (it's on the F12 key) but if I press it there's no reaction...

---

### Post by fluffyslippers on 2017-07-01
You're not going to believe this - desperate as I am to get my wifi up and running, I entered 'wifi key not working on keyboard Toshiba' into my search engine and found this really dum sounding solution.  The post advised me to turn off my computer then press 30 seconds on the power button and that will restore wifi. I turned off my computer, set a timer for 30 seconds and at the same time pressed the power button, then took my finger off the power button at 30 seconds.  A date reset appeared on my screen which took me to the 'bios' thingymajiggy.  I set the correct date, then saved this change and exited.  The computer restarted and I had wifi!!!!  No more wifi problems for me everybody, oh happy day! Not sure if it's just a Toshiba solution but it works.
Thanks to all on this forum for helping me out :p xx

---

### Post by chili555 on 2017-07-01
Thanks for posting your unexpected and interesting solution! We're glad it's working as expected. Please use thread tools to mark Solved. The searchers will appreciate it.

---

