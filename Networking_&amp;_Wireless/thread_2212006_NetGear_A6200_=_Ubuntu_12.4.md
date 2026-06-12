---
title: "NetGear A6200 = Ubuntu 12.4"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by Sam_Nicholson on 2014-03-18
I've just fresh installed Ubunti 12.4 LTS and I'm trying to configure my NetGear A6200 wireless adapter. I have NO lan connection available so everything I've needed I've been transporting using a USB from my Windows laptop.

I've used ndiswrapper 1.59 to install the A6200 linux driver extracted from the .exe.

I followed this guide [http://hansengel.wordpress.com/2007/11/10/installing-a-wireless-driver-with-ndiswrapper/](http://hansengel.wordpress.com/2007/11/10/installing-a-wireless-driver-with-ndiswrapper/)

However, the driver does not start properly until I use the command modprobe ndiswrapper. - After using that all my wireless networks appear! (Until I reboot).

However when trying to connect to my network it refused to accept my wireless key under WPA/WPA2. I'm using the same network and key as my laptop yet it does not connect.

Please linux gurus tell me what to do!

Oh and please note my frustration, the above synopsis comes from almost 4 hours or research and stumbling...

---

### Post by chili555 on 2014-03-18
What informative clues can we glean here?```
arch
dmesg | grep ndis
ndiswrapper -l
```> However, the driver does not start properly until I use the command modprobe ndiswrapper. - After using that all my wireless networks appear! (Until I reboot).Easy to fix:```
sudo -i
echo ndiswrapper  >>  /etc/modules
exit
```Compiling from source code using a 2007 tutorial wouldn't have been my first choice, but let's see.

---

### Post by Sam_Nicholson on 2014-03-18
Thank god, I'd hoped you'd reply, please note this my first time on linux :/

```

sam@sam-linux:~$ arch
x86_64
sam@sam-linux:~$ dmesg | grep ndis
[   17.007751] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   17.009082] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   17.256456] ndiswrapper: driver bcmwlhigh5 (NETGEAR,Inc.,08/01/2012, 6.30.61.21) loaded
[   17.258849] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b1e000, 32000, 8
[   17.258852] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b25d00, 32000, 9
[   17.258854] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b2da00, 32000, 9
[   17.258856] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b35700, 32000, 9
[   17.258857] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b3d400, 32000, 9
[   17.258859] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b45100, 32000, 8
[   17.258860] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b4ce00, 32000, 9
[   17.258862] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b54b00, 32000, 9
[   17.258863] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b5c800, 32000, 9
[   17.258865] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b64500, 32000, 9
[   17.258866] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b6c200, 32000, 8
[   17.258867] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b73f00, 32000, 9
[   17.258868] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b7bc00, 32000, 9
[   17.258870] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b83900, 32000, 9
[   17.258871] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b8b600, 32000, 9
[   17.258880] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b93300, 32000, 8
[   17.258882] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b9b000, 32000, 8
[   17.258883] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ba2d00, 32000, 9
[   17.258885] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007baaa00, 32000, 9
[   17.258886] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bb2700, 32000, 9
[   17.258888] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bba400, 32000, 9
[   17.258889] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bc2100, 32000, 8
[   17.258891] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bc9e00, 32000, 9
[   17.258892] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bd1b00, 32000, 9
[   17.258893] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bd9800, 32000, 9
[   17.258895] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007be1500, 32000, 9
[   17.258896] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007be9200, 32000, 8
[   17.258897] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bf0f00, 32000, 9
[   17.258899] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bf8c00, 32000, 9
[   17.258900] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c00900, 32000, 9
[   17.258902] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c08600, 32000, 9
[   17.258903] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c10300, 32000, 8
[   17.258904] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c18000, 32000, 8
[   17.258906] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c1fd00, 32000, 9
[   17.258907] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c27a00, 32000, 9
[   17.258908] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c2f700, 32000, 9
[   17.258910] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c37400, 32000, 9
[   17.258911] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c3f100, 32000, 8
[   17.258912] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c46e00, 32000, 9
[   17.258914] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c4eb00, 32000, 9
[   17.258915] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c56800, 32000, 9
[   17.258916] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c5e500, 32000, 9
[   17.258918] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c66200, 32000, 8
[   17.258919] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c6df00, 32000, 9
[   17.258920] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c75c00, 32000, 9
[   17.258922] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c7d900, 32000, 9
[   17.258923] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c85600, 32000, 9
[   17.258924] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c8d300, 32000, 8
[   17.258926] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c95000, 32000, 8
[   17.258927] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c9cd00, 32000, 9
[   39.264337] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   39.264342] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   39.264346] ndiswrapper (mp_halt:254): device ffff880210025800 is not initialized - not halting
[   39.264347] ndiswrapper: device eth%d removed
[   39.264415] ndiswrapper: probe of 3-3:1.0 failed with error -22
[   39.264447] usbcore: registered new interface driver ndiswrapper
[ 1660.762670] ndiswrapper: driver bcmwlhigh5 (NETGEAR,Inc.,08/01/2012, 6.30.61.21) loaded
[ 1661.055931] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c1f000, 32000, 8
[ 1661.055938] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c26d00, 32000, 9
[ 1661.055941] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c2ea00, 32000, 9
[ 1661.055944] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c36700, 32000, 9
[ 1661.055946] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c3e400, 32000, 9
[ 1661.055949] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c46100, 32000, 8
[ 1661.055952] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c4de00, 32000, 9
[ 1661.055955] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c55b00, 32000, 9
[ 1661.055957] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c5d800, 32000, 9
[ 1661.055960] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c65500, 32000, 9
[ 1661.055963] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c6d200, 32000, 8
[ 1661.055966] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c74f00, 32000, 9
[ 1661.055969] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c7cc00, 32000, 9
[ 1661.055972] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c84900, 32000, 9
[ 1661.055975] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c8c600, 32000, 9
[ 1661.055977] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c94300, 32000, 8
[ 1661.055980] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c9c000, 32000, 8
[ 1661.055983] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ca3d00, 32000, 9
[ 1661.055986] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007caba00, 32000, 9
[ 1661.055988] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cb3700, 32000, 9
[ 1661.055991] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cbb400, 32000, 9
[ 1661.055994] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cc3100, 32000, 8
[ 1661.055996] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ccae00, 32000, 9
[ 1661.055999] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cd2b00, 32000, 9
[ 1661.056003] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cda800, 32000, 9
[ 1661.056006] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ce2500, 32000, 9
[ 1661.056008] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cea200, 32000, 8
[ 1661.056011] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cf1f00, 32000, 9
[ 1661.056014] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007cf9c00, 32000, 9
[ 1661.056017] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d01900, 32000, 9
[ 1661.056020] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d09600, 32000, 9
[ 1661.056023] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d11300, 32000, 8
[ 1661.056025] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d19000, 32000, 8
[ 1661.056028] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d20d00, 32000, 9
[ 1661.056031] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d28a00, 32000, 9
[ 1661.056034] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d30700, 32000, 9
[ 1661.056037] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d38400, 32000, 9
[ 1661.056040] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d40100, 32000, 8
[ 1661.056043] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d47e00, 32000, 9
[ 1661.056046] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d4fb00, 32000, 9
[ 1661.056048] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d57800, 32000, 9
[ 1661.056051] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d5f500, 32000, 9
[ 1661.056054] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d67200, 32000, 8
[ 1661.056056] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d6ef00, 32000, 9
[ 1661.056059] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d76c00, 32000, 9
[ 1661.056062] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d7e900, 32000, 9
[ 1661.056065] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d86600, 32000, 9
[ 1661.056067] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d8e300, 32000, 8
[ 1661.056070] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d96000, 32000, 8
[ 1661.056073] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007d9dd00, 32000, 9
[ 1661.072440] ndiswrapper (ndis_encode_setting:383): unknown type: 3
sam@sam-linux:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
	device (0846:9050) present

```

---

### Post by chili555 on 2014-03-18
Now I think I see why the driver doesn't seem to load on boot. It does load and bails out:> [   39.264342] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   39.264346] ndiswrapper (mp_halt:254): device ffff880210025800 is not initialized - not halting
[   39.264347] ndiswrapper: device eth%d removed
[   39.264415] ndiswrapper: probe of 3-3:1.0 failed with error -22
[   39.264447] usbcore: registered new interface driver ndiswrapper...and then succeeds when you modprobe it:> [ 1660.762670] ndiswrapper: driver bcmwlhigh5 (NETGEAR,Inc.,08/01/2012, 6.30.61.21) loadedWeird.

Are you certain you have installed the x64 and Windows *XP* .inf and .sys files? 

This may be the first clue that we ought to try the Ubuntu-ized ndiswrapper .debs instead of the generic one-size-maybe-fits-all tar.gz. 

If it is specifically me you wanted, it is perfectly acceptable, all you searchers, to PM me and ask if I'd take a look at your post. I seldom refuse a polite invitation.

---

### Post by Sam_Nicholson on 2014-03-18
Damn, I followed a few guides at once and I don't remember that step. Can you please tell me how I can completely remove the driver and ndiswrapper and then perhaps link me to a guide I should follow to re-install? 

Bare in mind I have no internet so I have to compile and install. I only requested you as my google searches returned threads where you did some really helpful troubleshooting and I was hoping you would do the same for me.

---

### Post by chili555 on 2014-03-18
I don't think we're at that point yet. Can you open the .inf file with gedit? Does it read something like this?> ;;
;; bcmwlhigh5.inf
;;
;; Copyright 1998-2012, NETGEAR,Inc.
;; All Rights Reserved.
;;
;; This is UNPUBLISHED PROPRIETARY SOURCE CODE of ,NETGEAR,Inc.
;; the contents of this file may not be disclosed to third parties, copied or
;; duplicated in any form, in whole or in part, without the prior written
;; permission of NETGEAR,Inc.
;;

[version]
	Signature	= "$Windows NT$"		; Combined [COLOR="#FF0000"]WinXP[/COLOR]/Vista inf
	Class           = Net
	ClassGUID	= {4d36e972-e325-11ce-bfc1-08002be10318}
	Provider	= %NTGR%
	Compatible	= 1
DriverVer=08/01/2012, 6.30.61.21
	CatalogFile	= bcmh43xx.cat
	CatalogFile.NTamd64=bcmh43xx64.cat

; From Windows Server 2003 SP1, Manufacturer requires amd64 declaration 
; 	to differentiate with ia64
[Manufacturer]
	%NTGR% = NETGEAR, [COLOR="#FF0000"]NTamd64[/COLOR]
If those parts aren't in it, you simply need more appropriate .inf and .sys files. I think we should address that first, before we resort to dynamite!

---

### Post by Sam_Nicholson on 2014-03-18
Here's the .inf file contents

```

;;
;; bcmwlhigh5.inf
;;
;; Copyright 1998-2012, NETGEAR,Inc.
;; All Rights Reserved.
;;
;; This is UNPUBLISHED PROPRIETARY SOURCE CODE of ,NETGEAR,Inc.
;; the contents of this file may not be disclosed to third parties, copied or
;; duplicated in any form, in whole or in part, without the prior written
;; permission of NETGEAR,Inc.
;;


[version]
	Signature	= "$Windows NT$"		; Combined WinXP/Vista inf
	Class           = Net
	ClassGUID	= {4d36e972-e325-11ce-bfc1-08002be10318}
	Provider	= %NTGR%
	Compatible	= 1
DriverVer=08/01/2012, 6.30.61.21
	CatalogFile	= bcmh43xx.cat
	CatalogFile.NTamd64=bcmh43xx64.cat


; From Windows Server 2003 SP1, Manufacturer requires amd64 declaration 
; 	to differentiate with ia64
[Manufacturer]
	%NTGR% = NETGEAR, NTamd64


[ControlFlags] 
	ExcludeFromSelect = *


;       DisplayName             Section         DeviceID
;       -----------             -------         --------


;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[NETGEAR.NTamd64]
	%NTGRA6200_DeviceDesc% = BCM43XNMD, USB\VID_0846&PID_9050


;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[NETGEAR]
	%NTGRA6200_DeviceDesc% = BCM43XNMD, USB\VID_0846&PID_9050




-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) WinXP
;




[BCM43XNMD.NTamd64]
	Characteristics	= 0x84	; NCF_PHYSICAL | NCF_HAS_UI
	BusType		= 15	; PNP bus
	AddReg		= BCM43XX.reg, BCMH43XX.brcm.reg, common.reg, common.prevista.reg, bagn.options.reg, bagn40.options.reg, na20.channels.reg, na40.channels.reg, nbg20.channels.reg, nbg40.channels.reg
	DelReg          = common.delreg
	CopyFiles	= BCM43XNXD.files.NTamd64


[BCM43XNMD.NTamd64.Services]
	AddService = A6200, 2, A6200.Service.NTamd64, common.EventLog




;-----------------------------------------------------------------
; x86 - Win2k, WinXP
;


[BCM43XNMD.NT]
	Characteristics	= 0x84	; NCF_PHYSICAL | NCF_HAS_UI
	BusType		= 15	; PNP bus
	AddReg		= BCM43XX.reg, BCMH43XX.brcm.reg, common.reg, common.prevista.reg, bagn.options.reg, bagn40.options.reg, na20.channels.reg, na40.channels.reg, nbg20.channels.reg, nbg40.channels.reg
	DelReg          = common.delreg
	CopyFiles	= BCM43XNXD.files.NT


[BCM43XNMD.NT.Services]
	AddService = A6200, 2, A6200.Service.NT, common.EventLog




;-----------------------------------------------------------------
; NT systems
;
[BCM43XX.reg]
	; Ndis Info
	; Interfaces
	HKR,	Ndi\Interfaces,	UpperRange,	,	"ndis5"
	HKR,	Ndi\Interfaces,	LowerRange,	,	"ethernet"


[BCMH43XX.brcm.reg]
	HKR,	Ndi,	HelpText,		,	%A6200_HELP%
	HKR,	Ndi,	Service,		0,	"A6200"
	HKR,    ,"featureflag",      65537, "0x00000004"


[common.EventLog]
	AddReg = common.AddEventLog.reg


[common.AddEventLog.reg]
	HKR,	,	EventMessageFile,	0x00020000,	"%%SystemRoot%%\System32\netevent.dll"
	HKR,	,	TypesSupported,		0x00010001,	7




;-----------------------------------------------------------------
; service-install-section
; WinXP and 2k


; WinXP and 2k -high
[A6200.Service.NTamd64]
	DisplayName	= %A6200_Service_DispName%
	ServiceType	= 1			; %SERVICE_KERNEL_DRIVER%
	StartType	= 3			; %SERVICE_DEMAND_START%
	ErrorControl	= 1			; %SERVICE_ERROR_NORMAL%
	ServiceBinary	= %12%\bcmwlhigh564.sys
	LoadOrderGroup	= NDIS


; WinXP and 2k -high
[A6200.Service.NT]
	DisplayName	= %A6200_Service_DispName%
	ServiceType	= 1			; %SERVICE_KERNEL_DRIVER%
	StartType	= 3			; %SERVICE_DEMAND_START%
	ErrorControl	= 1			; %SERVICE_ERROR_NORMAL%
	ServiceBinary	= %12%\bcmwlhigh5.sys
	LoadOrderGroup	= NDIS




;-----------------------------------------------------------------
; filename for CopyFiles
;
; Flag = 2 is COPYFLG_NOSKIP (2)
; Flag = 33 is COPYFLG_WARN_IF_SKIP (1) | COPYFLG_NO_VERSION_DIALOG (32)
[BCM43XNXD.files.NTamd64]
	BCMWLHIGH564.SYS,,,6


[BCM43XNXD.files.NT]
	BCMWLHIGH5.SYS,,,6




; 11 == %windir%/system32
; 12 == %windir%/system32/drivers
[DestinationDirs]
	DefaultDestDir                                = 11
	BCM43XNXD.files.NT                            = 12
	BCM43XNXD.files.NTamd64                       = 12
	


[SourceDisksNames]
	1=%A6200_DiskName%,,


; for WinVista specify BCMWL664.SYS
[SourceDisksFiles.amd64]
		bcmwlhigh564.sys=1


; for WinVista specify BCMWL6.SYS
[SourceDisksFiles.x86]
		bcmwlhigh5.sys=1




; for WinVista specify BCMWL6.SYS
[SourceDisksFiles]
		bcmwlhigh5.sys=1




; common for all platform
[common.delreg]
	HKR, Ndi\params\Country
	HKR,,Country
	HKR,	Ndi\params\autoCountryDiscovery
	HKR,,autoCountryDiscovery
	HKR,,"gpiotimerval"
	HKR,,"gpio3"
	HKR,,"gpio2"
	HKR,,"gpio1"
	HKR,,"gpio0"
	HKR, Ndi\params\RoamPref
	HKR, Ndi\params\AssocPref
	HKR, Ndi\params\Locale
	HKR,,Locale
	HKR, Ndi\params\RoamTrigger
	HKR, Ndi\params\WME
	HKR, Ndi\params\MixedCell
	HKR, Ndi\params\Channel
	HKR,,Channel
	HKR, Ndi\params\IBSSGMode
	HKR,,IBSSGMode
	HKR, Ndi\params\Intolerant
	HKR,,Intolerant
	HKR, Ndi\params\BtAmp
	HKR, Ndi\params\OBSSCoex
	HKR,,OBSSCoex
	HKLM,Software\NETGEAR\802.11,SupportedApps
	       		       
[rate.delreg]
	HKR,	Ndi\params\Rate
	HKR,	Ndi\params\RateA


; common for all platform
[common.reg]
	HKR, ,"EnableSoftAP", 0, "0"
	HKR, ,"EnableAutoConnect", 0, "0"


	HKR,	Ndi\params\LOM, ParamDesc,	        0,	%DisableRadioUponWiredConnection%
	HKR,	Ndi\params\LOM, type,		        0,	"enum"
	HKR,	Ndi\params\LOM\enum, "0",		0,	%Disabled%
	HKR,	Ndi\params\LOM\enum, "1",		0,	%Enabled%
	HKR,	Ndi\params\LOM,default,,"0"


	HKR,	Ndi\params\RoamDelta, ParamDesc,	0,	%RoamingTendency%
	HKR,	Ndi\params\RoamDelta, type,		0,	"enum"
	HKR,	Ndi\params\RoamDelta\enum, "0",	        0,	%Aggressive%
	HKR,	Ndi\params\RoamDelta\enum, "1",         0,	%Moderate%
	HKR,	Ndi\params\RoamDelta\enum, "2",         0,	%Conservative%
	HKR,	Ndi\params\RoamDelta\enum, "3",         0,	%Auto%
	HKR,	Ndi\params\RoamDelta,default,,"3"


	HKR,	Ndi\params\MPC, ParamDesc,	        0,	%MinimumPowerConsumption%
	HKR,	Ndi\params\MPC, type,		        0,	"enum"
	HKR,	Ndi\params\MPC\enum, "0",		0,	%Disabled%
	HKR,	Ndi\params\MPC\enum, "1",		0,	%Enabled%
	HKR,	Ndi\params\MPC,default,,"1"


	HKR,	Ndi\params\frag, ParamDesc,	0,	%FragmentationThreshold%
	HKR,	Ndi\params\frag,type,0,"dword"
	HKR,	Ndi\params\frag,min,,"256"
	HKR,	Ndi\params\frag,max,,"2346"
	HKR,	Ndi\params\frag,default,,"2346"


	HKR,	Ndi\params\rts, ParamDesc,	0,	%RTSThreshold%
	HKR,	Ndi\params\rts,type,0,"dword"
	HKR,	Ndi\params\rts,min,,"0"
	HKR,	Ndi\params\rts,max,,"2347"
	HKR,	Ndi\params\rts,default,,"2347"


	HKR,	Ndi\params\NetworkAddress, ParamDesc,	0, %LocallyAdministeredMACAddress%
	HKR,	Ndi\params\NetworkAddress, type,	0, "edit"
	HKR,	Ndi\params\NetworkAddress, LimitText,	0, "12"
	HKR,	Ndi\params\NetworkAddress, UpperCase,  0, "1"
	HKR,	Ndi\params\NetworkAddress, default,	0, ""
	HKR,	Ndi\params\NetworkAddress, optional,	0, "1"


	HKR,	Ndi\params\PwrOut, ParamDesc,	0,	%PowerOutput%
	HKR,	Ndi\params\PwrOut, type,		0,	"enum"
	HKR,	Ndi\params\PwrOut\enum, "100",	0,	"100%"
	HKR,	Ndi\params\PwrOut\enum, "75",	0,	"75%"
	HKR,	Ndi\params\PwrOut\enum, "50",	0,	"50%"
	HKR,	Ndi\params\PwrOut\enum, "25",	0,	"25%"
	HKR,	Ndi\params\PwrOut,default,,"100"


	HKR,	Ndi\params\FrameBursting, ParamDesc,	0,	%XPress_Technology%
	HKR,	Ndi\params\FrameBursting, type,		0,	"enum"
	HKR,	Ndi\params\FrameBursting\enum, "0",		0,	%Disabled%
	HKR,	Ndi\params\FrameBursting\enum, "1",		0,	%Enabled%
	HKR,	Ndi\params\FrameBursting,default,,"0"	


	HKR,	Ndi\params\BTCoexist, ParamDesc,	0,	%BlueToothCollaboration%
	HKR,	Ndi\params\BTCoexist, type,		0,	"enum"
	HKR,	Ndi\params\BTCoexist\enum, "0",	0,	%Disable%
	HKR,	Ndi\params\BTCoexist\enum, "1",	0,	%Enable%
	HKR,	Ndi\params\BTCoexist\enum, "3",	0,	%Auto%
	HKR,	Ndi\params\BTCoexist,default,,"3"


	HKR,	Ndi\params\WakeUpCapabilities, ParamDesc,	0,	%WakeUpCapabilities%
	HKR,	Ndi\params\WakeUpCapabilities, type,		0,	"enum"
	HKR,	Ndi\params\WakeUpCapabilities\enum, "0",	0,	%None%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "1",	0,	%MagicPacket%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "2",	0,	%NetPattern%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "28",	0,	%LossofAP%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "3",	0,	%MagicNet%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "29",	0,	%LossMagic%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "30",	0,	%LossNet%
	HKR,	Ndi\params\WakeUpCapabilities\enum, "31",	0,	%All%
	HKR,	Ndi\params\WakeUpCapabilities,default,,"3"


	HKR,					,"WowlKeyRot", 0, "1"
	HKR,					,"WEP",	0,	""
	HKR,					,"NetworkType",	0,	"-1"
	HKR,					,"SSID",	0,	""


	HKR,					,"ledbh0",	0,	"-1"
	HKR,					,"ledbh1",	0,	"-1"
	HKR,					,"ledbh2",	0,	"-1"
	HKR,					,"ledbh3",	0,	"-1"
	HKR,					,"ledbh9",	0,	"150"
	HKR,					,"ledbh10",	0,	"151"		
	HKR,					,"ledblinkslow",	0,	"0x03E803E8"
	HKR,					,"ledblinkmed",	0,	"-1"
	HKR,					,"ledblinkfast",	0,	"-1"
	HKR,					,"leddc",	0,	"0"


	HKR,					,"scan_channel_time",	0,	"-1"
	HKR,					,"scan_unassoc_time",	0,	"-1"
	HKR,					,"scan_home_time",		0,	"-1"
	HKR,					,"scan_passes",			0,	"-1"


	HKR,					,"BadFramePreempt",		0,	"0"


	HKR,					,"Interference_Mode",		0,	"-1"


	HKR,					,"ccx_rm",			0,	"1"
	HKR,					,"ccx_rm_limit",		0,	"300"


	HKR,					,"EFCEnable",		0,	"0"


	HKR,	Ndi\params\antdiv, ParamDesc,	0,	%AntennaDiversity%
	HKR,	Ndi\params\antdiv, type,	0,	"enum"
	HKR,	Ndi\params\antdiv\enum, "-1",	0,	%Auto%
	HKR,	Ndi\params\antdiv\enum, "0",	0,	%Main%
	HKR,	Ndi\params\antdiv\enum, "1",	0,	%Aux%
	HKR,	Ndi\params\antdiv,default,,"-1"


	HKR,	Ndi\params\WME, ParamDesc,	0,	%WME%
	HKR,	Ndi\params\WME, type,		0,	"enum"
	HKR,	Ndi\params\WME\enum, "-1",	0,	%Auto%
	HKR,	Ndi\params\WME\enum, "1",	0,	%Enabled%
	HKR,	Ndi\params\WME\enum, "0",	0,	%Disabled%
	HKR,	Ndi\params\WME,default,,"-1"
; the next line forces upgrade installation to configure WME value to be -1 
	HKR,	,"WME",0,"-1"


	HKR, 	Ndi\params\MixedCell, ParamDesc,0,	%MixedCell%
	HKR, 	Ndi\params\MixedCell, type,     0, 	"enum"
	HKR, 	Ndi\params\MixedCell\enum, "0", 0,	%Disabled%
	HKR,	Ndi\params\MixedCell\enum, "1", 0,	%Enabled%
	HKR,	Ndi\params\MixedCell,default,,"0"


	HKR,	Ndi\params\BtAmp, ParamDesc,	0,	%BTAMP%
	HKR,	Ndi\params\BtAmp, type,		0,	"enum"
	HKR,	Ndi\params\BtAmp\enum, "0",	0,	%Disabled%
	HKR,	Ndi\params\BtAmp\enum, "1",	0,	%Enabled%
	HKR,	Ndi\params\BtAmp,default,,"0"
	HKR, 	,IovarOverrides, 0x00010008, "iovar:ampdu_density"
    HKR,	,"iovar:ampdu_density",0,"7"
    HKR,	,"PendUrb", 0, "0"
	


[nbg20.channels.reg]
	; Chanspec parameters
	; 2G-band, 20MHz channels supported
	HKR,	Ndi\params\Chanspec\enum, "1",   0, "  1(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "2",   0, "  2(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "3",   0, "  3(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "4",   0, "  4(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "5",   0, "  5(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "6",   0, "  6(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "7",   0, "  7(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "8",   0, "  8(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "9",   0, "  9(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "10",   0, " 10(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "11",   0, " 11(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "12",   0, " 12(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "13",   0, " 13(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "14",   0, " 14(20MHz)"


[nbg40.channels.reg]
	; 2G-band, 40MHz channels supported
	HKR,	Ndi\params\Chanspec\enum, "1/40l", 0, "  1(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "6/40l", 0, "  6(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "6/40u", 0, "  6(40MHz-U)"
	HKR,	Ndi\params\Chanspec\enum, "11/40u",0, " 11(40MHz-U)"




[na20.channels.reg]
	; Chanspec parameters
	; USA Low Band
	HKR,	Ndi\params\Chanspec\enum, "36",   0, " 36(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "40",   0, " 40(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "44",   0, " 44(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "48",   0, " 48(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "52",   0, " 52(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "56",   0, " 56(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "60",   0, " 60(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "64",   0, " 64(20MHz)"
	; Europe
	HKR,	Ndi\params\Chanspec\enum, "100",   0, "100(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "104",   0, "104(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "108",   0, "108(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "112",   0, "112(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "116",   0, "116(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "120",   0, "120(20MHz)"


	HKR,	Ndi\params\Chanspec\enum, "124",   0, "124(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "128",   0, "128(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "132",   0, "132(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "136",   0, "136(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "140",   0, "140(20MHz)"


	HKR,	Ndi\params\Chanspec\enum, "149",   0, "149(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "153",   0, "153(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "157",   0, "157(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "161",   0, "161(20MHz)"
	HKR,	Ndi\params\Chanspec\enum, "165",   0, "165(20MHz)"


[na40.channels.reg]
	; 5G-band, 40MHz channels supported
	HKR,	Ndi\params\Chanspec\enum, "36/40",  0, " 36(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "44/40",  0, " 44(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "52/40",  0, " 52(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "60/40",  0, " 60(40MHz-L)"
	; Europe
	HKR,	Ndi\params\Chanspec\enum, "100/40",  0, "100(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "108/40",  0, "108(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "116/40",  0, "116(40MHz-L)"


	HKR,	Ndi\params\Chanspec\enum, "124/40",  0, "124(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "132/40",  0, "132(40MHz-L)"


	HKR,	Ndi\params\Chanspec\enum, "149/40",  0, "149(40MHz-L)"
	HKR,	Ndi\params\Chanspec\enum, "157/40",  0, "157(40MHz-L)"




; options for 40MHz band for n
[bagn40.options.reg]
	HKR,	Ndi\params\BandwidthCap, ParamDesc,     0,      "Bandwidth Capability"
	HKR,	Ndi\params\BandwidthCap, type,          0,      "enum"
	HKR,	Ndi\params\BandwidthCap\enum, "0",      0,      "11a/b/g:20MHz"
	HKR,	Ndi\params\BandwidthCap\enum, "1",      0,      "11a/b/g:20/40MHz"
	HKR,	Ndi\params\BandwidthCap\enum, "2",      0,      "11a:20/40;11bg:20MHz"
	HKR,	Ndi\params\BandwidthCap,default,,"1"


[bagn.options.reg]
	HKR, 	Ndi\params\11HNetworks, ParamDesc, 0, 	"802.11h+d"
	HKR, 	Ndi\params\11HNetworks, type, 		0, "enum"
	HKR, 	Ndi\params\11HNetworks\enum, "1", 	0, %Loose_11h%
	HKR, 	Ndi\params\11HNetworks\enum, "2", 	0, %Strict_11h%
	HKR, 	Ndi\params\11HNetworks,default,,"1"


	HKR,	Ndi\params\RoamTrigger, ParamDesc,	0,	%RoamingDecision%
	HKR,	Ndi\params\RoamTrigger, type,		0,	"enum"
	HKR,	Ndi\params\RoamTrigger\enum, "3",	0,	%Auto%
	HKR,	Ndi\params\RoamTrigger\enum, "1",	0,	%OptimizeBandwidth%
	HKR,	Ndi\params\RoamTrigger\enum, "0",	0,	%Default%
	HKR,	Ndi\params\RoamTrigger\enum, "2",	0,	%OptimizeDistance%
	HKR,	Ndi\params\RoamTrigger,default,,"3"


	HKR,	Ndi\params\PLCPHeader, ParamDesc,	0,	%BSSPLCPHeader%
	HKR,	Ndi\params\PLCPHeader, type,		0,	"enum"
	HKR,	Ndi\params\PLCPHeader\enum, "-1",	0,	%Long%
	HKR,	Ndi\params\PLCPHeader\enum, "0",	0,	%AutoShortLong%
	HKR,	Ndi\params\PLCPHeader,default,,"0"


	HKR,	Ndi\params\band, ParamDesc,	0,	%DisableBands%
	HKR,	Ndi\params\band, type,		0,	"enum"
	HKR,	Ndi\params\band\enum, "0",	0,	%None%
	HKR,	Ndi\params\band\enum, "1",	0,	%Disable80211gb%
	HKR,	Ndi\params\band\enum, "2",	0,	%Disable80211a%
	HKR,	Ndi\params\band,default,,"0"


	HKR,	Ndi\params\BandPref, ParamDesc,	0,	%BandPreference%
	HKR,	Ndi\params\BandPref, type,		0,	"enum"
	HKR,	Ndi\params\BandPref\enum, "0",	0,	%None%
	HKR,	Ndi\params\BandPref\enum, "1",	0,	%Prefer80211a%
	HKR,	Ndi\params\BandPref\enum, "2",	0,	%Prefer80211gb%
	HKR,	Ndi\params\BandPref,default,,"0"
        
	HKR,	Ndi\params\AssocRoamPref, ParamDesc,	0,	%AssociationRoamPreference%
	HKR,	Ndi\params\AssocRoamPref, type,		0,	"enum"
	HKR,	Ndi\params\AssocRoamPref\enum, "0",	0,	%Disabled%
	HKR,	Ndi\params\AssocRoamPref\enum, "1",	0,	%Enabled%
	HKR,	Ndi\params\AssocRoamPref,default,,"0"


	HKR,	Ndi\params\IBSSMode, ParamDesc,	0,      %IBSSMode%
	HKR,	Ndi\params\IBSSMode, type,         0,      "enum"
	HKR,	Ndi\params\IBSSMode\enum, "0",     0,      %80211abOnly%
	HKR,	Ndi\params\IBSSMode\enum, "2",     0,      %80211abgAuto%
	HKR,	Ndi\params\IBSSMode\enum, "4",     0,      %80211abgPerf%
	HKR,	Ndi\params\IBSSMode\enum, "5",     0,      %80211abgnAuto%
	HKR,	Ndi\params\IBSSMode,default,,"5"


	HKR,	Ndi\params\IBSSGProtection, ParamDesc,	0,      %IBSS54gtmProtectionMode%
	HKR,	Ndi\params\IBSSGProtection, type,       0,      "enum"
	HKR,	Ndi\params\IBSSGProtection\enum, "0",   0,      %Disabled%
	HKR,	Ndi\params\IBSSGProtection\enum, "2",   0,      %Auto%
	HKR,	Ndi\params\IBSSGProtection,default,,"2"


	HKR,	Ndi\params\RateA, ParamDesc,	0,	%Rate_802_11a%
	HKR,	Ndi\params\RateA, type,		0,	"enum"
	HKR,	Ndi\params\RateA\enum, "0",	0,	%Usebestrate%
	HKR,	Ndi\params\RateA\enum, "12",	0,	" 6"
	HKR,	Ndi\params\RateA\enum, "18",	0,	" 9"
	HKR,	Ndi\params\RateA\enum, "24",	0,	"12"
	HKR,	Ndi\params\RateA\enum, "36",	0,	"18"
	HKR,	Ndi\params\RateA\enum, "48",	0,	"24"
	HKR,	Ndi\params\RateA\enum, "72",	0,	"36"
	HKR,	Ndi\params\RateA\enum, "96",	0,	"48"
	HKR,	Ndi\params\RateA\enum, "108",0,	"54"
	HKR,	Ndi\params\RateA,default,,"0"


	HKR,	Ndi\params\Rate, ParamDesc,	0,	%Rate_802_11bg%
	HKR,	Ndi\params\Rate, type,		0,	"enum"
	HKR,	Ndi\params\Rate\enum, "0",	0,	%Usebestrate%
	HKR,	Ndi\params\Rate\enum, "2",	0,	" 1"
	HKR,	Ndi\params\Rate\enum, "4",	0,	" 2"
	HKR,	Ndi\params\Rate\enum, "11",	0,	" 5.5"
	HKR,	Ndi\params\Rate\enum, "12",	0,	" 6"
	HKR,	Ndi\params\Rate\enum, "18",	0,	" 9"
	HKR,	Ndi\params\Rate\enum, "22",	0,	"11"
	HKR,	Ndi\params\Rate\enum, "24",	0,	"12"
	HKR,	Ndi\params\Rate\enum, "36",	0,	"18"
	HKR,	Ndi\params\Rate\enum, "48",	0,	"24"
	HKR,	Ndi\params\Rate\enum, "72",	0,	"36"
	HKR,	Ndi\params\Rate\enum, "96",	0,	"48"
	HKR,	Ndi\params\Rate\enum, "108",0,	"54"
	HKR,	Ndi\params\Rate,default,,"0"


	HKR,	Ndi\params\Chanspec, ParamDesc, 0, %IBSSChannelNumber%
	HKR,	Ndi\params\Chanspec, type,      0, "enum"
	HKR,	Ndi\params\Chanspec, default,   0, "11"


	HKR,	Ndi\params\ApCompatMode, ParamDesc,	0,	%ApCompatibilityMode%
	HKR,	Ndi\params\ApCompatMode, type,		0,	"enum"
	HKR,	Ndi\params\ApCompatMode\enum, "1",	0,	%BroaderCompat%
	HKR,	Ndi\params\ApCompatMode\enum, "0",	0,	%HigherPerf%
	HKR,	Ndi\params\ApCompatMode,default,,"0"


	HKR,	Ndi\params\Intolerant, ParamDesc,	0,      %Intolerant%
	HKR,	Ndi\params\Intolerant, type,         0,      "enum"
	HKR,	Ndi\params\Intolerant\enum, "0",     0,      %Disabled%
	HKR,	Ndi\params\Intolerant\enum, "1",     0,      %Enabled%
	HKR,	Ndi\params\Intolerant,default,,"0"


	HKR,	Ndi\params\OBSSCoex, ParamDesc,	0,	%OBSSCoex%
	HKR,	Ndi\params\OBSSCoex, type,	0,	"enum"
	HKR,	Ndi\params\OBSSCoex\enum, "0",	0,	%Disabled%
	HKR,	Ndi\params\OBSSCoex\enum, "1",	0,	%Enabled%
	HKR,	Ndi\params\OBSSCoex\enum, "-1", 0,      %Auto%
	HKR,	Ndi\params\OBSSCoex,default,,"-1"


	HKR, 	Ndi\params\11NPreamble, ParamDesc,  0, 	"802.11n Preamble"
	HKR, 	Ndi\params\11NPreamble, type, 		0, "enum"
	HKR, 	Ndi\params\11NPreamble\enum, "-1", 	0, %Auto%
	HKR, 	Ndi\params\11NPreamble\enum, "0", 	0, %Mixed_Mode%
	HKR, 	Ndi\params\11NPreamble,default,,"-1"


	HKR, 	Ndi\params\ShortGI, ParamDesc,  0, 	"Short GI"
	HKR, 	Ndi\params\ShortGI, type, 		0, "enum"
	HKR, 	Ndi\params\ShortGI\enum, "-1", 	0, 	%Auto%
	HKR, 	Ndi\params\ShortGI\enum, "0", 	0,	%Disabled%
	HKR, 	Ndi\params\ShortGI,default,,"-1"


[strings]
NTGR="NETGEAR,Inc."
A6200_HELP="The NETGEAR A6200 WiFi Adapter provides wireless local area networking."
A6200_Service_DispName="NETGEAR A6200 WiFi Adapter Driver"
A6200_DiskName="802.11 Network Adapter Install Disk"
NTGRA6200_DeviceDesc="NETGEAR A6200 WiFi Adapter"
A6200_Service_DispName="NETGEAR A6200 WiFi Adapter Driver"


54gAuto="54g - Auto"
54gPerformance="54g - Performance"
80211bOnly="802.11b Only"
AntennaDiversity="Antenna Diversity"
Auto="Auto"
AutoShortLong="Auto (Short/Long)"
BSSPLCPHeader="BSS PLCP Header"
BlueToothCollaboration="Bluetooth Collaboration"
Default="Default"
Disable="Disable"
Disable80211a="Disable 802.11a"
Disable80211gb="Disable 802.11g/b"
DisableBands="Disable Bands"
Disabled="Disabled"
Enable="Enable"
Enabled="Enabled"
FragmentationThreshold="Fragmentation Threshold"
IBSS54gtmMode="IBSS 54g(tm) Mode"
IBSS54gtmProtectionMode="IBSS 54g(tm) Protection Mode"
IBSSMode="IBSS Mode"
LocallyAdministeredMACAddress="Locally Administered MAC Address"
Long="Long"
None="None"
OptimizeBandwidth="Optimize Bandwidth"
OptimizeDistance="Optimize Distance"
PLCPHeader="PLCP Header"
PowerOutput="Power Output"
PowerSaveMode="Power Save Mode"
Prefer80211a="Prefer 802.11a"
Prefer80211gb="Prefer 802.11g/b"
RTSThreshold="RTS Threshold"
RadioEnableDisable="Radio Enable/Disable"
Rate="Rate"
RoamingDecision="Roaming Decision"
XPress_Technology="XPress (TM) Technology"
Fast="Fast"
MinimumPowerConsumption="Minimum Power Consumption"
AssociationRoamPreference="Association Roam Preference"
BandPreference="Band Preference"
RoamingTendency="Roam Tendency"
Aggressive="Aggressive"
Moderate="Moderate"
Conservative="Conservative"
Aux="Aux"
Main="Main"
ApCompatibilityMode="AP Compatibility Mode"
BroaderCompat="Broader Compatibility"
HigherPerf="Higher Performance"
WME="WMM"
Rate_802_11a="Rate (802.11a)"
Rate_802_11bg="Rate (802.11b/g)"
WZC_Managed_Ethernet="WZC Managed Ethernet"
Legacy="Legacy"
IBSS_Link_Indication="IBSS Link Indication"
Manage_Wireless_Settings="Manage Wireless Settings"
DisableRadioUponWiredConnection="Disable Upon Wired Connect"
SSIDAutoPromote="SSID Autopromote"
IBSSChannelNumber="WZC IBSS Channel Number"
IbssAllowed="IBSS Allowed"
Loose_11h="Loose 11h"
Strict_11h="Strict 11h"
MixedCell="Mixed Cell Support"
vlan_mode="VLAN Priority Support"
80211bgnAuto="802.11b/g/n Auto"
80211abOnly="802.11a/b Only"
80211abgAuto="802.11a/b/g Auto"
80211abgPerf="802.11a/b/g Performance"
80211abgnAuto="802.11a/b/g/n Auto"
PriorityVLANTag="Priority & VLAN"
PriorityAndVLANDisabled="Priority & VLAN Disabled"
PriorityAndVLANEnabled="Priority & VLAN Enabled"
PriorityEnabled="Priority Enabled"
VLANEnabled="VLAN Enabled"
Lock_Wireless_Settings="Lock Wireless Settings"
Usebestrate="Best Rate"
WakeUpCapabilities="Wake-Up Mode"
MagicPacket="Magic Packet"
NetPattern="Wake Up Frame"
Intolerant="40MHz Intolerant"
All="All"
MagicNet="Magic & WakeUp Frame"
LossofAP="LossOfLink"
Mixed_Mode="Mixed Mode"
LossMagic="MagicPkt & LinkLoss"
LossNet="WakeUpPkt & LinkLoss"
BTAMP="BT-AMP"
OBSSCoex="20/40 Coexistance"

```

---

### Post by chili555 on 2014-03-18
That only looks perfect! OK, now the dynamite. Let's uninstall the current ndiswrapper package:```
sudo modprobe -r ndiswrapper
cd ~/Desktop/ndiswrapper-1.59  <--or wherever you downloaded and extracted the tar.gz
sudo make uninstall
sudo rm -rf /etc/ndiswrapper
```Now,using the USB transfer technique, download and transfer these files to your desktop. [http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb) and also: [http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.57-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.57-1ubuntu1_all.deb) Once they are on the desktop,install them with:```
cd ~/Desktop
sudo dpkg -i ndis*.deb
```Now re-install the .inf file:```
cd ~/Desktop/windows_files  <--or wherever you dropped them
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
ndiswrapper -l
```Any improvement?

---

### Post by Sam_Nicholson on 2014-03-19
Hi Chili, thanks for your help. - I am at work now and will be able to check in around 9/10 hours time for you. - I'm in the UK, hence the time difference. - I will try and report back later.

---

### Post by chili555 on 2014-03-19
This is truly a community without borders. I have become accustomed to time zone delays. I look forward to your success! :popcorn:

---

### Post by Sam_Nicholson on 2014-03-19
I am now home again, following your instructions I now get a fatal error. See below for the terminal session log I did following your instructions.

```
sam@sam-linux:~/Desktop/A6200_Linux_Drivers$ sudo modprobe -r ndiswrapper[sudo] password for sam: 
sam@sam-linux:~/Desktop/A6200_Linux_Drivers$ cd
sam@sam-linux:~$ cd Desktop/ndiswrapper-1.59
sam@sam-linux:~/Desktop/ndiswrapper-1.59$ sudo make uninstall
rm -f /usr/share/man/man8/ndiswrapper.8
rm -f /usr/share/man/man8/loadndisdriver.8
make -C driver uninstall
make[1]: Entering directory `/home/sam/Desktop/ndiswrapper-1.59/driver'
rm -f /lib/modules/3.11.0-15-generic/misc/ndiswrapper.ko
/sbin/depmod -a 3.11.0-15-generic
make[1]: Leaving directory `/home/sam/Desktop/ndiswrapper-1.59/driver'
make -C utils uninstall
make[1]: Entering directory `/home/sam/Desktop/ndiswrapper-1.59/utils'
rm -f /sbin/loadndisdriver
rm -f /usr/sbin/ndiswrapper
rm -f /usr/sbin/ndiswrapper-buginfo
make[1]: Leaving directory `/home/sam/Desktop/ndiswrapper-1.59/utils'
sam@sam-linux:~/Desktop/ndiswrapper-1.59$ sudo rm -rf /etc/ndiswrapper
sam@sam-linux:~/Desktop/ndiswrapper-1.59$ cd ~/Desktop
sam@sam-linux:~/Desktop$ sudo dpkg -i ndis*.deb
Selecting previously unselected package ndiswrapper-common.
(Reading database ... 144029 files and directories currently installed.)
Unpacking ndiswrapper-common (from ndiswrapper-common_1.57-1ubuntu1_all.deb) ...
Selecting previously unselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from ndiswrapper-utils-1.9_1.57-1ubuntu1_amd64.deb) ...
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.57-1ubuntu1) ...
sam@sam-linux:~/Desktop$ cd A6200_Linux_Drivers
sam@sam-linux:~/Desktop/A6200_Linux_Drivers$ sudo ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
couldn't find section "common.prevista.reg" -
installation may be incomplete
sam@sam-linux:~/Desktop/A6200_Linux_Drivers$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
sam@sam-linux:~/Desktop/A6200_Linux_Drivers$ cd
sam@sam-linux:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
sam@sam-linux:~$ 

