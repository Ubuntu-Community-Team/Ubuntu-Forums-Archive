---
title: "Wireless networks not showing up / Lenovo Thinkpad with Ubuntu"
date: 2014-02-25
forum: Networking &amp; Wireless
---

### Post by nicole5 on 2014-02-25
Hi, I recently installed Ubuntu 12.04 alongside Windows 8 on my Lenovo Thinkpad. Everything works fine except for the wireless networks, which don't show up at all (wireless still works fine on Windows 8). I've tried troubleshooting from other threads with this same issue but so far nothing has worked. 

I've activated my wireless driver in the System Settings, but the wlan0 doesn't show up when I run the following commands: 

```
$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:88:e3:e3:dc:1f  
          inet addr:128.61.94.142  Bcast:128.61.95.255  Mask:255.255.240.0
          inet6 addr: fe80::ba88:e3ff:fee3:dc1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1429827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:396632587 (396.6 MB)  TX bytes:3747911 (3.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:437673 (437.6 KB)  TX bytes:437673 (437.6 KB)
```

```
$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.
```

```
$ sudo lshw -C network
*-network               
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f1d00000-f1d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 07
       serial: b8:88:e3:e3:dc:1f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=128.61.94.142 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0c04000-f0c04fff memory:f0c00000-f0c03fff
```

---

### Post by varunendra on 2014-02-25
Welcome to Ubuntu Forums nicole5 !

> **nicole5 said:**
> ```
configuration: **driver=[COLOR="#FF0000"]bcma-pci-bridge[/COLOR]** latency=0
```

It doesn't look like the required driver was installed. Please post the outputs of the following commands -
```
uname -mr
lspci -nnk | grep -iA2 net
dpkg -l | grep bcmwl
apt-cache show bcmwl* | grep Version
lsmod | egrep 'b43|brcm|wl'
dmesg | egrep 'b43|brcm|wl'
```

---

### Post by nicole5 on 2014-02-26
Here's the outputs:

```
$ uname -mr
3.8.0-36-generic x86_64 
```

```
$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: bcma-pci-bridge
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:2205]
    Kernel driver in use: r8169
nicolette@nicolette-ThinkPad-Twist:~$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source                         6.20.155.1+bdcom-0ubuntu0.0.2                       Broadcom 802.11 Linux STA wireless driver source
```

```
$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source                         6.20.155.1+bdcom-0ubuntu0.0.2                       Broadcom 802.11 Linux STA wireless driver source 
```

```
$ apt-cache show bcmwl* | grep Version
Version: 6.20.155.1+bdcom-0ubuntu0.0.2
Version: 5.100.82.38+bdcom-0ubuntu6
```

```
$ lsmod | egrep 'b43|brcm|wl'
wl                   3074904  0 
cfg80211              526422  1 wl
lib80211               14381  1 wl
```

```
$ dmesg | egrep 'b43|brcm|wl'
[    8.580253] wl: module license 'MIXED/Proprietary' taints kernel.
```



I had the wireless halfway working at one point (the available networks were showing up, but I couldn't connect to any of them). In the process of trying to fix that, I made the wireless networks not show up again. So there's really no telling what all I've done.. I thought about just reinstalling Ubuntu so I could start fresh.

---

### Post by varunendra on 2014-02-26
Please try this (while being connected via Ethernet) -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
```
You may need to reboot after this for the change to take effect. Does wireless work any better? If not, we may have to try manually installing a newer version than what is available by default for you.

---

### Post by nicole5 on 2014-02-26
Ok, so I tried the codes you posted and I got an error when running the second one. My wireless driver was deactivated and when I tried to reactivate it, it said there was an error. So I ran this:

```
$ sudo apt-get install --reinstall bcmwl-kernel-source
$ sudo modprobe wl 
```

Wireless driver is activated and I actually have wireless networks showing up. But when I try to connect to one, it just continuously says connecting. It will ask for my username and password then open a window that says "No Certificate Authority certificate chosen". If I click "Choose CA Certificate" it takes me right back to the window where I type my username and password, if I click "Ignore" it tries to connect again and does the same thing.

EDIT: After rebooting, the wireless networks don't show up. I have to re-run the codes above a couple times (why it doesn't work the first time, I have no idea). But eventually the wireless networks show up again.

---

### Post by varunendra on 2014-02-26
Do you have a working wired connection? Have you tried 'Updating' the system while being connected? Please do if you haven't -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

And it would have helped a lot if you could tell exactly WHAT error occurred while running the second command I suggested. I can assume what it might be, but I don't want to rely on assumptions when we can have confirmations.

Also, let's get a complete picture of your network configuration in one go instead of running individual commands. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by nicole5 on 2014-02-26
When I ran the codes you posted earlier, I got this when running the second one: 
```
$ sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 3,514 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 212014 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-36-generic
Building for architecture x86_64
Building initial module for 3.8.0-36-generic
Error! Bad return status for module build on kernel: 3.8.0-36-generic (x86_64)Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-36-generic
```
And then a window popped up that said "System program problem detected." That's all it said.


And this is the contents of the file generated:
```


*************** info trace ***************


***** uname -a *****


Linux nicolette-ThinkPad-Twist 3.8.0-36-generic #52~precise1-Ubuntu SMP Mon Feb 3 21:54:46 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


***** lspci *****


03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
    Subsystem: Broadcom Corporation Device [14e4:0607]
    Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:2205]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1bcf:053e Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 03eb:8206 Atmel Corp. 
