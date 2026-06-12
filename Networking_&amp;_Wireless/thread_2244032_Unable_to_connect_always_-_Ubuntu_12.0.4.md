---
title: "Unable to connect always - Ubuntu 12.0.4 ?"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by Mark_Berger on 2014-09-13
Hello, 

                I have been faced with this problem for short time only cause i have recently change my connection here in the Philippines from Globe to SMARTBro... With Globe my connection never fails and alwayes connects but since I have switched to SMARTBro my connection when I am on my Ubuntu only connects sometimes. So... With that said when I am on windows I never have a problem with connection to the internet but when I boot to my Ubuntu it only wants to connect some times not every time as it should.

Connection: WIRED (Not Wireless)

Ubuntu Version: 12.0.4

Network Information:
================

```

orbit@darkorbit:~$ sudo lshw -C network
[sudo] password for orbit: 
  *-network               
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:02:0f.0
       logical name: eth0
       version: 10
       serial: 00:1d:7d:a3:a9:fa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:23 ioport:de00(size=256) memory:fdffe000-fdffe0ff memory:fde00000-fde1ffff
orbit@darkorbit:~$  [


orbit@darkorbit:~/Desktop$ lspci -nnk | grep -iA2 eth
02:0f.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
    Subsystem: Giga-byte Technology GA-MA69G-S3H Motherboard [1458:e000]
    Kernel driver in use: r8169
orbit@darkorbit:~/Desktop$


orbit@darkorbit:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:a3:a9:fa  
          inet6 addr: fe80::21d:7dff:fea3:a9fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1033988 (1.0 MB)  TX bytes:373550 (373.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9728 (9.7 KB)  TX bytes:9728 (9.7 KB)

orbit@darkorbit:~$ 



orbit@darkorbit:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        00:1D:7D:A3:A9:FA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on


orbit@darkorbit:~$ 

orbit@darkorbit:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
orbit@darkorbit:~$ 


orbit@darkorbit:~$ nslookup ubuntu.com
;; connection timed out; no servers could be reached

orbit@darkorbit:~$ dig ubuntuforums.org

; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached
orbit@darkorbit:~$ 

```


wireless_info.txt
===========
```


########## wireless info START ##########

Report from: 14 Sep 2014 00:17 PHT +0800

Script from: 05 Sep 2014 22:42 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

MATE

##### lspci #####

02:0f.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
    Subsystem: Giga-byte Technology GA-MA69G-S3H Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 002 Device 005: ID 1c4f:0003 SiGma Micro HID controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:2010 Dell Computer Corp. Keyboard

##### PCMCIA card info #####

##### rfkill #####

##### lsmod #####

mxm_wmi                13021  1 nouveau
wmi                    19256  2 nouveau,mxm_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet6 addr: fe80::21d:7dff:fea3:a9fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57110 (57.1 KB)  TX bytes:35856 (35.8 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

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

no-auto-default=<MAC addr eth0>,

[ifupdown]
managed=false

##### iw reg get #####

./wireless_script: line 141: iw: command not found

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos #####

##### module parameters #####

##### /etc/modules #####

lp
rtc

##### blacklists #####

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

##### rc.local #####

exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:14.4/0000:02:0f.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:14.4/0000:02:0f.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

########## wireless info END ############

```

Any help on this problem would be greatly appreciated and thank you for your time. :)

- Mark B.

---

### Post by ian-weisser on 2014-09-15
So Ubuntu networking used to work 100%? And the only change was your internet service provider?

I would start with route and ping tests before hardware.

---

