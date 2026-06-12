---
title: "Using NDISWrapper"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Vasto on 2008-06-19
Hi everyone!
My hp dv6500t has a Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61). This worked perfectly at school, but once I came home, it would make my router restart ([Bug Report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793). I heard I can fix this if I use NDISWrapper.
I downloaded the gtk version of ndiswrapper after failing multiple times with the terminal one. It says my hardware is present, but then when I go to connect using wireless, my router restarts again. I think I might still be using the normal drivers instead of the Vista drivers. How do I make my laptop use my vista drivers?

EDIT: After a restart, I don't even have an option to select wireless from nm-applet

---

### Post by Vasto on 2008-06-21
bump

---

### Post by cariboo on 2008-06-21
I just had to look at the ndiswrapper commands. Ndiswrapper is pretty easy to use:

```
ndiswrapper -i <driver.inf>
ndiswrapper -l to see device status
ndiswrapper -m to add the code to modprobe.d
modprobe ndiswrapper

```

The biggest thing is to get the correct driver for your wireless device. I had the best success with the winxp drivers that came with my wireless card.

Jim

---

### Post by kevmitch on 2008-06-21
> **Vasto said:**
> Hi everyone!
My hp dv6500t has a Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61). This worked perfectly at school, but once I came home, it would make my router restart ([Bug Report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793). I heard I can fix this if I use NDISWrapper.
I downloaded the gtk version of ndiswrapper after failing multiple times with the terminal one. It says my hardware is present, but then when I go to connect using wireless, my router restarts again.
[QUOTE]

I guess it would be good to determine if ndiswrapper is working independently of the router in question. The fact that it is communicating with the router enough to cause the same behaviour is a good sign that you've got wireless up and running with ndiswrapper, but it wouldn't hurt to test it on a less finicky router. Have you tried upgrading the router's firmware? If you already have, I would keep an eye out for future firmware revisions. 

[QUOTE]
I think I might still be using the normal drivers instead of the Vista drivers. How do I make my laptop use my vista drivers?
[\QUOTE]

If you're using ndiswrapper, you most definitely want to be using XP drivers. ndiswrapper will not work with Vista drivers. Furthermore, you want to use 32-bit XP drivers with a 32-bit kernel and 64-bit XP drivers (which often don't exist) with a 64-bit kernel.

[QUOTE]
EDIT: After a restart, I don't even have an option to select wireless from nm-applet

There are a couple possibilities that I could imagine here:
1. Somehow neither the ndiswrapper or iwl4965 (native linux) modules from loading. Check with the command
```
lsmod | egrep 'ndis|iwl'
```
If you get nothing back but the command line, this is the case. Try loading one with either
```
sudo modprobe ndiswrapper 
```
or
```
sudo modprobe iwl4965
```
2. Both modules are getting loaded on boot and are in conflict. In this case the lsmod command above will return both modules. Try removing one with 
```
sudo rmmod ndiswrapper 
```
or
```
sudo rmmod iwl4965
```

---

### Post by Vasto on 2008-06-22
Ok, I am not sure what the problem is. I tried running the commands kevmitch suggested.

sudo modprobe ndiswrapper
sudo rmmod iwl4965

```

michael@michael-ubuntu:~$ lsmod | egrep 'ndis|iwl'
ndiswrapper           243872  0 
usbcore               169904  6 uvcvideo,hci_usb,ndiswrapper,ehci_hcd,uhci_hcd
michael@michael-ubuntu:~$ sudo ndiswrapper -l
[sudo] password for michael: 
netw4v64 : driver installed
	device (8086:4229) present (alternate driver: iwl4965)

```

I then searched through my logs and discovered this. I don't know if this is because earlier I got frustrated and ran "sudo ndiswrapper -ma" and "sudo ndiswrapper -mi"

```

Jun 22 18:43:18 michael-ubuntu kernel: [   28.769931] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769939] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769945] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769950] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769959] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769966] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769971] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769981] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769987] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769993] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.769998] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770007] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770012] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770017] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770022] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770027] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770033] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770038] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770043] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770058] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770070] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770075] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770080] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770085] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770090] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770095] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770101] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770106] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770111] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770116] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770121] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770126] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770131] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw4v64'
Jun 22 18:43:18 michael-ubuntu kernel: [   28.770787] ndiswrapper (load_wrap_driver:112): couldn't load driver netw4v64; check system log for messages from 'loadndisdriver'

```

---

### Post by pokipoki08 on 2008-06-22
Checks kernel version
```
uname -ma
```

x86_64 = 64 bit kernel/ubuntu
i386/i686 = 32 bit kernel/ubuntu

Avoid Vista drivers, use WinXp instead. Locate the 32/64 bit driver, corresponding to your kernel and install in ndiswrapper.

Shutdown PC
Unplug wifi adapter
Restart PC
Login ubuntu
Plugin wifi adapter

Run & post output of these commands

List ndiswrapper loading messages
```
dmesg | grep ndiswrapper
```

List wifi adapter loading messages
```
dmesg | grep wlan
```

If all is well, proceed

```
sudo ifconfig wlan0 up
iwlist wlan0 scan
iwconfig wlan0
```

Are you trying to connect to an Open/Restricted router? WEP/WPA?

Maurice

---

### Post by Vasto on 2008-06-23
Because HP doesn't have the 64 bit drivers for Windows XP, so I downloaded the drivers from Intel's site.
When I went to restart with the wireless turned on, I got Loading hardware drivers... [FAIL]
So I turned the wireless switch off, and now it gets stuck on loading manual drivers...

I had to boot into recovery mode and remove it from the root shell, and I still get the [FAIL]. I have no idea what to do.

---

### Post by kevmitch on 2008-06-23
Ok, so it looks like you're only loading ndiswrapper, so we just need to figure out why that's behaving strangely. I would concur with pokipoki08. Make sure that you are using the windows XP drivers either 64 or 32 bit depending on your kernel and remove any other drivers with 
```
ndiswrapper -e <driver>
```
where <driver> is what comes before the ":" in the output of "ndiswrapper -l".

I might add, that unless using ndiswrapper actually does turn out to solve your router reboot problem, you're probably better off with the native linux drivers. Intel wireless cards probably have the best Linux support of any. Just make sure you're using at least kernel 2.6.24 (use uname -a to find out) which is the first one in which the drivers are included out of the box.

---

### Post by pokipoki08 on 2008-06-23
Unplug your wireless adapter as it hangs your PC.

Identify the driver which is installed in ndiswrapper
```
ls /etc/ndiswrapper
```

Uninstall the faulty driver in ndiswrapper, use either one below

```
sudo ndiswrapper -r [COLOR="Magenta"]driver[/COLOR]
```
**[COLOR="Blue"]or[/COLOR]**
```
sudo ndiswrapper -e [COLOR="Magenta"]driver[/COLOR]
```

Can you post the brand/model/revision of the wireless adapter?

Do a search here or google to check the successful driver (type/version) used in ndiswrapper.

Acquire the driver and install it in ndiswrapper.

The driver must be the WinXP version. If the 64-bit version does not exist, consider installing the 32-bit version of Ubuntu.

```
ndiswrapper -i [COLOR="Magenta"]driver[/COLOR].inf
```

Maurice

---

### Post by Vasto on 2008-07-01
I know it's been a week (unfortunately I've been having to use my Windows XP partition because I just haven't had time.)
Now I can't seem to boot into the recovery mode (even though I have the wifi switch disabled like I previously did.)

I booted up a livecd to double check that ndiswrapper was in fact using a XP 64 driver (it is.)

Could the problem be that the Netw4x64.INF file looks pretty excessive because I downloaded it from Intel's website because HP doesn't list it on theirs?