```

---

### Post by chili555 on 2014-03-19
Let's try another step. Please download and install this using the procedure as above: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.57-1ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.57-1ubuntu1_all.deb) and this: [http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu3_all.deb)

Then try again:```
sudo modprobe ndiswrapper
```Please give me a good report; my tanto beckons.

---

### Post by Sam_Nicholson on 2014-03-19
yet more problems I'm afraid.

Terminal
```

sam@sam-linux:~$ cd Desktop
sam@sam-linux:~/Desktop$ sudo dpkg -i *.deb
Selecting previously unselected package dkms.
(Reading database ... 144047 files and directories currently installed.)
Unpacking dkms (from dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package ndiswrapper-dkms.
Unpacking ndiswrapper-dkms (from ndiswrapper-dkms_1.57-1ubuntu1_all.deb) ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Processing triggers for man-db ...
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
First Installation: checking all kernels...
Building only for 3.11.0-15-generic
Building initial module for 3.11.0-15-generic
ERROR (dkms apport): kernel package linux-headers-3.11.0-15-generic is not supported
Error! Bad return status for module build on kernel: 3.11.0-15-generic (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.
sam@sam-linux:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
sam@sam-linux:~/Desktop$ 

```

Contents of the make.log

```

DKMS make.log for ndiswrapper-1.57 for kernel 3.11.0-15-generic (x86_64)
Wed Mar 19 23:16:20 GMT 2014


Cannot find kernel build files in /usr/src/linux-headers-3.11.0-15-generic
Please give the path to kernel build directory with
the KBUILD=<path> argument to make


make: *** [config_check] Error 1

```

---

### Post by chili555 on 2014-03-19
There are many things to love about Ubuntu and a teeny, tiny thing or two to ... errm, dislike. You have installed Ubuntu 12.04.4 which uses the same kernel and, I believe, build tools, as 13.10. We have dutifully grabbed the 12.04 bits and pieces and they don't work as expected. They don't work because 12.04.4 is really 13.10; sort of new wine in old bottles.

I suggest you remove what we've done so far:```
sudo apt-get purge ndiswrapper*
sudo apt-get purge dkms
```So we don't accidentally reinstall the non-working parts, right-click the desktop and create a new folder, name it whatever; old_ndis for example. Drag and drop all the debs you have now in to it.

Now try again with these 13.10 parts:  [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-common_1.58-2_all.deb) and also: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-utils-1.9_1.58-2_amd64.deb)

Then install and modprobe while I take a pill!

---

### Post by Sam_Nicholson on 2014-03-19
All the previous .deb files I deleted after my last post. - So what I did was install the two you've just linked too and still the same fatal error.

sorry but I think this might be a long troubleshoot.

terminal log
```

sam@sam-linux:~$ sudo apt-get purge ndiswrapper*
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ndiswrapper-utils' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-common' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-source' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-utils-1.9' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-dkms' for regex 'ndiswrapper*'
The following packages will be REMOVED
  ndiswrapper-common* ndiswrapper-dkms* ndiswrapper-utils-1.9*
0 to upgrade, 0 to newly install, 3 to remove and 0 not to upgrade.
After this operation, 961 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 144135 files and directories currently installed.)
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
dpkg: warning: while removing ndiswrapper-common, directory '/etc/ndiswrapper' not empty so not removed.
Removing ndiswrapper-dkms ...

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Processing triggers for man-db ...
sam@sam-linux:~$ sudo apt-get purge dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  dkms*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 347 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 144075 files and directories currently installed.)
Removing dkms ...
Purging configuration files for dkms ...
Processing triggers for man-db ...
sam@sam-linux:~$ cd Desktop
sam@sam-linux:~/Desktop$ sudo dpkg -i *.deb
Selecting previously unselected package ndiswrapper-common.
(Reading database ... 144029 files and directories currently installed.)
Unpacking ndiswrapper-common (from ndiswrapper-common_1.58-2_all.deb) ...
Selecting previously unselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from ndiswrapper-utils-1.9_1.58-2_amd64.deb) ...
Setting up ndiswrapper-common (1.58-2) ...
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.58-2) ...
sam@sam-linux:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

