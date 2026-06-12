---
title: "WiFi not connecting in in Ubuntu 14.10 after updating Lenovo Y50-70"
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by bhuveee on 2015-01-01
I recently updated my ubuntu and post that wifi stops connecting. Heres the output of my dmesg:
```

[  124.012908] cfg80211: Calling CRDA to update world regulatory domain
[  124.030496] cfg80211: World regulatory domain updated:
[  124.030499] cfg80211:  DFS Master region: unset
[  124.030501] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  124.030503] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  124.030504] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  124.030505] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  124.030506] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  124.030507] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  124.851375] wlan0: authenticate with c4:a8:1d:ee:ac:d8
[  124.871351] wlan0: send auth to c4:a8:1d:ee:ac:d8 (try 1/3)
[  124.877587] wlan0: authenticated
[  124.878982] wlan0: associate with c4:a8:1d:ee:ac:d8 (try 1/3)
[  124.884601] wlan0: RX AssocResp from c4:a8:1d:ee:ac:d8 (capab=0x411 status=0 aid=3)
[  124.884753] wlan0: associated
[  170.341423] wlan0: deauthenticating from c4:a8:1d:ee:ac:d8 by local choice (Reason: 3=DEAUTH_LEAVING)
[  170.372648] cfg80211: Calling CRDA to update world regulatory domain
[  170.381832] cfg80211: World regulatory domain updated:
[  170.381835] cfg80211:  DFS Master region: unset
[  170.381835] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  170.381837] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  170.381838] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  170.381839] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  170.381840] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  170.381841] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  173.148758] wlan0: authenticate with c4:a8:1d:ee:ac:d8

```


Output of lspci is:
```
lspci |grep Realtek
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader (rev 01)

```

---

