---
title: "Wireless won't associate"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by Winston_Smith on 2008-09-15
I'm trying to setup my wireless, but It won't associate with the AP. I'm using net applet to try and connect.

Here's the information on my card.

Sudo lshw -C Network
```

*-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:70:3e:00:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,02/ latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

iwconfig
```

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ndiswrapper -l
```

bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

```
lsmod | grep ndis
```

ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,hsfosspec,ehci_hcd,uhci_hcd

```

dmesg | grep -e ndis -e wlan
```

[   35.529078] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   35.669856] ndiswrapper: driver bcmwl5 (The Linksys Group, Inc.,02/14/2005, 3.90.36.0) loaded
[   35.678088] ndiswrapper: using IRQ 16
[   35.850259] wlan0: ethernet device 00:1a:70:3e:00:50 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   35.850308] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   35.850379] usbcore: registered new interface driver ndiswrapper
[   35.950504] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   35.950560] udev: renamed network interface wlan0 to wlan1
[  154.777364] ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

Now here's the thing I can manually connect
```

sudo ifconfig wlan1 down
sudo dhclient -r wlan1
sudo ifconfig wlan1 up
sudo iwconfig wlan1 essid "My Wireless AP"
sudo iwconfig wlan1 mode Managed
sudo dhclient wlan1

```

That connects me and I can browse the internet, it also shows as connect in the net applet icon. I switched to net applet because the network manager was not working. But if I hit disconnect then try and reconnect it does not work. 

Let me know if anymore information is needed, i've been trying to get this working myself for about a day now.

---

### Post by Red-Shield on 2008-09-15
sorry to inform you of this but the airforce one card wont work with your distro if you want to use the nm-applet you have to do it manually i had the same one replaced it with the intel wireless mini pro abg i think i payed 23.00 ebay

---

### Post by Winston_Smith on 2008-09-15
Well it's not a huge deal, I'm planning on updating to a Netgear WAG511 so I can use the madwifi drivers and be able to run kismet and other such programs.

---

