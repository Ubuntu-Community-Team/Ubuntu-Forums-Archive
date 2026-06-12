---
title: "WNA3100 Issues on Ubuntu 12.04 LTS"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by CXtHdHh on 2013-10-22
Hi,

Yesterday I decided that I would install Ubuntu on my old Dell PC. Having read some forums and seen that my Netgear WNA3100 wireless usb card should work with linux I decided to use that rather than try and provide a wired connection to my PC. I managed to install the 'bcmwlhigh5' drivers which are needed for this card, and it can see my wireless networks and attempt to connect to them.

The system usually connects to the network on startup with ease, but after about 2-5 minutes the connection will just drop (although it claims to still be connected on the status bar at the top) and I can no longer ping the router or receive an internet connection of any type. If I disconnect from the network and try to reconnect then it will just keep trying to connect and never succeed.

This isn't my first experience with linux but by no means am I an expert and I would really appreciate some help with this please :)

Matt

---

### Post by varunendra on 2013-10-23
Hello Matt, Welcome to the forums !

> **CXtHdHh said:**
> ..I managed to install the 'bcmwlhigh5' drivers which are needed for this card

I never heard of that driver, where did you get it from?

As for the current situation, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Run it when the USB adapter is plugged in and you are connected.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by jokodude on 2013-12-03
I am having the exact same issues.  I got the WNA3100 wireless usb working using using ndiswrapper and using the bcmwlhigh5.inf driver as the input for the program.  From there, the internet works fine as long as I don't start downloading a decent amount of content.  But even a picture or a 10 MB download can screw the internet up and it will disconnect me.  I then have to unplug the usb wireless adapter and plug it back in.  I am attaching the wireless script output Varun referred to in his previous post.  If you can find an answer to this problem among here it would be appreciated.

```
*************** info trace ***************

***** uname -a *****

Linux josh-Z68XP-UD3 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC [10ec:8169]
    Kernel driver in use: r8169
    Kernel modules: r8169
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 002: ID 1532:0015 Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 002 Device 005: ID 0665:6000 Cypress Semiconductor 
Bus 002 Device 006: ID 1044:7a03 Chu Yuen Enterprise Co., Ltd 

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11g  ESSID:"JSHKEI"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=72 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****


***** lsmod *****

ndiswrapper           197073  0 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [JSHKEI] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Fisher:          Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 40 WPA
    Tesla:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA
    *JSHKEI:         Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 51 WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



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
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"JSHKEI"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00064A53484B4549
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A0001101044000102104700109763C159AFE4879AABD1E6F5CCC018F9103C0001031049000600372A000120
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD890050F204104A0001101044000102103B000103104700109763C159AFE4879AABD1E6F5CCC018F91021000D4E4554474541522C20496E632E1023000A574E44523334303076331024000A574E44523334303076331042000230311054000800060050F20400011011000A574E4452333430307633100800020004103C0001031049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    ESSID:"2WIRE519"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00083257495245353139
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 03 - Address: <MAC address removed>
                    ESSID:"Fisher"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0006466973686572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405080800000000000000000000000000000000000000
                    IE: Unknown: 3D1605080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000000000000100000001C7EE540158E10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363135100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 04 - Address: <MAC address removed>
                    ESSID:"Tesla"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00055465736C61
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-29-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     61EDC02F8B884C063E14A06
depends:        
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/0000:04:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.6/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0846:0x9020 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    1.139693] r8169 0000:07:00.0 eth1: RTL8168evl/8111evl at 0xf843a000, <MAC address removed>, XID 0c900800 IRQ 44
[    1.139694] r8169 0000:07:00.0 eth1: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    6.038477] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    8.046804] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[    8.438994] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[    9.025621] wlan0: ethernet device <MAC address removed> using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[    9.029719] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   17.890896] r8169 0000:07:00.0 eth1: link down
[   17.890940] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.891281] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.960380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.960546] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.770211] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************


```

---

### Post by varunendra on 2013-12-04
Welcome to the forums jokodude !

The signal strength doesn't look good. How far you are from the router/access-point?

I suggest trying a 'Fixed' lower speed as a test -
```
sudo iwconfig wlan0 rate 12M
```
This is a very low speed, but if it proves to help the stability of the connection, we can try notching it up as long as the stability is maintained.

I hope you understand that the windows driver with ndiswrapper is not going to perform as good as it would when working natively on windows. So if possible, try this where the signal strength is relatively stronger.

---

### Post by jokodude on 2013-12-04
I am down 1 floor and the material between the signal and the usb adapter is wood.  I would say the distance is 25 meters max, maybe closer to 15-20m.  The router being used is a netgear WNDR3400v3.  I turned down the wireless speed from max to g type thinking there might be an issue with it connecting to an n speed signal, and the output i showed is with the speed turned down.  I'm guessing if I brought the signal speed back up it should also increase the signal strength.  Let me go ahead and do that change and also run the code you sent me.  Is there any output i should give you after I've done that?
 
 [FONT=Arial][COLOR=#ffffff]** d**[/COLOR][/FONT]

---

### Post by varunendra on 2013-12-04
The result of the command I suggested can be tested only by practical usage, posting back the output won't be of much help. But if it fails to make the connection stable, just post back a fresh report of the wireless_script, along with an output of -
```
ifconfig
```

If it does make the connection stable, you can also try "18M" instead of 12M in the iwconfig command to step it up. The "iwlist scan" part doesn't show any higher supported speeds, maybe a typical thing with ndiswrapper, but usually the supported speeds on a g-band router are 12, 18, 24, 36, 48 and 54 Mbps (54 Mbps is the limit of g-band). So you can also try fixing the speed at these values.

To reset the speed to "auto", use -
```
sudo iwconfig wlan0 rate auto
```

I don't think enabling n-channel is going to improve the signal strength, but then I don't have any idea how a windows driver on ndiswrapper may behave in different situations. So go ahead, try and see for yourself.

---

### Post by chili555 on 2013-12-04
>  I turned down the wireless speed from max to g type thinking there might be an issue with it connecting to an n speed signal, and the output i showed is with the speed turned down.But then:> wlan0     IEEE 802.11g  ESSID:"JSHKEI"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          [COLOR="#FF0000"]Bit Rate=72 Mb/s [/COLOR]  Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBmSo it's still at N speeds, isn't it? I'd try without.

---

