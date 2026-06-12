---
title: "TP-Link WN725N-V2 not working with Ubuntu 16.04"
date: 2017-05-28
forum: Networking &amp; Wireless
---

### Post by pat991 on 2017-05-28
[TABLE]
[TR]
[TD][/TD]
[TD]        I am using [this]("http://ubuntuhandbook.org/index.php/2014/09/3-ways-create-wifi-hotspot-ubuntu/") post to create a hotspot in Ubuntu 16.04. In the last step when i tried to connect to the hidden network I got this error:


  [IMG]https://i.stack.imgur.com/v4irh.png[/IMG]

  
Here is the output of `lsusb` and `ifconfig` command:


  Output of lsusb



[[IMG]https://i.stack.imgur.com/gwZBz.png[/IMG]]("https://i.stack.imgur.com/gwZBz.png")  

Output of ifconfig

  [IMG]https://i.stack.imgur.com/i0g13.png[/IMG]

  
The highlighted lines in the output disappears when i remove the  TP-LINK device, so I am guessing Ubuntu is able to detect the device.

  So where is the problem then ?

I also tried to install driver from [here]("http://www.tp-link.com/us/download/TL-WN725N.html"). But when tried to compile the source after cd'ing into the driver directory I got this error:


  [IMG]https://i.stack.imgur.com/VQeGR.png[/IMG]
[/TD]
[/TR]
[/TABLE]

Please help! 

Thanks

---

### Post by Hadaka on 2017-05-28
Hi, to load the driver for your TP link
ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS
go here..Post #8
[https://ubuntuforums.org/showthread.php?t=2349486](https://ubuntuforums.org/showthread.php?t=2349486)

If you are trying to run 2 wireless units in your pc...the pppo
point to point connection and now and additional TP-Link wifi connection
I doubt that will work, you can have one or the other ..but not both as
far as I know.
good luck.

---

### Post by pat991 on 2017-05-28
Thanks for the quick reply.

I followed post #8 and installed the driver. But after the reboot still getting "Failed to activate the connection".

No I I am not trying to run two wireless at the same time.

What's the issue here ?

I am banging my head for hours on this issue. 

Thanks :)

---

### Post by Hadaka on 2017-05-28
Hi, please do..
```
sudo modprobe -v 8188eu
```
If it still does not activate, then..

Please open a terminal ctrl/alt/t then Copy and paste the following command
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
~OR~
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
thanks.

---

### Post by pat991 on 2017-05-28
Here is the output of wireless-info.txt. Please take a look.


```

########## wireless info START ##########

Report from: 28 May 2017 16:19 IST +0530

Booted last: 28 May 2017 00:00 IST +0530

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-52-generic #55~16.04.1-Ubuntu SMP Fri Apr 28 14:36:29 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    DeviceName:  Onboard LAN
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:2abf]

##### lsusb #############################

Bus 002 Device 005: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 002 Device 003: ID 0bc2:a013 Seagate RSS LLC 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04ca:003a Lite-On Technology Corp. 
Bus 001 Device 003: ID 03f0:0941 Hewlett-Packard 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

8188eu                720896  0
cfg80211              581632  0
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet6 addr: fe80::46e4:58aa:f5c5:8ace/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34379685 (34.3 MB)  TX bytes:3528865 (3.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:36835 (36.8 KB)  TX bytes:36835 (36.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.25.101.165  P-t-P:120.89.73.10  Mask:255.255.255.255
          inet6 addr: fe80::5de5:e85b:f1fa:3ab4/10 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:892 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:395482 (395.4 KB)  TX bytes:146900 (146.9 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

ppp0      no wireless extensions.

wlx<IF from MAC [IF2]>  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         120.89.73.10    0.0.0.0         UG    100    0        0 ppp0
120.89.73.10    0.0.0.0         255.255.255.255 UH    100    0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 4.2.2.2
nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       891     1  0 13:34 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:07:00.0/net/eno1
GENERAL.IP-IFACE:                       ppp0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     DSL connection 1
GENERAL.CON-UUID:                       e7126caa-73ef-4908-9b6a-e051c11dcb3e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e7126caa-73ef-4908-9b6a-e051c11dcb3e | DSL connection 1
IP4.ADDRESS[1]:                         172.25.101.165/32
IP4.GATEWAY:                            120.89.73.10
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             4.2.2.2
IP6.ADDRESS[1]:                         fe80::5de5:e85b:f1fa:3ab4/10
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fe80::/10, nh = ::, mt = 1

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/net/wlx<IF from MAC [IF2]>
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
WIFI-PROPERTIES.AP:                     no
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

[[/etc/NetworkManager/system-connections/Wi-Fi hotspot]] (600 root)
[connection] id=Wi-Fi hotspot | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=Wi-Fi hotspot
[ipv4] method=shared
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

eno1      no frequency information.

ppp0      no frequency information.

wlx<IF from MAC [IF2]>  13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

wlx<IF from MAC [IF2]>  No scan results

##### module infos ######################

[8188eu]
filename:       /lib/modules/4.8.0-52-generic/kernel/drivers/net/wireless/8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     5FC9DAA41D43AC6564D82F7
depends:        
vermagic:       4.8.0-52-generic SMP mod_unload modversions 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

[cfg80211]
filename:       /lib/modules/4.8.0-52-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-52-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 0
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/50-8188eu.conf]
blacklist r8188eu

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

[ 2335.217961] [UFW BLOCK] IN=eno1 OUT= MAC= SRC=fe80:0000:0000:0000:46e4:58aa:f5c5:8ace DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=432682 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 2335.217982] [UFW BLOCK] IN=eno1 OUT= MAC= SRC=fe80:0000:0000:0000:46e4:58aa:f5c5:8ace DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=967102 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 2335.228084] [UFW BLOCK] IN=eno1 OUT= MAC= SRC=fe80:0000:0000:0000:46e4:58aa:f5c5:8ace DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=432682 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 2335.228103] [UFW BLOCK] IN=eno1 OUT= MAC= SRC=fe80:0000:0000:0000:46e4:58aa:f5c5:8ace DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=967102 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 2592.084862] r8169 0000:07:00.0 eno1: link down
[ 2593.457751] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[ 2593.950072] r8169 0000:07:00.0 eno1: link up

########## wireless info END ############



```

---

### Post by Hadaka on 2017-05-28
Hi, now that you have the correct wifi driver loaded, I would suggest
using this method to create your hotspot.
[https://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot](https://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot)
hope this helps

---

