---
title: "Wireless RT8191SU chipset on Ubuntu 14.04 only works for the first 30 seconds"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by garrop on 2014-09-28
Hi there,

After years of Ubuntu usage and many many doubts clarified thanks to ubuntuforums, this is my first post ever. I do have an Edubuntu install for my kids with an EMTEC WIFI dongle that uses the RT8191SU chipset. When I start the machine the network works fine for about 30 seconds and then kind of freezes in terms of speed: it seems to loose connection, pings do not come back, but if I ping this machine from the network, the ping comes back ok. It seems that a tiny connection stays on, although it is worth for nothing in terms of connectivity.

The driver I seem to use is the .bin from the ubuntu kernell. I have tried all the alternatives read on this forum to no avail (including modifying the .bin file as suggested by chili555) Here is my wireless script:



```

########## wireless info START ##########

Report from: 28 Sep 2014 11:19 CEST +0200

Booted last: 28 Sep 2014 10:48 CEST +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset [11ab:1fa7] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device [1043:138f]

01:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01)

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              409394  0 
r8712u                158706  0 
mxm_wmi                12893  1 nouveau
wmi                    18673  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202973868 (202.9 MB)  TX bytes:4937726 (4.9 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe35:76cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1121 errors:0 dropped:535 overruns:0 frame:0
          TX packets:1119 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:449818 (449.8 KB)  TX bytes:243480 (243.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Exenpluenea"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Exenpluenea' [AC1]>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=89/100  Signal level=75/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Exenpluenea] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
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
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AN1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 76 WPA2 Enterprise
    NEUF_CA54:       Infra, <MAC 'NEUF_CA54' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AN4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 76
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    *Exenpluenea:    Infra, <MAC 'Exenpluenea' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 89 WPA

  IPv4 Settings:
    Address:         192.168.1.20
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

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

[[/etc/NetworkManager/system-connections/Exenpluenea]] (600 root)
[connection] id=Exenpluenea | type=802-11-wireless
[802-11-wireless] ssid=Exenpluenea | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency=2.417 GHz (Channel 2)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Exenpluenea' [AC1]>
                    ESSID:"Exenpluenea"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8712u]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

##### /etc/modules ######################

lp

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
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   18.562321] sky2 0000:02:00.0 eth1: enabling interface
[   18.562409] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   18.787757] usb 3-2: r8712u: CustomerID = 0x0000
[   18.787765] usb 3-2: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[   18.787770] usb 3-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   19.051965] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  408.287040] r8712u: Staging version
[  408.287079] r8712u: register rtl8712_netdev_ops to netdev_ops
[  408.287090] usb 3-1: r8712u: USB_SPEED_LOW with 4 endpoints
[  408.289949] usb 3-1: r8712u: Boot from EFUSE: Autoload OK
[  411.140378] usb 3-1: r8712u: CustomerID = 0x0000
[  411.140386] usb 3-1: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[  411.140391] usb 3-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  412.066840] r8712u 3-1:1.0 wlan0: 1 RCR=0x153f00e
[  412.069837] r8712u 3-1:1.0 wlan0: 2 RCR=0x553f00e
[  412.192959] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  423.180575] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  546.918331] r8712u: Staging version
[  546.918368] r8712u: register rtl8712_netdev_ops to netdev_ops
[  546.918378] usb 3-1: r8712u: USB_SPEED_LOW with 4 endpoints
[  546.921249] usb 3-1: r8712u: Boot from EFUSE: Autoload OK
[  549.770674] usb 3-1: r8712u: CustomerID = 0x0000
[  549.770682] usb 3-1: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[  549.770686] usb 3-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  550.678129] r8712u 3-1:1.0 wlan0: 1 RCR=0x153f00e
[  550.681130] r8712u 3-1:1.0 wlan0: 2 RCR=0x553f00e
[  550.805248] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  591.715753] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  612.997308] r8712u 3-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC 'Exenpluenea' [AC1]>, seq = 0, tid = 0

########## wireless info END ############


```


The motherboard does have an integrated WIFI hardware (88W8310 and 88W8000G) that I have never managed to make work. At the time, the EMTEC dongle would work fine with Ubuntu 10.04, and that is what I have continued to do so far. I can guess there is a driver conflict between the on-board chipset and the dongle one.Thus I have:

Disabled the WIFI chipset from the motherboard: no sucess

Blacklisted the sky2 module: the system crashes, as it seems such module controls much more stuff

Read this forum and try different solutions (including modified settings on my router): no luck there either

More info:

```

dmesg | tail

[ 3687.418207] usb 3-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 3687.421053] usb 3-2: r8712u: Boot from EFUSE: Autoload OK
[ 3690.278050] usb 3-2: r8712u: CustomerID = 0x0000
[ 3690.278058] usb 3-2: r8712u: MAC Address from efuse = 80:1f:02:35:76:cd
[ 3690.278062] usb 3-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3691.186052] r8712u 3-2:1.0 wlan0: 1 RCR=0x153f00e
[ 3691.189052] r8712u 3-2:1.0 wlan0: 2 RCR=0x553f00e
[ 3691.313107] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3691.313990] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3691.621102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3732.555194] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


```


