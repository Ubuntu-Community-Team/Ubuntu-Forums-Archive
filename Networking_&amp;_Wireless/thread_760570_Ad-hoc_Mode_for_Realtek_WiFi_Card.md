---
title: "Ad-hoc Mode for Realtek WiFi Card"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by MrQuincle on 2008-04-20
Hi all!

On my mobo, an Asus P5N32, I've some problems with setting it up in an ad-hoc mode (Ubuntu 7.10). It's already connected to the internet by a cable. But I would like to use the WIFI antenna that comes with it, as a means to connect to the internet by it. So that I can use my laptop outside, and have a connection to this PC (or even better a Remote Deskop).

My problem is that I can't make the Ad-Hoc mode to work. It is described in the Asus WiFi-AP Solo user guide that comes with it, but that's only for Windows.

So, let me start with figuring out which card/chip/board is inside:
```

$ lspci | grep thernet

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Okay, so that's Realtek. Additional confirmation:

```

$lsusb

Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0932:1100 Crescentec Corp. 
Bus 002 Device 001: ID 0000:0000  

```

Okay, so it should be somewhere added to my kernel, if it is an build-in driver. And that seems indeed the case.

```

$lsmod | grep 8187

rtl8187                35328  0 
mac80211              171016  2 rc80211_simple,rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  6 snd_usb_audio,rtl8187,snd_usb_lib,ehci_hcd,ohci_hcd

```

If I check it in a "managed" mode, it seems to work:

```

$sudo iwconfig wlan0 essid "freaky-network-name" mode managed
$sudo ifup wlan0
$sudo iwlist wlan0 scanning

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F6:03:70:BC
                    ESSID:"SomeNetworkInMyNeighbourhood"

```
I have no wireless router, so I didn't check if a real connection can be made, but I figure that wont be a problem. So, now I want to continue to the "ad-hoc" mode. I have first to shutdown the interface by ifdown, or I will get an error message "Error for wireless request "Set Mode" (8B06)", with "Device or resource busy". Hence, the first command.

```

$sudo ifdown wlan0
$sudo iwconfig wlan0 essid "cozy-network-name" mode ad-hoc channel 11
$sudo ifup wlan0 --verbose

Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/bridge
run-parts: executing /etc/network/if-pre-up.d/vde
run-parts: executing /etc/network/if-pre-up.d/vde2
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
SIOCSIFFLAGS: Operation not supported
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

ifconfig wlan0 172.19.3.90 netmask 255.255.255.0                up
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
Failed to bring up wlan0.

```

Now I am quite clueless how to make this work, and where I can find the reason for those "Operation not supported" errors.

In dmesg there are sentences like, dont know if that says something useful:
```

[14062.935366] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14114.156572] wlan0: Trigger new scan to find an IBSS to join

```

FYI:
```

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth2
       version: 10
       serial: 00:02:44:2d:80:63
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=172.19.3.100 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0b:aa:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.19.3.90 multicast=yes wireless=IEEE 802.11g

```
Yes, it is not configured, I already knew... :-(

If anyone has made this work I would really appreciate to hear if you encountered some problems or not. And anyone that may have some ideas about in which direction I have to find it, I'd appreciate it very much.

I think the default driver is installed correctly, and that it is only a matter of settings. 

Regards!

---

