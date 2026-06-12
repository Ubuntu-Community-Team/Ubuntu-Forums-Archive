---
title: "Using ndiswrapper in Ubuntu 14.04, broken after reboot. Module Verification Failed?"
date: 2015-08-31
forum: Networking &amp; Wireless
---

### Post by jinjo2 on 2015-08-31
EDIT: It turns out I never had ndiswrapper working correctly in he first place, so the title is not accurate. Ended up updating my firmware for iwlwifi and that seems to have solved most of my problems.

Hi, I'm using ndiswrapper to run a Windows driver for my wireless card. I had it working (Installed from the Software Center, and ran using the GUI) and I could connect to wireless networks using the Windows driver; however, after the first reboot, I'm not even able to see any wireless networks anymore.

EDIT: It looks like loadndisdriver isn't able to load my Windows driver. I'm confused since it was working at least once before. Why was it working before the reboot if it's not working now? It's giving a lot of "Unknown Symbol" errors now.


I've I updated my system and produced the wireless info log below:


```

########## wireless info START ##########

Report from: 31 Aug 2015 21:42 EDT -0400

Booted last: 31 Aug 2015 21:31 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]

0d:00.0 System peripheral [0880]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 08)

##### lsusb #############################

Bus 002 Device 003: ID 17ef:1003 Lenovo Integrated Smart Card Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              484040  0 
ndiswrapper           283985  0 
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1057639 (1.0 MB)  TX bytes:71567 (71.5 KB)
          Interrupt:20 Memory:f2500000-f2520000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       865     1  0 21:31 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.116
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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=UCF_WPA2 | type=802-11-wireless
[802-11-wireless] ssid=UCF_WPA2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto
[802-1x] ca-cert=/home/czehr/Documents/Windows Wireless Driver Files/addtrustexternalcaroot.crt

[[/etc/NetworkManager/system-connections/Apollinaire]] (600 root)
[connection] id=Apollinaire | type=802-11-wireless
[802-11-wireless] ssid=Apollinaire | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-A4D2]] (600 root)
[connection] id=HOME-A4D2 | type=802-11-wireless
[802-11-wireless] ssid=HOME-A4D2 | mac-address=<MAC address>
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.0-62-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[ndiswrapper]
debug: 0
hangcheck_interval: 0
if_name: wlan%d
proc_gid: 0
proc_uid: 0
utils_version: 1.9

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
alias pci:v00008086d00000083sv00001205sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001206sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001225sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001226sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001305sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001306sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001325sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv00001326sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000083sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00000084sv00001215sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000084sv00001216sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000084sv00001315sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000084sv00001316sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000084sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00000087sv00001301sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000087sv00001306sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000087sv00001321sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000087sv00001326sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000087sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00000089sv00001311sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000089sv00001316sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00000089sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Bsv00001101sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Bsv00001121sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Csv00001301sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Csv00001306sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Csv00001307sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Csv00001321sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Csv00001326sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d0000422Csv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001201sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001204sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001205sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001206sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001221sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001224sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001225sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001226sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001301sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001304sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001305sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001306sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001321sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001324sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001325sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv00001326sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004232sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001001sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001004sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001021sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001024sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001101sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001104sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001121sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv00001124sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004235sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004236sv00001011sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004236sv00001014sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004236sv00001111sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004236sv00001114sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004236sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001211sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001214sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001215sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001216sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001311sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001314sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001315sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv00001316sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004237sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004238sv00001111sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004238sv*sd*bc*sc*i* ndiswrapper
alias pci:v00008086d00004239sv00001311sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004239sv00001316sd00008086bc*sc*i* ndiswrapper
alias pci:v00008086d00004239sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  299.327690] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  299.339356] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  299.339362] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  299.339368] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  299.339371] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  299.339374] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  299.339376] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  299.339379] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  299.339382] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  299.339384] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  299.339392] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[  299.339395] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  299.339398] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  299.339403] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  299.339405] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  299.339408] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  299.339411] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  299.339414] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  299.339416] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  299.339429] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  299.339432] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  299.339435] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  299.339437] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  299.339440] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  299.339443] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  299.339446] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  299.339449] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[  299.339451] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  299.339454] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[  299.339457] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  299.339459] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  299.339462] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  299.339465] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  299.339468] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  299.339470] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  299.339473] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  299.339476] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  299.339479] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netw5s64'
[  299.340255] ndiswrapper (load_wrap_driver:103): couldn't load driver netw5s64; check system log for messages from 'loadndisdriver'

########## wireless info END ############



```

