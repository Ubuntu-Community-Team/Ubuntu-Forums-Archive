---
title: "RTL8191SEvB Wireless LAN Controller unclaimed in TOSHIBA m645 sp6001L"
date: 2015-10-26
forum: Networking &amp; Wireless
---

### Post by ricardo41 on 2015-10-26
Hi everyone, 

Im new in ubuntu and i`ve been l having this problem for days , i 'd appreciatte some help. I am using ubuntu 14.04 LTS 64 bit OS and it worked very well until one day without any previous update the wireless began to fail ,oscillating too much , sometimes even desconecting from network. So i decided to reinstall ubuntu but it didnt work . Now i decided to install the driver using the windows wireless driver application. After this my wifi dissapeared and appeared as UNCLAIMED.


gian@gian-Satellite-M645:~$ sudo lshw -C network

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:44:6b:0c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=131.225.56.203     latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:7000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:5000(size=256) memory:d4600000-d4603fff



I`ve desinstalled already the driver but a i am still having it UNCLAIMED. Can anybody help me to claim it back and to solve the oscillation problem it will certainly appear?

---

### Post by Vladlenin5000 on 2015-10-26
Hi and welcome.

Your wireless device is most likely defective. If so, there's nothing you can do about it. And using Windows drivers can only make it worse.
Does it work as expected in a live session?

---

### Post by ricardo41 on 2015-10-26
I havent try yet , but i am using a netgear N900 wifi usb adapter and is happening exactly the same thing. It oscillates too much.

---

### Post by Vladlenin5000 on 2015-10-26
Netgear N900 has the Ralink RT3573. Supported OOTB? Yes, check [here]("https://wikidevi.com/wiki/Netgear_WNDA4100"). Stable? No, not even close without some tweaks. Even so and considering you're experiencing similar symptoms... Have you checked the router/AP yet? Perhaps you should reboot it or even reset it.

Anyway, please follow [this]("http://ubuntuforums.org/showthread.php?t=370108") instructions and post back the results of the script so we can have a clear picture of your network config, drivers and parameters in use, etc. Needless to say do it while the dongle you want to troubleshoot is connected.

---

### Post by ricardo41 on 2015-10-26
Ok . i ran the script via wired internet connection cause as i told you the netgear N900 is giving me troubles too. I`ve got  this:

```
########## wireless info START ##########

Report from: 26 Oct 2015 18:39 CDT -0500

Booted last: 26 Oct 2015 12:51 CDT -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd80]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]

15:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 20)

##### lsusb #############################

