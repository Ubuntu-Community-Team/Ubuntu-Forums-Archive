---
title: "Ralink 5390sta driver does not build on kernel 3.12.7"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by ukbeast on 2014-01-11
I am on ubuntu 13.10 with kernel 3.12.7

I don't like using the rt2800pci driver that comes with ubuntu due to low signal.
I have tried to use Ralink rt5390sta driver but it fails to compile 

/home/ukbeast/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.c:1129:20: error: incompatible types when assigning to type ‘int’ from type ‘kgid_t’
   pOSFSInfo->fsgid = current_fsgid();
                    ^
make[2]: *** [/home/ukbeast/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/ukbeast/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.12.7-031207-generic'
make: *** [LINUX] Error 2
ukbeast@ASUSTeK:~/2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ 

I have patched it with rt5592sta_fix_64bit_3.8.patch.

that only works on older kernels

---

### Post by ukbeast on 2014-01-13
Bump
The patch is [http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch](http://gridlox.net/diff/rt5592sta_fix_64bit_3.8.patch)

---

### Post by chili555 on 2014-01-13
If you are running kernel 3.12.7, then you are running a much newer version of the driver than this old-timer:> [COLOR="#FF0000"]2011[/COLOR]_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPOWe no longer use wooden wheels on our sleek black BMWs! 

I think you have three options: first, tweak the available driver parameters in rt2800pci to try to improve performance. ```
modinfo rt2800pci
```Second, compile this: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13-rc2/backports-3.13-rc2-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13-rc2/backports-3.13-rc2-1.tar.bz2) It is a little tricky, so if you need guidance, I'll be happy to help.

Third, get a crowbar and rip out the wireless device and get a new one, preferably not a rt2800pci!

---

### Post by ukbeast on 2014-01-13
I've installed the backport (filename:       /lib/modules/3.12.7-031207-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
version:        backported from Linux (next-20131206-0-gc0a1029) using backports backports-20131206-0-g0cca7ab)

still weak signal. I will try ndiswrapper with rt5390sta windows driver

---

### Post by ukbeast on 2014-01-13
No luck 
>  dmesg | grep ndis
[   12.231288] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   12.232420] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.068198] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[   13.069323] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit'
[   13.070329] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   13.071403] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   13.072500] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   13.073628] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   13.074759] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopySendNetBufferListInfo'
[   13.075977] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   13.077240] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   13.078424] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   13.079570] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   13.080665] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   13.081733] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   13.082861] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   13.083956] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   13.085011] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   13.086121] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   13.087281] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   13.088496] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   13.089501] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   13.090670] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   13.091861] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   13.092887] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   13.094107] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   13.095215] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   13.096241] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   13.097377] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   13.098450] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   13.099606] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   13.100717] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   13.101806] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   13.102951] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   13.103927] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   13.105171] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   13.106388] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   13.107583] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   13.108606] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   13.109650] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   13.110861] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   13.112154] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   13.113316] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   13.114370] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netr28x'
[   13.115949] ndiswrapper (load_wrap_driver:103): couldn't load driver netr28x; check system log for messages from 'loadndisdriver'
[   13.121293] usbcore: registered new interface driver ndiswrapper
[  147.835196] usbcore: deregistering interface driver ndiswrapper
[  147.844225] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  147.855654] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit


I even blacklisted rt2800pci driver

---

### Post by chili555 on 2014-01-13
> **ukbeast said:**
> No luck 


I even blacklisted rt2800pci driverDid you use the x64 (I assume you are running 64-bit on your sleek black system) and Windows XP .inf and .sys files? XP is specified by ndiswrapper:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Win&#8208;
       dows  XP drivers and kernel module to load the Windows XP drivers. Both
       are called ndiswrapper.

---

### Post by chili555 on 2014-01-13
> **ukbeast said:**
> I've installed the backport (filename:       /lib/modules/3.12.7-031207-generic/updates/drivers/net/wireless/rt2x00/rt2800pci.ko
version:        backported from Linux (next-20131206-0-gc0a1029) using backports backports-20131206-0-g0cca7ab)

still weak signal. I will try ndiswrapper with rt5390sta windows driverMy link was to 3.13-rc2-1. Did you try that? Did you try options rt2800pci nohwcrypt=Y?

---

### Post by ukbeast on 2014-01-13
~$ ndiswrapper -l
netr28x : driver installed
    device (1814:5390) present (alternate driver: rt5390sta)

 339.977964] usbcore: registered new interface driver ndiswrapper