---

### Post by chili555 on 2014-03-20
Arrrgghh!! Everything looked just perfect until the last line. The classic fixes for that error:> sam@sam-linux:~/Desktop$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.Are to either compile the tar.gz, which you already did and failed, or to install ndiswrapper-dkms. In a very few cases, the installation fails because it wants linux-headers. We don't see that 'Please consult /var/log/whatever.log,' and, as well, we know you have installed the needed headers as they are needed to compile the tar.gz without error.

Let's try the 13.10 version of ndiswrapper-dkms: [http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.58-2_all.deb) and its dependency dkms: [http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu4_all.deb)

dkms has a whole list of dependencies, all of which, I believe were satisfied when you installed the build tools to compile from source. When you dpkg -i these two, you may find something we missed but is easily satisfiable.

---

### Post by Sam_Nicholson on 2014-03-20
Ok so do I need to do anything other than install those .deb's ? Do I need to remove anything before I do that?

---

### Post by chili555 on 2014-03-20
> **Sam_Nicholson said:**
> Ok so do I need to do anything other than install those .deb's ? Do I need to remove anything before I do that?Nope. Install them. Look for and post any errors and then:```
sudo modprobe ndiswrapper
```

---

### Post by Sam_Nicholson on 2014-03-20
Thanks, I shall be home in the next hour and will continue my journey then.

---

### Post by Sam_Nicholson on 2014-03-20
We've now come full circle. - I did what you said and received no errors. Even the modprobe command worked, no FATAL error yay!

I then rebooted and linux popped up saying there are wireless networks available. - I then tried to connect and again it would not accept the key.

I've posted below what you asked for originally.

```

