---
title: "RTL8190 card not working"
date: 2016-07-06
forum: Networking &amp; Wireless
---

### Post by fvenable on 2016-07-06
I recently decided to switch over to ubuntu from windows with my desktop and for the most part everything works. Unfortunately my wireless card is not. Unfortunately, the lack of wireless makes copying things over from it a pain as I have to do it by hand (I'm using a laptop right now).

That said it says the following if I type sudo lshw -C network:

```
*-network UNCLAIMED
description: Network controller
product: RTL8190 802.11n PCI Wireless Nework Adapeter
...
```

If you need something else from that let me know.

Because of this, I tried to get ndiswrapper to work. I think I successfully installed the driver as ndiswrapper -l says:

```
net819xp : driver installed
device (10EC:8190) present
```

However sudo modprobe ndiswrapper returns: ```
modprobe: FATAL: Module ndiswrapper not found.
```

My searches there have indicated that this can be fixed by installing ndiswrapper-dkms, as well as ndiswrapper-common, and ndiswrapper-utils-1.9. The latter were mentioned less frequently but when the initial package didn't fix the problem I installed them as well. Unfortunately that also doesn't work.

I also tried ndisgtk, which seem to work further into the process but returns a slew of permissions errors into the console as soon as I try to add a network with it, despite requiring sudo in the first place.

I attempted to compile ndiswrapper from source myself since that was also described as fixing the problem, but when I use "make" the compiler errors out on a comment.

Also "Additional drivers" only has drivers for my video card.

Thanks!

---

### Post by fvenable on 2016-07-07
I managed to log onto the forums by tethering with my phone. Sorry for taking so long to get this to you but my system is fully updated and here's the diagnostic document requested:

```

########## wireless info START ##########

Report from: 07 Jul 2016 00:05 MDT -0600

Booted last: 06 Jul 2016 23:50 MDT -0600

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-41-generic #48~14.04.1-Ubuntu SMP Fri Jun 24 17:11:27 UTC 2016 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:06.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8190 802.11n PCI Wireless Network Adapter [10ec:8190]

05:00.0 USB controller [0c03]: Etron Technology, Inc. EJ188/EJ198 USB 3.0 Host Controller [1b6f:7052]

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 19d2:1373 ZTE WCDMA Technologies MSM 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 062a:0003 Creative Labs 
Bus 008 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF2]>  
          inet addr:192.168.42.134  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50740 (50.7 KB)  TX bytes:85931 (85.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth1      no wireless extensions.

usb0      no wireless extensions.

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

root       757     1  0 Jul06 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF2]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.134
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF1]>

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

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=ellen
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Denver (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0)

##### iwlist channels ###################

lo        no frequency information.

eth1      no frequency information.

usb0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
ndiswrapper

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
alias pci:v000007AAd00000044sv*sd*bc*sc*i* ndiswrapper
alias pci:v000007AAd00000046sv*sd*bc*sc*i* ndiswrapper
alias pci:v000007AAd00000047sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv00003304sd00001186bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv0000C12Dsd00001259bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000005Esd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00006896sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00007160sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008151sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008154sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000E01Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000E01Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[    3.328660] r8169 0000:06:00.0 eth1: renamed from eth0
[    3.375970] systemd-udevd[425]: renamed network interface eth0 to eth1
[    3.709564] r8169 0000:06:00.0 eth1: link down
[    3.709599] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  924.486498] rndis_host 6-5:1.0 usb0: register 'rndis_host' at usb-0000:00:13.2-5, RNDIS device, <MAC 'usb0' [IF2]>

########## wireless info END ############


```

---

### Post by fvenable on 2016-07-07
Feel free to mark this solved. I got a different adapter and it works.

---