---

### Post by chili555 on 2015-09-01
Where do I even start??

You are using ndiswrapper for your Intel wireless? What was not working about the built-in iwlwifi?

My Intel wireless, from which I am replying to this post, works perfectly.

The tainted kernel warning is trivial and harmless. It may safely be ignored.

---

### Post by jinjo2 on 2015-09-01
My school's wireless WPA2 network wasn't allowing me to connect using Linux drivers regardless of the security settings I chose through the network manager. Ndiswrapper seemed to be working fine, but my solution didn't survive a reboot, so I'm hoping I can get it working again without too much trouble.

I thought the module verification may have caused the unknown symbol errors from loadndisdriver. It seems to me that some sort of header file is not in the right spot anymore. Is it possible that there is just a file that needs to be moved somewhere?

EDIT: Or is it possible to run loadndisdriver manually after boot?

---

### Post by chili555 on 2015-09-01
Normally, all these errors imply that you used the wrong .inf and .sys files; that is, for Windows 7 or 8 or 10 or some such. ndiswrapper prefers XP:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install Windows XP drivers and kernel
       module to load the Windows XP drivers. Both are called ndiswrapper.I have heard reports that Windows 7 drivers can work but I've seen no confirming SOLVED thread so far. What drivers did you use?

I'd really rather coax iwlwifi to life. As a matter of fact, here is a post about your exact same device: [http://ubuntuforums.org/showthread.php?t=2292752](http://ubuntuforums.org/showthread.php?t=2292752)

I suggest installing the latest firmware as outlined there, set your crda, setting 11n_disable=8, setting IPv6 to Ignore and reboot. Then load iwlwifi:```
sudo modprobe iwlwifi
```Then try to connect. You shouldn't need to enter any encryption details. Select the network, supply the WPA2 key and connect.

If you need additional guidance for any of these steps, I'll be pleased to help.

---

### Post by jinjo2 on 2015-09-01
I am using netw5s64, I'm fairly certain it was for Windows XP, but I wouldn't be surprised if I actually downloaded Windows 7 drivers. Since it was working for a day (before I rebooted), is it safe to assume I was using the XP driver?

Thank you,

```

sudo modprobe iwlwifi

```

Got my wireless up and running again here at home; however, my main goal is to get my wireless running on campus. Do you think that installing the latest firmware (as well as the other instructions you just gave me) could possibly fix that issue with iwlwifi? 


On reboot, loadndisdriver still failed with all of the unknown symbol errors, and I had to run the "modprobe iwlwifi" command again to get my wireless network to appear. 


...
...


Ok, so I uninstalled netw5s64 using ndisgtk and rebooted. No errors. Ran "modprobe iwlwifi" and got my wireless connection going. (How do I get that to happen automatically again??) Once the connection was established, I re-installed netw5s64 using ndisgtk, and it looks like its working again, although I bet if I reboot it's going to fall apart again. (Yep, breaks on reboot)


NOTE: I apparently need to run
```

sudo modprobe iwlwifi

```
before I install netw5s64 using ndisgtk, or else it doesn't work.



I won't know for sure if this works until I can test it again on campus tomorrow, but this might be a work around that solves my problem. Just uninstall netw5s64>reboot>"modprobe iwlwifi">reinstalling the windows driver every time I need to use the campus wifi. 

Any ideas on whats going on here?

---

### Post by chili555 on 2015-09-01
> is it safe to assume I was using the XP driver?I never assume anything. You can sometimes read the file and tell:```
cd /etc/ndiswrapper/netw5s64
cat netw5s64.inf 
```You may need to scroll back and forth in the terminal to see if there is a reference to 7 or XP or whatever.>  Do you think that installing the latest firmware (as well as the other instructions you just gave me) could possibly fix that issue with iwlwifi? I do, but the only way to know is to try it, without ndiswrapper, of course.> Just uninstall netw5s64>reboot>"modprobe iwlwifi">reinstalling the windows driver every time I need to use the campus wifi. 

Any ideas on whats going on here?Not a single clue! It shouldn't work like that at all! I'm actually shocked.

I suggest you try the steps I outlined in the other thread and then see if you connect at work with iwlwifi alone. If not, you can always use the process you used (and that I would bet the house payment would *never* work!) to get going again. Then report back and we'll tweak as needed.