Bus 001 Device 004: ID 0a5c:21f3 Broadcom Corp. 
Bus 002 Device 003: ID 0483:91d1 SGS Thomson Microelectronics 
Bus 002 Device 004: ID 04f2:b315 Chicony Electronics Co., Ltd 


***** PCMCIA Card Info *****




***** iwconfig *****


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** iw reg get *****




***** route -n *****


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         128.61.80.1     0.0.0.0         UG    0      0        0 eth0
128.61.80.0     0.0.0.0         255.255.240.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0


***** lsmod *****


wl                   3074904  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
cfg80211              526422  2 wl,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth1  [GTwifi] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Chromecast16774: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA2
    GTother:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2 Enterprise
    GTwifi:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2 Enterprise
    GTother:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    HP-Print-8D-Deskjet 3510 series: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    GTother:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    GTother:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2 Enterprise
    Chromecast16775: Infra, <MAC address removed>, Freq 5765 MHz, Rate 54 Mb/s, Strength 40 WPA2
    GTother:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    GTother:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    Chromecast27885: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    GTother:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    GTwifi:          Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    GTother:         Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 32 WPA2
    PS4-99C821D3D43E:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    2WIRE633:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    TB Proprietary Channel. vx: Infra, <MAC address removed>, Freq 5220 MHz, Rate 18 Mb/s, Strength 29 WPA2
    GTvisitor:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57
    GTvisitor:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    GTvisitor:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    GTvisitor:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    GTvisitor:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    GTvisitor:       Infra, <MAC address removed>, Freq 5200 MHz, Rate 54 Mb/s, Strength 32
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 11 Mb/s, Strength 27
    GTwifi:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    GTother:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    2WIRE827:        Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    GTother:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    GTwifi:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    2WIRE080:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    GTvisitor:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    GTvisitor:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    Kins:            Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    2WIRE562:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    PS3-5595313:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    GTvisitor:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65
    GTvisitor:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    GTwifi:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    AKRK:            Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    GTother:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    GTother:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    GTwifi:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA2 Enterprise
    GTother:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    GTvisitor:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    1028279-1447:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA2
    GTother:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    GTvisitor:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32
    GTwifi:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    GTvisitor:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    GTother:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         128.61.92.72
    Prefix:          20 (255.255.240.0)
    Gateway:         128.61.80.1


    DNS:             128.61.244.254
    DNS:             130.207.244.251
    DNS:             130.207.244.244






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=true


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****


nameserver 127.0.0.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


***** modinfo *****


filename:       /lib/modules/3.8.0-36-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-36-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[    6.704195] bcma: bus0: Found chip with id 0xA8DC, rev 0x00 and package 0x08
[    6.704230] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[    6.704255] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1E, class 0x0)
[    6.704305] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x12, class 0x0)
[    6.704332] bcma: bus0: Core 3 found: SDIO Device (manuf 0x4BF, id 0x829, rev 0x07, class 0x0)
[    6.712819] bcma: bus0: Bus registered
[    8.631463] Bluetooth: can't load firmware, may not work correctly
[   19.608574] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[  728.043232] wl: module license 'MIXED/Proprietary' taints kernel.
[  728.077323] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  728.237044] eth1: Broadcom BCM4359 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[  789.436687] ERROR @wl_dev_intvar_get : error (-1)
[  789.436692] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************
```

EDIT: Oh and I ran the update commands you just posted while connected through the ethernet cord. The wireless networks are available, it still just continues to ask for my username/password over and over again without ever actually connecting.

---

### Post by varunendra on 2014-02-26
Assuming you had not updated before, and this last one completed successfully, please check again which versions of the driver are available now -
```
apt-cache show bcmwl-kernel-source | grep Version
```
If you see the version 5.100.... again, please try re-installing it -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
```
..and when (if) it returns the same error, post back the log file it referred to -
```
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log
```

