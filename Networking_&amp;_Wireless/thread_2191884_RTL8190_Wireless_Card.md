---
title: "RTL8190 Wireless Card"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by brasus on 2013-12-04
I'm having the hardest time trying to get this wireless nic card to work without much of luck. Now this is my 3rd day reading after reading, trying and trying and nothing. I have installed the driver via ndiswrapper and it says that it's install but for some reason I can't get to work. Could someone help. 

Thanks, 
Brasus

net819xp : driver installed
	device (10EC:8190) present

XXXX@XXXX:~$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


usb0      no wireless extensions.

eth0      Link encap:Ethernet   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f0180000-f01a0000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229117 (229.1 KB)  TX bytes:229117 (229.1 KB)


usb0      Link encap:Ethernet    
          inet addr:192.168.42.34  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286611 (286.6 KB)  TX bytes:158236 (158.2 KB)

  *-network UNCLAIMED
       description: Network controller
       product: RTL8190 802.11n Wireless LAN
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:07:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:1100(size=256) memory:f0200000-f0200fff

---

### Post by chili555 on 2013-12-04
Is the module loaded?```
lsmod | grep ndis
```If not, load it and look for errors, warnings, etc.```
sudo modprobe ndiswrapper
```Check the logs for informative messages:```
dmesg | grep ndis
```

---

### Post by brasus on 2013-12-04
rndis_host             14087  0 
cdc_ether              13967  1 rndis_host
usbnet                 37607  2 rndis_host,cdc_ether
ndiswrapper           192828  0

---

### Post by chili555 on 2013-12-04
> **brasus said:**
> rndis_host             14087  0 
cdc_ether              13967  1 rndis_host
usbnet                 37607  2 rndis_host,cdc_ether
ndiswrapper           192828  0Great. How about:```
dmesg | grep ndis
```

---

### Post by brasus on 2013-12-04
[   15.510886] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   16.154359] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   16.154380] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   16.154392] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   16.154403] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   16.154414] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   16.154425] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   16.154436] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   16.154447] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   16.154458] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   16.154469] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   16.154480] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   16.154490] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   16.154501] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   16.154512] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   16.154523] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   16.154551] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   16.154561] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   16.154572] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   16.154588] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   16.154601] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   16.154618] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   16.154628] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   16.154638] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   16.154666] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   16.154676] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   16.154691] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   16.154701] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   16.154712] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   16.154722] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   16.154744] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   16.154750] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net819xp'
[   16.154839] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net819xp'
[   16.154941] usbcore: registered new interface driver ndiswrapper
[ 1155.553876] rndis_host 2-3:1.0 usb0: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 02:52:66:65:69:61
[ 1155.554182] usbcore: registered new interface driver rndis_host

---

### Post by chili555 on 2013-12-04
> [ 16.154750] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net819xp'
[ 16.154839] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net819xp'
[ 16.154941] usbcore: registered new interface driver ndiswrapperWhere did you get the file? Is it XP or Vista or 7 or ... Klingon? 32- or 64-bit?```
arch
```

---

### Post by brasus on 2013-12-04
Chilli I got the file from Realtek (RTL819xP_WindowsDriver_2002.1.0106.2011.F1032.P0703_ISS_1.00.0168.L) 

Win7X86 driver, 32 bit. 

Thanks.

---

### Post by chili555 on 2013-12-04
> Win7X86 driver, 32 bit. However, check here:```
man ndiswrapper-1.9
```> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Windows  [COLOR="#FF0000"]XP[/COLOR] drivers and kernel module to load the Windows [COLOR="#FF0000"]XP[/COLOR] drivers. Both are called ndiswrapper.Would you please try again? Do you need some guidance as to removing the 7 and loading the XP?

EDIT: This might help.

---

### Post by brasus on 2013-12-04
You are the man!!!!! I did all correct based on your information from other post with the most important part...XP Driver only :confused::confused:

Thank you very much :P:P

Attached is the ZIP file that I used to get it to work.

---

### Post by chili555 on 2013-12-04
I assume you are all set! Please mark the thread solved. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

