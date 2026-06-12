---
title: "network not connecting on reboot, have to remove cable and replug for connection"
date: 2014-07-12
forum: Networking &amp; Wireless
---

### Post by patrick50 on 2014-07-12
Good Evening All!

When I boot my computer the wired network does not work, in the system settings it says unplugged (but it's not) If I disable then enable networking then re-plug the cable it will work every time ( I feel like this is some kind of rain dance ritual ;) ).

I have run the wireless info thing from the sticky post both ways so that you can see if there is anything that is obvious to someone that knows more than I.

Here is the log when it doesn't work:

```



########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux redbearded-X10SLH-F-X10SLM-F 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


05:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
    Subsystem: Super Micro Computer Inc Device [15d9:1533]
    Kernel driver in use: igb
06:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
    Subsystem: Super Micro Computer Inc Device [15d9:1533]
    Kernel driver in use: igb


##### lsusb #####


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 006: ID 0557:2419 ATEN International Co., Ltd 
Bus 003 Device 003: ID 0000:0001  
Bus 003 Device 002: ID 13fd:163e Initio Corporation 
Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### lsmod #####


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            igb
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            igb
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,00:25:90:D6:E2:C5,


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### modinfo #####


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    0.556028] GHES: APEI firmware first mode is enabled by APEI bit and WHEA _OSC.
[    1.921391] igb 0000:06:00.0: eth1: (PCIe:2.5Gb/s:Width x1) <MAC address removed>
[    1.921458] igb 0000:06:00.0: eth1: PBA No: 011000-000
[    4.835624] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.109880] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.110448] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready


########## wireless info END ############


```

and here is the same thing when it does work after doing the rain dance:

```



########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux redbearded-X10SLH-F-X10SLM-F 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


05:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
    Subsystem: Super Micro Computer Inc Device [15d9:1533]
    Kernel driver in use: igb
06:00.0 Ethernet controller [0200]: Intel Corporation I210 Gigabit Network Connection [8086:1533] (rev 03)
    Subsystem: Super Micro Computer Inc Device [15d9:1533]
    Kernel driver in use: igb


##### lsusb #####


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 006: ID 0557:2419 ATEN International Co., Ltd 
Bus 003 Device 003: ID 0000:0001  
Bus 003 Device 002: ID 13fd:163e Initio Corporation 
Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### lsmod #####


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            igb
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            igb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.55
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC address removed>,00:25:90:D6:E2:C5,


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### modinfo #####


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x8086:0x1533 (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #####


[    0.552140] GHES: APEI firmware first mode is enabled by APEI bit and WHEA _OSC.
[    1.917450] igb 0000:06:00.0: eth1: (PCIe:2.5Gb/s:Width x1) <MAC address removed>
[    1.917520] igb 0000:06:00.0: eth1: PBA No: 011000-000
[    5.014083] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.584743] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.585005] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   74.885039] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  999.222278] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready


########## wireless info END ############


```


I attempted to search for answers, but as I have almost zero knowledge on this I did not get far...

Thanks for the help this whole community thing is pretty cool.

Be well,

---

### Post by praseodym on 2014-07-12
> ```
##### resolv.conf #####


nameserver 127.0.1.1
```
There is the difference:
```

sudo apt-get remove resolvconf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
```

---

### Post by patrick50 on 2014-07-12
Thanks for the speedy reply praseodym,

I ran the code you posted and rebooted, the issue still remains. The network cable is still needing to be removed and put back in before the network will connect. Is there anything else I can provide that may help out?

Thanks again for the assistance!

Edit: rebooted again and now it seems to be working properly!!!!! Am I able to donate Beans?

Thanks for the assistance!

WOOT!

---