sam@sam-linux:~$ sudo -i
[sudo] password for sam: 
root@sam-linux:~# dmesg | grep ndis
[   16.865907] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   16.866455] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   17.070940] ndiswrapper: driver bcmwlhigh5 (NETGEAR,Inc.,08/01/2012, 6.30.61.21) loaded
[   17.359164] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ab6000, 32000, 8
[   17.359168] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007abdd00, 32000, 9
[   17.359170] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ac5a00, 32000, 9
[   17.359171] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007acd700, 32000, 9
[   17.359172] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ad5400, 32000, 9
[   17.359173] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007add100, 32000, 8
[   17.359175] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ae4e00, 32000, 9
[   17.359176] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007aecb00, 32000, 9
[   17.359178] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007af4800, 32000, 9
[   17.359179] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007afc500, 32000, 9
[   17.359180] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b04200, 32000, 8
[   17.359182] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b0bf00, 32000, 9
[   17.359183] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b13c00, 32000, 9
[   17.359184] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b1b900, 32000, 9
[   17.359186] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b23600, 32000, 9
[   17.359187] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b2b300, 32000, 8
[   17.359189] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b33000, 32000, 8
[   17.359190] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b3ad00, 32000, 9
[   17.359192] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b42a00, 32000, 9
[   17.359193] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b4a700, 32000, 9
[   17.359195] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b52400, 32000, 9
[   17.359196] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b5a100, 32000, 8
[   17.359197] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b61e00, 32000, 9
[   17.359198] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b69b00, 32000, 9
[   17.359200] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b71800, 32000, 9
[   17.359201] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b79500, 32000, 9
[   17.359203] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b81200, 32000, 8
[   17.359204] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b88f00, 32000, 9
[   17.359206] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b90c00, 32000, 9
[   17.359207] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007b98900, 32000, 9
[   17.359209] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ba0600, 32000, 9
[   17.359210] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007ba8300, 32000, 8
[   17.359211] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bb0000, 32000, 8
[   17.359213] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bb7d00, 32000, 9
[   17.359214] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bbfa00, 32000, 9
[   17.359216] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bc7700, 32000, 9
[   17.359217] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bcf400, 32000, 9
[   17.359218] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bd7100, 32000, 8
[   17.359220] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bdee00, 32000, 9
[   17.359221] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007be6b00, 32000, 9
[   17.359223] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bee800, 32000, 9
[   17.359224] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bf6500, 32000, 9
[   17.359225] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007bfe200, 32000, 8
[   17.359227] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c05f00, 32000, 9
[   17.359228] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c0dc00, 32000, 9
[   17.359229] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c15900, 32000, 9
[   17.359231] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c1d600, 32000, 9
[   17.359232] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c25300, 32000, 8
[   17.359234] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c2d000, 32000, 8
[   17.359235] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90007c34d00, 32000, 9
[   17.375081] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   17.637957] usbcore: registered new interface driver ndiswrapper
root@sam-linux:~# ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9050) present
root@sam-linux:~# ^C
root@sam-linux:~# 