```

;*****************************************
; NETw4x64.INF
;
; Intel Wireless WiFi Link Adapters
; Installation Script for Windows XP 64 bit
;
; Copyright (c) 2007 Intel, Inc. All Rights Reserved
;
;------------------------------------------------------------------------------

;******************************************************************************
; Version Section
;------------------------------------------------------------------------------
[version]
Signature   = "$Windows NT$"
Compatible  = 1
Class       = net
ClassGUID   = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %PROVIDER_NAME%
DriverVer   = 03/13/2008,11.5.1.15 ;DATE HAS TO BE IN FOLLOWING FORMAT MM/DD/YYYY


CatalogFile = NETw4x64.cat


;*****************************************
; Manufacturer
;-----------------------------------------

[Manufacturer]
%COMPANY_NAME% = Device, NTamd64.5.2

;[ControlFlags]
;ExcludeFromSelect = \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11008086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11018086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11028086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11038086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11048086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11058086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11068086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11078086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11008086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11018086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11028086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11038086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11048086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11058086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11068086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11078086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10008086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10018086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10028086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10038086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10048086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10058086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10068086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10078086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10008086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10018086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10028086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10038086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10048086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10008086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10018086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10028086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10038086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10048086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10308086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10318086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10328086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10338086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10058086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10348086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11108086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11118086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11128086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11138086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11148086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11158086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11168086 , \ 
;        PCI\VEN_8086&DEV_4233&SUBSYS_11178086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11108086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11118086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11128086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11138086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11148086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11158086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11168086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_11178086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10108086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10118086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10128086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10138086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10148086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10158086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10168086 , \ 
;        PCI\VEN_8086&DEV_4230&SUBSYS_10178086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10108086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10118086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10128086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10138086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10148086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11208086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11218086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11228086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11238086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11248086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11258086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11268086 , \ 
;        PCI\VEN_8086&DEV_422D&SUBSYS_11278086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11208086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11218086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11228086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11238086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11248086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11258086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11268086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_11278086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10208086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10218086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10228086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10238086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10248086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10258086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10268086 , \ 
;        PCI\VEN_8086&DEV_4229&SUBSYS_10278086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10208086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10218086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10228086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10238086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10248086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10208086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10218086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10228086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10238086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10248086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10408086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10418086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10428086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10438086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10448086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10408086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10418086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10428086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10438086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10448086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10508086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10518086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10528086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10538086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_10548086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10508086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10518086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10528086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10538086 , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_10548086 , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_135B103C , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_135C103C , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_135D103C , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_135E103C , \ 
;        PCI\VEN_8086&DEV_4228&SUBSYS_135F103C , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_135B103C , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_135C103C , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_135D103C , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_135E103C , \ 
;        PCI\VEN_8086&DEV_4222&SUBSYS_135F103C , \ 
;        PCI\VEN_8086&DEV_4227&SUBSYS_10108086 , \ 
;        PCI\VEN_8086&DEV_4227&SUBSYS_10118086 , \ 
;        PCI\VEN_8086&DEV_4227&SUBSYS_10128086 , \ 
;        PCI\VEN_8086&DEV_4227&SUBSYS_10138086 , \ 
;        PCI\VEN_8086&DEV_4227&SUBSYS_10148086 , \ 

;*****************************************
;Device
;-----------------------------------------

;*****************************************
;Device XP64
;-----------------------------------------
[Device.NTamd64.5.2]

; GEN_4965_AGN_C
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW1    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11008086 ; MOW1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW2    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11018086 ; MOW2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_RoW    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11028086 ; RoW
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_JPN    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11038086 ; JPN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_KRA    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11048086 ; KRA
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_SP1    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11058086 ; SP1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_SP2    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11068086 ; SP2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_C_XP64_SP3    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11078086 ; SP3

; GEN_4965_AGN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_MOW1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11008086 ; MOW1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_MOW2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11018086 ; MOW2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_RoW    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11028086 ; RoW
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_JPN    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11038086 ; JPN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_KRA    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11048086 ; KRA
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_SP1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11058086 ; SP1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_SP2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11068086 ; SP2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_GEN_4965_AGN_XP64_SP3    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11078086 ; SP3

; GEN_4965_AG
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10008086 ; MOW1
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10018086 ; MOW2
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_RoW    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10028086 ; RoW
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_JPN    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10038086 ; JPN
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_KRA    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10048086 ; KRA
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_SP1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10058086 ; SP1
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_SP2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10068086 ; SP2
%NIC_MPCIEX_4965AG% = Install_MPCIEX_GEN_4965_AG_XP64_SP3    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10078086 ; SP3

; GEN_3965_ABG
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_GEN_3965_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10008086 ; MOW1
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_GEN_3965_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10018086 ; MOW2
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_GEN_3965_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10028086 ; RoW
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_GEN_3965_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10038086 ; JPN
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_GEN_3965_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10048086 ; KRA

; GEN_3945_ABG
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10008086 ; MOW1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10018086 ; MOW2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10028086 ; RoW
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10038086 ; JPN
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10048086 ; KRA

; GEN_3945_ABG_SP1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_SP1_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10308086 ;

; GEN_3945_ABG_SP2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_SP2_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10318086 ;

; GEN_3945_ABG_SP3
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_SP3_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10328086 ;

; GEN_3945_ABG_SP4
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_GEN_3945_ABG_SP4_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10338086 ;

; GEN_3945_BG
%NIC_MPCIEX_3945BG% = Install_MPCIEX_GEN_3945_BG_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10058086 ;

; GEN_3945_BGX
%NIC_MPCIEX_3945BG% = Install_MPCIEX_GEN_3945_BGX_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10348086 ;

; Lenovo_4965_AGN_C
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_MOW1    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11108086 ; MOW1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_MOW2    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11118086 ; MOW2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_RoW    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11128086 ; RoW
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_JPN    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11138086 ; JPN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_KRA    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11148086 ; KRA
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP1    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11158086 ; SP1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP2    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11168086 ; SP2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP3    ,   PCI\VEN_8086&DEV_4233&SUBSYS_11178086 ; SP3

; Lenovo_4965_AGN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_MOW1    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11108086 ; MOW1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_MOW2    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11118086 ; MOW2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_RoW    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11128086 ; RoW
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_JPN    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11138086 ; JPN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_KRA    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11148086 ; KRA
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_SP1    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11158086 ; SP1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_SP2    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11168086 ; SP2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Lenovo_4965_AGN_XP64_SP3    ,   PCI\VEN_8086&DEV_4230&SUBSYS_11178086 ; SP3

; Lenovo_4965_AG
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10108086 ; MOW1
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10118086 ; MOW2
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_RoW    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10128086 ; RoW
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_JPN    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10138086 ; JPN
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_KRA    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10148086 ; KRA
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_SP1    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10158086 ; SP1
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_SP2    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10168086 ; SP2
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Lenovo_4965_AG_XP64_SP3    ,   PCI\VEN_8086&DEV_4230&SUBSYS_10178086 ; SP3

; Lenovo_3965_ABG
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Lenovo_3965_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10108086 ; MOW1
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Lenovo_3965_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10118086 ; MOW2
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Lenovo_3965_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10128086 ; RoW
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Lenovo_3965_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10138086 ; JPN
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Lenovo_3965_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10148086 ; KRA

; Dell_4965_AGN_C
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_MOW1    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11208086 ; MOW1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_MOW2    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11218086 ; MOW2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_RoW    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11228086 ; RoW
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_JPN    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11238086 ; JPN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_KRA    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11248086 ; KRA
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_SP1    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11258086 ; SP1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_SP2    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11268086 ; SP2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_C_XP64_SP3    ,   PCI\VEN_8086&DEV_422D&SUBSYS_11278086 ; SP3

; Dell_4965_AGN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_MOW1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11208086 ; MOW1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_MOW2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11218086 ; MOW2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_RoW    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11228086 ; RoW
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_JPN    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11238086 ; JPN
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_KRA    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11248086 ; KRA
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_SP1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11258086 ; SP1
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_SP2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11268086 ; SP2
%NIC_MPCIEX_4965AGN% = Install_MPCIEX_Dell_4965_AGN_XP64_SP3    ,   PCI\VEN_8086&DEV_4229&SUBSYS_11278086 ; SP3

; Dell_4965_AG
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10208086 ; MOW1
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10218086 ; MOW2
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_RoW    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10228086 ; RoW
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_JPN    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10238086 ; JPN
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_KRA    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10248086 ; KRA
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_SP1    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10258086 ; SP1
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_SP2    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10268086 ; SP2
%NIC_MPCIEX_4965AG% = Install_MPCIEX_Dell_4965_AG_XP64_SP3    ,   PCI\VEN_8086&DEV_4229&SUBSYS_10278086 ; SP3

; Dell_3965_ABG
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Dell_3965_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10208086 ; MOW1
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Dell_3965_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10218086 ; MOW2
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Dell_3965_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10228086 ; RoW
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Dell_3965_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10238086 ; JPN
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Dell_3965_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10248086 ; KRA

; Dell_3945_ABG
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Dell_3945_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10208086 ; MOW1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Dell_3945_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10218086 ; MOW2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Dell_3945_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10228086 ; RoW
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Dell_3945_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10238086 ; JPN
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Dell_3945_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10248086 ; KRA

; Toshiba_3965_ABG
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Toshiba_3965_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10408086 ; MOW1
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Toshiba_3965_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10418086 ; MOW2
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Toshiba_3965_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10428086 ; RoW
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Toshiba_3965_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10438086 ; JPN
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Toshiba_3965_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10448086 ; KRA

; Toshiba_3945_ABG
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Toshiba_3945_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10408086 ; MOW1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Toshiba_3945_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10418086 ; MOW2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Toshiba_3945_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10428086 ; RoW
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Toshiba_3945_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10438086 ; JPN

; Toshiba_3945_BGX
%NIC_MPCIEX_3945BG% = Install_MPCIEX_Toshiba_3945_BGX_XP64    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10448086 ;

; Sony_3965_ABG
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Sony_3965_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10508086 ; MOW1
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Sony_3965_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10518086 ; MOW2
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Sony_3965_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10528086 ; RoW
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Sony_3965_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10538086 ; JPN
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_Sony_3965_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4228&SUBSYS_10548086 ; KRA

; Sony_3945_ABG
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Sony_3945_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10508086 ; MOW1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Sony_3945_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10518086 ; MOW2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Sony_3945_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10528086 ; RoW
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Sony_3945_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10538086 ; JPN
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_Sony_3945_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4222&SUBSYS_10548086 ; KRA

; HP_3965_ABG
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_HP_3965_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4228&SUBSYS_135B103C ; MOW1
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_HP_3965_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4228&SUBSYS_135C103C ; MOW2
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_HP_3965_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4228&SUBSYS_135D103C ; RoW
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_HP_3965_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4228&SUBSYS_135E103C ; JPN
%NIC_MPCIEX_3965ABG% = Install_MPCIEX_HP_3965_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4228&SUBSYS_135F103C ; KRA

; HP_3945_ABG
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_HP_3945_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4222&SUBSYS_135B103C ; MOW1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_HP_3945_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4222&SUBSYS_135C103C ; MOW2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_HP_3945_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4222&SUBSYS_135D103C ; RoW
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_HP_3945_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4222&SUBSYS_135E103C ; JPN
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_HP_3945_ABG_XP64_KRA    ,   PCI\VEN_8086&DEV_4222&SUBSYS_135F103C ; KRA

; IBM_3945_ABG
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_IBM_3945_ABG_XP64_MOW1    ,   PCI\VEN_8086&DEV_4227&SUBSYS_10108086 ; MOW1
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_IBM_3945_ABG_XP64_MOW2    ,   PCI\VEN_8086&DEV_4227&SUBSYS_10118086 ; MOW2
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_IBM_3945_ABG_XP64_RoW    ,   PCI\VEN_8086&DEV_4227&SUBSYS_10128086 ; RoW
%NIC_MPCIEX_3945ABG% = Install_MPCIEX_IBM_3945_ABG_XP64_JPN    ,   PCI\VEN_8086&DEV_4227&SUBSYS_10138086 ; JPN

; IBM_3945_BG
%NIC_MPCIEX_3945BG% = Install_MPCIEX_IBM_3945_BG_XP64    ,   PCI\VEN_8086&DEV_4227&SUBSYS_10148086 ;



;*****************************************
;INSTALL XP64
;-----------------------------------------

;-----------------------------------------
; Intel  4965AGN XP64 GEN_4965_AGN_C
;-----------------------------------------

[Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_MOW1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_MOW2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_RoW, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_JPN, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_KRA, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_SP1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_SP2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN_C, Reg_GEN_4965_AGN_C_SP3, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_C_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AGN XP64 GEN_4965_AGN
;-----------------------------------------

[Install_MPCIEX_GEN_4965_AGN_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_MOW1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_MOW2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_RoW, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_JPN, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_KRA, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_SP1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_SP2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AGN_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AGN, Reg_GEN_4965_AGN_SP3, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AGN_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AG XP64 GEN_4965_AG
;-----------------------------------------

[Install_MPCIEX_GEN_4965_AG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_MOW1, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_MOW2, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_RoW, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_JPN, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_KRA, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_SP1, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_SP2, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_4965_AG_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_4965_AG, Reg_GEN_4965_AG_SP3, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_4965_AG_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3965ABG XP64 GEN_3965_ABG
;-----------------------------------------

[Install_MPCIEX_GEN_3965_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3965_ABG, Reg_GEN_3965_ABG_MOW1, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3965_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3965_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3965_ABG, Reg_GEN_3965_ABG_MOW2, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3965_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3965_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3965_ABG, Reg_GEN_3965_ABG_RoW, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3965_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3965_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3965_ABG, Reg_GEN_3965_ABG_JPN, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3965_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3965_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3965_ABG, Reg_GEN_3965_ABG_KRA, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3965_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 GEN_3945_ABG
;-----------------------------------------

[Install_MPCIEX_GEN_3945_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG, Reg_GEN_3945_ABG_MOW1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3945_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG, Reg_GEN_3945_ABG_MOW2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3945_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG, Reg_GEN_3945_ABG_RoW, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3945_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG, Reg_GEN_3945_ABG_JPN, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_GEN_3945_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG, Reg_GEN_3945_ABG_KRA, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 GEN_3945_ABG_SP1
;-----------------------------------------

[Install_MPCIEX_GEN_3945_ABG_SP1_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG_SP1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_SP1_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 GEN_3945_ABG_SP2
;-----------------------------------------

[Install_MPCIEX_GEN_3945_ABG_SP2_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG_SP2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_SP2_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 GEN_3945_ABG_SP3
;-----------------------------------------

[Install_MPCIEX_GEN_3945_ABG_SP3_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG_SP3, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_SP3_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 GEN_3945_ABG_SP4
;-----------------------------------------

[Install_MPCIEX_GEN_3945_ABG_SP4_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_ABG_SP4, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_ABG_SP4_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945BG XP64 GEN_3945_BG
;-----------------------------------------

[Install_MPCIEX_GEN_3945_BG_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_BG, Reg_MPCIEX_3945BG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_BG_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945BG XP64 GEN_3945_BGX
;-----------------------------------------

[Install_MPCIEX_GEN_3945_BGX_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_GEN_3945_BGX, Reg_MPCIEX_3945BG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_GEN_3945_BGX_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AGN XP64 Lenovo_4965_AGN_C
;-----------------------------------------

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_MOW1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_MOW2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_RoW, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_JPN, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_KRA, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_SP1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_SP2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN_C, Reg_Lenovo_4965_AGN_C_SP3, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_C_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AGN XP64 Lenovo_4965_AGN
;-----------------------------------------

[Install_MPCIEX_Lenovo_4965_AGN_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_MOW1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_MOW2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_RoW, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_JPN, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_KRA, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_SP1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_SP2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AGN, Reg_Lenovo_4965_AGN_SP3, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AGN_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AG XP64 Lenovo_4965_AG
;-----------------------------------------

[Install_MPCIEX_Lenovo_4965_AG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_MOW1, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_MOW2, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_RoW, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_JPN, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_KRA, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_SP1, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_SP2, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_4965_AG_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_4965_AG, Reg_Lenovo_4965_AG_SP3, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_4965_AG_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3965ABG XP64 Lenovo_3965_ABG
;-----------------------------------------

[Install_MPCIEX_Lenovo_3965_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_3965_ABG, Reg_Lenovo_3965_ABG_MOW1, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_3965_ABG, Reg_Lenovo_3965_ABG_MOW2, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_3965_ABG, Reg_Lenovo_3965_ABG_RoW, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_3965_ABG, Reg_Lenovo_3965_ABG_JPN, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Lenovo_3965_ABG, Reg_Lenovo_3965_ABG_KRA, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Lenovo_3965_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AGN XP64 Dell_4965_AGN_C
;-----------------------------------------

[Install_MPCIEX_Dell_4965_AGN_C_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_MOW1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_MOW2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_RoW, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_JPN, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_KRA, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_SP1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_SP2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN_C, Reg_Dell_4965_AGN_C_SP3, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_C_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AGN XP64 Dell_4965_AGN
;-----------------------------------------

[Install_MPCIEX_Dell_4965_AGN_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_MOW1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_MOW2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_RoW, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_JPN, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_KRA, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_SP1, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_SP2, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AGN_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AGN, Reg_Dell_4965_AGN_SP3, Reg_MPCIEX_4965AGN, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AGN_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  4965AG XP64 Dell_4965_AG
;-----------------------------------------

[Install_MPCIEX_Dell_4965_AG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_MOW1, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_MOW2, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_RoW, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_JPN, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_KRA, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_SP1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_SP1, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_SP1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_SP2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_SP2, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_SP2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_4965_AG_XP64_SP3]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_4965_AG, Reg_Dell_4965_AG_SP3, Reg_MPCIEX_4965AG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_KDR
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_4965_AG_XP64_SP3.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3965ABG XP64 Dell_3965_ABG
;-----------------------------------------

[Install_MPCIEX_Dell_3965_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3965_ABG, Reg_Dell_3965_ABG_MOW1, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3965_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3965_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3965_ABG, Reg_Dell_3965_ABG_MOW2, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3965_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3965_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3965_ABG, Reg_Dell_3965_ABG_RoW, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3965_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3965_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3965_ABG, Reg_Dell_3965_ABG_JPN, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3965_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3965_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3965_ABG, Reg_Dell_3965_ABG_KRA, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3965_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 Dell_3945_ABG
;-----------------------------------------

[Install_MPCIEX_Dell_3945_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3945_ABG, Reg_Dell_3945_ABG_MOW1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3945_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3945_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3945_ABG, Reg_Dell_3945_ABG_MOW2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3945_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3945_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3945_ABG, Reg_Dell_3945_ABG_RoW, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3945_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3945_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3945_ABG, Reg_Dell_3945_ABG_JPN, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3945_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Dell_3945_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Dell_3945_ABG, Reg_Dell_3945_ABG_KRA, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Dell_3945_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3965ABG XP64 Toshiba_3965_ABG
;-----------------------------------------

[Install_MPCIEX_Toshiba_3965_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3965_ABG, Reg_Toshiba_3965_ABG_MOW1, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3965_ABG, Reg_Toshiba_3965_ABG_MOW2, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3965_ABG, Reg_Toshiba_3965_ABG_RoW, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3965_ABG, Reg_Toshiba_3965_ABG_JPN, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3965_ABG, Reg_Toshiba_3965_ABG_KRA, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3965_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 Toshiba_3945_ABG
;-----------------------------------------

[Install_MPCIEX_Toshiba_3945_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3945_ABG, Reg_Toshiba_3945_ABG_MOW1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3945_ABG, Reg_Toshiba_3945_ABG_MOW2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3945_ABG, Reg_Toshiba_3945_ABG_RoW, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3945_ABG, Reg_Toshiba_3945_ABG_JPN, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3945_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945BG XP64 Toshiba_3945_BGX
;-----------------------------------------

[Install_MPCIEX_Toshiba_3945_BGX_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Toshiba_3945_BGX, Reg_MPCIEX_3945BG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Toshiba_3945_BGX_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3965ABG XP64 Sony_3965_ABG
;-----------------------------------------

[Install_MPCIEX_Sony_3965_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3965_ABG, Reg_Sony_3965_ABG_MOW1, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3965_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3965_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3965_ABG, Reg_Sony_3965_ABG_MOW2, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3965_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3965_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3965_ABG, Reg_Sony_3965_ABG_RoW, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3965_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3965_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3965_ABG, Reg_Sony_3965_ABG_JPN, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3965_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3965_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3965_ABG, Reg_Sony_3965_ABG_KRA, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3965_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 Sony_3945_ABG
;-----------------------------------------

[Install_MPCIEX_Sony_3945_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3945_ABG, Reg_Sony_3945_ABG_MOW1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3945_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3945_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3945_ABG, Reg_Sony_3945_ABG_MOW2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3945_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3945_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3945_ABG, Reg_Sony_3945_ABG_RoW, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3945_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3945_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3945_ABG, Reg_Sony_3945_ABG_JPN, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3945_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_Sony_3945_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_Sony_3945_ABG, Reg_Sony_3945_ABG_KRA, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_Sony_3945_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3965ABG XP64 HP_3965_ABG
;-----------------------------------------

[Install_MPCIEX_HP_3965_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3965_ABG, Reg_HP_3965_ABG_MOW1, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3965_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3965_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3965_ABG, Reg_HP_3965_ABG_MOW2, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3965_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3965_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3965_ABG, Reg_HP_3965_ABG_RoW, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3965_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3965_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3965_ABG, Reg_HP_3965_ABG_JPN, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3965_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3965_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3965_ABG, Reg_HP_3965_ABG_KRA, Reg_MPCIEX_3965ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3965_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 HP_3945_ABG
;-----------------------------------------

[Install_MPCIEX_HP_3945_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3945_ABG, Reg_HP_3945_ABG_MOW1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3945_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3945_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3945_ABG, Reg_HP_3945_ABG_MOW2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3945_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3945_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3945_ABG, Reg_HP_3945_ABG_RoW, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3945_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3945_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3945_ABG, Reg_HP_3945_ABG_JPN, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3945_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_HP_3945_ABG_XP64_KRA]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_HP_3945_ABG, Reg_HP_3945_ABG_KRA, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_HP_3945_ABG_XP64_KRA.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945ABG XP64 IBM_3945_ABG
;-----------------------------------------

[Install_MPCIEX_IBM_3945_ABG_XP64_MOW1]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_IBM_3945_ABG, Reg_IBM_3945_ABG_MOW1, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_IBM_3945_ABG_XP64_MOW1.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_IBM_3945_ABG_XP64_MOW2]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_IBM_3945_ABG, Reg_IBM_3945_ABG_MOW2, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_IBM_3945_ABG_XP64_MOW2.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_IBM_3945_ABG_XP64_RoW]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_IBM_3945_ABG, Reg_IBM_3945_ABG_RoW, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_IBM_3945_ABG_XP64_RoW.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Install_MPCIEX_IBM_3945_ABG_XP64_JPN]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_IBM_3945_ABG, Reg_IBM_3945_ABG_JPN, Reg_MPCIEX_3945ABG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_IBM_3945_ABG_XP64_JPN.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

;-----------------------------------------
; Intel  3945BG XP64 IBM_3945_BG
;-----------------------------------------

[Install_MPCIEX_IBM_3945_BG_XP64]
AddReg         = Reg_Common, Reg_Common_XP64, Reg_IBM_3945_BG, Reg_MPCIEX_3945BG, Reg_NDIS_XP64, Reg_CoInstaller64, Reg_NCPA64, Reg_ALM
Characteristics = 0x84; NCF_HAS_UI, NCF_PHYSICAL
BusType         = 5; PCI bus
CopyFiles       = CopyFiles_Driver_XP64, CopyFiles_NCPA64

[Install_MPCIEX_IBM_3945_BG_XP64.Services]
AddService      = NETw4x64, 2, NIC_Service_XP64, Common_EventLog_XP64

[Reg_Common]
HKR,,ModulationType,2,"2"
HKR,,RecommendedBand,2,"0"
HKR,,RecommendedBeaconInterval,0x10001,0x64
HKR,,CardType,0x00010001,2
HKR,,ConnectionPriority,0,"2"
HKR,,DesiredPortType,0x10003,0x1
HKR,,NdisEnvironment,0x10001,0
HKR,,NetType,0,"WLAN"
HKR,,Provider,0,%PROVIDER_NAME%
HKR,,PibssShortSlot,0x10001,0x1
HKR,,IBSSTxPower,0x00000002,"100"
HKR,,CtsToItself,0x10003,0x1
HKR,,ConfigurationName,0,"PR0W1RELE55"
HKR,,DesiredAuthenticationMode,0x10003,0x0
HKR,,DesiredCipher,0x10003,0x1
HKR,,FixedLongPreamble,0x10001,0x0
HKR,,PropPacketBurstEnabled,0x10003,0x0
HKR,,DesiredPSKey1,0x2,""
HKR,,DesiredPSKey2,0x2,""
HKR,,DesiredPSKey3,0x2,""
HKR,,DesiredPSKey4,0x2,""
HKR,,DesiredDefaultKeyId,0x10003,0x1
HKR,,IbssQosEnabled,0x10003,0x1
HKR,,RecommendedAtimWindow,0x10003,0x0
HKR,,RadioEnable,0x10003,0x1
HKR,,CCXv4FeatureSet,0x10001,0x0
HKR,,WoWLanEnable,0x10001,0x1
HKR,,RoamAggressiveness,0x10003,0x2
HKR,,ApsdTriggerQueues,0x10001,0x0
HKR,,HdEnabled,0x10003,0x0
HKR,,CcxSdkActive,0x10003,0x0
HKR,,CcxVersion,0x10003,0x4

[Reg_ALM]
HKR,,CalibrationActive,0x10001,0x0000001F
HKR,,IEEE11nMode,0x10001,0x00000000
HKR,,CLSGUID,0,"{AA7636EC-77CB-4e5a-9C1C-43950899EAAA}"


[Reg_KDR]
HKR,,ScanMode,0x10001,0x18
HKR,,WatchDogEnabled,0x10001,0x1
HKR,,CalibrationActive,0x10001,0x0000197F
HKR,,ChannelWidth,0x10003,0x1
HKR,,rlcChainSettings,0x10001,0x0
HKR,,ScanChainSelection,0x10001,0x37
HKR,,CLSGUID,0,"{4E82578B-20D2-4709-B663-CC9C3EA9C74A}"
HKR,,FatChannelIntolerant,0x10003,0x0



[Reg_Common_XP64]

[Reg_GEN_4965_AGN]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,IEEE11nMode,0x10003,0x00000001
HKR,,FeatureSet,0x10001,0x01900001

[Reg_GEN_4965_AGN_MOW1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x1

[Reg_GEN_4965_AGN_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_C]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,IEEE11nMode,0x10003,0x00000001
HKR,,FeatureSet,0x10001,0x01900001

[Reg_GEN_4965_AGN_C_MOW1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_C_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x1

[Reg_GEN_4965_AGN_C_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_C_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_C_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_GEN_4965_AG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_4965_AG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_4965_AG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_GEN_4965_AG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_4965_AG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3965_ABG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_GEN_3965_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_3965_ABG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3965_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_GEN_3965_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3965_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3945_ABG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_GEN_3945_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_3945_ABG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3945_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_GEN_3945_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3945_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_GEN_3945_BG]
HKR,,BandType,0x10003,0x0
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_GEN_3945_BGX]
HKR,,BandType,0x10003,0x0
HKR,,DesiredSsid,0x00000002,"Intel 802.11 Default SSID"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Lenovo_4965_AGN]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"WXYZ"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"11"
HKR,,IEEE11nMode,0x10003,0x00000001
HKR,,FeatureSet,0x10001,0x01900001

[Reg_Lenovo_4965_AGN_MOW1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x1

[Reg_Lenovo_4965_AGN_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_C]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"WXYZ"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"11"
HKR,,IEEE11nMode,0x10003,0x00000001
HKR,,FeatureSet,0x10001,0x01900001

[Reg_Lenovo_4965_AGN_C_MOW1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_C_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x1

[Reg_Lenovo_4965_AGN_C_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_C_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_C_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"WXYZ"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Lenovo_4965_AG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Lenovo_4965_AG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Lenovo_4965_AG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_Lenovo_4965_AG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_Lenovo_4965_AG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Lenovo_3965_ABG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"WXYZ"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Lenovo_3965_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0


[Reg_Lenovo_3965_ABG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Lenovo_3965_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_Lenovo_3965_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_Lenovo_3965_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_4965_AGN]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"101"
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"1"
HKR,,IEEE11nMode,0x10003,0x00000001
HKR,,FeatureSet,0x10001,0x01900001

[Reg_Dell_4965_AGN_MOW1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x1

[Reg_Dell_4965_AGN_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_C]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"101"
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"1"
HKR,,IEEE11nMode,0x10003,0x00000001
HKR,,FeatureSet,0x10001,0x01900001

[Reg_Dell_4965_AGN_C_MOW1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_C_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x1

[Reg_Dell_4965_AGN_C_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_C_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_C_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,ForceDuplicateDcr,0x10001,0x0


[Reg_Dell_4965_AG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"101"
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"1"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Dell_4965_AG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0


[Reg_Dell_4965_AG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_4965_AG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_Dell_4965_AG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_4965_AG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_3965_ABG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"101"
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"1"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Dell_3965_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0


[Reg_Dell_3965_ABG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_3965_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_Dell_3965_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_3965_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_3945_ABG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"101"
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"1"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Dell_3945_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0


[Reg_Dell_3945_ABG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_3945_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_Dell_3945_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_Dell_3945_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_Toshiba_3965_ABG]
HKR,,BandType,0x10003,0x2
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"10"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Toshiba_3965_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3965_ABG_MOW2]
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3965_ABG_RoW]
HKR,,RecommendedChannel52,2,"149"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3965_ABG_JPN]
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3965_ABG_KRA]
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3945_ABG]
HKR,,BandType,0x10003,0x2
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"10"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Toshiba_3945_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3945_ABG_MOW2]
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3945_ABG_RoW]
HKR,,RecommendedChannel52,2,"149"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3945_ABG_JPN]
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Toshiba_3945_BGX]
HKR,,BandType,0x10003,0x0
HKR,,LedMode,0x10001,0x1
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"10"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Sony_3965_ABG]
HKR,,BandType,0x10003,0x2
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Sony_3965_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3965_ABG_MOW2]
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3965_ABG_RoW]
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3965_ABG_JPN]
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3965_ABG_KRA]
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3945_ABG]
HKR,,BandType,0x10003,0x2
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_Sony_3945_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3945_ABG_MOW2]
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3945_ABG_RoW]
HKR,,RecommendedChannel52,2,"149"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3945_ABG_JPN]
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Sony_3945_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_HP_3965_ABG]
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"6"
HKR,,BandType,0x10003,0x2
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_HP_3965_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_HP_3965_ABG_MOW2]
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_HP_3965_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_HP_3965_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_HP_3965_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_HP_3945_ABG]
HKR,,BandType,0x10003,0x2
HKR,,LedMode,0x10001,0x2
HKR,,PowerIndex,0x00000002,"6"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_HP_3945_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_HP_3945_ABG_MOW2]
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"
HKR,,IEEE11dMode,0x10001,0x0

[Reg_HP_3945_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_HP_3945_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_HP_3945_ABG_KRA]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_IBM_3945_ABG]
HKR,,BandType,0x10003,0x2
HKR,,DesiredSsid,0x00000002,"WXYZ"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_IBM_3945_ABG_MOW1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_IBM_3945_ABG_MOW2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x0
HKR,,RecommendedChannel52,2,"36"

[Reg_IBM_3945_ABG_RoW]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,RecommendedChannel52,2,"149"

[Reg_IBM_3945_ABG_JPN]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,JPNLegacyChannels,0x10003,0x1
HKR,,RecommendedChannel52,2,"36"

[Reg_IBM_3945_BG]
HKR,,BandType,0x10003,0x0
HKR,,DesiredSsid,0x00000002,"WXYZ"
HKR,,LedMode,0x10001,0x3
HKR,,PowerIndex,0x00000002,"3"
HKR,,RecommendedChannel24,2,"11"
HKR,,FeatureSet,0x10001,0x01907001

[Reg_CoInstaller64]
HKR,,CoInstallers32,0x00010000,"NETw4c64.dll,ClassCoInstallerEntryPoint"

[Reg_NCPA64]
HKR,,EnumPropPages32,0,"NETw4c64.dll,AddWirelessPPToNCPA"

[Reg_MPCIEX_3945ABG]  
HKR,,Diversity11a,0x10003,0x0
HKR,,Diversity11b,0x10003,0x0
HKR,,Diversity11g,0x10003,0x0
HKR,,AdapterModel,0,%NIC_MPCIEX_AdapterModel_3945ABG%
HKR,,DriverDesc,0,%NIC_DriverDesc_3945ABG%

[Reg_MPCIEX_3945BG]  
HKR,,Diversity11a,0x10003,0x0
HKR,,Diversity11b,0x10003,0x0
HKR,,Diversity11g,0x10003,0x0
HKR,,AdapterModel,0,%NIC_MPCIEX_AdapterModel_3945BG%
HKR,,DriverDesc,0,%NIC_DriverDesc_3945BG%

[Reg_MPCIEX_3965ABG]  
HKR,,Diversity11a,0x10003,0x3
HKR,,Diversity11b,0x10003,0x3
HKR,,Diversity11g,0x10003,0x3
HKR,,AdapterModel,0,%NIC_MPCIEX_AdapterModel_3965ABG%
HKR,,DriverDesc,0,%NIC_DriverDesc_3965ABG%

[Reg_MPCIEX_4965AGN] 
HKR,,Diversity11a,0x10003,0x0
HKR,,Diversity11b,0x10003,0x0
HKR,,Diversity11g,0x10003,0x0 
HKR,,AdapterModel,0,%NIC_MPCIEX_AdapterModel_4965AGN%
HKR,,DriverDesc,0,%NIC_DriverDesc_4965AGN%

[Reg_MPCIEX_4965AG]  
HKR,,Diversity11a,0x10003,0x0
HKR,,Diversity11b,0x10003,0x0
HKR,,Diversity11g,0x10003,0x0
HKR,,AdapterModel,0,%NIC_MPCIEX_AdapterModel_4965AG%
HKR,,DriverDesc,0,%NIC_DriverDesc_4965AG%

[Reg_NDIS_XP64]
HKR, Ndi\Interfaces,  UpperRange,   0, "ndis5,wifipro"
HKR, Ndi\Interfaces,  LowerRange,   0, "ethernet,wifimon"
HKR, Ndi,             Service,      0, "NETw4x64"

[Common_EventLog_XP64]
AddReg = Reg_CommonAddEventLog_XP64

[Reg_CommonAddEventLog_XP64]
HKR,, EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll;%%SystemRoot%%\System32\Drivers\NETw4x64.sys"
HKR,, TypesSupported,   0x00010001, 7

[Reg_GEN_3945_ABG_SP1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_3945_ABG_SP2]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_3945_ABG_SP3]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_3945_ABG_SP4]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_4965_AGN_C_SP1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_C_SP2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_C_SP3]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_SP1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_SP2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AGN_SP3]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_GEN_4965_AG_SP1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_4965_AG_SP2]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_GEN_4965_AG_SP3]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Lenovo_4965_AGN_C_SP1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_C_SP2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_C_SP3]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_SP1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_SP2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AGN_SP3]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Lenovo_4965_AG_SP1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Lenovo_4965_AG_SP2]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Lenovo_4965_AG_SP3]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Dell_4965_AGN_C_SP1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_C_SP2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_C_SP3]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_SP1]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_SP2]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AGN_SP3]
HKR,,IEEE11dMode,0x10001,0x0
HKR,,ForceDuplicateDcr,0x10001,0x0

[Reg_Dell_4965_AG_SP1]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Dell_4965_AG_SP2]
HKR,,IEEE11dMode,0x10001,0x0

[Reg_Dell_4965_AG_SP3]
HKR,,IEEE11dMode,0x10001,0x0

[NIC_Service_XP64]
DisplayName = %NIC_Service_DispName_XP64%
ServiceType     = 1 ;%SERVICE_KERNEL_DRIVER%
StartType       = 3 ;%SERVICE_DEMAND_START%
ErrorControl    = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary = %12%\NETw4x64.sys
LoadOrderGroup  = NDIS

[Common_EventLog_XP64]
AddReg = Reg_CommonAddEventLog_XP64

;-----------------------------------------
; DestinationDirs

[CopyFiles_Driver_XP64]
NETw4x64.sys,,,2


[CopyFiles_NCPA64]
NETw4c64.dll,,,2
NETw4r64.dll,,,2

[SourceDisksNames]
1=%SOURCEDISK1%,,

[SourceDisksFiles]
NETw4x64.sys   = 1,,
NETw4c64.dll = 1,,
NETw4r64.dll = 1,,

[DestinationDirs]
DefaultDestDir            = 11 ; Windows\System32
CopyFiles_Driver_XP64=12;Windows\System32\Drivers
CopyFiles_NCPA64          = 11 ; Windows\System32

[Strings]
PROVIDER_NAME                      = "Intel"
COMPANY_NAME                       = "Intel Corporation"

NIC_MPCIEX_3945ABG                 = "Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  = "Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 = "Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  = "Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 = "Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  = "Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    = "Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     = "Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    = "Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     = "Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    = "Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     = "Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             = "Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       = "Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  = "Intel(R) Wireless WiFi Link 3945ABG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_3945BG              = "Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   = "Intel(R) Wireless WiFi Link 3945BG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             = "Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  = "Intel(R) Wireless WiFi Link 3965ABG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_3965BG              = "Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   = "Intel(R) Wireless WiFi Link 3965BG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             = "Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  = "Intel(R) Wireless WiFi Link 4965AGN Adapter Driver for Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   = "Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   = "Intel(R) Wireless WiFi Link 4965AG Adapter Driver for Windows XP 64 Bit"

NIC_Service_DispName_XP64          = "Intel(R) Wireless WiFi Link Adapter Driver for Windows XP 64 Bit"

SOURCEDISK1                        = "Intel(R) Wireless WiFi Link 4965AGN Install Disk"


[Strings.0401] ; Arabic (Saudi Arabia)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link 3945ABG áäÙÇã Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link 3945BG áäÙÇã Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link 3965ABG áäÙÇã Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link 3965BG áäÙÇã Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link 4965AGN áäÙÇã Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link 4965AG áäÙÇã Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="ÈÑäÇãÌ ÊÔÛíá ãÍæá Intel(R) Wireless WiFi Link áäÙÇã Windows XP 64 Bit"

SOURCEDISK1                        ="ÞÑÕ ÊËÈíÊ Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0804] ; Chinese (Simplified)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Intel(R) Wireless WiFi Link 3945ABG ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XT 64 Î»£©"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Intel(R) Wireless WiFi Link 3945BG ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XP 64 Î»£©"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Intel(R) Wireless WiFi Link 3965ABG ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XP 64 Î»£©"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Intel(R) Wireless WiFi Link 3965BG ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XP 64 Î»£©"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Intel(R) Wireless WiFi Link 4965AGN ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XP 64 Î»£©"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Intel(R) Wireless WiFi Link 4965AG ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XP 64 Î»£©"

NIC_Service_DispName_XP64          ="Intel(R) Wireless WiFi Link ÊÊÅäÆ÷Çý¶¯³ÌÐò£¨ÊÊÓÃÓÚ Windows XT 64 Î»£©"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN °²×°ÅÌ"


[Strings.0404] ; Chinese (Traditional)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3945ABG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3945BG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3965ABG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3965BG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 4965AGN ¤¶*±¥dÅX°Êµ{¦¡"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 4965AG ¤¶*±¥dÅX°Êµ{¦¡"

NIC_Service_DispName_XP64          ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link ¤¶*±¥dÅX°Êµ{¦¡"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN ¦w¸ËºÏºÐ"


[Strings.0405] ; Czech (Czech Republic)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Ovladaè adaptéru Intel(R) Wireless WiFi Link 3945ABG pro systém Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Ovladaè adaptéru Intel(R) Wireless WiFi Link 3945BG pro systém Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Ovladaè adaptéru Intel(R) Wireless WiFi Link 3965ABG pro systém Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Ovladaè adaptéru Intel(R) Wireless WiFi Link 3965BG pro systém Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Ovladaè adaptéru Intel(R) Wireless WiFi Link 4965AGN pro systém Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Ovladaè adaptéru Intel(R) Wireless WiFi Link 4965AG pro systém Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Ovladaè adaptéru Intel(R) Wireless WiFi Link pro systém Windows XP 64 Bit"

SOURCEDISK1                        ="Instalaèní disk adaptéru Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0406] ; Danish (Denmark)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Intel(R) Wireless WiFi Link 3945BG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Intel(R) Wireless WiFi Link 3965ABG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Intel(R) Wireless WiFi Link 3965BG Adapter Driver for Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Intel(R) Wireless WiFi Link 4965AGN Adapter Driver for Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Intel(R) Wireless WiFi Link 4965AG Adapter Driver for Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Intel(R) Wireless WiFi Link Adapter Driver for Windows XP 64 Bit"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN Install Disk"


[Strings.0407] ; German (Germany)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Intel(R) Wireless WiFi Link 3945ABG Adaptertreiber für Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Intel(R) Wireless WiFi Link 3945BG Adaptertreiber für Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Intel(R) Wireless WiFi Link 3965ABG Adaptertreiber für Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Intel(R) Wireless WiFi Link 3965BG Adaptertreiber für Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Intel(R) Wireless WiFi Link 4965AGN Adaptertreiber für Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Intel(R) Wireless WiFi Link 4965AG Adaptertreiber für Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Intel(R) Wireless WiFi Link Adaptertreiber für Windows XP 64 Bit"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN Installationsdisk"


[Strings.0408] ; Greek (Greece)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link 3945ABG ãéá Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link 3945BG ãéá Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link 3965ABG ãéá Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link 3965BG ãéá Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link 4965AGN ãéá Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link 4965AG ãéá Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Ðñüãñáììá ïäÞãçóçò ðñïóáñìïãÝá Intel(R) Wireless WiFi Link ãéá Windows XP 64 Bit"

SOURCEDISK1                        ="ÄéóêÝôá åãêáôÜóôáóçò Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0C0A] ; Spanish (Spain)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Controlador del adaptador Intel(R) Wireless WiFi Link 3945ABG para Windows XP de 64 bits"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Controlador del adaptador Intel(R) Wireless WiFi Link 3945BG para Windows XP de 64 bits"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Controlador del adaptador Intel(R) Wireless WiFi Link 3965ABG para Windows XP de 64 bits"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Controlador del adaptador Intel(R) Wireless WiFi Link 3965BG para Windows XP de 64 bits"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Controlador del adaptador Intel(R) Wireless WiFi Link 4965AGN para Windows XP de 64 bits"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Controlador del adaptador Intel(R) Wireless WiFi Link 4965AG para Windows XP de 64 bits"

NIC_Service_DispName_XP64          ="Controlador del adaptador Intel(R) Wireless WiFi Link para Windows XP de 64 bits"

SOURCEDISK1                        ="Disco de instalación de Intel(R) Wireless WiFi Link 4965AGN"


[Strings.040B] ; Finnish (Finland)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Intel(R) Wireless WiFi Link 3945ABG -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Intel(R) Wireless WiFi Link 3945BG -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Intel(R) Wireless WiFi Link 3965ABG -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Intel(R) Wireless WiFi Link 3965BG -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Intel(R) Wireless WiFi Link 4965AGN -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Intel(R) Wireless WiFi Link 4965AG -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"

NIC_Service_DispName_XP64          ="Intel(R) Wireless WiFi Link -sovitinohjain Windows XP 64-bit -käyttöjärjestelmään"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN -asennuslevy"


[Strings.040C] ; French (France)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Pilote de carte Intel(R) Wireless WiFi Link 3945ABG pour Windows XP 64 bits"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Pilote de carte Intel(R) Wireless WiFi Link 3945BG pour Windows XP 64 bits"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Pilote de carte Intel(R) Wireless WiFi Link 3965ABG pour Windows XP 64 bits"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Pilote de carte Intel(R) Wireless WiFi Link 3965BG pour Windows XP 64 bits"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Pilote de carte Intel(R) Wireless WiFi Link 4965AGN pour Windows XP 64 bits"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Pilote de carte Intel(R) Wireless WiFi Link 4965AG pour Windows XP 64 bits"

NIC_Service_DispName_XP64          ="Pilote de carte Intel(R) Wireless WiFi Link pour Windows XP 64 bits"

SOURCEDISK1                        ="Disque d'installation de la carte Intel(R) Wireless WiFi Link 4965AGN"


[Strings.040D] ; Hebrew (Israel)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link 3945ABG òáåø Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link 3945BG òáåø Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link 3965ABG òáåø Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link 3965BG òáåø Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link 4965AGN òáåø Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link 4965AG òáåø Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="îðäì äú÷ï ùì îúàí Intel(R) Wireless WiFi Link  òáåø Windows XP 64 Bit"

SOURCEDISK1                        ="ãéñ÷ äú÷ðä ùì Intel(R) Wireless WiFi Link 4965AGN"


[Strings.040E] ; Hungarian (Hungary)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Intel(R) Wireless WiFi Link 3945ABG adapter illesztõprogram 64 bites Windows XP-hez"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Intel(R) Wireless WiFi Link 3945BG adapter illesztõprogram 64 bites Windows XP-hez"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Intel(R) Wireless WiFi Link 3965ABG adapter illesztõprogram 64 bites Windows XP-hez"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Intel(R) Wireless WiFi Link 3965BG adapter illesztõprogram 64 bites Windows XP-hez"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Intel(R) Wireless WiFi Link 4965AGN adapter illesztõprogram 64 bites Windows XP-hez"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Intel(R) Wireless WiFi Link 4965AG adapter illesztõprogram 64 bites Windows XP-hez"

NIC_Service_DispName_XP64          ="Intel(R) Wireless WiFi Link adapter illesztõprogram 64 bites Windows XP-hez"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN telepítõ lemez"


[Strings.0410] ; Italian (Italy)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Driver scheda Intel(R) Wireless WiFi Link 3945ABG per Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Driver scheda Intel(R) Wireless WiFi Link 3945BG per Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Driver scheda Intel(R) Wireless WiFi Link 3965ABG per Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Driver scheda Intel(R) Wireless WiFi Link 3965BG per Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Driver scheda Intel(R) Wireless WiFi Link 4965AGN per Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Driver scheda Intel(R) Wireless WiFi Link 4965AG per Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Driver scheda Intel(R) Wireless WiFi Link per Windows XP 64 Bit"

SOURCEDISK1                        ="Disco di installazione per Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0411] ; Japanese (Japan)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 3945ABG &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 3945BG &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 3965ABG &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 3965BG &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 4945AGN &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 4965AG &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"

NIC_Service_DispName_XP64          ="Windows XP 64 &#402;r&#402;b&#402;g&#8212;p&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link &#402;A&#402;_&#402;v&#402;^ &#402;h&#402;&#8240;&#402;C&#402;o"

SOURCEDISK1                        ="&#402;C&#402;&#8220;&#402;e&#402;&#8249;(R) Wireless WiFi Link 4965AGN &#402;C&#402;&#8220;&#402;X&#402;g[&#402;&#8249; &#402;f&#402;B&#402;X&#402;N"


[Strings.0412] ; Korean (Korea)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 3945ABG ¾î´ðÅÍ µå¶óÀÌ¹ö"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 3945BG ¾î´ðÅÍ µå¶óÀÌ¹ö"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 3965ABG ¾î´ðÅÍ µå¶óÀÌ¹ö"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 3965BG ¾î´ðÅÍ µå¶óÀÌ¹ö"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 4965AGN ¾î´ðÅÍ µå¶óÀÌ¹ö"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 4965AG ¾î´ðÅÍ µå¶óÀÌ¹ö"

NIC_Service_DispName_XP64          ="Windows XP 64ºñÆ®¿ë ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© ¾î´ðÅÍ µå¶óÀÌ¹ö"

SOURCEDISK1                        ="ÀÎÅÚ(R) ¹«¼± WiFi ¸µÅ© 4965AGN ¼³Ä¡ µð½ºÅ©"


[Strings.0413] ; Dutch (Netherlands)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Stuurprogramma voor Intel(R) Wireless WiFi Link 3945ABG Adapter onder Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Stuurprogramma voor Intel(R) Wireless WiFi Link 3945BG Adapter onder Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Stuurprogramma voor Intel(R) Wireless WiFi Link 3965ABG Adapter onder Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Stuurprogramma voor Intel(R) Wireless WiFi Link 3965BG Adapter onder Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Stuurprogramma voor Intel(R) Wireless WiFi Link 4965AGN Adapter onder Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Stuurprogramma voor Intel(R) Wireless WiFi Link 4965AG Adapter onder Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Stuurprogramma voor Intel(R) Wireless WiFi Link Adapter onder Windows XP 64 Bit"

SOURCEDISK1                        ="Installatieschijf voor Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0414] ; Norwegian (Bokmål) (Norway)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Intel(R) Wireless WiFi Link 3945ABG kortdriver for Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Intel(R) Wireless WiFi Link 3945BG kortdriver for Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Intel(R) Wireless WiFi Link 3965ABG kortdriver for Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Intel(R) Wireless WiFi Link 3965BG kortdriver for Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Intel(R) Wireless WiFi Link 4965AGN kortdriver for Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Intel(R) Wireless WiFi Link 4965AG kortdriver for Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Intel(R) Wireless WiFi Link kortdriver for Windows XP 64 Bit"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN Installasjonsdiskett"


[Strings.0415] ; Polish (Poland)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Sterownik karty Intel(R) Wireless WiFi Link 3945ABG dla systemu Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Sterownik karty Intel(R) Wireless WiFi Link 3945BG dla systemu Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Sterownik karty Intel(R) Wireless WiFi Link 3965ABG dla systemu Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Sterownik karty Intel(R) Wireless WiFi Link 3965BG dla systemu Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Sterownik karty Intel(R) Wireless WiFi Link 4965AGN dla systemu Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Sterownik karty Intel(R) Wireless WiFi Link 4965AG dla systemu Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Sterownik karty Intel(R) Wireless WiFi Link dla systemu Windows XP 64 Bit"

SOURCEDISK1                        ="Dysk instalacyjny Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0416] ; Portuguese (Brazil)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Driver do Adaptador Intel(R) Wireless WiFi Link 3945ABG para Windows XP 64 bits"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Driver do Adaptador Intel(R) Wireless WiFi Link 3945BG para Windows XP 64 bits"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Driver do Adaptador Intel(R) Wireless WiFi Link 3965ABG para Windows XP 64 bits"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Driver do Adaptador Intel(R) Wireless WiFi Link 3965BG para Windows XP 64 bits"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Driver do Adaptador Intel(R) Wireless WiFi Link 4965AGN para Windows XP 64 bits"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Driver do Adaptador Intel(R) Wireless WiFi Link 4965AG para Windows XP 64 bits"

NIC_Service_DispName_XP64          ="Driver do Adaptador Intel(R) Wireless WiFi Link para Windows XP 64 bits"

SOURCEDISK1                        ="Disco da instalação do Intel(R) Wireless WiFi Link 4965AGN"


[Strings.0816] ; Portuguese (Portugal)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) 3945ABG para Windows XP 64 Bits"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) 3945BG para Windows XP 64 Bits"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) 3965ABG para Windows XP 64 Bits"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) 3965BG para Windows XP 64 Bits"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) 4965AGN para Windows XP 64 Bits"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) 4965AG para Windows XP 64 Bits"

NIC_Service_DispName_XP64          ="Controlador do Adaptador da ligação WiFi sem fios Intel(R) para Windows XP 64 Bits"

SOURCEDISK1                        ="Disco de instalação da Ligação WiFi sem fios Intel(R) 4965AGN"


[Strings.0419] ; Russian (Russia)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link 3945ABG äëÿ Windows XP 64 Bit"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link 3945BG äëÿ Windows XP 64 Bit"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link 3965ABG äëÿ Windows XP 64 Bit"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link 3965BG äëÿ Windows XP 64 Bit"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link 4965AGN äëÿ Windows XP 64 Bit"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link 4965AG äëÿ Windows XP 64 Bit"

NIC_Service_DispName_XP64          ="Äðàéâåð àäàïòåðà Intel(R) Wireless WiFi Link äëÿ Windows XP 64 Bit"

SOURCEDISK1                        ="Óñòàíîâî÷íûé äèñê àäàïòåðà Intel(R) Wireless WiFi Link 4965AGN"


[Strings.041D] ; Swedish (Sweden)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link 3945ABG"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link 3945BG"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link 3965ABG"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link 3965BG"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link 4965AGN"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link 4965AG"

NIC_Service_DispName_XP64          ="Kortdrivrutin för Windows XP 64-bitars för Intel(R) Wireless WiFi Link"

SOURCEDISK1                        ="Installationsdisk för Intel(R) Wireless WiFi Link 4965AGN"


[Strings.041E] ; Thai (Thailand)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link 3945ABG ÊÓËÃÑº Windows XP 64 ºÔµ"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link 3945BG ÊÓËÃÑº Windows XP 64 ºÔµ"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link 3965ABG ÊÓËÃÑº Windows XP 64 ºÔµ"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link 3965BG ÊÓËÃÑº Windows XP 64 ºÔµ"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link 4965AGN ÊÓËÃÑº Windows XP 64 ºÔµ"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link 4965AG ÊÓËÃÑº Windows XP 64 ºÔµ"

NIC_Service_DispName_XP64          ="ä´ÃàÇÍÃìÍá´ç»àµÍÃì Intel(R) Wireless WiFi Link ÊÓËÃÑº Windows XP 64 ºÔµ"

SOURCEDISK1                        ="´ÔÊ¡ìµÔ´µÑé§ Intel(R) Wireless WiFi Link 4965AGN"


[Strings.041F] ; Turkish (Turkey)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link 3945ABG Baðdaþtýrýcý Sürücüsü"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link 3945BG Baðdaþtýrýcý Sürücüsü"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link 3965ABG Baðdaþtýrýcý Sürücüsü"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link 3965BG Baðdaþtýrýcý Sürücüsü"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link 4965AGN Baðdaþtýrýcý Sürücüsü"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link 4965AG Baðdaþtýrýcý Sürücüsü"

NIC_Service_DispName_XP64          ="Windows XP 64 Bit için Intel(R) Wireless WiFi Link Baðdaþtýrýcý Sürücüsü"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN Yükleme Diski"


[Strings.0C04] ; Chinese (Hong Kong)
PROVIDER_NAME                      ="Intel"
COMPANY_NAME                       ="Intel Corporation"

NIC_MPCIEX_3945ABG                 ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_3945BG                  ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_3965ABG                 ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_3965BG                  ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_4965AGN                 ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_4965AG                  ="Intel(R) Wireless WiFi Link 4965AG"

NIC_MPCIEX_AdapterModel_3945ABG    ="Intel(R) PRO/Wireless 3945ABG Network Connection"
NIC_MPCIEX_AdapterModel_3945BG     ="Intel(R) PRO/Wireless 3945BG Network Connection"
NIC_MPCIEX_AdapterModel_3965ABG    ="Intel(R) PRO/Wireless 3965ABG Network Connection"
NIC_MPCIEX_AdapterModel_3965BG     ="Intel(R) PRO/Wireless 3965BG Network Connection"
NIC_MPCIEX_AdapterModel_4965AGN    ="Intel(R) Wireless WiFi Link 4965AGN"
NIC_MPCIEX_AdapterModel_4965AG     ="Intel(R) Wireless WiFi Link 4965AG"

NIC_DriverDesc_3945ABG             ="Intel(R) Wireless WiFi Link 3945ABG Driver"
NIC_Service_DispName_3945ABG       ="Intel(R) Wireless WiFi Link 3945ABG Adapter Driver"
NIC_Service_DispName_3945ABG_XP64  ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3945ABG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_3945BG              ="Intel(R) Wireless WiFi Link 3945BG Driver"
NIC_Service_DispName_3945BG_XP64   ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3945BG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_3965ABG             ="Intel(R) Wireless WiFi Link 3965ABG Driver"
NIC_Service_DispName_3965ABG_XP64  ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3965ABG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_3965BG              ="Intel(R) Wireless WiFi Link 3965BG Driver"
NIC_Service_DispName_3965BG_XP64   ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 3965BG ¤¶*±¥dÅX°Êµ{¦¡"
NIC_DriverDesc_4965AGN             ="Intel(R) Wireless WiFi Link 4965AGN Driver"
NIC_Service_DispName_4965AGN_XP64  ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 4965AGN ¤¶*±¥dÅX°Êµ{¦¡"

NIC_DriverDesc_4965AG          	   ="Intel(R) Wireless WiFi Link 4965AG Driver"
NIC_Service_DispName_4965AG_XP64   ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link 4965AG ¤¶*±¥dÅX°Êµ{¦¡"

NIC_Service_DispName_XP64          ="¥Î©ó Windows XP 64 Bit ªº Intel(R) Wireless WiFi Link ¤¶*±¥dÅX°Êµ{¦¡"

SOURCEDISK1                        ="Intel(R) Wireless WiFi Link 4965AGN ¦w¸ËºÏºÐ"

```

