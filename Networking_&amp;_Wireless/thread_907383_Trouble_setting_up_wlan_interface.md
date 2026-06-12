---
title: "Trouble setting up wlan interface"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by Tweek3d920 on 2008-09-01
Hi, I am running into a strange problem when I try to set up my Trendnet TEW-424ub device. I downloaded and installed ndiswrapper, installed the drivers to it and ran the modprobe command but the wlan interface still doesn't show up. I ran the lsusb command and it says driver present and devie present but still no interface. Please help!

---

### Post by pytheas22 on 2008-09-01
Please post the output of these commands:
```

ndiswrapper -l
lshw -C Network
lsmod | grep ndis
dmesg | grep -e ndis -e wlan
```

---

### Post by Tweek3d920 on 2008-09-02
Ok, here's the results of ndiswrapper -l 

net8187b : driver installed
        device (0BDA:8189) present

results of lshw -C Network

 *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:8a:32:37
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt          00bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 drive         2.0 duplex=full ip=192.168.1.66 latency=64 link=yes module=ssb multicas         t=twisted pair speed=100MB/s


results of dmesg | grep -e ndis -e wlan

[   27.030912] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[   27.462075] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   27.462090] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   27.462101] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   27.462112] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   27.462123] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   27.462134] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   27.462148] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   27.462159] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   27.462171] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   27.462181] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   27.462236] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   27.462251] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   27.462277] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   27.462303] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   27.462319] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   27.462330] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   27.462340] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   27.462351] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   27.462359] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   27.462368] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   27.462372] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net8187b'
[   27.462884] ndiswrapper (load_wrap_driver:118): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[   27.462920] usbcore: registered new interface driver ndiswrapper

results of lsmod | grep ndis

ndiswrapper           193500  0
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd


Thank you for your help!

---

### Post by pytheas22 on 2008-09-02
It looks like ndiswrapper doesn't like the Windows driver that you loaded into it.  Sometimes this happens.  First, remove the Windows driver that you have currently installed:
```

sudo ndiswrapper -r net8187b
```

Then install a better driver.  According to the [ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/"), these are links to ones that should work for your card:

```
ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip
http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true used winXP driver contained in RTL8187B_logo_6.1074.0406_silent_install.zip
```

Also remember that if you're using 64-bit Ubuntu, the Windows driver needs to be for 64-bit Windows.

---