### Post by bhuveee on 2015-01-01
Here is the output of the wireless script mentioned here [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

```


########## wireless info START ##########

Report from: 02 Jan 2015 00:54 IST +0530

Booted last: 02 Jan 2015 00:20 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 5986:055e Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

rtl8723be              84972  0 
btcoexist              50429  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26674  1 rtl8723be
rtlwifi                64237  2 rtl_pci,rtl8723be
mac80211              660592  3 rtl_pci,rtlwifi,rtl8723be
mxm_wmi                13021  1 nouveau
cfg80211              510218  2 mac80211,rtlwifi
ideapad_laptop         18278  0 
wmi                    19193  2 mxm_wmi,nouveau
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f276:1cff:fe19:e6a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21165 errors:0 dropped:32 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22855449 (22.8 MB)  TX bytes:3037350 (3.0 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:914 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:304229 (304.2 KB)  TX bytes:180464 (180.4 KB)

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
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

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
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             103.8.44.5
    DNS:             103.8.45.5

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Mommy]] (600 root)
[connection] id=Mommy | type=802-11-wireless
[802-11-wireless] ssid=Mommy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BigDaddy]] (600 root)
[connection] id=BigDaddy | type=802-11-wireless
[802-11-wireless] ssid=BigDaddy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SuperDaddy]] (600 root)
[connection] id=SuperDaddy | type=802-11-wireless
[802-11-wireless] ssid=SuperDaddy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

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

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
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
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 1525.632796] wlan0: authenticate with <MAC address>
[ 1526.111369] wlan0: send auth to <MAC address> (try 1/3)
[ 1526.113269] wlan0: authenticated
[ 1526.114414] wlan0: associate with <MAC address> (try 1/3)
[ 1526.118123] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=4)
[ 1526.118272] wlan0: associated
[ 1571.873110] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1574.700393] wlan0: authenticate with <MAC address>
[ 1575.181655] wlan0: send auth to <MAC address> (try 1/3)
[ 1575.183489] wlan0: authenticated
[ 1575.184310] wlan0: associate with <MAC address> (try 1/3)
[ 1575.188240] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=4)
[ 1575.188405] wlan0: associated
[ 1620.927142] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1623.740777] wlan0: authenticate with <MAC address>
[ 1624.222562] wlan0: send auth to <MAC address> (try 1/3)
[ 1624.224397] wlan0: authenticated
[ 1624.226184] wlan0: associate with <MAC address> (try 1/3)
[ 1624.229864] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=4)
[ 1624.230017] wlan0: associated
[ 1669.982040] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1672.791793] wlan0: authenticate with <MAC address>
[ 1673.270043] wlan0: send auth to <MAC address> (try 1/3)
[ 1673.271916] wlan0: authenticated
[ 1673.272046] wlan0: associate with <MAC address> (try 1/3)
[ 1673.275911] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=4)
[ 1673.276081] wlan0: associated
[ 1719.036983] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1822.957960] wlan0: authenticate with <MAC address>
[ 1823.439575] wlan0: send auth to <MAC address> (try 1/3)
[ 1823.441433] wlan0: authenticated
[ 1823.445044] wlan0: associate with <MAC address> (try 1/3)
[ 1823.448864] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=4)
[ 1823.449040] wlan0: associated
[ 1869.197897] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1872.020393] wlan0: authenticate with <MAC address>
[ 1872.501717] wlan0: send auth to <MAC address> (try 1/3)
[ 1872.503722] wlan0: authenticated
[ 1872.506934] wlan0: associate with <MAC address> (try 1/3)
[ 1872.511045] wlan0: RX AssocResp from <MAC address> (capab=0x431 status=0 aid=2)
[ 1872.511201] wlan0: associated
[ 1877.686102] wlan0: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

---

### Post by jeremy31 on 2015-01-01
The result of the script shows a soft block on wifi, try the FN combo to see if it will enable

---

### Post by bhuveee on 2015-01-01
It was disabled by me, not working after enabling.

---

### Post by jeremy31 on 2015-01-01
> **bhuveee said:**
> It was disabled by me, not working after enabling.

Please run the script again with wifi enabled and after attempting to connect

---

### Post by bhuveee on 2015-01-01
heres the result
```


########## wireless info START ##########

Report from: 02 Jan 2015 01:22 IST +0530

Booted last: 02 Jan 2015 00:20 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 5986:055e Acer, Inc 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              84972  0 
btcoexist              50429  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26674  1 rtl8723be
rtlwifi                64237  2 rtl_pci,rtl8723be
mac80211              660592  3 rtl_pci,rtlwifi,rtl8723be
mxm_wmi                13021  1 nouveau
cfg80211              510218  2 mac80211,rtlwifi
ideapad_laptop         18278  0 
wmi                    19193  2 mxm_wmi,nouveau
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::f276:1cff:fe19:e6a8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34191 errors:0 dropped:32 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32225265 (32.2 MB)  TX bytes:5472666 (5.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::c238:96ff:fe01:9383/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:459950 (459.9 KB)  TX bytes:207364 (207.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: connecting

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [SuperDaddy] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    A-202:           Infra, <MAC 'A-202' [AN1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    dlink_DIR-506L:  Infra, <MAC 'dlink_DIR-506L' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60
    Subrata:         Infra, <MAC 'Subrata' [AN3]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 67 WPA
    MGMNT:           Infra, <MAC 'MGMNT' [AN4]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 67 WEP
    BigDaddy:        Infra, <MAC 'BigDaddy' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Mommy:           Infra, <MAC 'Mommy' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    SuperDaddy:      Infra, <MAC 'SuperDaddy' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Narad-Muni:      Infra, <MAC 'Narad-Muni' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA
    skesavan:        Infra, <MAC 'skesavan' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2

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

[[/etc/NetworkManager/system-connections/Mommy]] (600 root)
[connection] id=Mommy | type=802-11-wireless
[802-11-wireless] ssid=Mommy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BigDaddy]] (600 root)
[connection] id=BigDaddy | type=802-11-wireless
[802-11-wireless] ssid=BigDaddy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SuperDaddy]] (600 root)
[connection] id=SuperDaddy | type=802-11-wireless
[802-11-wireless] ssid=SuperDaddy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
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
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        AF:30:E7:F3:7B:41:30:1C:96:F9:85:F4:78:9D:A5:F4:37:3E:9E:92
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 3488.672154] wlan0: authenticated
[ 3488.672971] wlan0: associate with <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3488.713508] wlan0: RX AssocResp from <MAC 'SuperDaddy' [AN7]> (capab=0x411 status=0 aid=3)
[ 3488.713657] wlan0: associated
[ 3534.035024] wlan0: deauthenticating from <MAC 'SuperDaddy' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3536.848332] wlan0: authenticate with <MAC 'SuperDaddy' [AN7]>
[ 3537.326648] wlan0: send auth to <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3537.331765] wlan0: authenticated
[ 3537.334453] wlan0: associate with <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3537.338832] wlan0: RX AssocResp from <MAC 'SuperDaddy' [AN7]> (capab=0x411 status=0 aid=3)
[ 3537.338986] wlan0: associated
[ 3566.213471] wlan0: deauthenticating from <MAC 'SuperDaddy' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3573.832459] wlan0: authenticate with <MAC 'BigDaddy' [AN5]>
[ 3574.310694] wlan0: send auth to <MAC 'BigDaddy' [AN5]> (try 1/3)
[ 3574.312515] wlan0: authenticated
[ 3574.315033] wlan0: associate with <MAC 'BigDaddy' [AN5]> (try 1/3)
[ 3574.318780] wlan0: RX AssocResp from <MAC 'BigDaddy' [AN5]> (capab=0x431 status=0 aid=5)
[ 3574.318932] wlan0: associated
[ 3620.130125] wlan0: deauthenticating from <MAC 'BigDaddy' [AN5]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3622.938837] wlan0: authenticate with <MAC 'SuperDaddy' [AN7]>
[ 3623.420067] wlan0: send auth to <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3623.422693] wlan0: authenticated
[ 3623.424957] wlan0: associate with <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3623.429373] wlan0: RX AssocResp from <MAC 'SuperDaddy' [AN7]> (capab=0x411 status=0 aid=3)
[ 3623.429539] wlan0: associated
[ 3669.185631] wlan0: deauthenticating from <MAC 'SuperDaddy' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3672.003229] wlan0: authenticate with <MAC 'SuperDaddy' [AN7]>
[ 3672.481480] wlan0: send auth to <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3672.483024] wlan0: authenticated
[ 3672.486925] wlan0: associate with <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3672.492955] wlan0: RX AssocResp from <MAC 'SuperDaddy' [AN7]> (capab=0x411 status=0 aid=3)
[ 3672.493109] wlan0: associated
[ 3696.546481] wlan0: deauthenticating from <MAC 'SuperDaddy' [AN7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3697.414685] wlan0: authenticate with <MAC 'Mommy' [AN6]>
[ 3697.434637] wlan0: send auth to <MAC 'Mommy' [AN6]> (try 1/3)
[ 3697.538434] wlan0: send auth to <MAC 'Mommy' [AN6]> (try 2/3)
[ 3697.642520] wlan0: send auth to <MAC 'Mommy' [AN6]> (try 3/3)
[ 3697.746667] wlan0: authentication with <MAC 'Mommy' [AN6]> timed out
[ 3719.987602] wlan0: authenticate with <MAC 'Mommy' [AN6]>
[ 3724.810548] wlan0: send auth to <MAC 'Mommy' [AN6]> (try 1/3)
[ 3724.810720] wlan0: aborting authentication with <MAC 'Mommy' [AN6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3740.069595] wlan0: authenticate with <MAC 'SuperDaddy' [AN7]>
[ 3744.900589] wlan0: send auth to <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3744.903721] wlan0: authenticated
[ 3744.906418] wlan0: associate with <MAC 'SuperDaddy' [AN7]> (try 1/3)
[ 3744.910823] wlan0: RX AssocResp from <MAC 'SuperDaddy' [AN7]> (capab=0x411 status=0 aid=3)
[ 3744.910977] wlan0: associated

