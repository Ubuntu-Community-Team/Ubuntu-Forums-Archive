---
title: "[ubuntu]  Wifi Drops and Slowdowns TPLINK TL-WN823N on ubuntu 14.04 LTS"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by zampoodle on 2015-02-04
Consistently and seemingly randomly I will experience massive slowdowns in wifi speeds as well as drops that require me to restart before having it be able to reconnect. I have looked around for many fixes and couldn't find any.
Script output: ```


########## wireless info START ##########

Report from: 04 Feb 2015 21:24 EST -0500

Booted last: 04 Feb 2015 21:20 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7850]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 093a:2521 Pixart Imaging, Inc. 
Bus 003 Device 005: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 003 Device 004: ID 047f:c010 Plantronics, Inc. 
Bus 003 Device 002: ID 1532:011a Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630669  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

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

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::68d:38ff:fe07:9f23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25540549 (25.5 MB)  TX bytes:1247036 (1.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"beaner99"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'beaner99' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:252   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

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

- Device: wlan1  [beaner99 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *beaner99:       Infra, <MAC 'beaner99' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2

  IPv4 Settings:
    Address:         192.168.1.135
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/beaner99]] (600 root)
[connection] id=beaner99 | type=802-11-wireless
[802-11-wireless] ssid=beaner99 | mac-address=<MAC address> | mtu=1500
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/beaner99 1]] (600 root)
[connection] id=beaner99 1 | type=802-11-wireless
[802-11-wireless] ssid=beaner99 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'beaner99' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"beaner99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029d55a95a1
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2E676CE01D91070679A9EF3
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

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
options iwlwifi 11n_disable=1 wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    8.458235] rtl8192cu: Chip version 0x11
[    8.486865] rtl8192cu: MAC address: <MAC 'wlan1' [IF]>
[    8.486866] rtl8192cu: Board Type 0
[    8.486945] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    8.486956] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    8.860178] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.860364] rtlwifi: wireless switch is on
[    8.886426] systemd-udevd[330]: renamed network interface wlan0 to wlan1
[   10.293716] rtl8192cu: MAC auto ON okay!
[   10.304231] rtl8192cu: Tx queue select: 0x05
[   10.660053] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[   12.184610] wlan1: authenticate with <MAC 'beaner99' [AC1]>
[   12.205847] wlan1: send auth to <MAC 'beaner99' [AC1]> (try 1/3)
[   12.232619] wlan1: authenticated
[   12.232736] rtl8192cu 3-11:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[   12.232738] rtl8192cu 3-11:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   12.232739] rtl8192cu 3-11:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   12.236330] wlan1: associate with <MAC 'beaner99' [AC1]> (try 1/3)
[   12.244053] wlan1: RX AssocResp from <MAC 'beaner99' [AC1]> (capab=0x411 status=0 aid=2)
[   12.244068] wlan1: associated
[   12.244078] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   12.264419] wlan1: deauthenticating from <MAC 'beaner99' [AC1]> by local choice (reason=2)
[   12.280841] wlan1: authenticate with <MAC 'beaner99' [AC1]>
[   12.281243] wlan1: send auth to <MAC 'beaner99' [AC1]> (try 1/3)
[   12.290507] wlan1: authenticated
[   12.290607] rtl8192cu 3-11:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[   12.290608] rtl8192cu 3-11:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   12.290609] rtl8192cu 3-11:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   12.292295] wlan1: associate with <MAC 'beaner99' [AC1]> (try 1/3)
[   12.309301] wlan1: RX AssocResp from <MAC 'beaner99' [AC1]> (capab=0x411 status=0 aid=2)
[   12.309315] wlan1: associated

########## wireless info END ############


```

Thanks in advance for any and all help

---

### Post by Pilot6 on 2015-02-05
You need to install another driver. Run in terminal

```
sudo apt-get install git
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install
```

---

### Post by absurdcakes on 2015-02-16
^I did that. My screen freezes at the start up screen.

---

### Post by marcin29 on 2015-05-03
I had the same problem. I've used solution from this topic:

[http://ubuntuforums.org/showthread.php?t=2266703&highlight=tp+wn823n](http://ubuntuforums.org/showthread.php?t=2266703&highlight=tp+wn823n)

1. I've changed network manager to wcid
2. I've installed drivers from this link:
[https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)
(could be that this driver installation is enough to fix this)

It seems that Wifi working properly right now.

---

### Post by tte11 on 2015-09-07
> **marcin29 said:**
> I had the same problem. I've used solution from this topic:

[http://ubuntuforums.org/showthread.php?t=2266703&highlight=tp+wn823n](http://ubuntuforums.org/showthread.php?t=2266703&highlight=tp+wn823n)

1. I've changed network manager to wcid
2. I've installed drivers from this link:
[https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md](https://github.com/pvaret/rtl8192cu-fixes/blob/master/README.md)
(could be that this driver installation is enough to fix this)

It seems that Wifi working properly right now.

Just wanted to say that I just installed the driver from the source listed and it worked. Changing from network manager to wicd wasn't necessary in my experience.

---

### Post by pmaccer79 on 2015-11-14
> **tte11 said:**
> Just wanted to say that I just installed the driver from the source listed and it worked. Changing from network manager to wicd wasn't necessary in my experience.
Same for me, too.  Massive thanks to marcin29 and tte11.

---

