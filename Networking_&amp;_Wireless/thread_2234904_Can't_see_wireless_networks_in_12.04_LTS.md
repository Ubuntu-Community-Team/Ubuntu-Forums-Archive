---
title: "Can't see wireless networks in 12.04 LTS"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by webcomm on 2014-07-17
I was having problems with dropped wireless connections and very low wireless range.  To fix the problem, I upgraded the driver for my Ralink 3592 wireless card.  This fixed the problem and it continued to work until sometime today, when the connection dropped and all wireless networks disappeared.  I have rebooted several times and the computer can no longer find any wireless networks.  Please see below for debug info.

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux ryan-HP-ProBook-4530s 3.2.0-67-generic #101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

25:00.0 Network controller [0280]: Ralink corp. RT3592 Wireless 802.11abgn 2T/2R PCIe [1814:3592]
    Subsystem: Hewlett-Packard Company Device [103c:1638]
    Kernel modules: rt2800pci
26:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:167c]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 004: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam

##### PCMCIA Card Info #####

##### rfkill #####

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #####

##### iw reg get #####

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.241
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

##### iwlist channel #####

##### modinfo #####

##### modules #####

lp
rtc

##### blacklist #####

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

[/etc/modprobe.d/blacklist-local.conf]
blacklist fglrx_experimental_13

[/etc/modprobe.d/blacklist-rt2800pci.conf]
blacklist rt2800pci

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:26:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.3/0000:25:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.3/0000:25:00.0 (rt2860)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ra*", NAME="ra0"

##### dmesg #####

########## wireless info END ############

```

---

### Post by webcomm on 2014-07-18
I repeated the steps at [http://askubuntu.com/a/182132/305908](http://askubuntu.com/a/182132/305908)

I went through these exact same steps a couple days ago, to fix the original problem.  And I've now just gone through the steps again and it has fixed this new problem.  I now see the wireless networks and can connect wirelessly.  I'm not sure why I had to go through these steps again, though, and wonder if I will have to keep doing this.

---

### Post by jeremy31 on 2014-07-18
You should only have to do it after a kernel update

---

