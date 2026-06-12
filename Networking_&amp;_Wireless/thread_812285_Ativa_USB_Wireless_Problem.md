---
title: "Ativa USB Wireless Problem"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by dlmoak on 2008-05-29
OK, I'm a new user - 64 bit Ubuntu 8.04  Core 2 Duo e8400 w/4 gigs of ram
wired network functions properly
I connected an Ativa Wireless G USB adapter because it is in the supported list, but I am missing something simple here (I hope).
1. **iwlistscan shows my wireless network:**
eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:C3:E1:C7
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=5/100  
                    Extra: Last beacon: 16ms ago
2. **lshw shows the wireless usb adapter**
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:6b:cd:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
3. **lsusb shows the Ativa(Belkin) USB adapter**
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 050d:705c Belkin Components 
Bus 005 Device 001: ID 0000:0000 
4. **dmseg shows the following (which I don't understand)**
[   54.656318] eth0: no IPv6 routers present
[   55.196041] eth1: no IPv6 routers present
[ 2226.495112] UDF-fs: No VRS found
[ 2226.522397] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2226.523433] ISOFS: changing to secondary root
[ 2350.363702] usb 5-6: USB disconnect, address 3
[ 2350.374173] zd1211rw 5-6:1.0: error ioread32(CR_REG1): -22
[ 2914.412812] usb 5-8: new high speed USB device using ehci_hcd and address 4
[ 2914.545551] usb 5-8: configuration #1 chosen from 1 choice
[ 2914.660705] usb 5-8: reset high speed USB device using ehci_hcd and address 4
[ 2914.794389] zd1211rw 5-8:1.0: eth1
[ 2914.846220] zd1211rw 5-8:1.0: firmware version 4725
[ 2914.886205] zd1211rw 5-8:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
[ 2914.907033] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2915.276538] SoftMAC: Open Authentication completed with 00:0f:66:c3:e1:c7
[ 2915.316080] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2925.439152] eth1: no IPv6 routers present
5. System>Administration>Network Tools shows:
[IMG]http://www.mabie-todd.com/networktools.png[/IMG]

So it looks like it can't receive.
My wireless router is a Linksys Wireless G 2.4 model WRT54G Ver. 2

---

### Post by dlmoak on 2008-05-29
**[SIZE="5"]OOPS![/SIZE]**

Apparently a reboot solved the problem ](*,)

---