---

### Post by kevmitch on 2008-07-02
As far as I can tell, you pretty much have to accept a given .inf as it is. Either it works for your card and kernel, or it doesn't. Just to confirm, you are running a 64 bit kernel right? If you are, then it doesn't look like the prognosis is good for getting ndiswrapper up and running.

Something else you could try is to download the latest native linux driver and microcode from the intel website [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

Similarly, you probably want to check if your router has a firmware update available.

As for your current bootup issues, from the livecd, edit your /etc/modprobe.d/blacklist file to add the following lines:
```

blacklist ndiswrappwer
blacklist iwl4965

```
and remove any mention of the above two modules from /etc/modules. That should at least get you back into your system.

Once you get either iwl4965 or ndiswrapper working, you'll want to remove the blacklist from that driver and possibly add it to /etc/modules to get it to load on boot.

---

### Post by Vasto on 2008-07-03
> **kevmitch said:**
> 
Something else you could try is to download the latest native linux driver and microcode from the intel website [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)
I was using that before, and it worked perfectly at school. The problem is at home I have a 2wire router. There are bugreports in Launchpad about it, and in the IntelWireless Bugzilla (It says it is assigned, so hopefully it gets fixed eventually.)

> **kevmitch said:**
> 
Similarly, you probably want to check if your router has a firmware update available.

2wire won't respond to my emails for requests of an updated driver. I called ATT and they told me that 2wire routers don't work with Linux. (LIE). ATT just controls what firmware gets released to their customers, and 2wire is an evil company with no sympathy. (Newest firmware is 3.7.x--unrealsed to ATT subscribers, I have 3.5.5 which is the newest one ATT has out.)

> **kevmitch said:**
> 
As for your current bootup issues, from the livecd, edit your /etc/modprobe.d/blacklist file to add the following lines:
```

blacklist ndiswrappwer
blacklist iwl4965

```
and remove any mention of the above two modules from /etc/modules. That should at least get you back into your system.

I added both to the blacklist. I also added ndiswrapper because I assumed you mispelt it, but wanted to be safe anyways, and I also added iw14965 because I couldn't tell if it was an 1 or L. Anyways, now sometimes hardware drives [FAIL] comes up, other times the system just hangs. It's starting to look like I might have to back up some data and reformat.

---

### Post by kevmitch on 2008-07-04
Yeah, sorry about that it was indeed "ndiswrappwer" and it was a lower case "L" in "iwl". It would seem that either udev is not listening to your blacklist, or something other than your wireless card is the problem. 

From the live cd, can you go in and see what's in /var/log/syslog after a failed boot?

---

