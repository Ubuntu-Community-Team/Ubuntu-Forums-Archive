---
title: "wireless disconnecting HP 255 G4 Notebook"
date: 2016-02-28
forum: Networking &amp; Wireless
---

### Post by armorlingar on 2016-02-28
Hi all,

This is my first post and I don even know if it's the right place to post it. I've found some threads about a wireless script and I hope I can post the txt file here.

My wifi on 14.04 is disconnecting all the time and the range is very short. No issues with other devices.

Here is my txt file:

```

########## wireless info START ##########

Report from: 28 Feb 2016 11:34 GMT +0000

Booted last: 28 Feb 2016 11:07 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:8137]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 002: ID 064e:9325 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              94208  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.26  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: fd51:20d:3e10:0:15f7:f19a:bbf4:3b82/64 Scope:Global
          inet6 addr: fd51:20d:3e10:0:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17488817 (17.4 MB)  TX bytes:949511 (949.5 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fd51:20d:3e10:0:6972:8f4c:ad78:5363/64 Scope:Global
          inet6 addr: fd51:20d:3e10:0:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48797 (48.7 KB)  TX bytes:52665 (52.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SKY0D4CB"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'SKY0D4CB' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       704     1  0 11:07 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Connessione via cavo 1] ---------------------------------------
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
    Address:         192.168.0.26
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

  IPv6 Settings:
    Address:         fd51:20d:3e10:0:15f7:f19a:bbf4:3b82
    Prefix:          64
    Gateway:         ::

    Address:         fd51:20d:3e10:0:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

    DNS:             fd51:20d:3e10:0:7e4c:a5ff:fe31:888

- Device: wlan0  [SKY0D4CB] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *SKY0D4CB:       Infra, <MAC 'SKY0D4CB' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2

  IPv4 Settings:
    Address:         192.168.0.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

  IPv6 Settings:
    Address:         fd51:20d:3e10:0:6972:8f4c:ad78:5363
    Prefix:          64
    Gateway:         ::

    Address:         fd51:20d:3e10:0:<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         ::

    Address:         fe80::<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         ::

    DNS:             fd51:20d:3e10:0:7e4c:a5ff:fe31:888

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

[[/etc/NetworkManager/system-connections/SKY0D4CB]] (600 root)
[connection] id=SKY0D4CB | type=802-11-wireless
[802-11-wireless] ssid=SKY0D4CB | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
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
          Cell 01 - Address: <MAC 'SKY0D4CB' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"SKY0D4CB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000035fcf962069
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     B60F970654516A3D2F6FC24
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
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
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
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
minstrel_vht_only: Y
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

[   18.219690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.463662] r8169 0000:03:00.0 eth0: link down
[   18.463754] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.900247] wlan0: authenticate with <MAC 'SKY0D4CB' [AC1]>
[   19.915466] wlan0: send auth to <MAC 'SKY0D4CB' [AC1]> (try 1/3)
[   19.918628] wlan0: authenticated
[   19.922860] wlan0: associate with <MAC 'SKY0D4CB' [AC1]> (try 1/3)
[   19.927857] wlan0: RX AssocResp from <MAC 'SKY0D4CB' [AC1]> (capab=0x1411 status=0 aid=3)
[   19.930256] wlan0: associated
[   19.930286] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.161112] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'SKY0D4CB' [AC1]>
[   20.670194] r8169 0000:03:00.0 eth0: link up
[   20.670221] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  320.764236] wlan0: deauthenticating from <MAC 'SKY0D4CB' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  321.763355] wlan0: authenticate with <MAC 'SKY0D4CB' [AC1]>
[  321.786280] wlan0: send auth to <MAC 'SKY0D4CB' [AC1]> (try 1/3)
[  321.790310] wlan0: authenticated
[  321.794484] wlan0: associate with <MAC 'SKY0D4CB' [AC1]> (try 1/3)
[  321.799437] wlan0: RX AssocResp from <MAC 'SKY0D4CB' [AC1]> (capab=0x1411 status=0 aid=3)
[  321.801096] wlan0: associated
[  321.870714] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'SKY0D4CB' [AC1]> (repeated 3 times)

########## wireless info END ############


```

Can you help me with this? :confused:

Thank you

---

### Post by jeremy31 on 2016-02-28
```
sudo apt-get install git build-essentials
git clone -b rock.new_btcoex [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)
cd rtlwifi_new
make
sudo make install
```[COLOR=#111111][FONT=Ubuntu]Reboot and then[/FONT][/COLOR]
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=1
```[COLOR=#111111][FONT=Ubuntu]Test wireless, if no change then[/FONT][/COLOR]
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=2
```[COLOR=#111111][FONT=Ubuntu]Test wireless again, one or the other should result in better reception[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When you find that one works better than the other[/FONT][/COLOR]
```
echo "options rtl8723be ant_sel=X" | sudo tee /etc/modprobe.d/rtlbtcoex.conf
```
Replace X with 1 or 2
[COLOR=#111111][FONT=Ubuntu]Then the parameter will be remembered following a restart[/FONT][/COLOR]

---

### Post by armorlingar on 2016-03-04
Thanks for your help, but I tried both options and it doesn't connect to the network.

---

### Post by jeremy31 on 2016-03-04
Post ```
modinfo -p rtl8723be
```

---

