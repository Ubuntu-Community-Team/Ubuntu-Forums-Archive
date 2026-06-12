---
title: "Atheros QCA9565 / AR9565: Wifi not working in ubuntu 12.04"
date: 2014-12-28
forum: Networking &amp; Wireless
---

### Post by ANKIT_YADAV on 2014-12-28
output of my wireless sript is here. 
please suggest how it will work as my wired connection is working perfectly.

```
########## wireless info START ##########

Report from: 28 Dec 2014 14:24 IST +0530

Booted last: 28 Dec 2014 14:21 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-74-generic #109-Ubuntu SMP Tue Dec 9 16:45:49 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020c]

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 054c:05b8 Sony Corp. 
Bus 003 Device 004: ID 04ca:0061 Lite-On Technology Corp. 
Bus 001 Device 003: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0c45:64ad Microdia 

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_laptop            18119  0 
dell_wmi               12681  0 
dcdbas                 14490  1 dell_laptop
sparse_keymap          13890  1 dell_wmi
wmi                    19256  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eef4:bbff:fe74:5c7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135106 (135.1 KB)  TX bytes:56047 (56.0 KB)
          Interrupt:42 Base address:0x4000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

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
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.113.218.106
    DNS:             8.8.8.8

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############
```

---

### Post by Bucky Ball on 2014-12-28
*Thread moved to **Networking & Wireless**.*

Welcome. Please use [code] tags for terminal/code output. I have added them. To see how, check the last link in my signature or click 'Edit Post' on your first post and see where I've put them. Good luck.

---

### Post by Hadaka on 2014-12-28
Hi, from a working wired connection please do
```
sudo apt-get updates
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic
```
disconnect the wired connection and test.

---

### Post by Bucky Ball on 2014-12-28
> **Hadaka said:**
> Hi, from a working wired connection please do
```
sudo apt-get updates
sudo apt-get install linux-backports-modules-cw-3.8-precise-generic
```
disconnect the wired connection and test.

Don't mean to jump on your toes, Hadaka, but do you mean:

```
sudo apt-get update
```

? ;)

---

### Post by praseodym on 2014-12-28
The driver ath9k should work ootb:
```

sudo modprobe -v ath9k
```

Edit: if you install the LTS stack of trusty in 12.04:

```
sudo apt-get -s install --install-recommends linux-generic-lts-trusty linux-image-generic-lts-trusty linux-headers-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
```
This is a test. If it runs without errors, repeat it without "-s"

---