[ 2823.280430] usbcore: deregistering interface driver ndiswrapper
[ 2823.291637] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 2823.301812] usbcore: registered new interface driver ndiswrapper
[ 2975.135534] usbcore: deregistering interface driver ndiswrapper
[ 2977.329478] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 2977.342039] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit'
[ 2977.342049] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[ 2977.342062] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeSetCoalescableTimer'
[ 2977.342072] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 2977.342077] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 2977.342087] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 2977.342093] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 2977.342098] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 2977.342104] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 2977.342109] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopySendNetBufferListInfo'
[ 2977.342115] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 2977.342120] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 2977.342126] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 2977.342132] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 2977.342137] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 2977.342143] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 2977.342163] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 2977.342169] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 2977.342174] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 2977.342180] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 2977.342185] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 2977.342191] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 2977.342196] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 2977.342204] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 2977.342219] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 2977.342225] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 2977.342231] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 2977.342237] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 2977.342245] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 2977.342250] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 2977.342256] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 2977.342261] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 2977.342267] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 2977.342272] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 2977.342278] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 2977.342288] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[ 2977.342293] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[ 2977.342320] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 2977.342326] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 2977.342332] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 2977.342337] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 2977.342342] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 2977.342345] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netr28x'
[ 2977.343086] ndiswrapper (load_wrap_driver:103): couldn't load driver netr28x; check system log for messages from 'loadndisdriver'
[ 2977.343166] usbcore: registered new interface driver ndiswrapper

Using 64bit and same driver from my laptop support page (Asus x54c)

---

### Post by chili555 on 2014-01-13
> **ukbeast said:**
> 
Using 64bit and same driver from my laptop support page (Asus x54c)And it specifically says XP?

---

### Post by ukbeast on 2014-01-13
Have tried windows 7,8 and winxp (64bit)
Thank you so far

---

### Post by chili555 on 2014-01-13
Did you apt-get the ndiswrapper base packages or compile from source? [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

---

### Post by ukbeast on 2014-01-14
I compiled it myself from [COLOR=#000000] [/COLOR][http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)
Ndiswrapper does not load in kernel from apt

---

### Post by chili555 on 2014-01-14
If you have tried the one available driver parameter for rt2800pci, tried the latest available backports and tried ndiswrapper, then I have no further suggestions aside from a different wireless card.

---

### Post by ubase133 on 2014-02-04
Hi, i had the same problem, so i made a patch to make it compile on kernel 3.12. So far, the driver works, but i cannot guarantee that there isn't something else wrong, so use it at your own risk. I use Debian Jessie with kernel 3.12, i guess this will work with Saucy's too.

cd into the driver directory, apply the 3.8 patch first, then this with 
patch -p1 < rt5390sta_3.12.patch

I hope this will be useful to you!

---

### Post by ukbeast on 2014-02-10
> **ubase133 said:**
> Hi, i had the same problem, so i made a patch to make it compile on kernel 3.12. So far, the driver works, but i cannot guarantee that there isn't something else wrong, so use it at your own risk. I use Debian Jessie with kernel 3.12, i guess this will work with Saucy's too.

cd into the driver directory, apply the 3.8 patch first, then this with 
patch -p1 < rt5390sta_3.12.patch

I hope this will be useful to you!

Thanks very much, :D.

---

### Post by jhay2 on 2014-04-18
thanks with this . it also works on kernel 3.13 with ubuntu 14.04

---

### Post by mqy on 2014-04-18
> **ubase133 said:**
> Hi, i had the same problem, so i made a patch to make it compile on kernel 3.12. So far, the driver works, but i cannot guarantee that there isn't something else wrong, so use it at your own risk. I use Debian Jessie with kernel 3.12, i guess this will work with Saucy's too.

cd into the driver directory, apply the 3.8 patch first, then this with 
patch -p1 < rt5390sta_3.12.patch

I hope this will be useful to you!

Thanks a bunch! 

Just installed Ubuntu 14.04 on a PC that previously ran 13.10 with the patch for the driver, only to find that it wouldn't compile anymore with kernel 3.13!

Your small patch made my day, the module compiles and loads just fine! :)

---

### Post by fifthager on 2014-04-19
Worked for me, too (kernel 3.13 with ubuntu 14.04). Many thanks!

---

### Post by LUCASBSTANLEY on 2014-05-26
god@slave:~$  patch -p1 < rt5390sta_3.12.patch
bash: rt5390sta_3.12.patch: No such file or directory
god@slave:~$ file:///home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/rt5390sta_3.12.patch 
bash: file:///home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2/rt5390sta_3.12.patch: No such file or directory
god@slave:~$  patch -p1 < rt5390sta_3.12.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- ../rt_linux.h    2013-05-22 03:28:50.000000000 +0000
|+++ ./include/os/rt_linux.h    2014-02-04 21:54:39.982679908 +0000
--------------------------
File to patch: '/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2' 
'/home/god/2010_0915_RT3572_Linux_STA_v2.4.0.2' : No such file or directory
Skip this patch? [y] 
Skipping patch.
1 out of 1 hunk ignored
god@slave:~$  patch -p1 < rt5390sta_3.12.patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------

 help all i want is for my wifi adapter to stop becoming non responsive i know this is the thread i need to fix it i just am having a little trouble trying to figure out how to complete this

---

### Post by LUCASBSTANLEY on 2014-05-26
also this is my details
memory 2.0gib
processor AMD Sempron(tm) Processor 3400+ 
graphics Gallium 0.4 on AMD RV635
os type 32-bit
disk 76.5GB help i also have a 5450 hd silent graphics card

---

### Post by Tridentine_Avenger on 2014-06-25
Brilliant!  Of note, both patch files must be applied.

I've been spending weeks thinking I've been going cray-cray because of how slow my RT5390 was on my ASUS box under Ubuntu 14.4 running kernel 3.13.  This works like a charm.

---

