---
title: "Cant Get Wifi To work"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by Timothy_Morrison on 2016-04-19
Okay, so I recently HAD to come back to Linux. Ubuntu has always been my favorite Distro. Anyway, My wi-fi won't connect on my laptop. Its a **HP 15-f337wm**. It works fine on ethernet. But wifi it just doesn't work correctly. It'll show it's connected to my Wi-Fi, but then it won't load a page, or even work with the Ubuntu store. Help and advice appreciated. [U]sudo lshw -c network returns:

```
[/U]*-network               
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 40:b8:9a:a0:fb:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=4.2.0-35-generic firmware=N/A ip=192.168.0.22 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:42 ioport:e000(size=256) memory:fea00000-fea03fff
*-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 07
       serial: 3c:a8:2a:bd:3d:c4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.0.25 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:35 ioport:d000(size=256) memory:fe914000-fe914fff memory:fe910000-fe913fff memory:fe900000-fe90ffff
aelix@aelix-laptop:~$ 
aelix@aelix-laptop:~$ 
```

Extremely confused.

---

### Post by howefield on 2016-04-19
Hello and welcome to the forums.

Thread moved to the "*Networking & Wireless*"forum.

---

### Post by Bucky Ball on 2016-04-19
Welcome. Perhaps post the output of the wirelessinfo script linked in my signature at the bottom of this post, please. The driver in your output appears to be correct.

---

### Post by Timothy_Morrison on 2016-04-19
```
########## wireless info START ##########

Report from: 19 Apr 2016 15:40 EDT -0400

Booted last: 19 Apr 2016 14:58 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:8015]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:022a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0eef:c04d D-WAV Scientific Co., Ltd 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8188ee              86016  0 
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl_pci                28672  1 rtl8188ee
rtlwifi                77824  2 rtl_pci,rtl8188ee
mac80211              741376  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              552960  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28389077 (28.3 MB)  TX bytes:2423883 (2.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.22  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22439 (22.4 KB)  TX bytes:33739 (33.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Morrison"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Morrison' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       918     1  0 14:58 ?        00:00:01 NetworkManager

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
    Address:         192.168.0.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0  [Morrison] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Morrison:       Infra, <MAC 'Morrison' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.0.22
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

[[/etc/NetworkManager/system-connections/Morrison]] (600 root)
[connection] id=Morrison | type=802-11-wireless
[802-11-wireless] ssid=Morrison | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Morrison' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"Morrison"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000225290bb383
                    Extra: Last beacon: 168ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     EDDC8377FF3876C7E120E9C
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     867B4080247A86ABBA59D17
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: Y
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
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    9.863645] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.864086] rtlwifi: rtlwifi: wireless switch is on
[   17.775245] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.013780] r8169 0000:02:00.0 eth0: link down
[   18.013849] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.461749] wlan0: authenticate with <MAC 'Morrison' [AC1]>
[   19.471835] wlan0: send auth to <MAC 'Morrison' [AC1]> (try 1/3)
[   19.475985] wlan0: authenticated
[   19.476739] wlan0: associate with <MAC 'Morrison' [AC1]> (try 1/3)
[   19.493627] wlan0: RX AssocResp from <MAC 'Morrison' [AC1]> (capab=0xc11 status=0 aid=7)
[   19.493900] wlan0: associated
[   19.493920] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  163.995789] r8169 0000:02:00.0 eth0: link up
[  163.995892] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

```


Hope this'll help.

---

### Post by kc1di on 2016-04-19
Go to [this page]("http://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04") and follow the instruction given in the answer.  You'll need to be connected to the internet via hard wire to do it.  after that wireless should work. 
good luck

---

### Post by Timothy_Morrison on 2016-04-19
Followed it up to to **git clone **and got lost.. help please? It's been a while since I have used ubuntu, and forgot alot about it.

---

### Post by jeremy31 on 2016-04-19
Replace cd  /path/to/rtlwifi_new with
```
cd rtlwifi_new
```

Then you should be able to continue with the commands from the askubuntu answer

---

### Post by Timothy_Morrison on 2016-04-19
Alright, got to the last bit, but I keep getting an error saying 
```
 modprobe: ERROR: could not insert 'rtl8188ee': Invalid argument

```

---

### Post by jeremy31 on 2016-04-19
Try a reboot, if you still have that issue post ```
dmesg | grep rtl
```

---

### Post by Timothy_Morrison on 2016-04-19
Still nothing..

```

[   12.452858] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   12.480576] rtl8188ee 0000:01:00.0: enabling device (0000 -> 0003)
[   12.488291] rtl8188ee: Power Save off (module option)
[   12.488303] rtl8188ee: FW Power Save off (module option)
[   12.491176] Using firmware rtlwifi/rtl8188efw.bin
[   12.491367] rtlwifi: channel plan 0x20
[   12.491372] rtlwifi: country code 11
[   12.532679] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.533203] rtlwifi: wireless switch is on

```

---

### Post by jeremy31 on 2016-04-19
Post the results from the wireless script from [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)

The results will be in the wireless-info.txt file

---

### Post by Timothy_Morrison on 2016-04-19
here it is:

```


########## wireless info START ##########

Report from: 19 Apr 2016 17:12 EDT -0400

Booted last: 19 Apr 2016 16:52 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:8015]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 05c8:022a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0eef:c04d D-WAV Scientific Co., Ltd 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8188ee             135168  0 
rtl_pci                40960  1 rtl8188ee
rtlwifi                98304  2 rtl_pci,rtl8188ee
mac80211              741376  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              552960  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3282782 (3.2 MB)  TX bytes:426367 (426.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23372 (23.3 KB)  TX bytes:88325 (88.3 KB)

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
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       799     1  0 16:52 ?        00:00:01 NetworkManager

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
    Address:         192.168.0.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    PS4-CC2448A28E16:Infra, <MAC 'PS4-CC2448A28E16:Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Morrison:        Infra, <MAC 'Morrison' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2

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

[[/etc/NetworkManager/system-connections/Morrison]] (600 root)
[connection] id=Morrison | type=802-11-wireless
[802-11-wireless] ssid=Morrison | mac-address=<MAC 'wlan0' [IF]>
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

wlan0     Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     6C71D8C9AD168B6FF9B1EA9
depends:        rtlwifi,rtl_pci,mac80211
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8552A7BAFD0FCC2C41CF075
depends:        mac80211,rtlwifi
vermagic:       4.2.0-35-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     990116D31097F1C4C1F7006
depends:        mac80211,cfg80211
vermagic:       4.2.0-35-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 1
disable_watchdog: N
fwlps: N
ips: N
msi: Y
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
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  520.364930] wlan0: authenticated
[  520.368401] wlan0: associate with <MAC 'Morrison' [AN2]> (try 1/3)
[  520.388751] wlan0: RX AssocResp from <MAC 'Morrison' [AN2]> (capab=0xc11 status=0 aid=7)
[  520.389056] wlan0: associated
[  523.637092] wlan0: deauthenticated from <MAC 'Morrison' [AN2]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  529.894255] wlan0: authenticate with <MAC 'Morrison' [AN2]>
[  529.913636] wlan0: send auth to <MAC 'Morrison' [AN2]> (try 1/3)
[  529.917435] wlan0: authenticated
[  529.921299] wlan0: associate with <MAC 'Morrison' [AN2]> (try 1/3)
[  529.936788] wlan0: RX AssocResp from <MAC 'Morrison' [AN2]> (capab=0xc11 status=0 aid=7)
[  529.937068] wlan0: associated
[  533.598971] wlan0: deauthenticated from <MAC 'Morrison' [AN2]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  546.903275] wlan0: authenticate with <MAC 'Morrison' [AN2]>
[  546.922920] wlan0: send auth to <MAC 'Morrison' [AN2]> (try 1/3)
[  546.927029] wlan0: authenticated
[  546.930685] wlan0: associate with <MAC 'Morrison' [AN2]> (try 1/3)
[  546.948000] wlan0: RX AssocResp from <MAC 'Morrison' [AN2]> (capab=0xc11 status=0 aid=7)
[  546.948283] wlan0: associated
[  550.248687] wlan0: deauthenticated from <MAC 'Morrison' [AN2]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  556.219580] r8169 0000:02:00.0 eth0: link down
[  557.763130] r8169 0000:02:00.0 eth0: link up
[  570.053187] wlan0: authenticate with <MAC 'Morrison' [AN2]>
[  570.072739] wlan0: send auth to <MAC 'Morrison' [AN2]> (try 1/3)
[  570.076965] wlan0: authenticated
[  570.080307] wlan0: associate with <MAC 'Morrison' [AN2]> (try 1/3)
[  570.099953] wlan0: RX AssocResp from <MAC 'Morrison' [AN2]> (capab=0xc11 status=0 aid=7)
[  570.100292] wlan0: associated
[  573.374016] wlan0: deauthenticated from <MAC 'Morrison' [AN2]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-04-19
Here is chili555's standard advise

If your router is capable of N speeds, I have better luck with a channel width
of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also
have better luck with a fixed channel, either 1, 6 or 11, rather than
 automatic channel selection. After making these changes, reboot the
 router.


Next, I recommend that your regulatory domain be set explicitly. Check yours:  


    sudo iw reg get 


If you get 00, that is a one-size-maybe-fits-all setting. Find yours [here]([http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)) 
Then set it temporarily:  


    sudo iw reg set IS  


Of course, substitute your country code if not Iceland. Set it permanently:  


    gksudo gedit /etc/default/crda


Use nano or kate or vim if you don't have the text editor gedit.


Change the last line to read:  


    REGDOMAIN=IS


Proofread carefully, save and close the text editor.


Next, I'd set IPv6 to Ignore in Network Manager

Are you manually loading rtl8188ee with fwlps parameter options?

---

### Post by Timothy_Morrison on 2016-04-19
Nothing..

---

### Post by jeremy31 on 2016-04-19
Have you tried to connect with the ethernet disconnected?  With just wifi what is the result of ```
ping -c3 8.8.8.8
```

---

### Post by Timothy_Morrison on 2016-04-19
Yes, Ive tried the normal wifi way. 

result: 

```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2000ms

```

---

### Post by jeremy31 on 2016-04-19
Run the script with just the wifi connection ```
./wireless-info
```

Then use ethernet to post the result

---

