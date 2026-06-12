---
title: "Wireless Driver assistance"
date: 2014-07-15
forum: Networking &amp; Wireless
---

### Post by jonathan43 on 2014-07-15
Hello! I am very new to linus(two days) and I cant for the life of me, get my wireless driver working. I have a Rosewill N600PCE dualband wireless card and im running ubuntu 14.04. I am confused about the directions that came with the driver(I downloaded the driver for the ASUS PCE N53 which I was told worked with my driver, at least on windows 8 it did.) I tried to use NDISwrapper but I dont really think Im using that properly either, as when I install the driver, it shows that there is matching hardware, but the wireless still doesnt work. Please, if you can, help me!

---

### Post by jonathan43 on 2014-07-15
Im looking at the driver and it has instructions but I dont know what it means. This is what it says.



RT5592 Linux Driver quick start		


====================
Check tools:  


====================
*Before install driver, please check already install compile tool and  kernel source code


1>Install compile tool
    $yum install gcc-c++


2>check kernel source code exists /usr/src/kernels/ "kernel name"


    Download your kernel source code
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/) 		
	or
    $yum install kernel-devel






====================
Build Instructions:  


====================
1> $tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_vx.x.x.x.tar.bz2
     go to "DPO_GPL_RT5592STA_LinuxSTA_vx.x.x.x" directory.
    




2> In Makefile
	 
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 
     define the linux kernel source include file path LINUX_SRC
	 
     modify to meet your need.




3> In os/linux/config.mk 
	
     define the GCC and LD of the target machine
	
     define the compiler flags CFLAGS
	
     modify to meet your need.
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   	   
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
     ** Build for being controlled by WpaSupplicant with Ralink Driver
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d


4> $make			
	
     # compile driver source code, need administrator.
	
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	 
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c


5> $make install
     #install driver
     #copy RT2860STA.dat to /etc/Wireless/RT2860STA/RT2860STA.dat


6>$vi /etc/rc.d/rc.local
     #input "ifconfig ra0 up"
    $reboot


7> unload driver    
    
     $ifconfig ra0 down


     $rmmod rt5592sta

---

### Post by jonathan43 on 2014-07-16
Also, if theres anything different I can try, please let me know(I tried ndiswrapper but I cant tell if I did something wrong or if it doesnt work)

---

