---
title: "Wifi network missing, nothing new installed on Dell Inspiron with Ubuntu 12.04"
date: 2014-11-26
forum: Networking &amp; Wireless
---

### Post by catfishy3 on 2014-11-26
Last night I noticed that my wireless network, which had been working before, was missing from the connection list. The network itself is fine, I can access it from other devices around the house. I've already done several searches but all of the threads I've found seem to be for issues that came up after a new installation of Ubuntu. I did not install Ubuntu just yesterday. I've already run the wireless_script, and have gotten this:

```
########## wireless info START ##########

Report from: 26 Nov 2014 15:18 EST -0500

Booted last: 26 Nov 2014 15:13 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:041a]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:8101 Suyin Corp. 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

##### PCMCIA card info ##################

##### rfkill ############################

0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.10.116  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::5e26:aff:fe0d:ee73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2284093 (2.2 MB)  TX bytes:191573 (191.5 KB)
          Interrupt:42 Base address:0xe000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

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
    Address:         192.168.10.116
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1

    DNS:             192.168.10.1

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/2WIRE556]] (600 root)
[connection] id=2WIRE556 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE556 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/elkaccess]] (600 root)
[connection] id=elkaccess | type=802-11-wireless
[802-11-wireless] ssid=elkaccess | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/shelby]] (600 root)
[connection] id=shelby | type=802-11-wireless
[802-11-wireless] ssid=shelby | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pv]] (600 root)
[connection] id=pv | type=802-11-wireless
[802-11-wireless] ssid=pv | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

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

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:05:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:07:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```
The network I want is shelby. I can't figure out what could have triggered this or what to do about it, so any help would be greatly appreciated.

---

### Post by jeremy31 on 2014-11-26
You might want to remove wifi card, clean the connection and insert it back in, after powering down the computer.  Ubuntu is not detecting any trace of the wifi card but it must have been an Atheros card

---

### Post by catfishy3 on 2014-11-26
As much as I realise it probably does need to be cleaned (I've had this  netbook for, what, 3 years now?) I'm a bit reluctant to disassemble  anything without being totally certain what the problem is. Now that I  think about it, though, I think my brother was trying (unsuccessfully)  to log in to my computer yesterday and might have gotten crumbs or  whatever on it... I guess I'll post back here after I clean it up and  see if that helps. Bleh...

EDIT: Interestingly enough, one of the screws was stuck and I couldn't even remove the keyboard to get to the wifi card underneath... but apparently, just pulling the battery seemed to have solved the problem? Maybe I managed to shake some dust loose when I was trying to get that screw out? I don't know how or why but I'm marking this as solved since I don't seem to have any other issues.

---

### Post by jeremy31 on 2014-11-26
I don't blame you if that laptop is that much of a problem to check on the wifi card, I have a N411z that the card will never be changed again in

---

