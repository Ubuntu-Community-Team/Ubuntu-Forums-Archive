---
title: "Ubuntu Edgy w/ D-Link DWL-G510 (B)"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by tohvanah on 2007-03-07
Hi...I've been trying to get wifi to work with Ubuntu in a Dell desktop. After spending a lot of time browsing forums and Ubuntu/MadWifi docs, I've hit a wall. My goal is to have Ubuntu act as a wifi router. 

I've been trying adhoc mode because Master mode froze the computer. Now, with the settings below seem to work ok, however it did freeze/crash Ubuntu when I /etc/init.d/network restart ... 
I'd like to have WEP working (as you can see from the commented line in interfaces). However, I have yet to get my OSX laptop to communicate with WEP. Usually after I load ath0 with a key/encryption enabled, as soon as I connect via my laptop, Ubuntu freezes/crashes (literally the screen is frozen, requiring hard-reset) or they connect, but can't ping (no report of wrong passwd, etc...perhaps because it's adhoc?)... 

I just upgraded to Edgy from Dapper thinking with the new version of madwifi my problems would be solved, but now it crashes harder more often....help! 

Thank you!

** Info on my card from lshw:
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@02:0b.0
       logical name: wifi0
       version: 01
       serial: 00:11:95:f9:56:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.2.1) ip=10.1.1.3 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ff9e0000-ff9effff irq:3

** from lspci:
02:0b.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
        Flags: bus master, medium devsel, latency 168, IRQ 3
        Memory at ff9e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

** ath0 config in /etc/network/interfaces:
iface ath0 inet static
        address 10.1.1.3
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        post-down wlanconfig ath0 destroy
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
#        pre-up iwconfig ath0 key 382e4b7529
        pre-up ifconfig ath0 up
        pre-up iwconfig ath0 essid intuit rate 54M mode ad-hoc

auto ath0

** haven't noticed anything of signifigance in syslog, but here are relevant greps:
[17179592.776000] ath_hal: module license 'Proprietary' taints kernel.
[17179592.780000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179593.236000] ath_rate_sample: 1.2 (0.9.2.1)
[17179593.252000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179618.956000] ath0: no IPv6 routers present
[17180280.156000] ath0: no IPv6 routers present
[17180335.616000] ath0: no IPv6 routers present
**and:
[17179594.428000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179594.428000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179594.428000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179594.428000] wifi0: mac 7.8 phy 4.5 radio 5.6
[17179594.428000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179594.428000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179594.428000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179594.428000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179594.428000] wifi0: Use hw queue 8 for CAB traffic
[17179594.428000] wifi0: Use hw queue 9 for beacons
[17179594.564000] wifi0: Atheros 5212: mem=0xff9e0000, irq=3

---

### Post by tohvanah on 2007-03-09
So I seem to have found a stable "solution" for my goals of a wireless network w/WEP.

I've set up OS X on my laptop to be the AP, and Ubuntu as a regular client. This is the only set up I've found where these machines were able to communicate w/any kind of security enabled...or without Ubuntu crashing (Adhoc w/WEP or any Master)

Also, does anyone have an idea why my wireless interface doesn't come up on boot? I havn't found any error messages, and it loads find normally after boot...

**/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

iface ath0 inet static
        pre-up /etc/network/athwifi.sh
        address 10.1.1.3
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        post-down wlanconfig ath0 destroy
auto ath0


**/etc/network/athwifi.sh:
#!/bin/sh
sudo ifconfig ath0 down

sudo wlanconfig ath0 destroy
sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed

sudo iwconfig ath0 key xxxxxxxxxx
sudo iwpriv ath0 authmode 2
sudo ifconfig ath0 up
sudo iwconfig ath0 essid peaceful rate 54M mode managed ap xx:xx:xx:xx:xx:xx

---

### Post by tetobear on 2007-03-11
Hi i had the same issue with the WEP key
and the command
sudo iwpriv ath0 authmode 2

seems the key of the key LOL

so now where i can add that somewhere to get it loaded on the boot?

---

### Post by cmichaelboyd on 2007-04-15
Add those lines to your "/etc/rc.local" file.

They'll be run last after every other service has started up.

cheers,

Chris

---

