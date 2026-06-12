---
title: "TP-Link TL-WDN4800, no wifi connection, Ubuntu 14.04"
date: 2015-01-12
forum: Networking &amp; Wireless
---

### Post by KozaG on 2015-01-12
Hi, 

I don't have wifi connection. Please help. I can find my card with code *lspci -nn -d 10ec:*

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
```

The script give this code

```

########## wireless info START ##########

Report from: 12 Jan 2015 14:00 EET +0200

Booted last: 12 Jan 2015 13:54 EET +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0736 Microsoft Corp. Sidewinder X5 Mouse
Bus 003 Device 004: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 003 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fef9:f35e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX p







ackets:1199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:667140 (667.1 KB)  TX bytes:151214 (151.2 KB)

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
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Region: Europe/Helsinki (based on set time zone)

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by chili555 on 2015-01-12
> Please help. I can find my card with code lspci -nn -d 10ec:

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet 
```This is not your wireless device. It is, as the name implies, your ethernet device. It is working, has a driver and an IP address.

We see no sign of your wireless whatever. Is it properly installed in a PCI slot in the computer? Is it enabled in the BIOS? 

Is this your device? [https://wikidevi.com/wiki/TP-LINK_TL-WDN4800](https://wikidevi.com/wiki/TP-LINK_TL-WDN4800) This reference says the driver is ath9k. It is installed by default in Ubuntu 14.04, so the device should work with no further intervention.

---

### Post by KozaG on 2015-01-12
> **chili555 said:**
> Is this your device? [https://wikidevi.com/wiki/TP-LINK_TL-WDN4800](https://wikidevi.com/wiki/TP-LINK_TL-WDN4800) 

Yes this is the device.

It is properly installed in PCIe slot. But I can't see the device in any distro, Win, Linux, OSX. There must be some problem with the card or somewhere else. How do I enable it in bios?

---

### Post by chili555 on 2015-01-12
I haven't any idea how to enable it in your BIOS; I haven't your computer and, I regret, I'm not familiar with every BIOS that exists, although I try!

I do know that, over the years, I've seen similar issues and, after exhaustive troubleshooting, found that there was an 'Enable Wireless' or some such setting in the BIOS that needed to be set. I suggest you look around the BIOS and check.

It is possible, but I think unlikely, that the device is defective.

If you find no BIOS setting that seems relevant, let's look at the boot messages:```
dmesg > wifi.txt
```Find the file wifi.txt in your user directory and paste it here for our review: [http://paste.ubuntu.com](http://paste.ubuntu.com) Give us the link in your reply.

---

### Post by KozaG on 2015-01-12
I'm sorry I forgot to post here my hardware specs

GIGABYTE GA-H97M-D3M S1150 MATX retail
Intel Core i5-4690K 3.9GHz Socket 1150 Boxed
EVGA GeForce GTX 750Ti Sc 2GB DDR5
Crusial BallistiX Sport Kit 2x8GB DDR3 1600MHz
Corsair Power Supply 500W CX500 80 Plus Bronze
SEA BARRACUDA 1TB 3.5" SATA3 7.2K 64MB
TP-LINK TL-WDN4800 450Mbps Wireless N Dual Band PCI Express Adapter

I can't find anything in that Gigabyte's bios that would relate  anyhow to Wifi.

Here is the pastebin link [http://paste.ubuntu.com/9719157/](http://paste.ubuntu.com/9719157/)

---

### Post by chili555 on 2015-01-12
I see dozens of these:> [    0.000000] *BAD*gran_size: 64K 	chunk_size: 32M 	num_reg: 10  	lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 64K 	chunk_size: 64M 	num_reg: 10  	lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 64K 	chunk_size: 128M 	num_reg: 10  	lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 64K 	chunk_size: 256M 	num_reg: 10  	lose cover RAM: -16M
[    0.000000] *BAD*gran_size: 64K 	chunk_size: 512M 	num_reg: 10  	lose cover RAM: -272M
[    0.000000] *BAD*gran_size: 64K 	chunk_size: 1G 	num_reg: 10  	lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 64K 	chunk_size: 2G 	num_reg: 10  	lose cover RAM: -1280MI am guessing that has something to do with memory. I suggest you Google this and see if you can fix it. 

I looked for '168c,' part of the pci.id for the wireless device and it is not listed at all. By way of comparison, my wireless device is:```
Intel Corporation Centrino Advanced-N 6200 [[COLOR="#FF0000"]8086:4239[/COLOR]] (rev 35)
```If I check my dmesg for '8086,' I see:> pci 0000:03:00.0: [[COLOR="#FF0000"]8086:4239[/COLOR]] type 00 class 0x028000In your case, the device never appears on the PCI bus, at least in any way any operating system recognizes.

Now I suspect either the RAM or the wireless card is defective.

---

### Post by KozaG on 2015-01-12
Whoa. This is above my head. I run Windows and Ubuntu memory check and both showed no error. I assume the card is defective. I'll talk with the seller about this. Thank you alot for the good help!

---

