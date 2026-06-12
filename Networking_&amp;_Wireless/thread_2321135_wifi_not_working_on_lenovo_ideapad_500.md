---
title: "wifi not working on lenovo ideapad 500"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by dollar2 on 2016-04-20
Hola ubuntu forum! 

I have lenovo ideapad 500 laptop which came with windows 10 pre-installed. The wifi works on windows but there is no sign of wifi on ubuntu 14.04. wire connection works ok on ubuntu 14.04. Please help !!:)

 following are contents of my wireless-info.txt file

```
########## wireless info START ##########

Report from: 20 Apr 2016 21:14 BST +0100

Booted last: 20 Apr 2016 21:03 BST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

##### kernel ############################

Linux 3.19.0-58-generic #64~14.04.1-Ubuntu SMP Fri Mar 18 19:05:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
        Subsystem: Lenovo Device [17aa:3833]
        Kernel driver in use: r8169

03:00.0 Network controller [0280]: Intel Corporation Device [8086:3166] (rev 79)
        Subsystem: Intel Corporation Device [8086:4210]

##### lsusb #############################

Bus 002 Device 002: ID 8086:0a66 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no

##### lsmod #############################

ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:46.33.12.3  Bcast:46.33.12.127  Mask:255.255.255.128
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47599811 (47.5 MB)  TX bytes:1280809 (1.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         46.33.12.1      0.0.0.0         UG    0      0        0 eth0
46.33.12.0      0.0.0.0         255.255.255.128 U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search studentcom.co.uk

##### network managers ##################

Installed:

        NetworkManager

Running:

root      1108     1  0 21:03 ?        00:00:00 NetworkManager

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
    Address:         46.33.12.3
    Prefix:          25 (255.255.255.128)
    Gateway:         46.33.12.1

    DNS:             77.244.128.44
    DNS:             77.244.128.45

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

Region: Europe/London (based on set time zone)

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

[   21.324305] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   21.324349] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.954994] r8169 0000:02:00.0 eth0: link up
[   22.955003] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  535.684520] r8169 0000:02:00.0 eth0: link down
[  648.942925] r8169 0000:02:00.0 eth0: link up

########## wireless info END ############
```

---

### Post by Hadaka on 2016-04-20
Hi, please open a terminal then copy and paste..
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
then try jermy31's fix here..post #4
[http://ubuntuforums.org/showthread.php?t=2311656](http://ubuntuforums.org/showthread.php?t=2311656)
thanks.

---

### Post by wildmanne39 on 2016-04-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