On the other hand, if you see a newer version (I'm expecting 6.30..), please report that also.

There are lots of Access-Points with same name, which may sometimes confuse Network Manager. So which is the one (or which are the ones) that you are trying to connect?

---

### Post by nicole5 on 2014-02-26
This is what I got for the version:
```
Version: 6.20.155.1+bdcom-0ubuntu0.0.2Version: 5.100.82.38+bdcom-0ubuntu6

```

I'm not really sure why there's two.. or if it's supposed to be like that. 

I tried reinstalling again anyway and got the same error. So this is the contents of that file:
```
DKMS make.log for bcmwl-5.100.82.38+bdcom for kernel 3.8.0-36-generic (x86_64)Wed Feb 26 22:15:43 EST 2014
make: Entering directory `/usr/src/linux-headers-3.8.0-36-generic'
  LD      /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-36-generic'
```

After running all of that I checked the version again and it was the same as what I posted above. 

And I'm only trying to connect to the GTwifi.

---

### Post by varunendra on 2014-02-26
> **nicole5 said:**
> I'm not really sure why there's two.. or if it's supposed to be like that. 
It is normal to have multiple versions available. They are just 'Available', and usually (but not always) the latest one is installed.

> **nicole5 said:**
> ```
/var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/src/wl/sys/wl_linux.c:43:24: fatal error: **[COLOR="#FF0000"]asm/system.h: No such file or directory[/COLOR]**
```
Yeah, a known problem with that version of the driver, I thought it was patched in the repository versions, but apparently it is not. Used to be easily fixable but probably not worth the trouble. We'll try a newer version first, and see if it works better.

Please manually download the file "bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb" from here : [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/)

Double-click to install it. If the Software Center does not let you install it (the install button remains inactive), install it with 'dpkg' command.

Assuming you have copied the file onto your Desktop, this command will install it with dpkg -
```
sudo dpkg -i Desktop/bcmwl*.deb
```
Watch out for errors and report back if there are any.

Once it is installed, you would probably need another modification in your Network Manager connection file. Please check -
```
sudo cat /etc/NetworkManager/system-connections/GTwifi
```
(assuming your connection is saved with the name "GTwifi". If not, please change it accordingly)

The above command will just show the contents of you connection's "Key File". **DO NOT POST** its contents here as it also **[COLOR="#FF0000"]contains sensitive information like your security password[/COLOR]** (or remove the password before posting here).

Do you see a line "system-ca-certs=true" in it? If yes, change its value to "false" with following command -
```
sudo sed -i '/system-ca-cert/ s/true/false/' /etc/NetworkManager/system-connections/GTwifi
```
(again, change the name "GTwifi" if you have saved the connection with a different name)

Then disable / re-enable wifi and retry to connect. Can you now?

If still not, try deleting the line altogether -
```
sudo sed -i '/system-ca-cert/ d' /etc/NetworkManager/system-connections/GTwifi
```
Any improvement?

Lastly, if the newer driver fails to install (although I *believe* it shouldn't), is a fresh install an option for you? If not, we may try upgrading only your kernel so that it supports the newer driver properly.
(as a last resort, we can also try to compile the same older driver 5.100... with the patch I mentioned, but that is a messy solution).

---

### Post by nicole5 on 2014-02-27
We're making some progress. After downloading and installing the new driver, it's kind of working. It's able to make a complete connection (I'm connected to the GTwifi right now). The only problem is that when I reboot, I have to reinstall the new driver (before I reinstall it, the wireless networks aren't listed). Once it's reinstalled though, wireless works perfectly fine.

---

### Post by varunendra on 2014-02-27
> **nicole5 said:**
> The only problem is that when I reboot, I have to reinstall **the new driver**

The 6.30 version that you manually downloaded I guess? Please confirm, although the version doesn't matter, you shouldn't need to reinstall it everytime if it installed properly. While installing, make sure it doesn't return any errors.

On next attempt, when you reboot, please run these commands without installing the driver again, and post back their outputs -
```
lsmod | egrep 'b43|brcm|ssb|wl'
dmesg | egrep 'b43|brcm|ssb|wl'
rfkill list
sudo iwlist scan
dpkg -l | grep bcmwl
```
And do you remember having created or edited any configuration files to make the wifi work earlier? If yes, we may need to revert the changes.

There are certain ways to 'Force' the driver automatically on reboot if required, but I want it to happen naturally, decently like it should. :)

---

### Post by nicole5 on 2014-02-27
Yes, the 6.30 version. And there were never any errors when installing it. 

Here's the output to those codes (before installing the driver again):

```
$ lsmod | egrep 'b43|brcm|ssb|wl'b43                   392246  0 
mac80211              631450  1 b43
cfg80211              526422  2 b43,mac80211
ssb                    57871  1 b43
bcma                   41273  1 b43
```

This one had no output:
```
$ dmesg | egrep 'b43|brcm|ssb|wl'
```

```
$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

```
$ sudo iwlist scan
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.
```

```
$ dpkg -l | grep bcmwl
ii  bcmwl-kernel-source                         6.30.223.141+bdcom-0ubuntu2                         Broadcom 802.11 Linux STA wireless driver source
```

And I specifically remember altering one file when I was trying to fix this before. That's when everything crashed (I couldn't connect to wired either). I had to change it back to exactly how it was before so that I'd at least have wired internet. That's the only file I remember changing.

