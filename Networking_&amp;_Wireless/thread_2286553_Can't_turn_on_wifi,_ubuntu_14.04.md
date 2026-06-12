---
title: "Can't turn on wifi, ubuntu 14.04"
date: 2015-07-13
forum: Networking &amp; Wireless
---

### Post by gonzalo17 on 2015-07-13
Hello everyone :p.

My problem is that today when I turn on my notebook the wifi connection doesn't work anymore.

My computer has a keyboard combo that activates the wifi (Fn + F11), but when I try this nothing happens. Despite this, when I press Fn + F12 I can activate the bluetooth so the problem has nothing to do with the keyboard or something like that.

The modem is working well, because on windows 7 (I have two SO installed in the pc) the wifi work just fine (and also the wifi switch through keyboard Fn + F11).

I also tried things like reset the bios setup but the problem persists.

I read this thread before posting: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

And this are the results from the "wireless info script":



```

########## wireless info START ##########

Report from: 13 Jul 2015 03:15 ART -0300

Booted last: 12 Jul 2015 23:35 ART -0300

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:18 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:9196]
    Kernel driver in use: rtl8192ce

03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:4140]
    Kernel driver in use: jme

##### lsusb #############################

Bus 002 Device 004: ID 5986:0315 Acer, Inc 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

rtl8192ce              52806  0 
rtl_pci                26314  1 rtl8192ce
rtlwifi                52835  2 rtl_pci,rtl8192ce
rtl8192c_common        47340  1 rtl8192ce
mac80211              546067  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              409394  2 mac80211,rtlwifi
wmi                    18673  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd11:2233:4455:1:290:f5ff:fec1:46d3/64 Scope:Global
          inet6 addr: fe80::290:f5ff:fec1:46d3/64 Scope:Link
          inet6 addr: fd11:2233:4455:1:4f5:73c0:6cba:2fc1/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6904190 (6.9 MB)  TX bytes:1435738 (1.4 MB)
          Interrupt:44 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search ft.com

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1058     1  0 Jul12 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Conexión cableada 1] -----------------------------------------
  Type:              Wired
  Driver:            jme
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.34
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fd11:2233:4455:1:4f5:73c0:6cba:2fc1
    Prefix:          64
    Gateway:         fe80::1

    Address:         fd11:2233:4455:1:290:f5ff:fec1:46d3
    Prefix:          64
    Gateway:         fe80::1

    Address:         fe80::290:f5ff:fec1:46d3
    Prefix:          64
    Gateway:         fe80::1

    DNS:             fe80::1

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

[[/etc/NetworkManager/system-connections/Speedy-1171F0]] (600 root)
[connection] id=Speedy-1171F0 | type=802-11-wireless
[802-11-wireless] ssid=Speedy-1171F0 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/faibertel wifi]] (600 root)
[connection] id=faibertel wifi | type=802-11-wireless
[802-11-wireless] ssid=faibertel wifi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Homero]] (600 root)
[connection] id=Homero | type=802-11-wireless
[802-11-wireless] ssid=Homero | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/OliWifi]] (600 root)
[connection] id=OliWifi | type=802-11-wireless
[802-11-wireless] ssid=OliWifi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AlpatacoLGA]] (600 root)
[connection] id=AlpatacoLGA | type=802-11-wireless
[802-11-wireless] ssid=AlpatacoLGA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/-Casa-abuela-]] (600 root)
[connection] id=-Casa-abuela- | type=802-11-wireless
[802-11-wireless] ssid=-Casa-abuela- | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Austral2]] (600 root)
[connection] id=Austral2 | type=802-11-wireless
[802-11-wireless] ssid=Austral2 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SpeedyWiFi]] (600 root)
[connection] id=SpeedyWiFi | type=802-11-wireless
[802-11-wireless] ssid=SpeedyWiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/tolosa01]] (600 root)
[connection] id=tolosa01 | type=802-11-wireless
[802-11-wireless] ssid=tolosa01 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/casa wifi 2 1]] (600 root)
[connection] id=casa wifi 2 1 | type=802-11-wireless
[802-11-wireless] ssid=casa wifi 2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Speedy-8XqaIo 1]] (600 root)
[connection] id=Speedy-8XqaIo 1 | type=802-11-wireless
[802-11-wireless] ssid=Speedy-8XqaIo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DAMI]] (600 root)
[connection] id=DAMI | type=802-11-wireless
[802-11-wireless] ssid=DAMI | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/casa wifi 2]] (600 root)
[connection] id=casa wifi 2 | type=802-11-wireless
[802-11-wireless] ssid=casa wifi 2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Speedy-8XqaIo]] (600 root)
[connection] id=Speedy-8XqaIo | type=802-11-wireless
[802-11-wireless] ssid=Speedy-8XqaIo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Argentina/Buenos_Aires (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A5286D03221770A227ABC5B
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        73:3F:01:E9:F4:92:70:4C:66:EB:0B:0F:52:53:4B:69:F3:D4:32:84
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        73:3F:01:E9:F4:92:70:4C:66:EB:0B:0F:52:53:4B:69:F3:D4:32:84
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        73:3F:01:E9:F4:92:70:4C:66:EB:0B:0F:52:53:4B:69:F3:D4:32:84
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
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
vermagic:       3.13.0-48-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        73:3F:01:E9:F4:92:70:4C:66:EB:0B:0F:52:53:4B:69:F3:D4:32:84
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-48-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        73:3F:01:E9:F4:92:70:4C:66:EB:0B:0F:52:53:4B:69:F3:D4:32:84
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-48-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        73:3F:01:E9:F4:92:70:4C:66:EB:0B:0F:52:53:4B:69:F3:D4:32:84
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: Y
ips: Y
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

coretemp

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x197b:0x0250 (jme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.167342] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   14.398550] rtl8192ce 0000:02:00.0: Direct firmware load failed with error -2
[   14.398555] rtl8192ce 0000:02:00.0: Falling back to user helper
[   14.546241] rtlwifi: Firmware rtlwifi/rtl8192cfw.bin not available

########## wireless info END ############


```


Sorry if my english is bad, it is not my native language.


Edit: For the moment I'm using a wired connection.

---

### Post by jeremy31 on 2015-07-13
It looks like firmware is missing ```
sudo apt-get install linux-firmware
```

Reboot and if you still have issues, run the script again and post the new results

---

### Post by gonzalo17 on 2015-07-13
> **jeremy31 said:**
> It looks like firmware is missing ```
sudo apt-get install linux-firmware
```

Reboot and if you still have issues, run the script again and post the new results

Thank you! I did that and now everything is working again. I see it was something very simple but I'm just a beginner.

---

