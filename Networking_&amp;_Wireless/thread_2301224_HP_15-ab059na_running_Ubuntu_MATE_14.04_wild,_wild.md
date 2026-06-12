---
title: "HP 15-ab059na running Ubuntu MATE 14.04 wild, wild wireless!"
date: 2015-10-31
forum: Networking &amp; Wireless
---

### Post by Timothy Taylor on 2015-10-31
Wireless signal comes and goes, mostly goes.

I ran the full updates, re-booted.  Still no joy.

```

########## wireless info START ##########

Report from: 31 Oct 2015 01:53 GMT +0000

Booted last: 31 Oct 2015 01:47 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-51-generic #69~14.04.1-Ubuntu SMP Wed Oct 7 15:32:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:804c]
	Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:80b8]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723be              85054  0 
btcoexist              50304  1 rtl8723be
hp_wmi                 14109  0 
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
sparse_keymap          13948  1 hp_wmi
rtlwifi                64255  2 rtl_pci,rtl8723be
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              498458  2 mac80211,rtlwifi
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4780273 (4.7 MB)  TX bytes:398157 (398.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tha Mitey Bizzo NotWork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Tha Mitey Bizzo NotWork' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:642   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       985     1  0 01:47 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Tha Mitey Bizzo NotWork] -------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Tha Mitey Bizzo NotWork: Infra, <MAC 'Tha Mitey Bizzo NotWork' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/Tha Mitey Bizzo NotWork]] (600 root)
[connection] id=Tha Mitey Bizzo NotWork | type=802-11-wireless
[802-11-wireless] ssid=Tha Mitey Bizzo NotWork | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tha Mitey Bizzo NotWork' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Tha Mitey Bizzo NotWork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001db808cea2
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
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
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F027B13105AEA0ECF6ABE3F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

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

[   26.948754] wlan0: send auth to <MAC 'Tha Mitey Bizzo NotWork' [AC1]> (try 1/3)
[   26.950770] wlan0: authenticated
[   26.953660] wlan0: associate with <MAC 'Tha Mitey Bizzo NotWork' [AC1]> (try 1/3)
[   26.958153] wlan0: RX AssocResp from <MAC 'Tha Mitey Bizzo NotWork' [AC1]> (capab=0x411 status=0 aid=1)
[   26.958339] wlan0: associated
[   26.958374] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

I found [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI") after searching for **rtl8723be** and followed the advice to add "options rtl8723be msi=1 ips=0" in /etc/modprobe.d/rtl8723be.conf.

Though I have the 8723BE, it behaves as the 8723AE listed above =  "Data rates and signal strengths fluctuate wildly and network connection drops occasionally."

Any ideas?

---

### Post by jeremy31 on 2015-10-31
I see no sign of any /etc/modprobe.d/rtl8723be.conf file but try something similar
```
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot

---