### Post by chili555 on 2014-07-16
Let's gather some information first. Please open a terminal and run and post:```
lspci -nn | grep 0280
uname -r
ndiswrapper -l
```Thanks.

---

### Post by jonathan43 on 2014-07-17
**lspci -nn | grep 0280**

03:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]

[B]uname -r

[/B]3.13.0-30-generic

[B][COLOR=#000000][FONT=Ubuntu Mono]ndiswrapper -l[/FONT][/COLOR]
[/B][COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]	device (1814:5592) present

---

### Post by chili555 on 2014-07-17
This is a tricky device to get going. I guess ndiswrapper is as good a place as any to start. Did you use XP files? They are required by ndiswrapper and none other will work.

Let's see:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by jonathan43 on 2014-07-17
There was no output for the first command but the second command generated this:

jonathan@Jonathan:~$ dmesg | grep ndis
[   26.068389] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   26.069148] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   27.152998] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[   27.153030] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit'
[   27.153062] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   27.153088] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   27.153113] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   27.153139] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   27.153164] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopySendNetBufferListInfo'
[   27.153190] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   27.153216] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   27.153244] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   27.153269] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   27.153294] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   27.153320] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   27.153347] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   27.153375] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   27.153402] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   27.153425] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   27.153452] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   27.153480] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   27.153508] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   27.153533] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   27.153558] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   27.153584] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   27.153615] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   27.153642] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   27.153670] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   27.153699] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   27.153722] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   27.153750] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   27.153778] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   27.153807] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   27.153830] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   27.153856] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   27.153882] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   27.153906] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   27.153932] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   27.153960] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   27.153987] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   27.154011] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   27.154065] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   27.154089] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   27.154113] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netr28x'
[   27.154595] ndiswrapper (load_wrap_driver:103): couldn't load driver netr28x; check system log for messages from 'loadndisdriver'
[   27.158726] usbcore: registered new interface driver ndiswrapper
[104980.521091] usbcore: deregistering interface driver ndiswrapper
[104980.528875] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[104980.560973] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[104980.560979] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'
[104980.561735] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'
[104980.561842] usbcore: registered new interface driver ndiswrapper
[105042.081700] usbcore: deregistering interface driver ndiswrapper
[105042.090635] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[105042.120614] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[105042.120620] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'
[105042.121477] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'
[105042.123589] usbcore: registered new interface driver ndiswrapper
[105087.137415] usbcore: deregistering interface driver ndiswrapper
[105087.145387] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[105087.174137] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[105087.174233] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'
[105087.175061] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'
[105087.176935] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2014-07-18
You have one unhappy ndiswrapper there! Let's see what we can fix.

First, you have evidently tried two, or perhaps more, driver packages; viz:> [ 27.154113] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netr28x'And...> [105042.120620] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'We should try to see which is incorrect, or perhaps more incorrect and eliminate it. As the second one is loading, we see this sequence:> 104980.560979] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'
[104980.561735] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'
[104980.561842] usbcore: registered new interface driver ndiswrapper
[105042.081700] usbcore: deregistering interface driver ndiswrapper
[105042.090635] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[105042.120614] ndiswrapper (check_nt_hdr:141): [COLOR="#FF0000"]kernel is 64-bit, but Windows driver is not 64-bit;bad magic:[/COLOR] 010B
[105042.120620] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'For ndiswrapper to possibly work, we need the Windows **XP** drivers appropriate to your architecture; either 32- or 64-bit. Windows 7 or 8 or Vista or 3.1 won't ever work. For the benefit of the searchers, I note that many of you just grab the drivers from your Windows 7 or 8 dual-boot and hope for the best. It never works. 

Since we know that rt2860 is incorrect, let's remove it and see if things improve:```
sudo ndiswrapper -e rt2860
```In this context -e means 'erase.' 

Next, where did you get netr28x? Is it a 64-bit Windows XP file? You can get some clues by reading the netr28x.inf file with gedit or any other text editor.

---

### Post by jonathan43 on 2014-07-18
When I opened netr28x.inf in gedit, I get this error message


Unexpected error: invalid byte sequence in conversion input

Also, is there supposed to be any output to the command you gave me?
 I downloaded the drivers from the ASUS website for the PCEN53 and all of the drivers(XP 32/64, Vista 32/64, and Win7 32/64) were included in their own folders.

---

### Post by jonathan43 on 2014-07-18
Also, I dont believe that the issue was fixed by removing the other driver.

---

### Post by jonathan43 on 2014-07-18
Does Ubuntu automatically detect networks or do I have to enter the SSID, WPA information, etc?

---

### Post by chili555 on 2014-07-18
It should automatically detect networks like this: [http://www.oulu.fi/it/graphics/nmgui.png](http://www.oulu.fi/it/graphics/nmgui.png) You then click on the one you want and it asks for the WPA2 password and, if correct, you connect.> When I opened netr28x.inf in gedit, I get this error message
Unexpected error: invalid byte sequence in conversion inputCan you please zip it up and attach it to your reply using the paperclip at the top of the reply box?```
cd ~/Desktop/folderwiththefiles
zip netr28x.zip netr28x.inf
```> I downloaded the drivers from the ASUS website for the PCEN53 and all of the drivers(XP 32/64, Vista 32/64, and Win7 32/64) were included in their own folders.And so your netr28x.inf comes from the XP 64-bit folder? Yes?

---

### Post by jonathan43 on 2014-07-19
Wait hold on,, I just looked in my folder for the netr28x.inf and I realized it was in Vista(I am SOOO sorry, I mustve misread) So I uninstalled that the same way you had me remove rt2860 and then I tried to open the .inf for 2860 and I cannot load that either.

[ATTACH]254833[/ATTACH]

---

### Post by chili555 on 2014-07-19
I would think that the file you attached should work. It says, in part:> [Ralink.[COLOR="#FF0000"]NTamd64[/COLOR]]
; DisplayName                  Section                 DeviceID
; -----------                  -------                 --------
<snip>
%Generic.DeviceDesc%           = RT3900E4.ndi,         PCI\VEN_[COLOR="#FF0000"]1814[/COLOR]&DEV_[COLOR="#FF0000"]5592[/COLOR]
Since you removed netr28x, did you try this one?

EDIT: For the benefit of you driver dawgs out there, you can read these with vim.

---

### Post by jonathan43 on 2014-07-19
I did, and it doesn't work

---

### Post by jonathan43 on 2014-07-20
I think I am going to switch back to Windows. Linux is cool and I'm sure better than windows in some cases, but ive had five years experience in windows and i know it like the back of my hand, so Im going to switch back! Thank you for all the help even though it didnt quite work out.

---

### Post by praseodym on 2014-07-20
Sorry, I haven't read the whole thread, but did you try this driver:

[http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915](http://ubuntuforums.org/showthread.php?t=2217996&page=2&p=12997915#post12997915)

---

