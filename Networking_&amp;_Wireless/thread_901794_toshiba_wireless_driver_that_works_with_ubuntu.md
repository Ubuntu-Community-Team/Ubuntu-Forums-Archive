---
title: "toshiba wireless driver that works with ubuntu?"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by rustyray on 2008-08-26
hi there. i am new to ubuntu as i just changed my OS from vista. i am using a toshiba equium p200-178 with an in-built Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. Unfortunately, my wireless drives are not detecting the device despite that it claims that both drivers and device are present. no matter the driver i install, i.e. madwifi, atheros drivers etc, networking does not provide any wireless networking option, nor does it detect the wireless network of my home router. does anybody know how i can make the device work or does any one know of a compatable wireless pci express card that will work with my toshiba model? please help me out. Thanks  :popcorn:

---

### Post by Zer0Nin3r on 2008-08-26
I'm disappointed to hear your problems as I have the same problems with my Toshiba laptop.  I have a U405D-S2852 from Best Buy.  Bought it as my Compaq R3000's power converter crapped out on me the other week (the  beast used 120w!!)  Anyway, thought Toshiba would work with Ubuntu right out of the box.  Everything except networking that is.  Even wired isn't recognized!!

I was going to go the routes of MadWiFi, but it looks like it's a dead end.  Have you tried ndiswrapper?

---

### Post by enternet1988 on 2008-08-26
Yeah I am in the same boat, I have a Toshiba laptop and pretty much everything else works except the wireless, Dam Wires

---

### Post by rustyray on 2008-08-28
i am really disappointed with Toshiba now. it seems that i am not the only one with this problem. i have even tried ndiswrapper and it doesn't work. :( i don't know wat to do man. hope we get a solution soon though.:)

if i am unable to sort out the wireless problem internally, does anyone know any other wireless devices preferably express pci card device?
thanks a bunch

---

### Post by cybrsaylr on 2008-08-29
I have a 5 month old Toshiba laptop that had wireless working great until an Ubuntu upgrade 2 days ago that knocked out all wireless networks. I've tried a numbers of fixes so far but still have no wireless only a wired connection.

---

### Post by homeboy2kfun on 2008-09-01
im so lost can you help me

---

### Post by dmizer on 2008-09-01
Rustyray, your problem is not Toshiba. You just need to get your wireless card configured correctly.

Try looking here: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by rustyray on 2008-09-01
thanks man. i'll try that:KS

---

### Post by rustyray on 2008-09-14
i have tried several times with the different ideas that the furom offered but i am still in the same boat.
when i check my dmesg output as well, i get this result.

root@reindolf-laptop:/home/reindolf# dmesg | grep -e ndis -e wlan
[   43.766283] wlan: 0.9.4
[   46.887362] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   47.028502] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   47.028514] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   47.028521] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   47.028612] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   47.028621] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   47.028630] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   47.028639] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   47.028648] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   47.028670] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   47.028681] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   47.028694] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   47.028703] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   47.028715] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   47.028725] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   47.028736] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   47.028745] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   47.028762] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   47.028771] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   47.028802] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   47.028811] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   47.028820] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   47.028829] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   47.028838] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   47.028847] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   47.028858] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   47.028867] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   47.028876] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   47.028888] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   47.028897] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   47.028909] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   47.028918] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   47.028927] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   47.028936] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   47.028945] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   47.028955] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   47.028964] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   47.028973] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   47.028982] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   47.028986] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathr'
[   47.029532] ndiswrapper (load_wrap_driver:108): couldn't load driver netathr; check system log for messages from 'loadndisdriver'
[   47.029597] usbcore: registered new interface driver ndiswrapper
root@reindolf-laptop:/home/reindolf# 


can anybody please tell me what this means and what else i can try?
thanx

---

### Post by fmartinez on 2008-09-14
I have a Toshiba Satellite A215 S4747 with an Atheros card and followed this install: 
[http://kankman.org/atherosinstall.html](http://kankman.org/atherosinstall.html)

and it worked flawless afterwards. 
let me know what you think of the tutorial.

---

### Post by rustyray on 2008-09-16
thanx mate. will try that as well.:KS

---

### Post by rustyray on 2008-09-19
guys, fmartinez's method worked for me. thanks again fam. i now can connect wirelessly. however, it worked very well the first time i fixed the problem but after a while, my computer will claim an excellent connection but will not send or recieve info over the net. i tried restarting both pc and router but everyone else in my house gets a good connection except me. i know that the router is not the problem so what settings have i not done properly? why did it work then suddenly stopped communicating? and what can i do to rectify this problem?

thanks:popcorn:

---

### Post by -M-ric on 2009-05-29
Hi all,

I just checked [http://kankman.org/atherosinstall](http://kankman.org/atherosinstall) URL and it seems to be not valid anymore. I am very interested on running Wireless on Toshiba laptop since I will have to install Ubuntu on this kind of laptop soon. Does anyone know a tutorial URL for atheros? I found a lot of broken links throughout google search.

---

