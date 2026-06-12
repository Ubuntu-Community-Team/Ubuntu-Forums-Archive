---
title: "Problems With Wireless Dual Boot D-Link DWA-130"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by nickdlc on 2008-09-13
Hi.

I was so happy when I bought my D-Link DIR-615 Wireless Router and DWA-130 USB Adapter and actually got it working by following instructions on the forums.

Then I decided to Dual Boot my computer with windows XP and now wireless internet only works with windows XP and not Ubuntu. I've tried reinstalling ndiswrapper and the drivers but this has not worked.

I am not sure why the wireless internet works with windows but not with ubuntu, i've searched the forums but nothing seems to work.

This is what I get when I type some commands in the Terminal:

nick@Ubuntu:~$ ndiswrapper -l
rt2870 : driver installed
        device (07D1:3C13) present

nick@Ubuntu:~$ sudo lshw -C Network
[sudo] password for nick:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:20:ed:6e:29:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.198 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:91:23:0f:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.45+Ralink Technology, Corp.,01 link=no multicast=yes wireless=IEEE 802.11g

nick@Ubuntu:~$ dmesg | grep -e ndis -e wlan
[   40.496011] ndiswrapper version 1.45 loaded (smp=yes)
[   41.341585] ndiswrapper: driver rt2870 (Ralink Technology, Corp.,01/31/2008, 1.01.01.0000) loaded
[   43.849068] wlan0: ethernet device 00:21:91:23:0f:a1 using NDIS driver: rt2870, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11n Wireless Card.', 07D1:3C13.F.conf
[   43.849117] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   43.849159] usbcore: registered new interface driver ndiswrapper
[   46.302193] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  443.555698] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  507.426620] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  517.419871] wlan0: no IPv6 routers present
[  565.259080] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  643.200535] ADDRCONF(NETDEV_UP): wlan0: link is not ready

nick@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:ED:6E:29:35  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe6e:2935/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2644687 (2.5 MB)  TX bytes:543889 (531.1 KB)
          Interrupt:17 Base address:0x8f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12363 (12.0 KB)  TX bytes:12363 (12.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:91:23:0F:A1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:168 (168.0 b)

wlan0:ava Link encap:Ethernet  HWaddr 00:21:91:23:0F:A1  
          inet addr:169.254.5.14  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

nick@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It would be great if you guys could help me out as this is really annoying me and I've been able to solve all problems in the past by just searching the forums, but i just can't figure this one out!

---

### Post by nickdlc on 2008-09-15
No one can help me out? I've tried millions of different things and it's driving me crazy.

Thanks

---

### Post by arialys on 2008-10-26
The drivers on the DWA-130 cd do not work with ndiswrapper for some reason. You need to go to the D-Link website and get their drivers. Easily Googleable. You will see that it will ask for your specific version of the device just make sure you have the right one for the right driver, it will give you a zip file. Open that zip, grab the XP driver for whichever you have 64 bit or 32 bit and then wrap that and you should be wonderful again.

Took me a week to figure this out, hope you haven't given up hope on linux yet.

---

