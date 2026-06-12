---
title: "USB sitecom TW-169: installed though no connection"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by rickmans on 2008-08-31
I habe an USB sitecom TW-169 that should be to connect my local to my wireless network. With the help of ndiswrapper I installed the windows driver and the device was recognized. Alsi my wireless network became visible. However when I try to connect to it, it won't connect.

Anybody an idea how to make this work?

Some info from my system:
```
rick@servert:~$ ndiswrapper -l
net8187b : driver installed
    device (0DF6:002A) present
netrtuw : driver installed

``````

rick@servert:~$ lsusb
Bus 005 Device 007: ID 0df6:002a Sitecom Europe B.V. 
Bus 005 Device 005: ID 0566:3013 Monterey International Corp. 
Bus 005 Device 003: ID 0566:3020 Monterey International Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c046 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
``````

rick@servert:~$ uname -m
i686
``````

rick@servert:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:13:d4:0e:15:e2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth1
       version: 85
       serial: 00:40:f4:60:4c:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:f6:41:ce:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. multicast=yes wireless=IEEE 802.11g
rick@servert:~$ dmesg | grep -e ndis -e wlan
[   61.838201] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   62.390658] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[   65.911271] wlan0: ethernet device 00:0c:f6:41:ce:67 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0DF6:002A.F.conf
[   65.911355] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   65.911440] usbcore: registered new interface driver ndiswrapper
[   95.911377] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  229.867636] usbcore: deregistering interface driver ndiswrapper
[  229.930655] ndiswrapper: device wlan0 removed
[  229.961095] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  230.282704] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[  233.812920] wlan0: ethernet device 00:0c:f6:41:ce:67 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0DF6:002A.F.conf
[  233.813452] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  233.813751] usbcore: registered new interface driver ndiswrapper
[  645.140517] usbcore: deregistering interface driver ndiswrapper
[  645.338261] ndiswrapper: device wlan0 removed
[  645.376572] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  645.674904] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  645.674920] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  645.674932] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  645.674943] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  645.674953] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  645.674964] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  645.674979] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  645.674990] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  645.675001] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  645.675012] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  645.675072] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  645.675086] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  645.675115] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  645.675143] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  645.675160] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  645.675170] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  645.675181] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  645.675192] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  645.675199] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  645.675206] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  645.675209] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
[  645.679069] ndiswrapper (load_wrap_driver:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[  645.679101] usbcore: registered new interface driver ndiswrapper
[  714.455702] usbcore: deregistering interface driver ndiswrapper
[  714.457067] ndiswrapper (ntoskernel_exit:2708): object f19ff320(2) was not freed, freeing it now
[  714.482849] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  714.496190] usbcore: registered new interface driver ndiswrapper
[  723.643851] usbcore: deregistering interface driver ndiswrapper
[  723.670524] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  723.929692] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[  727.459661] wlan0: ethernet device 00:0c:f6:41:ce:67 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0DF6:002A.F.conf
[  727.460076] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  727.460378] usbcore: registered new interface driver ndiswrapper
[  979.714536] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1132.652371] ndiswrapper: device wlan0 removed
[ 1147.130239] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[ 1150.660329] wlan0: ethernet device 00:0c:f6:41:ce:67 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0DF6:002A.F.conf
[ 1150.660767] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1660.962364] ndiswrapper: device wlan0 removed
[ 2106.200066] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded
[ 2109.733807] wlan0: ethernet device 00:0c:f6:41:ce:67 using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0DF6:002A.F.conf
[ 2109.734218] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
```

---

### Post by rickmans on 2008-09-01
*bump*.

---

### Post by rickmans on 2008-09-03
nobody?

---

### Post by dekatvandeburen on 2011-01-02
Hi All!

Not sure whether this is the proper thread to post this solution in, but it is the only one I could find that was specifically on the Sitecom TW-169 wireless adapter. :)

After a lot of fiddling around, I got this adapter to work (on Ubuntu 10.10) with NDIS wrapper.

Going through the installed files for this adapter in WinXP, I only found a .sys file, but the NDIS wrapper needs a .inf file.
Thanks to the info in [this post]("http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/") I figured out I might be able to use the Realtek Driver for the chipset RTL8187, since the sitecom adapter uses this chipset.
 I downloaded [this driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") from the Realtek support site. (That page shows several drivers, scroll down for the 8187B driver..)
Then, I tried using this driver in NDIS wrapper, but it reported "Hardware present: No". 

I was stumped for a while, but finally thought about the fact that the Sitecom device might have a different hardware id. So I used
```
lsusb
```to find the hardware id for my device. In my case this came back with:
```
Bus 001 Device 006: ID 0df6:002a Sitecom Europe B.V. 
```Then I opened up the .inf file (from the Realtek driver package) and changed the hardware id references to match my hardware. In my case this meant changing
```
USB\VID_0BDA&PID_8187&REV_0200
```into
```
USB\VID_0DF6&PID_002A&REV_0200
```for every occurence in the .inf file (except the line that starts with "ExcludeFromSelect").

After removing and installing the driver again (via the NDIS wrapper GUI) it reported "Hardware present: Yes" ! 

I am posting this reply via the Sitecom TW-169 connected to my home wireless network, so it seems to be working well :)

Hope this helps anyone who might be struggling to get this USB Wireless adapter to work with Ubuntu!

---