---

### Post by jinjo2 on 2015-09-01
> **chili555 said:**
> It shouldn't work like that at all! I'm actually shocked.
If not, you can always use the process you used (and that I would bet the house payment would *never* work!) to get going again. Then report back and we'll tweak as needed.

Then I'm likely misunderstanding what's actually going on here! Let me poke around a bit.

... Ah, yep.

I saw that the windows driver was installed, but that doesn't mean that it was being used to connect to the wireless. *sigh*

```

*-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:eb:b7:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi

```

Yep, currently using iwlwifi driver after installing the windows driver with ndisgtk. Ok, this might mean that I wasn't using netw5s64 on campus the other day either?   ... but it may mean that iwlwifi was working on campus.... this is making more and less sense to me as I go.. lol


```

cat netw5s64.inf | grep -C 20 version

```

returns:
```

;*****************************************
; NETw5s64.INF
;
; Intel Wireless WiFi Link Adapters
; Installation Script for Windows7 64 bit
;
; Copyright (c) 2009 Intel, Inc. All Rights Reserved
;
;------------------------------------------------------------------------------

;******************************************************************************
; Version Section
;------------------------------------------------------------------------------
[version]
Signature   = "$Windows NT$"
Compatible  = 1
Class       = net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %PROVIDER_NAME%
DriverVer   = 09/15/2009,13.0.0.107 ;DATE HAS TO BE IN FOLLOWING FORMAT MM/DD/YYYY

```

While if I grep for "XP" I just get a few DispName strings for different chips. Looks like a Windows 7 Driver to me.

Ok, so it looking like I never had ndiswrapper working properly in the first place. I'm going to work on installing the latest firmware and then try connecting again on campus tomorrow. 

Thanks for all your help so far!

---

### Post by chili555 on 2015-09-01
> [version]
Signature   = "$Windows NT$"NT drivers are generally workable. NT was roughly contemporaneous with XP.

I'll look forward to your report.

---

### Post by jinjo2 on 2015-09-01
> **chili555 said:**
> NT drivers are generally workable. NT was roughly contemporaneous with XP.


Well that's encouraging! It took me forever to find that .inf file!

I still have to load the iwlwifi module manualy after rebooting. Not sure what I did to stop that from loading automatically. I did add iwlwifi to the blacklist temporarilly in /etc/modprobe.d/blacklist.conf but I removed it after it clearly didn't solve my problem with ndiswrapper.

I've now installed the latest firmware (the correct files show up when we grep for "6000"), set my IPv6 settings to Ignore, but I'm not sure how to set my crda. Below is the same information you asked for in the previous thread. (Commands were run after installing latest firmware)

rfkill list all
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```



dmesg | grep -e wlan -e iwl
```

[   49.065344] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   49.065474] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   49.143305] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   49.143311] iwlwifi 0000:03:00.0: Falling back to user helper
[   49.143814] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   49.143817] iwlwifi 0000:03:00.0: Falling back to user helper
[   49.172256] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   49.241119] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   49.241122] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   49.241124] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   49.241125] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   49.241221] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   49.286399] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   49.290749] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   49.290971] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   49.508629] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   49.508837] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   49.636703] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.637015] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.141103] wlan0: authenticate with 48:f8:b3:81:6c:4f
[   56.147346] wlan0: send auth to 48:f8:b3:81:6c:4f (try 1/3)
[   56.169095] wlan0: authenticated
[   56.172032] wlan0: associate with 48:f8:b3:81:6c:4f (try 1/3)
[   56.195742] wlan0: RX AssocResp from 48:f8:b3:81:6c:4f (capab=0x411 status=0 aid=1)
[   56.201837] wlan0: associated
[   56.201910] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.838566] wlan0: deauthenticating from 48:f8:b3:81:6c:4f by local choice (reason=2)
[   56.840625] wlan0: authenticate with 48:f8:b3:81:6c:4f
[   56.845264] wlan0: send auth to 48:f8:b3:81:6c:4f (try 1/3)
[   56.872760] wlan0: authenticated
[   56.876166] wlan0: associate with 48:f8:b3:81:6c:4f (try 1/3)
[   56.900571] wlan0: RX AssocResp from 48:f8:b3:81:6c:4f (capab=0x411 status=0 aid=1)
[   56.905158] wlan0: associated