```

---

### Post by chili555 on 2014-03-20
Googling the error, ndiswrapper (MmBuildMdlForNonPagedPool:1864), I found myself peeking back at me in some kind of Twilight Zone here: [http://ubuntuforums.org/showthread.php?t=2111917&page=3](http://ubuntuforums.org/showthread.php?t=2111917&page=3) Here, I say:> 64-bit is hit or miss; some report it works fine, some report it never works. I haven't been able to spot a pattern yet.I suggested:> I also wonder if the creaky old Windows XP driver has trouble with N speeds. Is 802.11N enabled in your router? If you disable it, can you connect? And the OP then reports:>  tried changing it to 11bg mixed, and bam it works!I suggest you try it.

Although it is tedious to do, I'd love to see the result on a 32-bit install, ideally a live USB.

---

### Post by carolyn3 on 2014-07-29
Hey I'm coming across a similar but different issue. I feel like a total doofus but I'm stumped >:[ 

I have the ndiswrapper and dkms for ubuntu 12.04 installed as recommended by chili555, but as I tried to reinstall the bcmwlhigh5.inf file I got a response saying it was already installed! Can anyone help me figure out why this usb adapter won't work then if the driver has already been installed? Any additional steps I need to take?
[B]
[email]carolyn@TheHottieBox:~/.wine[/email]/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ sudo ndiswrapper -i bcmwlhigh5.inf
driver bcmwlhigh5 is already installed[/B]

I have also typed in the following (as recommended by askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04)
[B]
[email]carolyn@TheHottieBox:~/.wine[/email]/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ sudo modprobe ndiswrapper
[email]carolyn@TheHottieBox:~/.wine[/email]/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modules.conf ...[/B]

---

### Post by chili555 on 2014-07-29
Let's ask the system what's going on here:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```The result of these three should tell us a lot.

