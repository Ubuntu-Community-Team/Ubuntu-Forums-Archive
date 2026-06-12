---
title: "m1210 dell wireless driver help on gutsy"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by tmac503 on 2008-01-16
I installed gutsy gibbon on my XPS M1210  a couple of days ago and have been trying to use ndiswrapper to get my wireless working with the windows driver. This is the first time I've used linux on my own computer so I'm kind of lost as to what as going on.
My wireless card is Dell Wireless 1505 Draft 802.11n WLAN Mini-Card
hopefully these outputs clue you guys in on where I am

evan@evans-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

evan@evans-laptop:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8B:DC:42:1B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48448 (47.3 KB)  TX bytes:48448 (47.3 KB)

evan@evans-laptop:~/Desktop$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:dc:42:1b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s

evan@evans-laptop:~/Desktop$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4328) present
evan@evans-laptop:~/Desktop$ sudo depmod -a
evan@evans-laptop:~/Desktop$ sudo modprobe ndiswrapper
evan@evans-laptop:~/Desktop$ dmesg | grep ndiswrapper
[ 1960.400000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 1960.420000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1960.420000] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl6'
[ 1960.428000] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[ 1960.436000] usbcore: registered new interface driver ndiswrapper

let me know if more info is needed
thanks

---

### Post by tmac503 on 2008-01-17
sorry about the obnoxious bumping but this could really help with one of my classes
is there a reason why dmesg | grep ndiswrapper doesn't seem to work?

---

### Post by boballen55 on 2008-01-17
I'm pretty new at this too but this site helped me set up my wireless, hasn't failed on me yet:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jpittack on 2008-01-17
A specific guide exists for a dell 1390 wireless card on the forums.  If you download the driver for your specific card, the same steps can be used, and should work for you.

Here is a link to the page. [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

There are reports of this working on many broadcom cards, what Dells wireless cards are.  Don't forget to get the right driver!

---

### Post by boballen55 on 2008-01-17
Ok actually paying attention to all your code there I see it looks like you were doing it right except I never used the
```
dmesg | grep ndiswrapper
```
bit.  Not sure what that is.  sorry not an expert, though I have read that sometimes removing the driver completely and starting again sometimes works.  Other wise go to:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
and see if there is a different driver suggestion for your device.

Sorry I'm not of more help, good luck.

---

