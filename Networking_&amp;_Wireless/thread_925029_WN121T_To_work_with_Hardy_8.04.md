---
title: "WN121T To work with Hardy 8.04"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by fred_200 on 2008-09-20
Dear All ! 

For the first time I cant find a solution to my problem. 

Im running Hardy 8.04 64 bit. and I try to get my Wireless usb card, Netgear WN121T to work. 

I have tried a lot of the tips but this is the reults i get: 

**Output of: lsusb:** 
Bus 004 Device 002: ID 0846:7100 NetGear, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c50c Logitech, Inc. 
Bus 001 Device 003: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 001: ID 0000:0000  

**Output of: iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

**Output of:  ndiswrapper -m**
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

Output of:  dmesg | grep ndiswrapper

[   28.050088] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.477645] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   28.477651] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netmw245'
[   28.478153] ndiswrapper (load_wrap_driver:112): couldn't load driver netmw245; check system log for messages from 'loadndisdriver'
[   28.478186] usbcore: registered new interface driver ndiswrapper
[  545.379371] usbcore: deregistering interface driver ndiswrapper
[  545.379849] ndiswrapper (ntoskernel_exit:2708): object ffff8100739f9c30(2) was not freed, freeing it now
[  545.390656] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  545.501691] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  545.501715] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  545.501721] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  545.501727] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  545.501750] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  545.501760] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  545.501768] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  545.501773] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  545.501779] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  545.501785] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  545.501791] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  545.501796] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[  545.501802] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  545.501807] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  545.501812] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[  545.501818] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  545.501824] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[  545.501839] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[  545.501845] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[  545.501851] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[  545.501856] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  545.501866] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  545.501877] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  545.501884] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  545.501889] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  545.501891] ndiswrapper (load_sys_files:210): couldn't prepare driver 'wn111x'
[  545.504653] ndiswrapper (load_wrap_driver:112): couldn't load driver wn111x; check system log for messages from 'loadndisdriver'
[  545.504676] usbcore: registered new interface driver ndiswrapper
[  638.728041] usbcore: deregistering interface driver ndiswrapper
[  638.728599] ndiswrapper (ntoskernel_exit:2708): object ffff8100739f9c30(2) was not freed, freeing it now
[  638.738494] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  638.753530] usbcore: registered new interface driver ndiswrapper
[  641.920534] usbcore: deregistering interface driver ndiswrapper
[  641.931657] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  641.946284] usbcore: registered new interface driver ndiswrapper
[  647.101921] usbcore: deregistering interface driver ndiswrapper
[  647.111178] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  647.340588] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  647.340598] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netmw245'
[  647.341188] ndiswrapper (load_wrap_driver:112): couldn't load driver netmw245; check system log for messages from 'loadndisdriver'
[  647.341220] usbcore: registered new interface driver ndiswrapper

**output of: sudo ndiswrapper -l**
netmw245 : driver installed
	device (0846:7100) present


It seems like thee driver is wrong, but i have tested all that ive found...[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
Anyone who has a clue of what is wrong ?

---