Bus 002 Device 008: ID 248a:0568  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              630728  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
ndiswrapper           283985  0 
wmi                    19177  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:131.225.56.203  Bcast:131.225.56.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:461565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129276196 (129.2 MB)  TX bytes:21019912 (21.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         131.225.56.200  0.0.0.0         UG    0      0        0 eth0
131.225.56.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search dhcp.fnal.gov fnal.gov fermi.win.fnal.gov win.fnal.gov minos-soudan.org

##### network managers ##################

Installed:

    NetworkManager

Running:

root       931     1  0 12:51 ?        00:00:05 NetworkManager

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
    Address:         131.225.56.203
    Prefix:          24 (255.255.255.0)
    Gateway:         131.225.56.200

    DNS:             131.225.0.254

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

[[/etc/NetworkManager/system-connections/guest 1]] (600 root)
[connection] id=guest 1 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/fgz]] (600 root)
[connection] id=fgz | type=802-11-wireless | permissions=user:gian:; | autoconnect=false
[802-11-wireless] ssid=fgz | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/fgz 1]] (600 root)
[connection] id=fgz 1 | type=802-11-wireless
[802-11-wireless] ssid=fgz | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/guest]] (600 root)
[connection] id=guest | type=802-11-wireless | permissions=user:gian:; | autoconnect=false
[802-11-wireless] ssid=guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     81F4CDE501CE72D2443EE38
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     C8AA2904FC6A58104E65BCC
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[rt2800lib]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     3AF2621F166C8604D7D8AA5
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     09822BD19555F112E3902D4
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-66-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CD516ABEC909374CB2C52DC
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-66-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.0-66-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

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

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008171sv00000311sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001000sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001001sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001002sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001003sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001004sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001005sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001107sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001467sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001586sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00001A07sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00006897sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007155sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007171sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007172sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007172sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007173sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007173sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007177sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00007811sd00001113bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008155sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008156sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008156sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008157sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008157sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008171sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008187sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008188sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv0000897Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00000094sd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00000308sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00001104sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00001A04sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00006897sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007155sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007172sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00007612sd00001432bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008155sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008156sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008157sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008158sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008158sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008159sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008159sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008172sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000897Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000A812sd00001113bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000B612sd00001113bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E020sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E021sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E021sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E022sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E022sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E023sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E024sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E025sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E93Fsd00001458bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008173sv00008173sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008173sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00003821sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007155sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007174sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00007187sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008155sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008156sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008156sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008157sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008157sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008174sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008187sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008188sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv00008193sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[16000.628766] wlan1: associated
[17312.576730] wlan1: authenticate with <MAC address>
[17312.659945] wlan1: direct probe to <MAC address> (try 1/3)
[17312.860051] wlan1: direct probe to <MAC address> (try 2/3)
[17313.064049] wlan1: direct probe to <MAC address> (try 3/3)
[17313.268048] wlan1: authentication with <MAC address> timed out
[17313.745731] wlan1: authenticate with <MAC address>
[17313.828201] wlan1: direct probe to <MAC address> (try 1/3)
[17314.032075] wlan1: direct probe to <MAC address> (try 2/3)
[17314.236082] wlan1: direct probe to <MAC address> (try 3/3)
[17314.440061] wlan1: authentication with <MAC address> timed out
[17314.731430] wlan1: authenticate with <MAC address>
[17314.802887] wlan1: send auth to <MAC address> (try 1/3)
[17314.810126] wlan1: authenticated
[17314.812027] wlan1: associate with <MAC address> (try 1/3)
[17314.841147] wlan1: RX AssocResp from <MAC address> (capab=0x421 status=34 aid=0)
[17314.841157] wlan1: <MAC address> denied association (code=34)
[17314.901450] wlan1: deauthenticating from <MAC address> by local choice (reason=3)
[17315.046886] wlan1: authenticate with <MAC address>
[17315.102560] wlan1: send auth to <MAC address> (try 1/3)
[17315.104632] wlan1: authenticated
[17315.108028] wlan1: associate with <MAC address> (try 1/3)
[17315.149010] wlan1: RX AssocResp from <MAC address> (capab=0x421 status=34 aid=0)
[17315.149022] wlan1: <MAC address> denied association (code=34)
[17315.202512] wlan1: deauthenticating from <MAC address> by local choice (reason=3)
[17318.820488] wlan1: authenticate with <MAC address>
[17318.897706] wlan1: direct probe to <MAC address> (try 1/3)
[17319.100141] wlan1: direct probe to <MAC address> (try 2/3)
[17319.304083] wlan1: direct probe to <MAC address> (try 3/3)
[17319.508073] wlan1: authentication with <MAC address> timed out
[17323.059949] wlan1: authenticate with <MAC address>
[17323.140435] wlan1: direct probe to <MAC address> (try 1/3)
[17323.344141] wlan1: direct probe to <MAC address> (try 2/3)
[17323.548062] wlan1: direct probe to <MAC address> (try 3/3)
[17323.752115] wlan1: authentication with <MAC address> timed out
[17325.413440] wlan1: authenticate with <MAC address>
[17325.530307] wlan1: direct probe to <MAC address> (try 1/3)
[17325.732138] wlan1: direct probe to <MAC address> (try 2/3)
[17325.936043] wlan1: direct probe to <MAC address> (try 3/3)
[17326.140063] wlan1: authentication with <MAC address> timed out
[17327.464189] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[17331.013983] wlan1: authenticate with <MAC address>
[17331.062863] wlan1: direct probe to <MAC address> (try 1/3)
[17331.264134] wlan1: direct probe to <MAC address> (try 2/3)
[17331.468054] wlan1: direct probe to <MAC address> (try 3/3)
[17331.672063] wlan1: authentication with <MAC address> timed out
[17342.380131] wlan1: authenticate with <MAC address>
[17342.457330] wlan1: direct probe to <MAC address> (try 1/3)
[17342.660141] wlan1: direct probe to <MAC address> (try 2/3)
[17342.864140] wlan1: direct probe to <MAC address> (try 3/3)
[17343.068100] wlan1: authentication with <MAC address> timed out
[17359.319384] wlan1: authenticate with <MAC address>
[17359.390904] wlan1: direct probe to <MAC address> (try 1/3)
[17359.592078] wlan1: direct probe to <MAC address> (try 2/3)
[17359.796079] wlan1: direct probe to <MAC address> (try 3/3)
[17360.000072] wlan1: authentication with <MAC address> timed out
[17370.697406] wlan1: authenticate with <MAC address>
[17370.785963] wlan1: direct probe to <MAC address> (try 1/3)
[17370.988091] wlan1: direct probe to <MAC address> (try 2/3)
[17371.192142] wlan1: direct probe to <MAC address> (try 3/3)
[17371.396125] wlan1: authentication with <MAC address> timed out
[17387.391154] wlan1: authenticate with <MAC address>
[17387.462901] wlan1: direct probe to <MAC address> (try 1/3)
[17387.664163] wlan1: direct probe to <MAC address> (try 2/3)
[17387.868084] wlan1: direct probe to <MAC address> (try 3/3)
[17388.072144] wlan1: authentication with <MAC address> timed out
[17475.920142] ieee80211 phy4: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[17476.606436] r8169 0000:01:00.0 eth0: link up
[17476.606451] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by Vladlenin5000 on 2015-10-26
First of all please post results from scripts or other commands in code tags -> Go Advanced, click "#" and paste inside) and sorry for not mentioning it before...

