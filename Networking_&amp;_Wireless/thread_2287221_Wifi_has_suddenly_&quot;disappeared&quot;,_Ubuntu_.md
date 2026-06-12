---
title: "Wifi has suddenly &quot;disappeared&quot;, Ubuntu 14.04, HP G5000"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by Patrik_H on 2015-07-17
I have been running Ubuntu on this computer for a couple of years now and I've never had any problems with my wifi, until now.
For a couple of months I have only used a cable, so I've had the wifi turned off. But now i can't seem to turn it on again.

I have been trying to fix this for hours, but now I'm stuck.
Here's the output of the wireless info script:

Edit: The computer is a HP G5238sc to be precise

```


########## wireless info START ##########

Report from: 17 Jul 2015 23:31 CEST +0200

Booted last: 17 Jul 2015 23:30 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, acpi=force, irqpoll, quiet, splash

##### desktop ###########################

Cinnamon

##### lspci #############################

00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 001 Device 006: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 005: ID 0781:5571 SanDisk Corp. Cruzer Fit
Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 002: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:2002:4e46:2025:4ceb:e843:6d52:27d6/64 Scope:Global
          inet6 addr: 2001:2002:4e46:2025:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:933519 (933.5 KB)  TX bytes:153441 (153.4 KB)

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
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       905     1  0 23:30 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         2001:2002:4e46:2025:4ceb:e843:6d52:27d6
    Prefix:          64
    Gateway:         fe80::3291:8fff:fe7e:4944

    Address:         2001:2002:4e46:2025:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::3291:8fff:fe7e:4944

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::3291:8fff:fe7e:4944

    DNS:             2001:2002:4e46:2025:3291:8fff:fe7e:4944

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

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3090 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```


The wireless card should be under "lspci" but it isn't. And yes, I have checked the card and it's there..
I apologise for my english and I hope that someone knows what I'm gonna do to fix this.

---

### Post by NoWayWin8 on 2015-07-17
> **Patrik_H said:**
> I have been running Ubuntu on this computer for a couple of years now and I've never had any problems with my wifi, until now.
For a couple of months I have only used a cable, so I've had the wifi turned off. But now i can't seem to turn it on again.
If it's not showing up on the PCI bus then it sounds like its the firmware setting you need to change (look in the BIOS settings for a WiFi/WLAN option that's still disabled).

---

### Post by Patrik_H on 2015-07-18
I just checked the BIOS settings and there&#8217;s nothing there that has to do with Wifi/WLAN.

Like I wrote earlier, it worked before, and I haven&#8217;t done anything that I know of that could&#8217;ve caused this problem.

Would it help if I took out the wifi card to look for a serial number or something?
Can wifi cards just die? Sounds weird

---

