---
title: "usb wireless adapter has stopped working"
date: 2016-10-29
forum: Networking &amp; Wireless
---

### Post by wsfield99 on 2016-10-29
Hi, I'm running Kubuntu 16.04.  Until recently my Raylink RT2870/RT3070 wireless usb adapter, was working fine.  Now it is recognized when I type lsusb, but it will no longer connect.  I have tested both the adapter and my usb ports and they are fine. Please let me know if you need any additional information.  Thanks in advance.  Scott  I dual boot my machine with windows 10 and have no trouble when I'm running under it.

---

### Post by wildmanne39 on 2016-10-29
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by bearlake on 2016-10-29
Hi,

Have you tried to reset the router yet and reboot the computer?

Sometimes it's the simple things that catch us.

---

### Post by wsfield99 on 2016-10-30
Here are the results:


```
########## wireless info START ##########

Report from: 30 Oct 2016 11:30 EDT -0400

Booted last: 30 Oct 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, recovery, nomodeset

##### desktop ###########################

/usr/share/xsessions/plasma

##### lspci #############################

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company MCP51 Ethernet Controller [103c:30b5]
    Kernel driver in use: forcedeth

01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              16384  1 rt2800lib
b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  4 b43,rt2x00lib,rt2x00usb,rt2800lib
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              565248  3 b43,mac80211,rt2x00lib
ssb_hcd                16384  0
mxm_wmi                16384  1 nouveau
ssb                    65536  2 b43,ssb_hcd
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s20   Link encap:Ethernet  HWaddr <MAC 'enp0s20' [IF1]>  
          inet addr:192.168.1.190  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::48ba:9cfa:9935:c2b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4403395 (4.4 MB)  TX bytes:360200 (360.2 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20   no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Managementoff
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp0s20
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s20

##### resolv.conf #######################

nameserver 127.0.1.1
search fios-router.home

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1020     1  0 11:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP51 Ethernet Controller
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s20' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/net/enp0s20
GENERAL.IP-IFACE:                       enp0s20
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     New 802-3-ethernet connection
GENERAL.CON-UUID:                       f4dd2ae0-846e-4717-8ca7-f85a817e854e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f4dd2ae0-846e-4717-8ca7-f85a817e854e | New 802-3-ethernet connection
IP4.ADDRESS[1]:                         192.168.1.190/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          fios-router.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.190
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1477927523
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = fios-router.home
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       domain_search = fios-router.home.
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       routers = 192.168.1.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::48ba:9cfa:9935:c2b2/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-5/1-5:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/New 802-11-wireless connection]] (600 root)
[connection] id=New 802-11-wireless connection | type=wifi | permissions=user:scott:;
[wifi] mac-address-blacklist= | ssid=Our Wifi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s20   no frequency information.

wlx<IF from MAC [IF2]>  14 channels in total; available frequencies :
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

##### iwlist scan #######################

wlx<IF from MAC [IF2]>  Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp0s20   Interface doesn't support scanning.

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[b43]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     B8F81D53A09CD1D43DDE810
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[ssb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

##### dmesg #############################

[   40.810882] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   40.840098] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   40.840120] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   40.950659] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   40.950932] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   40.950957] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   40.950959] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   40.950962] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   43.482571] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   43.514438] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[   43.789912] rt280

```
Thanks, Scott

---

### Post by chili555 on 2016-10-30
We wonder why you haven't activated the internal Broadcom. It ought to work better than the USB.

Second, please note:> 

0: hp-wifi: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

This usually suggests that the hardware switch is set to disable the wireless radio.

---

### Post by wsfield99 on 2016-10-30
My internal wireless card is old and is not compatible with the security settings on my router.  My usb wireless had been working fine but stopped suddenly.  Thanks, Scott

---

### Post by chili555 on 2016-10-30
> My internal wireless card is old and is not compatible with the security settings on my router.How can you know that without installing the required firmware and then testing?```
iw list
```I would be quite shocked if it didn't do WPA2-AES which is the latest and most secure.

And what about 'hard blocked:yes'? Do you believe that the wireless switch or airplane mode only applies to the internal device? This is not the usual behavior.

---

### Post by wsfield99 on 2016-10-30
Please let me know the commands to turn the internal wireless card back on.  Thanks, Scott

---

### Post by chili555 on 2016-10-30
> **wsfield99 said:**
> Please let me know the commands to turn the internal wireless card back on.  Thanks, ScottFirst, detach the USB. Next, get a working internet connection by ethernet, tethered or whatever means possible. Next, open a terminal and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Reboot.