Any help or hints on how to solve this problem will be extremely appreciatedd by myself and my kids :-)

Thanks in advance;

---

### Post by varunendra on 2014-09-29
Welcome to the forums garrop!

The r8712u is a staging driver, kinda experimental and we don't expect much from such drivers.

That being said, have you tried changing the encryption in your router to WPA2-PSK with AES (CCMP)? Please do so now, as the current mode, WPA with TKIP is an old, outdated and inefficient encryption type. WPA+AES should be faster.

Also, it usually helps to 'fix' the channel on the router. By default it may be set to 'Auto'. Channels 1 or 11 are most recommended ones, but you don't seem to have any neighbouring signal interference problem, so any channel should be okay. Reboot the router after saving the changes, and let us know if it helps.

---

### Post by garrop on 2014-09-29
Hi there and thanks for the tips.

I went on and modified both things as suggested to no avail. 

I guess the only road from no on is to get a new decent dongle, isn't it?

Kind regards.

---

### Post by varunendra on 2014-09-29
Can we see a fresh wireless_script report before dumping it? Currently I'm already too tired to make blind guesses, but I wonder why 'cfg80211' got loaded in your first report? It is not a dependency of 'r8712u', nor do we have traces of any other driver requiring it.

Maybe a fresh report and a fresh mind tomorrow could lead us to a solution. The r8712u is a staging driver, yes, but is out for quite sometimes now, so is worth trying a few things with it before going for something new.

---

### Post by garrop on 2014-09-29
Voila:


```

########## wireless info START ##########

Report from: 29 Sep 2014 19:55 CEST +0200

Booted last: 01 Jan 2002 01:01 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset [11ab:1fa7] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device [1043:138f]

01:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01)

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 003 Device 004: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              409394  0 
mxm_wmi                12893  1 nouveau
wmi                    18673  2 mxm_wmi,nouveau
r8712u                158706  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3780 (3.7 KB)  TX bytes:538800 (538.8 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe35:76cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:4 overruns:0 frame:0
          TX packets:71 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5888 (5.8 KB)  TX bytes:12228 (12.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Exenpluenea"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Exenpluenea' [AC1]>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=83/100  Signal level=63/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Exenpluenea] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
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
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA2 Enterprise
    NEUF_CA54:       Infra, <MAC 'NEUF_CA54' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46 WPA2 Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46
    *Exenpluenea:    Infra, <MAC 'Exenpluenea' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 83 WPA2

  IPv4 Settings:
    Address:         192.168.1.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

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

[[/etc/NetworkManager/system-connections/Exenpluenea]] (600 root)
[connection] id=Exenpluenea | type=802-11-wireless
[802-11-wireless] ssid=Exenpluenea | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      6   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Exenpluenea' [AC1]>
                    ESSID:"Exenpluenea"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'FreeWifi_secure' [AC2]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    Signal level=59/100  
          Cell 03 - Address: <MAC 'FreeWifi' [AC3]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Signal level=59/100  
          Cell 04 - Address: <MAC 'NEUF_CA54' [AC4]>
                    ESSID:"NEUF_CA54"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 05 - Address: <MAC 'SFR WiFi FON' [AC5]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=45/100  
          Cell 06 - Address: <MAC 'SFR WiFi Mobile' [AC6]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                            lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

  12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=46/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8712u]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

##### /etc/modules ######################

lp

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
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   19.783072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  105.282878] r8712u 3-2:1.0 wlan0: 1 RCR=0x153f00e
[  105.285873] r8712u 3-2:1.0 wlan0: 2 RCR=0x553f00e
[  105.408921] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  115.972052] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  145.505048] r8712u 3-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC 'Exenpluenea' [AC1]>, seq = 0, tid = 0
[ 7663.418146] r8712u: Staging version
[ 7663.418184] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 7663.418194] usb 3-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 7663.421054] usb 3-2: r8712u: Boot from EFUSE: Autoload OK
[ 7666.278061] usb 3-2: r8712u: CustomerID = 0x0000
[ 7666.278070] usb 3-2: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[ 7666.278075] usb 3-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 7666.328483] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7717.042068] r8712u 3-2:1.0 wlan0: 1 RCR=0x153f00e
[ 7717.045068] r8712u 3-2:1.0 wlan0: 2 RCR=0x553f00e
[ 7717.169129] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7727.910258] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

1k thanks

---

### Post by varunendra on 2014-10-01
Does it help or make matters worse if we forcibly prevent the cfg80211 driver from loading? Although I'm really curious why it is loading in the first place.

To prevent it from loading, try blacklisting it -
```
echo "blacklist cfg80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check -
```
lsmod | grep cfg80211
```
Does it show up in the output? If not, is the connection any better?

---

### Post by garrop on 2014-10-01
Hi there,

I have blacklisted "blacklist cfg80211" as suggested.

lsmod | grep cfg80211 did not return any results (so well blacklisted as well)