EDIT: I'm pretty sure the file I changed was /etc/network/interfaces
Then I had to change it back so it only contains these two lines:
```
auto lo
iface lo inet loopback
```

---

### Post by varunendra on 2014-02-28
> **nicole5 said:**
> ```
$ lsmod | egrep 'b43|brcm|ssb|wl'b43                   392246  0 
mac80211              631450  1 **[COLOR="#FF0000"]b43[/COLOR]**
cfg80211              526422  2 b43,mac80211
ssb                    57871  1 b43
bcma                   41273  1 b43
```

Hmm.. so there must be something that keeps loading the b43 driver and block the "wl" driver. This should never happen with default setup with the "wl" driver installed/removed/reinstalled properly. So I suspect there must be some other custom entry somewhere causing this, or something that I haven't seen yet.

Let's take a look at some other files/entries that should/shouldn't be there. On next boot, again _before/without_ reinstalling the "wl" driver, please run the following commands and post back their outputs -
```
cat /etc/rc.local
cat /etc/modules
egrep -nHR 'wl|b43' /etc/modprobe.d
modinfo wl | grep filename
```

With any and all customizations removed, and letting the "wl" driver do what it wants while installing, should make its loading automatic. I hope to find the culprit in the above outputs.

---

### Post by nicole5 on 2014-03-01
Here's the outputs: 

```
$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0
```

```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc
b43
```

```
$ egrep -nHR 'wl|b43' /etc/modprobe.d
/etc/modprobe.d/blacklist-bcm43.conf:1:# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
/etc/modprobe.d/blacklist-bcm43.conf:2:blacklist b43
/etc/modprobe.d/blacklist-bcm43.conf:3:blacklist b43legacy
/etc/modprobe.d/blacklist.conf~:34:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf~:57:blacklist b43
/etc/modprobe.d/blacklist.conf:34:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-watchdog.conf:41:blacklist twl4030_wdt
```

```
$ modinfo wl | grep filename
filename:       /lib/modules/3.8.0-36-generic/updates/dkms/wl.ko
```

---

### Post by varunendra on 2014-03-01
Okay, half the mystery is solved. This is how b43 is loading despite being blacklisted -
> **nicole5 said:**
> ```
$ cat **/etc/modules**
....
lp
rtc
**[COLOR="#FF0000"]b43[/COLOR]**
But it is still not clear why the "wl" is not loading automatically despite being installed and recognized by the system -
[CODE]$ modinfo wl | grep filename
filename:       /lib/modules/3.8.0-36-generic/updates/dkms/wl.ko
```

The above means you don't need to install it everytime. So what I can promise with this is that we can make it automatic by other ways, if required.

However, let us first give it a chance to happen normally as it should. Please run this command -
```
sudo sed -i '/^b43/ d' /etc/modules
```
This will delete the entry "b43" from the /etc/modules file. After this, the b43 module should not load since next boot. Assuming that it was the conflict with b43 that might be preventing the "wl" driver from loading, that problem may get solved too.

So after running the above command, reboot and check -
```
lsmod | egrep 'b43|wl'
```
I hope you should see "wl" this time, and am more hopeful that at least you won't see the "b43" in it this time.

If the "wl" shows up and "b43" doesn't your wireless should be working this time without doing anything.

If the "b43" doesn't show up, but neither does "wl" please run -
```
sudo modprobe -v wl
```
Is wireless active now?

If nothing changes, that is, b43 is still present, and "wl" is not in the lsmod output, please do this -
```
sudo modprobe -rv b43 ssb bcma
sudo modprobe -v wl
```
Wifi should be active now.

Please confirm which of the three cases is applicable and we shall take action accordingly, if needed.

---

### Post by nicole5 on 2014-03-01
It works! Thank you so much!


After taking the b43 off the list and rebooting, this is what I get:
```
$ lsmod | egrep 'b43|wl'
wl                   4207854  0 
cfg80211              526422  1 wl
lib80211               14381  2 lib80211_crypt_tkip,wl
```


I had to disable/enable wireless a couple times for it to connect but I think that's just because the wifi itself is finicky. I sometimes have to do that when I'm on windows too. I rebooted a second time to make sure it was still working and that time it connected to wifi immediately. Again, thank you for helping me and being so patient.

---

### Post by varunendra on 2014-03-01
No problem at all! It's a pleasure to make things work. O:)

---