```

iwconfig
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Apollinaire"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 48:F8:B3:81:6C:4F   
          Bit Rate=144.4 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:79   Missed beacon:0

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:21:cc:6c:0f:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37882 (37.8 KB)  TX bytes:37882 (37.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d7:eb:b7:ec  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d7ff:feeb:b7ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:426050 (426.0 KB)  TX bytes:208263 (208.2 KB)

```

---

### Post by chili555 on 2015-09-02
In spite of the presence of the -5 and -6 firmware, it appears that the version of the driver in 14.04 only uses -4:> loaded firmware version 9.221.[COLOR="#FF0000"]4[/COLOR].1May I assume the owner and permissions are correct?```
ls -al /lib/firmware | grep 6000
```You should see:```
-rw-r--r--  1 root root  454608 Nov 24  2014 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 Nov 24  2014 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  677296 Nov 24  2014 iwlwifi-6000g2a-6.ucode
-rw-r--r--  1 root root  679436 Nov 24  2014 iwlwifi-6000g2b-6.ucode

```This means readable by all and writable by root. We may consider updating the driver or, perhaps the entire kernel, if you can't connect at the office.

Here is how to set your CRDA. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor. 

If iwlwifi is no longer blacklisted, I suspect, in order to get it to load automatically, we'll need to look at ndiswrapper's settings. I'm confident it associates itself, not iwlwifi, with the pci.id; in your case, 8086:4238.

I suggest we be sure we have iwlwifi working well before we purge ndiswrapper.

---

### Post by jinjo2 on 2015-09-02
> **chili555 said:**
> May I assume the owner and permissions are correct?


As far as I know, yes.

> **chili555 said:**
> 
```
gksudo gedit /etc/default/crda
```

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor. 


I don't have gksudo installed, from what I can tell it's good for handling graphical applications? I updated my REGDOMAIN to "US" with sudo.


> **chili555 said:**
> 
If iwlwifi is no longer blacklisted, I suspect, in order to get it to load automatically, we'll need to look at ndiswrapper's settings. I'm confident it associates itself, not iwlwifi, with the pci.id; in your case, 8086:4238.

I suggest we be sure we have iwlwifi working well before we purge ndiswrapper.

I'm currently posting this from campus, so iwlwifi is working! Since I was able to connect a few days ago as well, I think that my problem after rebooting was entirely caused by my poor use of ndiswrapper. I've uninstalled ndiswrapper (although I kept the netw5s64 driver files just in case), rebooted, and I can connect to the campus' WPA2 network with the command:

```

sudo modprobe iwlwifi

```

So now the only thing left to do is associate iwlwifi with my card right? Thanks again for all the help you've given me! I would not have realized my mistake without your input. I was afraid I was going to have to install Windows on my laptop!

---

### Post by chili555 on 2015-09-02
First, let's have a look at the usual location of configuration files to see what we can find and, ideally, eliminate:```
ls /etc/modprobe.d
```Also:```
tail -n5 /etc/modprobe.d/blacklist.conf
```Just to be on the extreme side, let's also ask iwlwifi to load automatically:```
sudo -i
echo iwlwifi  >>  /etc/modules
exit
```> I'm currently posting this from campus, so iwlwifi is working!Totally awesome!!

---

### Post by jinjo2 on 2015-09-02
Contents of /etc/modprobe, "ndiswrapper.conf" looks like a candidate for removal.

```

alsa-base.conf              blacklist-modem.conf         iwlwifi.conf
blacklist-ath_pci.conf      blacklist-oss.conf           mlx4.conf
blacklist.conf              blacklist-rare-network.conf  ndiswrapper.conf
blacklist.conf~             blacklist-watchdog.conf      vmwgfx-fbdev.conf
blacklist-firewire.conf     dkms.conf
blacklist-framebuffer.conf  fbdev-blacklist.conf

```

End of blacklist.conf:

```

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

I added wilwifi to the /etc/modules file.

---

### Post by chili555 on 2015-09-02
I suggest:```
sudo rm /etc/modprobe.d/ndiswrapper.conf
```Reboot and tell us if it's working.

---

### Post by jinjo2 on 2015-09-03
It's working here at home now, I'll still have to test it again on campus, but I'll be able to mark this as solved tomorrow when I get back on campus. Thanks!

---

### Post by jinjo2 on 2015-09-04
Yep, working here on campus now as well. Thanks so much chili! You've been a huge help.

---

### Post by chili555 on 2015-09-04
Awesome! Glad it's working.

---