Now...
You're troubleshooting the WiFi therefore the dongle must be connected. Now that you have the script please run it again with the WiFi dongle connected to your network as usual. Considering your posted results the only think I can say is your system is a mess, an ugly mess. So much that I'm tempted to suggest reinstall from scratch but let's not go there yet. And as commented before, ndiswrapper made things worse, a lot worse.

---

### Post by wildmanne39 on 2015-10-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ricardo41 on 2015-10-27
Sorry about the mess, sure it is. Well i reinstalled UBUNTU 14.04 and my wireless came back but is still oscillating. I properly updated UBUNTU using the update manager and finally using again in the terminal :

```
sudo apt-get update
sudo apt-get dist-upgrade
```



The actual wireless-info.txt is :

```


########## wireless info START ##########

Report from: 27 Oct 2015 00:13 CDT -0500

Booted last: 26 Oct 2015 23:53 CDT -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd80]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
    Kernel driver in use: rtl8192se

##### lsusb #############################

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192se              63196  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              630728  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 toshiba_acpi

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
          inet addr:131.225.95.210  Bcast:131.225.95.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37784184 (37.7 MB)  TX bytes:2138158 (2.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"fgz"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'fgz' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:58   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         131.225.94.1    0.0.0.0         UG    0      0        0 wlan0
131.225.94.0    0.0.0.0         255.255.254.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search dhcp.fnal.gov fnal.gov fermi.win.fnal.gov win.fnal.gov minos-soudan.org

##### network managers ##################

Installed:

    NetworkManager

Running:

root       839     1  0 Oct26 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [fgz] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Fernanda's Wi-Fi Network: Infra, <MAC 'Fernanda's Wi-Fi Network' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    fgz:             Infra, <MAC 'fgz' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    fgz:             Infra, <MAC 'fgz' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    guest:           Infra, <MAC 'guest' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84
    fgz:             Infra, <MAC 'fgz' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    guest:           Infra, <MAC 'guest' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    guest:           Infra, <MAC 'guest' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    *fgz:            Infra, <MAC 'fgz' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 86
    fgz:             Infra, <MAC 'fgz' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    guest:           Infra, <MAC 'guest' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29

  IPv4 Settings:
    Address:         131.225.95.210
    Prefix:          23 (255.255.254.0)
    Gateway:         131.225.94.1

    DNS:             131.225.0.254

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/fgz]] (600 root)
[connection] id=fgz | type=802-11-wireless
[802-11-wireless] ssid=fgz | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/guest]] (600 root)
[connection] id=guest | type=802-11-wireless
[802-11-wireless] ssid=guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'fgz' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"fgz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6f9dd917b
                    Extra: Last beacon: 68ms ago
          Cell 02 - Address: <MAC 'guest' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6f9de504b
                    Extra: Last beacon: 68ms ago
          Cell 03 - Address: <MAC 'guest' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6f87b84ba
                    Extra: Last beacon: 25400ms ago
          Cell 04 - Address: <MAC 'guest' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6f886815c
                    Extra: Last beacon: 1872ms ago
          Cell 05 - Address: <MAC 'fgz' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"fgz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6f885c278
                    Extra: Last beacon: 1824ms ago
          Cell 06 - Address: <MAC 'Fernanda's Wi-Fi Network' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Fernanda's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000197637fc46f
                    Extra: Last beacon: 104ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'fgz' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"fgz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d6f9e2580a
                    Extra: Last beacon: 68ms ago
          Cell 08 - Address: <MAC 'fgz' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"fgz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016d2e6dbff0
                    Extra: Last beacon: 68ms ago

##### module infos ######################

[rtl8192se]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C53951858E34882052195CA
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
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
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-66-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-66-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CD516ABEC909374CB2C52DC
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-66-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-66-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:57:C2:FB:ED:0D:9F:B4:61:EF:AD:39:C9:CC:AF:B5:B5:E0:67:90
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   18.433297] r8169 0000:01:00.0 eth0: link down
[   18.433356] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   18.585746] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   19.988492] wlan0: authenticate with <MAC 'guest' [AC2]>
[   20.000213] wlan0: send auth to <MAC 'guest' [AC2]> (try 1/3)
[   20.003770] wlan0: authenticated
[   20.004047] wlan0: associate with <MAC 'guest' [AC2]> (try 1/3)
[   20.011980] wlan0: RX AssocResp from <MAC 'guest' [AC2]> (capab=0x421 status=0 aid=5)
[   20.013489] wlan0: associated
[   20.013501] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  620.042442] wlan0: deauthenticating from <MAC 'guest' [AC2]> by local choice (reason=3)
[  621.148900] wlan0: authenticate with <MAC 'fgz' [AC8]>
[  621.168281] wlan0: direct probe to <MAC 'fgz' [AC8]> (try 1/3)
[  621.372140] wlan0: direct probe to <MAC 'fgz' [AC8]> (try 2/3)
[  621.576144] wlan0: direct probe to <MAC 'fgz' [AC8]> (try 3/3)
[  621.780140] wlan0: authentication with <MAC 'fgz' [AC8]> timed out
[  622.309453] wlan0: authenticate with <MAC 'fgz' [AC5]>
[  622.328223] wlan0: send auth to <MAC 'fgz' [AC5]> (try 1/3)
[  622.329371] wlan0: authenticated
[  622.332075] wlan0: associate with <MAC 'fgz' [AC5]> (try 1/3)
[  622.338924] wlan0: RX AssocResp from <MAC 'fgz' [AC5]> (capab=0x421 status=34 aid=0)
[  622.338932] wlan0: <MAC 'fgz' [AC5]> denied association (code=34)
[  622.358492] wlan0: deauthenticating from <MAC 'fgz' [AC5]> by local choice (reason=3)
[  622.589013] wlan0: authenticate with <MAC 'fgz' [AC1]>
[  622.608204] wlan0: send auth to <MAC 'fgz' [AC1]> (try 1/3)
[  622.609493] wlan0: authenticated
[  622.612112] wlan0: associate with <MAC 'fgz' [AC1]> (try 1/3)
[  622.620324] wlan0: RX AssocResp from <MAC 'fgz' [AC1]> (capab=0x421 status=0 aid=6)
[  622.621839] wlan0: associated

########## wireless info END ############




```



