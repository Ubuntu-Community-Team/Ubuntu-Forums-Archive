---
title: "Ralink RT3090 takes time to connect"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by iebo on 2013-11-09
hey dear ubuntuforums members , my wlan interface takes more time to start find few wireless networks like 3/5 minutes  through network manager sometimes it doesn't connect to ap if i do (iwlist scan) i can't see nothing... this happens every time i boot after long shut down

its strange because usually all other aps show up  when i'm connected to my preferred network 
 
i have hp notebook 620 running ubuntu 10.04 

its show rt2860 module via iwconfig 
```

 wlan0     RT2860 Wireless  ESSID:"Vodafone"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0x:xx:xx:xx:xx   
          Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=60/100  Signal level:-63 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

hp-laptop:~$ cat sudo /etc/modules
cat: sudo: No such file or directory
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

rt2860sta

hp-laptop:~$ sudo cat  /etc/modprobe.d/blacklist.conf



# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


#NATIVE wirless mod
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt2860sta


hp-laptop:~$  lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: ex:2x:xx:xx:cx:xc        width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 ip=192.168.1.194 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:98800000-9880ffff

hp-laptop:~$  hwinfo --netcard
28: PCI 200.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1814_3090
  Unique ID: y9sn.drSOnGXMLV1
  Parent ID: qTvu.8Makl3iDVc3
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "RaLink WLAN controller"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x3090 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x1453 
  Driver: "rt3090"
  Driver Modules: "rt3090sta"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0x98800000-0x9880ffff (rw,non-prefetchable)
  IRQ: 17 (72098 events)
  HW Address: ex:2x:xx:xx:cx:xc
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00003090sv0000103Csd00001453bc02sc80i00"
  Driver Info #0:
    Driver Status: rt3090sta is active
    Driver Activation Cmd: "modprobe rt3090sta"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)



```

---

### Post by varunendra on 2013-11-11
Is it a desktop installation? 10.04 has reached its EOL (End Of Life), means it is no more supported. Besides, the native drivers in 12.04.3 have been improved quite a lot.

As such, I'd recommend you try 12.04.3 (or even 13.10) in live mode, and see if your wireless works any better with it. If it does, do a clean install of it. The proprietary driver (3090sta) would need some patching to install on the latest kernels, but it is possible. Although I hope the native ones should be good enough to not require the sta one.

---

### Post by iebo on 2013-11-11
hey varun , yes its desktop i know its not up to date  but i have been working with 10.04 for years now i'm become more familiar 

i have lost my faith on this rt3090 driver , even though i had less problems  connecting at some point ..it wasn't easy to make internet work 

handy network tools like ettercap ,tuxcut and many others are not functional

---

