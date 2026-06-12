---
title: "Ralink RT2870 Generic USB Adapter will not make/install on Ubuntu 14.04 Headless"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by zach25 on 2015-01-19
Hey all,

Been trying to get this thing going for a few days, and it's driving me crazy.

I currently have my old server wired, but the location it is in has to change, and the distance is too far (rather, would be annoying) to have a super long RJ45 cord trailing through my apartment. So I need to get this working.

This is the output of my 'wireless script' run:
```

########## wireless info START ##########

Report from: 19 Jan 2015 15:57 NST -0330

Booted last: 19 Jan 2015 12:54 NST -0330

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/xeddex/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

01:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:577c]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 001 Device 006: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless_script: line 176: rfkill: command not found

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe46:aeb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23608611 (23.6 MB)  TX bytes:40066014 (40.0 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 24.222.0.94
nameserver 24.222.0.95

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

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

Region: America/St_Johns (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

loop
lp

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
blacklist rt2800usb

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
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:01:0c.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

I have searched the forums, and the net far and wide trying to get this fixed, to no avail.

When I try and build the makefile, this is what happens:

```
make[2]: *** [/home/xeddex/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/xeddex/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-44-generic'
make: *** [LINUX] Error 2


```

..and before you ask, yes I googled it, and nothing worked. On one post, they said they fixed it by, editing a few files. I did that, but still nadda. I have tried, unplugging it and re-plugging it. I have done all updates and upgrades + restarted multiple times. I even got a VNC running on it and that just wasted my time.

So. Anyone have any ideas?

Also, this is my first time posting (I have lurked the forums **a lot **but usually only deem it appropriate to post on one as a last resort), so if I have failed to follow some rule, or have posted wrong, or have not provided enough info, please do let me know, and I will fix my error.

I appreciate any help you can provide.

Xedd-

---

### Post by chili555 on 2015-01-19
> make[2]: *** [/home/xeddex/[COLOR="#FF0000"]2010[/COLOR]_0709_RT2870_Linux_STA_v2.4.0.1/This creaky old antique will never compile on any kernel that is currently in use. We no longer use wooden wheels on our sleek, black BMWs!

I notice that you've blacklisted the driver that is supposed to correctly drive your device! If rt2800usb isn't working correctly, installing its great-grandfather is unlikely to help.

What was not working about the native driver?

---

### Post by zach25 on 2015-01-19
> **chili555 said:**
> This creaky old antique will never compile on any kernel that is currently in use. We no longer use wooden wheels on our sleek, black BMWs!

I notice that you've blacklisted the driver that is supposed to correctly drive your device! If rt2800usb isn't working correctly, installing its great-grandfather is unlikely to help.

What was not working about the native driver?

-.-... It wasn't working at all. The rt2800usb was not even installed, either that or it was automatically blacklisted, as I never blacklisted it.... So what do I do about it?..

Edit: This is also an upgraded system from 12.04 to 14.04, as I thought that would fix the issue.

---

### Post by chili555 on 2015-01-19
Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove the line: blacklist rt2800usb. Proofread carefully, save and close the text editor. Then:```
sudo modprobe rt2800usb
```Is it working?

---

