---
title: "ubuntu 14.04 LTS wifi problem"
date: 2016-02-27
forum: Networking &amp; Wireless
---

### Post by ubunginner2016 on 2016-02-27
I'm new to ubuntu and i have installed the 14.04LTS version 2 days  ago,But i have a wifi problem ! when i turn one the laptop and get  started everything works fine and the connection is good but not for a  long time it's just about 5 minutes and i lose the networking,  Everything looks to be good and working i have no disconnection error or  any sign it just loses the networking i can't open any site or do  anything just like it's disconnected, I have tried to disconnect it and connect again but when i do that it  never connects again " Disconnected , you are offline " , All i can do to connect to the internet is to use a wired connection or  to restart my laptop again :/ I'm really tired and starting to regret  installing ubuntu , i tried alot of things on this forum or other sites  about the terminal command lines but it's still the same, So please  someone help me !

---

### Post by Bucky Ball on 2016-02-27
Welcome. Please provide us with the output from the wireless info script. You'll find a link to it in my signature down below. 

If everything else is working fine and you like the OS, regretting installing it is a bit premature. Your wireless is probably fixable, and possibly with a couple of commands from one of the experts here.

We advise emailing the manufacturer and politely asking why their hardware doesn't work with Linux rather than the other way around. There's plenty of USB wireless dongles and internal wireless cards that work 'out of the box'.

When using Ubunutu, it is true, one needs to be aware of the fact that not all hardware is going to work perfectly out of the box, or perhaps not at all, and roll with it. It is no fault of the OS. 

Good luck. :)

PS: Remember installing Windows? You need to install a heap of drivers for all sorts of things which is unnecessary, in most cases, in Ubuntu. There is also a learning curve but this is the case with any new OS or anything new, really.

---

### Post by ubunginner2016 on 2016-02-27
> **Bucky Ball said:**
> Welcome. Please provide us with the output from the wireless info script. You'll find a link to it in my signature down below. 

If everything else is working fine and you like the OS, regretting installing it is a bit premature. Your wireless is probably fixable, and possibly with a couple of commands from one of the experts here.

We advise emailing the manufacturer and politely asking why their hardware doesn't work with Linux rather than the other way around. There's plenty of USB wireless dongles and internal wireless cards that work 'out of the box'.

When using Ubunutu, it is true, one needs to be aware of the fact that not all hardware is going to work perfectly out of the box, or perhaps not at all, and roll with it. It is no fault of the OS. 

Good luck. :)

PS: Remember installing Windows? You need to install a heap of drivers for all sorts of things which is unnecessary, in most cases, in Ubuntu. There is also a learning curve but this is the case with any new OS or anything new, really.

thanks for replying :) ,
this is my wifi info 
```

########## wireless info START ##########

Report from: 27 Feb 2016 10:33 EET +0200

Booted last: 27 Feb 2016 09:00 EET +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-30-generic #35~14.04.1-Ubuntu SMP Fri Feb 19 14:48:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380b]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 174f:14b2 Syntek 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 012: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 009: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rndis_wlan             57344  0 
rndis_host             16384  1 rndis_wlan
usbnet                 40960  3 rndis_host,rndis_wlan,cdc_ether
rtl8723be              90112  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              729088  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              540672  3 mac80211,rndis_wlan,rtlwifi
mxm_wmi                16384  1 nouveau
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  1 snd_soc_rt5640
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
snd_pcm               102400  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
video                  40960  3 i915,ideapad_laptop,nouveau
wmi                    20480  2 mxm_wmi,nouveau

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

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.132  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86095 errors:7 dropped:0 overruns:0 frame:7
          TX packets:72237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83388892 (83.3 MB)  TX bytes:11985551 (11.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11767106 (11.7 MB)  TX bytes:1353364 (1.3 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       838     1  0 09:00 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.132
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/ro_ma]] (600 root)
[connection] id=ro_ma | type=802-11-wireless
[802-11-wireless] ssid=ro_ma | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HUAWEI-97d6]] (600 root)
[connection] id=HUAWEI-97d6 | type=802-11-wireless
[802-11-wireless] ssid=HUAWEI-97d6 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ppmu]] (600 root)
[connection] id=ppmu | type=802-11-wireless
[802-11-wireless] ssid=ppmu | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Cairo (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

usb0      no frequency information.

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

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'mayar saad' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"mayar saad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a8684e17e
                    Extra: Last beacon: 812ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ppmu' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"ppmu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000036dec7157
                    Extra: Last beacon: 172ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ro_ma' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ro_ma"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000db6c2b15b
                    Extra: Last beacon: 1508ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0EB6BE33DFAD6AEFD4D63AE
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A5:12:3B:D7:BC:9F:40:9E:55:8B:C8:E5:DE:0B:BB:59:AA:18:40:1F
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A5:12:3B:D7:BC:9F:40:9E:55:8B:C8:E5:DE:0B:BB:59:AA:18:40:1F
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A5:12:3B:D7:BC:9F:40:9E:55:8B:C8:E5:DE:0B:BB:59:AA:18:40:1F
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F4CACC5FCAEBE7C22930A24
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A5:12:3B:D7:BC:9F:40:9E:55:8B:C8:E5:DE:0B:BB:59:AA:18:40:1F
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A5:12:3B:D7:BC:9F:40:9E:55:8B:C8:E5:DE:0B:BB:59:AA:18:40:1F
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-30-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A5:12:3B:D7:BC:9F:40:9E:55:8B:C8:E5:DE:0B:BB:59:AA:18:40:1F
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

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwl=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[ 3572.727341] usb 1-3: device firmware changed
[ 5568.365431] wlan0: authenticate with <MAC 'ppmu' [AC2]>
[ 5568.388846] wlan0: direct probe to <MAC 'ppmu' [AC2]> (try 1/3)

########## wireless info END ############


```

i hope it helps :/

---

### Post by praseodym on 2016-02-27
Lets try
```

echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
echo 'KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower 18"' | sudo tee -a /etc/udev/rules.d/75-wlan.rules 
```
Reboot.

---

### Post by ubunginner2016 on 2016-02-27
> **praseodym said:**
> Lets try
```

echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
echo 'KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower 18"' | sudo tee -a /etc/udev/rules.d/75-wlan.rules 
```
Reboot.

It Worked :) !! I don't know how to describe how thankful i'm right now xD thank you so much :)

---

### Post by Hadaka on 2016-02-27
Hi, Glad that worked for you and I am sure
*praseodym is pleased as well. Also your
country code is not set , please do..
```
sudo iw reg set EG
sudo sed -i 's/^REG.*=$/&EG/' /etc/default/crda
```
then please mark this thread solved by going to your first post
of your thread, clicking Thread TOOLS and then choose SOLVED.
thanks.

---

