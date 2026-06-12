---
title: "ASUS PCE-N53 wifi card with Ubuntu 14.04"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by wendallsan on 2014-12-05
Hi all,

I am on my 3rd wifi card for my server after moving into a situation where wired network connections are not available.  I am currently trying to get an ASUS PCE-N53 card to work, and have been following instructions at [http://ubuntuforums.org/showthread.php?t=2217996&page=4](http://ubuntuforums.org/showthread.php?t=2217996&page=4).  I have updated my server's kernel to 3.15.5-031505-generic per the instructions in that forum thread.  I downloaded the drivers from the ASUS site and then patched it with the patch discussed in that forum thread.  After the patch, I was able to compile the drivers with make && make install, which is further along than I have been able to get with the other 2 wifi cards that I have purchased.  After rebooting, I can see the wifi card in my network manager and even see nearby wifi networks, but any attempt to any network results in the error:

Connection Failure: Failed to add/activate connection
(32) Saving connection failed: (-1) (unknown)

This is the same error I was getting on one of the previous 2 wifi cards that I had tried with a different RAlink chip on it.  I was assured that this ASUS card would work with Linux, so I am hopeful that there is still something I can do to get this working.  What can I do to troubleshoot this and hopefully get my server on the wireless network?  I can't afford to buy any more wifi cards and we need to get this server into production.

---

### Post by wendallsan on 2014-12-05
update: realized that I had installed kernel 3.15.5 while the patch I was using was for 3.15.8.  Tried to install 3.15.8, but the bios got corrupted and the PC blackscreened on me, no POST or anything.  Had to reset the BIOS by removing the battery on the motherboard to get it back up and was not able to get 3.15.8 working at all.  So I am looking for any solution for any kernel that I can get running, but 3.15.8 is not on that list for me.  Still hoping someone can help explain the connection failure message I'm getting as the network card appears to be working well enough to at least see available wifi networks.

---

### Post by jeremy31 on 2014-12-05
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Please follow the instructions on how to run the wireless-script and post the results

---

### Post by wendallsan on 2014-12-05
Thanks, here is the output you have requested:


########## wireless info START ##########

Report from: 05 Dec 2014 16:34 PST -0800

Booted last: 31 Dec 2009 16:50 PST -0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.15.5-031505-generic #201407091543 SMP Wed Jul 9 19:44:36 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
	Subsystem: ASUSTeK Computer Inc. Device [1043:851a]
	Kernel driver in use: rt2860

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              514187  0 
ndiswrapper           283985  0 
rt5592sta            1168223  1 
wmi                    19379  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe3c:c705/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:828561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1466239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83004725 (83.0 MB)  TX bytes:2007490131 (2.0 GB)

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF]>  
          inet6 addr: fe80::12c3:7bff:fec8:a5ec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47416 (47.4 KB)  TX bytes:0 (0.0 B)
          Interrupt:16 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.wa.comcast.net

##### nm-tool ###########################

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
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'ra0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Zombiepocalypse: Infra, <MAC 'Zombiepocalypse' [AC1]>, Freq 2452 MHz, Rate 0 Mb/s, Strength 44 WEP

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
managed=true

##### NetworkManager profiles ###########

Acquisition of admin privileges failed.

##### iw reg get ########################

Region: America/Vancouver (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

ra0       11 channels in total; available frequencies :
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

Channel occupancy:

      1   APs on   Frequency:2.452 GHz (Channel 9)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: <MAC 'Zombiepocalypse' [AC1]>
                    Protocol:802.11b/g
                    ESSID:"Zombiepocalypse"
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality=55/100  Signal level=-68 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.15.5-031505-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BDA7AFAD5D9F6CD8ED8A92E
depends:        
intree:         Y
vermagic:       3.15.5-031505-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        28:B6:A0:AF:35:27:C6:15:A9:F5:FF:31:BC:74:44:A7:58:18:9E:34
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.15.5-031505-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.15.5-031505-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

[rt5592sta]
filename:       /lib/modules/3.15.5-031505-generic/kernel/drivers/net/wireless/rt5592sta.ko
version:        2.6.0.0_20120326
srcversion:     150B71061DC1EBE4DE31E22
depends:        
vermagic:       3.15.5-031505-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

##### module parameters #################

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

loop
lp
rtc
ndiswrapper

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
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x1814:0x3060 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

########## wireless info END ############

---

### Post by jeremy31 on 2014-12-05
Ok, I don't know anything about how to get a Ralink card working, but Linux wifi usually prefers WPA2 AES encryption where you have WEP

What were the other wifi cards you tried?

---

### Post by wendallsan on 2014-12-08
Hi, I have tried disabling my wifi security and this has not affected the error messages I receive when trying to connect, so I don't think that the wireless security protocol is the issue.  I have attached another script output, this time with the network cable disconnected and the wireless router set up with no security, in case that is helpful.  The script output does not have much for the wifi connection, as I cannot actually connect to it.

The other two wifi adapters I have are an Netgear N300 USB adapter and a Manhattan 525473 PCI card, which runs on the Ralink 3060F chipset.  I would be thrilled to get any of these 3 adapters to work, but in my testing with each, I get the same error message reported above for the ASUS card I have been trying to get to work.  Thanks again for any further help or ideas.

---

