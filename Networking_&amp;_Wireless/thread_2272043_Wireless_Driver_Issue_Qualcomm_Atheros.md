---
title: "Wireless Driver Issue Qualcomm Atheros"
date: 2015-04-03
forum: Networking &amp; Wireless
---

### Post by ka2012 on 2015-04-03
Recently, I dual-booted my new laptop. I am having issues in Ubuntu 14.04 with getting wi-fi to work (On windows it works fine, so its not a hardware issue).

Heres my info: 
```
 lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 20
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e4000000-e41fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 54:ee:75:42:46:95
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.1.217 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s


```

I ran the script on the "before posting in networking and wireless" and got this:

```
########## wireless info START ##########

Report from: 03 Apr 2015 13:54 EDT -0400

Booted last: 03 Apr 2015 09:37 EDT -0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3818]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 03eb:8a1d Atmel Corp. 
Bus 002 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 003: ID 5986:055e Acer, Inc 
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.217  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::56ee:75ff:fe42:4695/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255732857 (255.7 MB)  TX bytes:3627555 (3.6 MB)

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
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.217
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

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

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

I have tried searching for proprietary drivers, but none show up. Any suggestions for how to get my wireless driver to work are appreciated.

---

### Post by praseodym on 2015-04-03
Just load it:
```

sudo modprobe -v ath9k
```

---

### Post by jeremy31 on 2015-04-03
> **praseodym said:**
> Just load it:
```

sudo modprobe -v ath9k
```

Maybe not, looks to be a newer device with no current support [http://comments.gmane.org/gmane.linux.drivers.ath10k.devel/2022](http://comments.gmane.org/gmane.linux.drivers.ath10k.devel/2022)

---

### Post by praseodym on 2015-04-03
```
modprobe -c | grep -i "168c.*0041"
alias pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i* ath9k
alias pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i* ath9k
alias pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i* ath9k
```
showed it, but you're right, the grep-filter is wrong here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)

---

### Post by ka2012 on 2015-04-04
modprobe didn't work...I may just try NDISWrapper with the windows driver for now, unless anyone has an other suggestions. Thanks

---

### Post by chili555 on 2015-04-04
> I may just try NDISWrapper with the windows driver for nowPlease note that ndiswrapper requires Windows *XP* drivers appropriate to your architecture; in your case, 64-bit. If you have those, we suggest you proceed.

---

### Post by mitulsaha on 2015-07-16
Did it work with [COLOR=#000000]ndiswrapper?[/COLOR]

---

### Post by jeremy31 on 2015-07-16
> **mitulsaha said:**
> Did it work with [COLOR=#000000]ndiswrapper?[/COLOR]

Is there a Windows XP driver available for this wifi chipset?

---

### Post by mitulsaha on 2015-07-17
That would be nice, if someone can find XP drivers.

---