---

### Post by carolyn3 on 2014-07-29
Done. Anyone understand the following answer? 

[B]carolyn@TheHottieBox:~/.wine/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ sudo modprobe ndiswrapper
[sudo] password for carolyn: 
[email]carolyn@TheHottieBox:~/.wine[/email]/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9050) present
[email]carolyn@TheHottieBox:~/.wine[/email]/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ dmesg | grep ndis
[  869.652177] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  869.718932] usbcore: registered new interface driver ndiswrapper
[/B]

---

### Post by chili555 on 2014-07-29
> Anyone understand the following answer? Pretty well.> $ sudo modprobe ndiswrapper
[sudo] password for carolyn: That means 'command executed as requested and (most importantly) there are no errors, warnings, or sparks.' Good news so far.> $ ndiswrapper -l
bcmwlhigh5 : driver installed
device (0846:9050) presentAlso good news. That means a file is in place that matches your device and there are no errors, warnings or sparks. We're on a roll!> $ dmesg | grep ndis
[ 869.652177] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 869.718932] usbcore: registered new interface driver ndiswrapperNot quite as good but still not bad. The time-stamp of 869.xx indicates that the ndiswrapper module was loaded when you loaded it just now, not on boot. The boot process on my computers takes up to timestamp 22.xx or so. That's what suggests that ndiswrapper wasn't loading as expected on boot. I wonder if that's all that's wrong! Let's try:```
sudo -i
echo ndiswrapper  >>  /etc/modules
modprobe ndiswrapper
iwconfig
rfkill list all
exit
```It looks really very encouraging so far.

---

### Post by carolyn3 on 2014-07-29
Hmm

[B]carolyn@TheHottieBox:~/.wine/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ sudo -i
[sudo] password for carolyn: 
root@TheHottieBox:~# echo ndiswrapper >> /etc/modules
root@TheHottieBox:~# modprobe ndiswrapper
root@TheHottieBox:~# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"spot2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:D1:C4:7D:DF   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=27/70  Signal level=-83 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:419  Invalid misc:1353   Missed beacon:0

eth0      no wireless extensions.

root@TheHottieBox:~# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
root@TheHottieBox:~# exit
logout
[email]carolyn@TheHottieBox:~/.wine[/email]/drive_c/ProgramFilesx86/NETGEAR/A6200/Drivers$ 
[/B]

---

### Post by chili555 on 2014-07-29
> wlan0 IEEE 802.11bg ESSID:"spot2" 
Mode:Managed Frequency:2.412 GHz Access Point: xx:141:C4:7:xx
Bit Rate=6 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thrff Fragment thr:off
Encryption keyff
Power Management:off
Link Quality=27/70 Signal level=-83 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:419 Invalid misc:1353 Missed beacon:0Looks like you are connected to me. The only hitch I see is that the signal strength is poor at 27/70. I doubt you can pull many web pages at that rate. Can you step closer to the router and see some improvement?

---

### Post by WinEunuchs2Unix on 2014-07-30
I have signal strength of 38/70 going through 4 walls and the second floor.  Loading web pages is quick and snappy except the odd 1 or 2 minute lags every now and then.

I had just plugged in the NetGear A6200 USB (also ndiswrapped) a couple of hours ago for a speed test (unrelated to this thread) and it was about half the speed of the on-board Intel Advanced-N 6235 listed below:

```

