---
title: "Hp Dv6206us"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by beakerman30 on 2007-05-29
Intereseting question... I have an HP Pavillion dv6000 (dv6206us) to be precise I downloaded the wireless card drivers from HP site SP34488.exe and extracted them to my desktop. I installed the drivers using the ndiswrapper command and did a ndiswrapper -l to check that the card and driver were functioning. I get a thumbs up from that. I rebooted and still no wireless functionality. The card was not originally detected by ubuntu when I installed so i am wondering if I need to somehow add the interface. I tried a ifconfig and don't see the wireless listed. Any help you can provide would be appreciated.

Matthew
:o

---

### Post by jcaveman on 2007-05-30
Did the ndiswrapper kernel module load?  Do an lsmod and see if ndiswrapper is listed.  If not, type:

sudo modprobe ndiswrapper

Then try an ifconfig

---

### Post by beakerman30 on 2007-06-05
Okay I tried the commands you suggested the lsmod shows ndiswrapper as being loaded I do notice some errors in the background when my system comes up related to ndiswrapper. Maybe I should try an older version of ndis wrapper ?? or can I investigate these errors in a log somewhere. the errors are occuring during boot

Matthew

---

### Post by chili555 on 2007-06-05
> can I investigate these errors in a log somewhere```
sudo cat /var/log/messages | grep ndis
dmesg | grep ndis
```

---

### Post by beakerman30 on 2007-06-05
here is the output

229.920000] ndiswrapper version 1.38 loaded (preempt=no,smp=no)
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateM
dl'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegister
MiniportDriver'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetMinip
ortAttributes'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMGetBusDa
ta'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegister
ScatterGatherDma'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBu
fferList'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMRegister
InterruptEx'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMOidReque
stComplete'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateI
oWorkItem'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisQueueIoWo
rkItem'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateM
emoryWithTagPriority'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSetBusDa
ta'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateN
etBufferAndNetBufferList'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisAllocateN
etBufferListPool'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregist
erInterruptEx'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregist            erMiniportDriver'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMDeregist            erScatterGatherDma'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeNetBu            fferListPool'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisOpenConfi            gurationEx'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisFreeIoWor            kItem'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSendNetB            ufferListsComplete'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMSynchron            izeWithInterruptEx'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicate            StatusEx'
[  230.000000] ndiswrapper (import:245): unknown symbol: NDIS.SYS:'NdisMIndicate            ReceiveNetBufferLists'
[  230.000000] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl6            '
[  230.000000] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl6;             check system log for messages from 'loadndisdriver'
[  230.004000] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2007-06-05
Although I am no ndiswrapper expert, I believe SP34488.exe is the Vista driver. I think you will have better luck with the XP driver.

You may have even better luck removing ndiswrapper and going here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by beakerman30 on 2007-06-06
I followed the link instructions and downloaded the script and installed and Holy macaroni and cheese it works it works ! LOL thanks 
:popcorn:

---