The information about my network devices (the wireless is not anymore UNCLAIMED ) is:

```


gian@gian-Satellite-M645:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:44:6b:0c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:7000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:4d:a1:4c:e5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.13.0-66-generic firmware=N/A ip=131.225.95.210 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:d4600000-d4603fff


```


The wireless still oscillates .I would appreciatte any help.

---

### Post by Vladlenin5000 on 2015-10-27
It looks better now indeed. Nothing stands out, not even interference from nearby wireless networks, the device is using the correct driver (I think)...
Have you rebooted the router/AP already? Any difference?

---

### Post by ricardo41 on 2015-10-27
At my work we have lots of APs at each floor providing the same wifi network in all the buiding .The oscillation happens in any floor , in any place. Because i was needing wifi with urgency i returned the N900 NETGEAR  adapter and bought a LINKSYS AC 1200 WUSB6300 and installed using these instructions [HTML] http://askubuntu.com/questions/584822/linksys-ac1200-wireless-ac-usb-adapter-install [/HTML] . It is working really fine. However my wifi card is still having the oscillation problem .  Any idea?

---

### Post by Vladlenin5000 on 2015-10-28
Sorry, no... I was expecting to see something obvious in the script results but everything seems to be as it should.

This is a case for our great guru chili555 AKA "Dr. Chili". I hope he sees this.

---

### Post by praseodym on 2015-10-28
Hi,

there are several networks showing up named "fgz" which you'd like to connect to, aren't you? Please change the ESSID in your router to something different and to pure WPA2-AES (CCMP) encryption. Additionally, use a fixed channel and do not hide the network. Try to re-connect. Please run afterwards:
```

sudo iwlist scan
```

---