### Post by Timothy Taylor on 2015-11-02
Thanks for that:
```

########## wireless info START ##########

Report from: 02 Nov 2015 15:02 GMT +0000

Booted last: 02 Nov 2015 14:46 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-51-generic #69~14.04.1-Ubuntu SMP Wed Oct 7 15:32:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:804c]
	Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:80b8]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
rtl8723be              85054  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                64255  2 rtl_pci,rtl8723be
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              498458  2 mac80211,rtlwifi
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2735761 (2.7 MB)  TX bytes:504661 (504.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tha Mitey Bizzo NotWork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Tha Mitey Bizzo NotWork' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:345   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1273     1  0 14:46 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Tha Mitey Bizzo NotWork 1] -----------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Tha Mitey Bizzo NotWork: Infra, <MAC 'Tha Mitey Bizzo NotWork' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/Tha Mitey Bizzo NotWork]] (600 root)
[connection] id=Tha Mitey Bizzo NotWork | type=802-11-wireless
[802-11-wireless] ssid=Tha Mitey Bizzo NotWork | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Tha Mitey Bizzo NotWork 1]] (600 root)
[connection] id=Tha Mitey Bizzo NotWork 1 | type=802-11-wireless
[802-11-wireless] ssid=Tha Mitey Bizzo NotWork | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tha Mitey Bizzo NotWork' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Tha Mitey Bizzo NotWork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000050fc933985
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
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
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F027B13105AEA0ECF6ABE3F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

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

[  137.385816] wlan0: authenticate with <MAC 'Tha Mitey Bizzo NotWork' [AC1]>
[  137.405613] wlan0: send auth to <MAC 'Tha Mitey Bizzo NotWork' [AC1]> (try 1/3)
[  137.407530] wlan0: authenticated
[  137.409193] wlan0: associate with <MAC 'Tha Mitey Bizzo NotWork' [AC1]> (try 1/3)
[  137.412322] wlan0: RX AssocResp from <MAC 'Tha Mitey Bizzo NotWork' [AC1]> (capab=0x411 status=0 aid=1)
[  137.412435] wlan0: associated
[  137.412554] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

Wifi seems to be holding the connection so far.
Signal strength is still wildly variable, even though my router is just across the room.

---

### Post by Timothy Taylor on 2015-11-02
Ha!

Spoke too soon.
I went out to try the public wifi in a nearby pub: I briefly caught a flash of their wifi signal before it disappeared, never to return, despite various edits to rtl8723be.conf.

The wifi is seriously messed up.

I can't believe that something so simple should be such a problem.  I had an EEE-PC seven years ago which worked with Ubuntu and WiFi straight out of the box, with no messing about.  It still works.

I bought this new HP laptop for better graphics and find that the wretched thing can't even connect to WiFi.
Useless.

:(

---

### Post by Timothy Taylor on 2015-11-03
I finally lost patience trying to get this rubbish to work.  None of the "fixes" published online have made any difference to the pathetic performance of my laptop wireless.

I went to my local computer shop and bought a TL-WN823N USB wireless adapter.

The wifi signal is now strong, steady as a rock and it all works.  :)

The guys in the computer shop say there's a steady stream of folks with wifi problems on HP laptops, so I'm guessing that the RTL8723 is some cheap-as-possible rubbish which Spewlett Hackard imagined would do. That would also explain why people are still struggling with this adapter, years after it's release.

---

### Post by praseodym on 2015-11-03
You can try updating the driver:

[https://forum.ubuntuusers.de/topic/frage-w-lan-probleme/#post-7252963](https://forum.ubuntuusers.de/topic/frage-w-lan-probleme/#post-7252963)

Bluetooth?!

[https://forum.ubuntuusers.de/topic/probleme-mit-rtl8723be/2/#post-7239178](https://forum.ubuntuusers.de/topic/probleme-mit-rtl8723be/2/#post-7239178)

---

### Post by Timothy Taylor on 2015-11-05
> **praseodym said:**
> You can try updating the driver:

Ha!

That locked up my computer when I tried to connect.  Only way out was the power switch.

No worries though - I was going to return this laptop, citing wifi issues and I reinstalled the original disk image.
Out of curiosity, I tried the Windows 8 and discovered that the wifi works fine with that, so this is an Ubuntu problem.

Does the RTL8723 only work with Windows or something??

---

### Post by Timothy Taylor on 2015-11-05
I've now reinstalled Ubuntu on the Pavilion and run all the updates, etc.
I've noticed something else:

~ The wifi on my Pavilion running Windows 8  can see my router wifi plus 4-5 others nearby.
~ The wifi on my Pavilion running Ubuntu can *only* see my router's wifi - which is coming and going as before.
~ The wifi on my old 2008 EEE-PC running Ubuntu can see my router wifi plus **16** others!

It seems like the Wifi connection issue was all sorted and working seven years ago.
What happened?
Why are we still seeing these problems now?

update
The Pavilion has been on for about 45 minutes and now has lost my router wifi altogether.  Logging out and in again, rebooting, etc. have no effect.  The area to the right of the trackpad is now warm though, so maybe there's a thermal sensitivity issue?
The wifi still works fine in Windows though.

:(  ???

---

### Post by Timothy Taylor on 2015-11-08
I am trying out a Lenovo E555, which uses the same RTL8723BE wifi adapter.

The wifi was almost unusable, just like the Pavilion.
After installing the *rtlwifi_new* driver and creating */etc/modprobe.d/rtl8723be.conf* containing *options rtl8723be fwlps=N ips=N*, everything is working fine.  It still doesn't have the reception or performance of my old EEE-PC, but it's perfectly usable.

It would seem that there's some problem with the implementation of wireless in the Pavilion.
The guys in my local PC shop say there's a regular stream of HP laptop owners bringing machines in with wifi issues.  The usual problem is chips overheating and de-soldering themselves from the pcb, due to poor thermal design.  

The wifi in these machines is flying by the seat of it's pants..

---

