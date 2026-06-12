---
title: "WiFi Not working for Realtek RTL8723BE PCIe Wireless Network Adapter For Ubuntu 14.04"
date: 2016-01-16
forum: Networking &amp; Wireless
---

### Post by Hrushikesh_Turkhad on 2016-01-16
I use **HP Pavilion 15-ab032tx** Laptop and it has the above wireless card by **Realtek Semiconductors**.  I have tried various methods to start a wireless hotspot but nothing  worked for me. I want it to connect to my Android phone. Following is the  full specification of the card.
```
description: Wireless interface
   product: RTL8723BE PCIe Wireless Network Adapter
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:08:00.0
   logical name: wlan0
   version: 00
   serial: 70:77:81:19:a3:17
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
   configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-74-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
   resources: irq:18 ioport:5000(size=256) memory:c6100000-c6103fff
```

I have run the wireless script according to this thread.
[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

```


########## wireless info START ##########

Report from: 22 Jan 2016 19:37 IST +0530

Booted last: 22 Jan 2016 17:16 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, video.use_native_backlight=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136]  (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:8096]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

rtl8723be              87260  0 
btcoexist              55886  1 rtl8723be
rtl8723_common         23427  1 rtl8723be
rtl_pci                27306  1 rtl8723be
rtlwifi                69157  2 rtl_pci,rtl8723be
mac80211              687021  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              521225  2 mac80211,rtlwifi
hp_wmi                 18249  0 
sparse_keymap          13890  1 hp_wmi
mxm_wmi                13021  1 nouveau
wmi                    19379  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.1.0.63  Bcast:10.1.3.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:272960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51674303 (51.6 MB)  TX bytes:4492349 (4.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1202062 (1.2 MB)  TX bytes:259461 (259.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.0.254      0.0.0.0         UG    0      0        0 eth0
10.1.0.0        0.0.0.0         255.255.252.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1696     1  0 17:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.1.0.63
    Prefix:          22 (255.255.252.0)
    Gateway:         10.1.0.254

    DNS:             202.141.81.2

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Yo-Bro~]] (600 root)
[connection] id=Yo-Bro | type=802-11-wireless
[802-11-wireless] ssid=Yo-Bro | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=shared

[[/etc/NetworkManager/system-connections/JAGO]] (600 root)
[connection] id=JAGO | type=802-11-wireless
[802-11-wireless] ssid=JAGO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KAPILI_WIFI]] (600 root)
[connection] id=KAPILI_WIFI | type=802-11-wireless
[802-11-wireless] ssid=KAPILI_WIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: N
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/local.conf]
options drm_kms_helper poll=N

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC  'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1",  KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1729.550340] rtl8723be 0000:08:00.0: no hotplug settings from platform
[ 1731.485030] rtlwifi: wireless switch is on
[ 1732.061004] rtl8723be 0000:08:00.0: no hotplug settings from platform
[ 1732.427455] r8169 0000:09:00.0 eth0: link down
[ 1732.427538] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1734.061279] r8169 0000:09:00.0 eth0: link up
[ 1734.061286] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############




```

  
Also, I have dual booted with Windows 8.1 . As I start the system there  is no hard block but as I put it into sleep wireless card is hard  blocked. I have also turned off airplane mode from windows.


I have followed the instructions from this blog but didn't work for me.
[https://rtl8723beubuntu1404.wordpress.com/](https://rtl8723beubuntu1404.wordpress.com/)

---

### Post by slickymaster on 2016-01-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Hrushikesh_Turkhad on 2016-01-22
I recently upgraded to 3.16.0-031600-generic kernel.

I have followed the instructions from this blog but didn't work for me.
[https://rtl8723beubuntu1404.wordpress.com/](https://rtl8723beubuntu1404.wordpress.com/)

I have run the wireless script according to this thread.
[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

```


########## wireless info START ##########

Report from: 22 Jan 2016 19:37 IST +0530

Booted last: 22 Jan 2016 17:16 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, video.use_native_backlight=1, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:8096]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

rtl8723be              87260  0 
btcoexist              55886  1 rtl8723be
rtl8723_common         23427  1 rtl8723be
rtl_pci                27306  1 rtl8723be
rtlwifi                69157  2 rtl_pci,rtl8723be
mac80211              687021  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              521225  2 mac80211,rtlwifi
hp_wmi                 18249  0 
sparse_keymap          13890  1 hp_wmi
mxm_wmi                13021  1 nouveau
wmi                    19379  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.1.0.63  Bcast:10.1.3.255  Mask:255.255.252.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:272960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51674303 (51.6 MB)  TX bytes:4492349 (4.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1202062 (1.2 MB)  TX bytes:259461 (259.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.0.254      0.0.0.0         UG    0      0        0 eth0
10.1.0.0        0.0.0.0         255.255.252.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1696     1  0 17:16 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.1.0.63
    Prefix:          22 (255.255.252.0)
    Gateway:         10.1.0.254

    DNS:             202.141.81.2

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Yo-Bro~]] (600 root)
[connection] id=Yo-Bro | type=802-11-wireless
[802-11-wireless] ssid=Yo-Bro | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=shared

[[/etc/NetworkManager/system-connections/JAGO]] (600 root)
[connection] id=JAGO | type=802-11-wireless
[802-11-wireless] ssid=JAGO | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KAPILI_WIFI]] (600 root)
[connection] id=KAPILI_WIFI | type=802-11-wireless
[802-11-wireless] ssid=KAPILI_WIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: N
ips: Y
msi: N
swenc: N
swlps: N

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

lp
rtc

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

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

[/etc/modprobe.d/local.conf]
options drm_kms_helper poll=N

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1729.550340] rtl8723be 0000:08:00.0: no hotplug settings from platform
[ 1731.485030] rtlwifi: wireless switch is on
[ 1732.061004] rtl8723be 0000:08:00.0: no hotplug settings from platform
[ 1732.427455] r8169 0000:09:00.0 eth0: link down
[ 1732.427538] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1734.061279] r8169 0000:09:00.0 eth0: link up
[ 1734.061286] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############




```


ere is no hut as soon I put my ard block 
Also, I have dual booted with Windows 8.1 . As I start the system there is no hard block but as I put it into sleep wireless card is hard blocked. I have also turned off airplane mode from windows.

---