My script provides the following result:

```

########## wireless info START ##########

Report from: 01 Oct 2014 16:51 CEST +0200

Booted last: 01 Oct 2014 16:47 CEST +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset [11ab:1fa7] (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device [1043:138f]

01:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01)

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2

03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 15)
    Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus) [1043:8142]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 003 Device 002: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

r8712u                158706  0 
mxm_wmi                12893  1 nouveau
wmi                    18673  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::211:d8ff:fe3a:2f9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180 (180.0 B)  TX bytes:35157 (35.1 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe35:76cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:10 overruns:0 frame:0
          TX packets:208 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17854 (17.8 KB)  TX bytes:31053 (31.0 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Exenpluenea"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Exenpluenea' [AC1]>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=76/100  Signal level=59/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Exenpluenea] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
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
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    NEUF_CA54:       Infra, <MAC 'NEUF_CA54' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 46 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    *Exenpluenea:    Infra, <MAC 'Exenpluenea' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 76 WPA2

  IPv4 Settings:
    Address:         192.168.1.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

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

[[/etc/NetworkManager/system-connections/Exenpluenea]] (600 root)
[connection] id=Exenpluenea | type=802-11-wireless
[802-11-wireless] ssid=Exenpluenea | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Exenpluenea' [AC1]>
                    ESSID:"Exenpluenea"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'NEUF_CA54' [AC2]>
                    ESSID:"NEUF_CA54"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 03 - Address: <MAC 'SFR WiFi FON' [AC3]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=46/100  
          Cell 04 - Address: <MAC 'SFR WiFi Mobile' [AC4]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=44/100  
          Cell 05 - Address: <MAC 'FreeWifi' [AC5]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Signal level=56/100  
          Cell 06 - Address: <MAC 'FreeWifi_secure' [AC6]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMPlo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

 TKIP
                        Authentication Suites (1) : 802.1x
                    Signal level=58/100  

##### module infos ######################

[r8712u]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-36-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        FF:9A:DA:11:B8:55:51:6A:72:98:65:9D:4E:3F:BB:76:C5:4A:D3:30
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

##### module parameters #################

[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0

##### /etc/modules ######################

lp

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
blacklist 
80211

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
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.549701] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   15.551412] r8712u: Staging version
[   15.551444] r8712u: register rtl8712_netdev_ops to netdev_ops
[   15.551450] usb 3-2: r8712u: USB_SPEED_LOW with 4 endpoints
[   15.553902] usb 3-2: r8712u: Boot from EFUSE: Autoload OK
[   19.398397] usb 3-2: r8712u: CustomerID = 0x0000
[   19.398409] usb 3-2: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[   19.398416] usb 3-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   19.572146] sky2 0000:02:00.0 eth1: enabling interface
[   19.572779] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[   20.489370] r8712u 3-2:1.0 wlan0: 1 RCR=0x153f00e
[   20.491896] r8712u 3-2:1.0 wlan0: 2 RCR=0x553f00e
[   20.620990] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   41.477140] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

However, when I try to open firefox, the computer completely freezes out (I can not even log into a terminal window F1, F2, etc) with the following message on the screen:

Kernel panic - not syncing: Gatal exception in interrupt

drm_kms_helper: panic occurred, switching back to text console

This is exactly the same behaviour I had when I blacklisted the sky2.

1M thanks for your help.

---

### Post by varunendra on 2014-10-01
kernel panic is a bad sign - indicator of something seriously out of order. It can be one of the drivers, but does it happen ONLY when opening the browser?

What if you try to use the net without opening the browser? For example, just ping other devices or an internet address now, or try to run an update (sudo apt-get update).

The 'drm_kms_helper' driver is graphics related, so it could be a graphics issue somehow related to the browser or any activity that uses memory heavily. Although I remember an old bug in some _network_ driver that used to trigger this.

Does the "Additional Drivers" program have some proprietary driver to offer for your graphics card?

---

### Post by garrop on 2014-10-02
Hi there,

After some heavy usage by my kids of the PC,the kernel panic has not reproduced, not even when I have opened Firefox, so it seems to really be unrelated. No additional drivers offered by the system, though.

Today, following your instructions, I did ping google right after I logged in and it worked fine. I went next with the sudo apt-get udate and did not reach the repositories. I re-pinged google and this time I did not worked at all. The whole thing did not last over 45 seconds. Go figure....

Any final hints? Thanks for your patiente and support.

---

### Post by varunendra on 2014-10-02
Nope, I'm out of ideas too. Perhaps it was better to use our times in searching for a better supported adapter instead of wasting it on this card. :(

---

### Post by garrop on 2014-10-03
Ok, thanks for your help so far.

Just as a side remark, the Wireless USB dongle is marketed by EMTEC, as part of a home media HD which clearly runs on Linux. It is quite disappointing to see companies free-riding on free software and puting such products on the market.

A local shop is specialized in Ubuntu PCs and laptops, so that is where I will get decent hardware for this particular need.

Like I said, thanks for the help along the route.

---

