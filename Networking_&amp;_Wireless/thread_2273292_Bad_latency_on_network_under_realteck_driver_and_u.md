---
title: "Bad latency on network under realteck driver and ubuntu."
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by Frodobunny2 on 2015-04-12
Hello everyone. I have been lurking for awhile now, but I have hit a problem I cannot seem to deal with. A little help would be appreciated.

**Summary**

I am having some problems with insane latency on my ubuntu system, and although I have a few theories and a lot of data, I am not sure where to go from here. Basically, I am seeing insane latency on pings and corresponding degradation of network performance, particularly when downloading large amounts of information or streaming data. I also have a fairly complicated internal network which might be a factor. Also possibly significant: traffic is being routed through a network interface that I am not familiar with, and along ip addresses which I do not know.

**Brief System Overview**

I am running ubuntu 14.04 LTS on a 970A-G45 board.
I am connecting to the internet by wired connection and am running a propriatary driver from Radeon to allow GPU computing. 
I also tried to load a proprietary network driver after a search revealed that the default network driver might be having trouble, but I am not sure if it successfully loaded. 
The machine also has a windows partition on it.

**Detailed Problem Info**/ **Troubleshooting steps taken**

Using ping, I am seeing response times as high as a second going to  4.2.2.2, and when I boot the computer under windows (it is a duelboot), I  have a ping of around 32 ms. Notably, the ping time varies widely and  changes with each ping, while under the windows partition it is  constant. Large downloads and heavy traffic make the problem worse, and  netflix streaming often pushes ping replies up in the range of 1-2  seconds.

traceroute reveals that the issue really starts beyond the ipcop firewall installed on our network, which acts as the default gateway for the machine I am on. Pings on the local network are normal. Pings beyond the gateway are not. I inherited this network from my dad when he passed away, and though I can maintain it I am still learning about how tcp/ip networks works so I am not sure if it is a candidate for the problem or not. I do have full access to everything on the network through ssh and it has tcpdump available if it helps, but am inexperienced in using both.

Strangely, while investigating this I noticed I have some extra interfaces. I have been trying to setup a vpn and basically don't know what I am doing but was generating certificates on a local machine, and figured that the openvpn interface that gets installed might of been the problem. But after uninstalling openvpn, the interface is still there, and even more strange my ping are being routed along this interface and attached ip. It has an ip adress with no known correlation within my network. Eth1 is the weird one, my network is on 192.168.2.0. Feel free to check the info dump on it below. One note: it might be related to virtualbox (I have boinc running on this system), but it has been uninstalled with no resolution. It might just be part of how ubuntu works, I really don't know enough to say, so don't let me distract you. 

Also, I ruled out a hardware error already by booting into windows and pinging without any trouble. Whatever is going on, it's not in hardware.

**Attempted solutions**

Per the instructions in the sticky for the networking section, I have updated all repositories and distrobution. Running the provided script gave me a possible issue in terms of compatibility of the ubuntu driver with the onboard Realtek ethernet components, as seen in this thread: [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

However, it has not solved the issue. A further info dump reveals the new driver has been applied to eth1, but not eth0, and it is eth0 that has the local ip address. Perhaps it is being installed on the wrong interface? I really don't know enough about network protocals or driver installations to say.

[B]Additional comments
[/B]
I am happy to provide additional information about the system or issue as requested. Also, I provided as much as I could here, figuring the more information the better, but I would love comments about what is relevant and what is not. On a similar vein,  if I get stuck, I like to walk away from it knowing how to deal with similar issues in the future, and would love any comments on troubleshooting tools used to help solve this issue. Not necessary for sure, just nice :)

**Solution**
[Currently reserved for when the problem is resolved]

**Script Info dump**

```

########## wireless info START ##########

Report from: 11 Apr 2015 21:45 PDT -0700

Booted last: 11 Apr 2015 21:15 PDT -0700

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
    Kernel driver in use: r8168

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:12a0 Apple, Inc. iPhone 4S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID 046d:0a44 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
mxm_wmi                13021  0 
wmi                    19177  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.147  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8e89:a5ff:fe31:4eda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:290542 (290.5 KB)  TX bytes:20862 (20.8 KB)
          Interrupt:75 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:172.20.10.6  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::1834:51ff:fe26:640c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6327 errors:0 dropped:1 overruns:0 frame:0
          TX packets:6350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2934400 (2.9 MB)  TX bytes:797005 (797.0 KB)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    0      0        0 eth1
172.20.10.0     0.0.0.0         255.255.255.240 U     1      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search localdomain

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.147
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             208.67.220.220

- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ipheth
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.20.10.6
    Prefix:          28 (255.255.255.240)
    Gateway:         172.20.10.1

    DNS:             172.20.10.1

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

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

virbr0    no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:61:33:64:BC:2A:A1:9D:70:BF:0C:6E:59:BF:8A:CA:FF:65:C8:79
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

