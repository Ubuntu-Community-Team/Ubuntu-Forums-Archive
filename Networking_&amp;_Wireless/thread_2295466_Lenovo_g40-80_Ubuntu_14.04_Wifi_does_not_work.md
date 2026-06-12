---
title: "Lenovo g40-80 Ubuntu 14.04 Wifi does not work"
date: 2015-09-18
forum: Networking &amp; Wireless
---

### Post by alessio9 on 2015-09-18
Hello, 

I recently bought a Lenovo g40-80 and installed Ubuntu 14.04 LTS. Unfortunately, the Wi-Fi does not work; I followed the instructions in [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) but I was not able to solve the issue on my own. So I am posting here the info, and any help is much appreciated!! 

Thank you very much.

```


########## wireless info START ##########

Report from: 18 Sep 2015 21:53 EDT -0400

Booted last: 18 Sep 2015 21:51 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3821]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:98.222.192.54  Bcast:98.222.207.255  Mask:255.255.240.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130965 (130.9 KB)  TX bytes:23259 (23.2 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         98.222.192.1    0.0.0.0         UG    0      0        0 eth0
98.222.192.0    0.0.0.0         255.255.240.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.in.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       919     1  0 21:51 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

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
    Address:         98.222.192.54
    Prefix:          20 (255.255.240.0)
    Gateway:         98.222.192.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

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

Region: America/Indiana/Indianapolis (based on set time zone)

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   19.224802] Bluetooth: hci0: don't support firmware rome 0x200

########## wireless info END ############


```

---

### Post by praseodym on 2015-09-19
Sorry, but this device is not supported yet. Any "tricks" didn't work yet, see:

[http://ubuntuforums.org/showthread.php?t=2292252&highlight=168c%3A0041](http://ubuntuforums.org/showthread.php?t=2292252&highlight=168c%3A0041)

---

### Post by alessio9 on 2015-09-19
Ok, thanks :(

---

### Post by Bucky Ball on 2015-09-19
> **praseodym said:**
> Sorry, but this device is not supported yet.

Grab a $10 USB wireless dongle until it does. Easy to find. Could you mark thread as solved, please. See the first link in my signature. This will not close the thread for further discussion, but please post a new thread for any issues with any other wireless issues with a new device.

Good luck. :)

---

### Post by alessio9 on 2015-09-19
> **Bucky Ball said:**
> Grab a $10 USB wireless dongle until it does. Easy to find. 


I guess that's what I'm going to do. Thanks!

---