########## wireless info END ############


```

---

### Post by bhuveee on 2015-01-01
UPDATE: Rebooted with old kernel - 3.16.0-23-generic, wifi started working fine.

---

### Post by Hadaka on 2015-01-01
Hi,please COPY and paste these commands
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
boot
does this fix the problem? if not please run the wireless script again
thanks

---

### Post by bhuveee on 2015-01-01
Working perfectly fine now. Thanks:guitar:

---

### Post by Hadaka on 2015-01-01
Great ! is it working perfectly fine because you changed the kernel
or did you change it back and issue my commands and now its perfectly fine?

How to mark SOLVED->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by bhuveee on 2015-01-01
It worked after I issued your commands. Thanks a ton!

---

### Post by Kelvin_Tan on 2015-11-20
> **Hadaka said:**
> Hi,please COPY and paste these commands
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
boot
does this fix the problem? if not please run the wireless script again
thanks

Just want to say THANK YOU! I tried a whole bunch of stuff without success (disable hw scanning, disable power, disable 11n) and this was the only thing that worked for me.

---

### Post by corq on 2016-03-25
Also found this as a solution for Kali 2's wireless issue, I know this is an old thread but it's still very helpful info, thanks again!

---

### Post by oldos2er on 2016-03-25
Old thread closed.

---