lo        no wireless extensions.


wlan3     IEEE 802.11abgn  ESSID:"xxxxxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xxxxxxxxxx
          Bit Rate:115.6 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:1788   Missed beacon:0



```

It is 64 bit debian/ubuntu 14.04 Kernel 3.15.6.  802.11n is enabled on both the Intel and NetGear wireless.  There are weird times where the Intel will slow to 1 Mbps and I can plug in the A6200 that will report 114 Mbps but still lag quite a bit on web pages.

Don't know if any of this is helpful....

---

### Post by cfmackey on 2014-07-30
Hey guys, hopping on the train here to see if I can help out/be helped out.

I'm having the exact same issue Sam_Nicholson was having, but in Xubuntu 14.04. In terminal, ndiswrapper (from the 14.04 repos) throws an error at me when I try to install bcmwlhigh5.inf:
```
couldn't find section "common.prevista.reg" -
```
I get a successful install from ndisgtk, but the adapter doesn't seem to recognize 5ghz, and after about 20-30 minutes it stops working altogether.

Any help I can be to this problem, please let me know.

---

### Post by WinEunuchs2Unix on 2014-07-30
I believe when I created mine it crashed at the same "prevista registration" spot.  Documentation on the net said that was normal.  I don't have 5 Ghz router so cannot attest to performance but the A6200 can see more of the neighbour's routers that the other 3 wifi adapters aren't strong enough to see.

As far as timing out it used to work all night without interruption but lately I seem to experience the same using 2.4Ghz every 20 minutes to 30 minutes periodic time outs.  Truthfully I don't use the dongle much anymore and am in the process of selecting a fifth wifi adapter (sucker for punishment).

---

### Post by carolyn3 on 2014-07-31
@chili555, I have connection through the wireless card I already had plugged in. But my issue is that the NETGEAR A6200 usb adapter does not seem to be working (the LED light does not turn on), although the driver appears to be installed...Should I just keep messing with the hardware?

---

### Post by chili555 on 2014-07-31
> **carolyn3 said:**
> @chili555, I have connection through the wireless card I already had plugged in. But my issue is that the NETGEAR A6200 usb adapter does not seem to be working (the LED light does not turn on), although the driver appears to be installed...Should I just keep messing with the hardware?I hope you are not saying you have two devices working at once and, very likely, a conflict. Is there an internal device that needs to be blacklisted? Tell me more.

---

