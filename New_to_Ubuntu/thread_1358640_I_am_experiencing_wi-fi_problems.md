---
title: "I am experiencing wi-fi problems"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Yoaly on 2009-12-18
I only recently installed Ubuntu and experienced some troubles relating to the wireless adapter being unrecognized. After a bit of searching I found Ndiswrapper, it helped Ubuntu recognize the wireless card. Now, when I connect to the wireless router, then onto the internet, it seems as if there is no data transfer. 

when I input sudo lshw -C network I get

  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1d:da:aa
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.67 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f6000000-f6003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1d:d9:dd:85:fb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

When I input iwconfig i get

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE105"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

I have no idea as what any of this means or what I can do with it. Any help would be greatly appreciated.

---

### Post by Some Penguin on 2009-12-18
How are you trying to connect to the wireless router?   Network Manager?  wicd?  wpa_supplicant?

You're not associated with the AP; you first need to figure out why, such as parsing any error messages that are shown when you do try to connect.  You might have the wrong encryption options, you might have the wrong passphrase, you might have neglected to enter your MAC address into the WAP's MAC filtering (if enabled), it might be that you're using WPA with a non-broadcast SSID...

---

### Post by drpjkurian on 2009-12-19
> **Yoaly said:**
> I only recently installed Ubuntu and experienced some troubles relating to the wireless adapter being unrecognized. After a bit of searching I found Ndiswrapper, it helped Ubuntu recognize the wireless card. Now, when I connect to the wireless router, then onto the internet, it seems as if there is no data transfer. 

when I input sudo lshw -C network I get

  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1a:80:1d:da:aa
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.67 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f6000000-f6003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1d:d9:dd:85:fb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fa000000-fa00ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

When I input iwconfig i get

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"2WIRE105"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

I have no idea as what any of this means or what I can do with it. Any help would be greatly appreciated.

Hi Yoaly
Your wireless card appears to be Atheros.
Please try my thread to install Madwifi drivers, Which is a robust one.
I am sure you can solve this issue with ease.

The URL is [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck
Dr Kurian

---