Find the wireless switch or key combination and switch it to enable wireless. Check:```
rfkill list all
```Check the capabilities of the wireless:```
sudo iwlist auth
```I am confident that you will see, in part:```
Authentication capabilities :
		WPA
		[COLOR="#FF0000"]WPA2[/COLOR]
		CIPHER-TKIP
		[COLOR="#FF0000"]CIPHER-CCMP[/COLOR]


```If so, you are all set.

---

### Post by wsfield99 on 2016-10-31
Thanks, here are the results from running the script:

```
########## wireless info START ##########

Report from: 30 Oct 2016 11:30 EDT -0400

Booted last: 30 Oct 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, recovery, nomodeset

##### desktop ###########################

/usr/share/xsessions/plasma

##### lspci #############################

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company MCP51 Ethernet Controller [103c:30b5]
    Kernel driver in use: forcedeth

01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              16384  1 rt2800lib
b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  4 b43,rt2x00lib,rt2x00usb,rt2800lib
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              565248  3 b43,mac80211,rt2x00lib
ssb_hcd                16384  0
mxm_wmi                16384  1 nouveau
ssb                    65536  2 b43,ssb_hcd
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s20   Link encap:Ethernet  HWaddr <MAC 'enp0s20' [IF1]>  
          inet addr:192.168.1.190  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::48ba:9cfa:9935:c2b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4019 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4403395 (4.4 MB)  TX bytes:360200 (360.2 KB)

wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20   no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Managementoff
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp0s20
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s20

##### resolv.conf #######################

nameserver 127.0.1.1
search fios-router.home

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1020     1  0 11:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP51 Ethernet Controller
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s20' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/net/enp0s20
GENERAL.IP-IFACE:                       enp0s20
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     New 802-3-ethernet connection
GENERAL.CON-UUID:                       f4dd2ae0-846e-4717-8ca7-f85a817e854e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f4dd2ae0-846e-4717-8ca7-f85a817e854e | New 802-3-ethernet connection
IP4.ADDRESS[1]:                         192.168.1.190/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          fios-router.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.190
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1477927523
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = fios-router.home
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       domain_search = fios-router.home.
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       routers = 192.168.1.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::48ba:9cfa:9935:c2b2/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-5/1-5:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/New 802-11-wireless connection]] (600 root)
[connection] id=New 802-11-wireless connection | type=wifi | permissions=user:scott:;
[wifi] mac-address-blacklist= | ssid=Our Wifi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s20   no frequency information.

wlx<IF from MAC [IF2]>  14 channels in total; available frequencies :
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

##### iwlist scan #######################

wlx<IF from MAC [IF2]>  Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp0s20   Interface doesn't support scanning.

##### module infos ######################

[rt2800usb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/"), Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com/")
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[b43]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     B8F81D53A09CD1D43DDE810
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[ssb]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

##### module parameters #################

[rt2800usb]
nohwcrypt: N

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

##### dmesg #############################

[   40.810882] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   40.840098] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   40.840120] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   40.950659] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2 (repeated 2 times)
[   40.950932] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2 (repeated 2 times)
[   40.950957] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   40.950959] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   40.950962] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware") and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   43.482571] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   43.514438] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[   43.789912] rt280
```

---

### Post by chili555 on 2016-10-31
We see that the USB is not disconnected, the wireless switch is still set to disable wireless and the firmware has not been installed. Did you run into some trouble? Errors or warnings? Or ... ?

---

### Post by wsfield99 on 2016-10-31
Thanks.  I followed your instructions and obtained the correct results.  What do I need to do to connect to my network?  Thanks, Scott

---

### Post by chili555 on 2016-10-31
It appears that the firmware is not installed. Please check:```
sudo dpkg -s firmware-b43-installer
ls /lib/firmware/b43
```If the firmware is not installed, as we suspect, please retrace your steps.

---

### Post by wsfield99 on 2016-10-31
I've done this but still can't connect.  Thanks, Scott

---

### Post by wsfield99 on 2016-10-31
I've done this but still can't connect.  Thanks, Scott

---

### Post by chili555 on 2016-10-31
> **wsfield99 said:**
> I've done this but still can't connect.  Thanks, ScottThose were not commands designed to get your wireless working; they were commands to gather more information. Please run each one again and post the result.```
sudo dpkg -s firmware-b43-installer
ls /lib/firmware/b43
```I'm sorry if I was misunderstood.

---

### Post by wsfield99 on 2016-10-31
Thank you all for your help!!  Scott

---

