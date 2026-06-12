---
title: "Install prob dapper and ndiswrapper"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by FlowingSnake on 2007-09-06
I have dapper for 64bit installed and runing. I am trying to get ndiswrapper installed, so i can try and get my wirless card runing. I have extracted ndiswrapper-1.48rc1. however the problem comes when I issue the make command. I get kernnel not supported (or something very similar) error. I have been following these instructions:
[http://ubuntuforums.org/showthread.php?t=528398&highlight=installing+NdisWrapper]("http://ubuntuforums.org/showthread.php?t=528398&highlight=installing+NdisWrapper")

---

### Post by kevdog on 2007-09-06
Did you install the build-essential and linux headers??

Just wanted to make sure you did this since a lot of people dont install the linux headers and run into problems.  You need either an internet connection of the ubuntu installation cd to install these

If you could post the exact error it would help

---

### Post by FlowingSnake on 2007-09-06
The exact error is:
makefile:35 *** Cannot find kernel version in /lib/modules/2.6.16-26-amd64-generic/build, is it configured?. Stop.

Now also after i read your post i went back and reran this:
(put install disk in)
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential linux-headers- 'uname-r'

when running the last line it says it cannot find 'uname-r'
I am very new to this, have i typed it wrong, or is 'uname-r' some abbreviation?
Also while in ubuntu i have no internet connection

---

### Post by kevdog on 2007-09-06
uname -r

if you are having a problem type this command and then substitute it for the outpu in the command.  this command only gives your kernel version.
```

kevin@Homer:~$ uname -r
2.6.20-16-generic

```

---

### Post by kevdog on 2007-09-06
do you have the 64bit winxp driver for your wireless card????

If you dont you are going to run into trouble

---

### Post by FlowingSnake on 2007-09-06
yea i just downloaded it( then on to a flash and into ubuntu). However there are 3 *.sys files. (MRV8K50.sys, MRV8K51.sys, MRV8Kx64.sys). I have an A8V-E Deluxe mb, that I believe has the Marvell 88W8310 chipset. Any idea which *.sys file i put in ~/drivers. Or do i put them all (along with the *.inf)?

---

### Post by kevdog on 2007-09-06
Might need to look on the website for the specific driver, but Im guesing off the top of my head try just the one with 64 in the name.  If that doesnt work, just put them all in.  Something tells me however that they are a combination of 32 and 64 bit drivers, and by default the 32 bit  drivers will be installed.

Do a lspci -nn, this will confirm your chipset -- which I think you guessed correctly.
lshw -C network is also a very useful command.

---

### Post by FlowingSnake on 2007-09-06
ok with the mrv8kx64.sys and the mrv8knt.inf...when i go:
sudo ndiswrapper -i mrv8knt.inf
I get invalid driver error.
Now if i try any of the other *.sys it says driver already loaded

Now if i carry on with the install...i get no further errors. but I see no wirless card in network connects...there is an ether (eth0) and a dialup modem...but no wlan0 and no add tab or anything....man this is all very frustrating for a newcomer

---

### Post by kevdog on 2007-09-06
Ok, I would stick all the sys files and the inf file in the driver directory

With ndiswrapper you can only install one driver for each device.  You are trying to install a second device driver for the device.

You can either do the following:
sudo ndiswrapper -r ******  (this is the name of the inf file without the .inf extension -- kind of like when you installed it)

or
cd /etc/ndiswrapper
sudo -R *

This in effect does the same thing but more of a brute force method.  The install procedure sticks all the drivers in subdirectories located in /etc/ndiswrapper.  You are basically deleting all these subdirectories with this command.

---

### Post by FlowingSnake on 2007-09-06
when i do
sudo ndiswrapper -r ******
it states that there is no file... I shall try the other one now and see (lol i hate having to reboot into windows every time to post on the froum lol)

---

### Post by kevdog on 2007-09-06
Its not ****** <----- It means put in the name of the .inf file without the .inf extension

---

### Post by FlowingSnake on 2007-09-06
> **kevdog said:**
> Its not ****** <----- It means put in the name of the .inf file without the .inf extension

lol yea I new that...but anyway i sorted out the removal 
now when i use:
sudo ndiswrapper -i ******.inf
I get,
Couldnt open *****.inf: no such file or directory at /usr/sbin/ndiswrapper line 217

wow this just keeps coming..

I have also tryd
sudo ndiswrapper -i *****
same reasult
I looked iin /usr/sbin/ndiswrapper and only saw files no directorys

---

### Post by kevdog on 2007-09-06
Ok, all 3 sys files and the inf file are in the drivers directory??

Ive seen this error before and usually it means that all the drivers (sys files) are bad, or there is a naming error or something.

I would do the following (experiment).
#1. Open up the inf file in gedit (its text format) and do a search for any of the .sys files.  Usually in the inf file the corresponding sys file is mentioned by name.  It may possibly be referring to the file by a different name.
#2. One by one try each .sys file with the .inf file and see if that works.  
#3. Go to marvells website and see if you can download an alternative winxp 64 bit driver.

Unfortunately there is no good solution for this error, since it implies something is wrong with the driver files, not ndiswrapper.  Sometimes I can find a work-around, sometimes I can not.  Its a combination of trying some things or finding a different driver.

---

### Post by FlowingSnake on 2007-09-06
This is the .inf file.. and there all mentioned...but the ***x64.sys looks tobe the one i want. 
;===========================================================================
; 
; Windows 2K/XP/XP x64 NDIS driver INF for Libertas 802.11b/g Wireless
; Copyright (C) 2003 Marvell Semiconductor, Inc.
;
;=========================================================================== 
 
 
[Version] 
Signature = "$Windows NT$" 
Compatible  = 1
Class=Net
ClassGUID={4D36E972-E325-11CE-BFC1-08002BE10318} 
Provider=%MRVL% 
CatalogFile=mrv8knet.cat
DriverVer=11/16/2004,2.7.1.2

;===========================================================================
; Source Media Information Sections
;===========================================================================
[SourceDisksNames]
1 = "Marvell installation disk 1",,,

[SourceDisksFiles]
; On Marvell installation disk 1 
MRV8K50.sys =1
mrv8k51.sys =1
mrv8kx64.sys =1

[DestinationDirs]
W8100PCI.2K.CopyFiles  = 12 
W8100PCI.XP.CopyFiles  = 12
W8100PCI.x64.CopyFiles = 12
DefaultDestDirs        = 11

[Manufacturer] 
%MRVL%=MarvellDevices,NTamd64,NTx86.5.1

[MarvellDevices]
;===========================================================================
;ASUS Devices
;===========================================================================
%W8100PCI2K.DeviceDesc% = W8100PCI.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_138F1043
%W8100PCI2K.DeviceDesc% = W8100PCI.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_128F1043
%W8100PCI2K.DeviceDesc% = W8100PCI.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_108F1043

%W8100PCI2K.DeviceDesc% = W8100PCI.ndi, PCI\VEN_11AB&DEV_1FA4
%W8100PCI2K.DeviceDesc% = W8100PCI.ndi, PCI\VEN_11AB&DEV_1FA6
%W8100PCI2K.DeviceDesc% = W8100PCI.ndi, PCI\VEN_11AB&DEV_1FA7

[MarvellDevices.NTx86.5.1]
;===========================================================================
;ASUS Devices
;===========================================================================
%W8100PCIXP.DeviceDesc% = W8100PCIXP.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_138F1043
%W8100PCIXP.DeviceDesc% = W8100PCIXP.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_128F1043
%W8100PCIXP.DeviceDesc% = W8100PCIXP.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_108F1043

%W8100PCIXP.DeviceDesc% = W8100PCIXP.ndi, PCI\VEN_11AB&DEV_1FA4
%W8100PCIXP.DeviceDesc% = W8100PCIXP.ndi, PCI\VEN_11AB&DEV_1FA6
%W8100PCIXP.DeviceDesc% = W8100PCIXP.ndi, PCI\VEN_11AB&DEV_1FA7

[MarvellDevices.NTamd64]
;===========================================================================
;ASUS Devices
;===========================================================================
%W8100PCIx64.DeviceDesc% = W8100PCIx64.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_138F1043
%W8100PCIx64.DeviceDesc% = W8100PCIx64.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_128F1043
%W8100PCIx64.DeviceDesc% = W8100PCIx64.ndi, PCI\VEN_11AB&DEV_1FA6&SUBSYS_108F1043

%W8100PCIx64.DeviceDesc% = W8100PCIx64.ndi, PCI\VEN_11AB&DEV_1FA4
%W8100PCIx64.DeviceDesc% = W8100PCIx64.ndi, PCI\VEN_11AB&DEV_1FA6
%W8100PCIx64.DeviceDesc% = W8100PCIx64.ndi, PCI\VEN_11AB&DEV_1FA7

;===========================================================================
; ControlFlags section
;===========================================================================
[ControlFlags]
ExcludeFromSelect = *

;***************************************************************************
;**         
;**          Win 2K/XP DDInstall section
;**          
;***************************************************************************

[W8100PCI.ndi.NT]
; "Characteristics" is (NCF_PHYSICAL | NCF_HAS_UI)
Characteristics = 0x84 
; "BusType" is PCI or CardBus
BusType         = 5 
AddReg          = W8100PCI.reg
CopyFiles       = W8100PCI.2K.CopyFiles 

[W8100PCIXP.ndi]
; "Characteristics" is (NCF_PHYSICAL | NCF_HAS_UI)
Characteristics = 0x84 
; "BusType" is PCI or CardBus
BusType         = 5 
AddReg          = W8100PCI.reg,  W8100PCI.zerocfg
CopyFiles       = W8100PCI.XP.CopyFiles


[W8100PCIx64.ndi]
; "Characteristics" is (NCF_PHYSICAL | NCF_HAS_UI)
Characteristics = 0x84 
; "BusType" is PCI or CardBus
BusType         = 5 
AddReg          = W8100PCI.reg,  W8100PCI.zerocfg
CopyFiles       = W8100PCI.x64.CopyFiles

;===========================================================================
[W8100PCI.2K.CopyFiles]
MRV8K50.sys,,,2 

[W8100PCI.XP.CopyFiles]
mrv8k51.sys,,,2 

[W8100PCI.x64.CopyFiles]
mrv8kx64.sys,,,2

;===========================================================================
[W8100PCI.ndi.NT.Services]
AddService = W8100PCI2K, 2, W8100PCI2K.Service, Common.EventLog

[W8100PCIXP.ndi.Services]
AddService = W8100PCI, 2, W8100PCIXP.Service, Common.EventLog

[W8100PCIx64.ndi.Services]
AddService = W8100PCIx64, 2, W8100PCIx64.Service, Common.EventLog

;===========================================================================
[W8100PCI2K.Service]
DisplayName    = %W8100PCI2K.Service.DispName%
ServiceType    = 1 ;%SERVICE_KERNEL_DRIVER%
StartType      = 3 ;%SERVICE_DEMAND_START%
ErrorControl   = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary  = %12%\MRV8K50.sys
LoadOrderGroup = NDIS

[W8100PCIXP.Service]
DisplayName    = %W8100PCIXP.Service.DispName%
ServiceType    = 1 ;%SERVICE_KERNEL_DRIVER%
StartType      = 3 ;%SERVICE_DEMAND_START%
ErrorControl   = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary  = %12%\mrv8k51.sys
LoadOrderGroup = NDIS


[W8100PCIx64.Service]
DisplayName    = %W8100PCIx64.Service.DispName%
ServiceType    = 1 ;%SERVICE_KERNEL_DRIVER%
StartType      = 3 ;%SERVICE_DEMAND_START%
ErrorControl   = 1 ;%SERVICE_ERROR_NORMAL%
ServiceBinary  = %12%\mrv8kx64.sys
LoadOrderGroup = NDIS

;===========================================================================
[Common.EventLog]
AddReg = Common.AddEventLog.reg

[Common.AddEventLog.reg]
HKR, , EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR, , TypesSupported,   0x00010001, 7



;===========================================================================
; W8100 PCI common, MIB can be defined here
;===========================================================================
[W8100PCI.reg]
HKR, Ndi,            Service,    0, "W8100PCI"
HKR, Ndi\Interfaces, UpperRange, 0, "ndis5"
HKR, Ndi\Interfaces, LowerRange, 0, "ethernet"

HKR, Ndi\xparams\DesiredSSID,ParamDesc,,"%SSID%"
HKR, Ndi\xparams\DesiredSSID,default,,""
HKR, Ndi\xparams\DesiredSSID,type,,"edit" 
HKR, Ndi\xparams\DesiredSSID,LimitText,,"32"
HKR, Ndi\xparams\DesiredSSID,UpperCase,,"0" 
HKR, Ndi\xparams\DesiredSSID,Optional,,"1" 

HKR, Ndi\xparams\AuthMode,ParamDesc,,"%AuthMode%"
HKR, Ndi\xparams\AuthMode,default,,"0"
HKR, Ndi\xparams\AuthMode,type,,enum
HKR, Ndi\xparams\AuthMode\enum,"0",,"Open"
HKR, Ndi\xparams\AuthMode\enum,"1",,"Shared"

HKR, Ndi\xparams\NetworkMode,ParamDesc,,"%NetworkMode%"
HKR, Ndi\xparams\NetworkMode,default,,"1"
HKR, Ndi\xparams\NetworkMode,type,,enum
HKR, Ndi\xparams\NetworkMode\enum,"0",,"Ad Hoc"
HKR, Ndi\xparams\NetworkMode\enum,"1",,"Infrastructure"

;HKR, Ndi\xparams\Wireless,ParamDesc,,"%WirelessM%"
;HKR, Ndi\xparams\Wireless,default,,"0"
;HKR, Ndi\xparams\Wireless,type,,enum
;HKR, Ndi\xparams\Wireless\enum,"0",,"Auto"
;HKR, Ndi\xparams\Wireless\enum,"1",,"B rates only"
 
HKR, Ndi\xparams\FragThsd,  ParamDesc,0 , "%FragThsds%"
HKR, Ndi\xparams\FragThsd,  default, 0 , "2346"
HKR, Ndi\xparams\FragThsd,  min, 0 , "256"
HKR, Ndi\xparams\FragThsd,  max, 0 , "2346"
HKR, Ndi\xparams\FragThsd,  step, 0 , "1"
HKR, Ndi\xparams\FragThsd,  Base, 0 , "10"
HKR, Ndi\xparams\FragThsd,  type, 0 ,"dword"

HKR, Ndi\xparams\Channel,  ParamDesc,0 , "%Channel%"
HKR, Ndi\xparams\Channel,  default, 0 , "1"
HKR, Ndi\xparams\Channel,  min, 0 , "0"
HKR, Ndi\xparams\Channel,  max, 0 , "14"
HKR, Ndi\xparams\Channel,  step, 0 , "1"
HKR, Ndi\xparams\Channel,  Base, 0 , "16"
HKR, Ndi\xparams\Channel,  type, 0 ,"dword"

HKR, Ndi\xparams\TxAntenna,  ParamDesc,0 , "%TxAntennaStr%"
HKR, Ndi\xparams\TxAntenna,  default, 0 , "2"
HKR, Ndi\xparams\TxAntenna,  min, 0 , "1"
HKR, Ndi\xparams\TxAntenna,  max, 0 , "ffff"
HKR, Ndi\xparams\TxAntenna,  step, 0 , "1"
HKR, Ndi\xparams\TxAntenna,  Base, 0 , "16"
HKR, Ndi\xparams\TxAntenna,  type, 0 ,"dword"

HKR, Ndi\xparams\RxAntenna,  ParamDesc,0 , "%RxAntennaStr%"
HKR, Ndi\xparams\RxAntenna,  default, 0 , "ffff"
HKR, Ndi\xparams\RxAntenna,  min, 0 , "1"
HKR, Ndi\xparams\RxAntenna,  max, 0 , "ffff"
HKR, Ndi\xparams\RxAntenna,  step, 0 , "1"
HKR, Ndi\xparams\RxAntenna,  Base, 0 , "16"
HKR, Ndi\xparams\RxAntenna,  type, 0 ,"dword"

HKR, Ndi\xparams\RTSThsd,  ParamDesc, 0, "%RTSThsds%"
HKR, Ndi\xparams\RTSThsd,  default, 0, "2347"
HKR, Ndi\xparams\RTSThsd,  min, 0, "0"
HKR, Ndi\xparams\RTSThsd,  max, 0, "2347"
HKR, Ndi\xparams\RTSThsd,  step, 0, "1"
HKR, Ndi\xparams\RTSThsd,  Base, 0, "10"
HKR, Ndi\xparams\RTSThsd,  type, 0, "dword"

;HKR, Ndi\xparams\PowerMode,ParamDesc,,"%PowerMode%"
;HKR, Ndi\xparams\PowerMode,default,,"0"
;HKR, Ndi\xparams\PowerMode,type,,enum
;HKR, Ndi\xparams\PowerMode\enum,"0",,"CAM-Constantly Awake Mode"
;HKR, Ndi\xparams\PowerMode\enum,"1",,"MaxPSP-Max Power Savings"
;HKR, Ndi\xparams\PowerMode\enum,"2",,"FastPSP-Fast Power Savings"

HKR, Ndi\xparams\DataRate,ParamDesc,,"%DataRate%"
HKR, Ndi\xparams\DataRate,default,,"FF"
HKR, Ndi\xparams\DataRate,type,,enum
HKR, Ndi\xparams\DataRate\enum,"FF",,"Auto"
HKR, Ndi\xparams\DataRate\enum,"2",,"1 Mbps"
HKR, Ndi\xparams\DataRate\enum,"4",,"2 Mbps"
HKR, Ndi\xparams\DataRate\enum,"b",,"5.5 Mbps"
HKR, Ndi\xparams\DataRate\enum,"16",,"11 Mbps"
;HKR, Ndi\xparams\DataRate\enum,"2C",,"22 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"C",,"6 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"12",,"9 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"18",,"12 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"24",,"18 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"30",,"24 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"48",,"36 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"60",,"48 Mbps" 
HKR, Ndi\xparams\DataRate\enum,"6C",,"54 Mbps"

HKR, Ndi\xparams\WepStatus,ParamDesc,,"%WepStatus%"
HKR, Ndi\xparams\WepStatus,default,,"1"
HKR, Ndi\xparams\WepStatus,type,,enum
HKR, Ndi\xparams\WepStatus\enum,"0",,"Enabled"
HKR, Ndi\xparams\WepStatus\enum,"1",,"Disabled"


HKR, Ndi\xparams\Preamble,ParamDesc,,"%PreambleStr%"
HKR, Ndi\xparams\Preamble,default,,"3"
HKR, Ndi\xparams\Preamble,type,,enum 
HKR, Ndi\xparams\Preamble\enum,"1",,"Auto"
HKR, Ndi\xparams\Preamble\enum,"2",,"Short Preamble" 
HKR, Ndi\xparams\Preamble\enum,"3",,"Long Preamble"

HKR,, TxWepKey, 2, "" 
HKR,, WepKey1, 2, "" 
HKR,, WepKey2, 2, "" 
HKR,, WepKey3, 2, "" 
HKR,, WepKey4, 2, "" 


;Special for Driver on WinXP OS.
[W8100PCI.zerocfg]
 
;===========================================================================
; Strings section
;===========================================================================
[Strings]
MRVL = "Marvell"

TxAntennaStr = "Tx Antenna Select"
RxAntennaStr = "Rx Antenna Select" 
Channel = "Channel"
FragThsds = "Fragamentation Threshold"
DataRate = "Data Rate"
RTSThsds = "RTS Threshold"
AuthMode = "Authentication Mode"
;WirelessM = "Wireless Mode"
NetworkMode = "Operation Mode"
WepStatus = "WEP Status"
SSID = "SSID"
PreambleStr = "Preamble Select"
;PowerMode = "Power Save Mode"

W8100PCI2K.DeviceDesc     = "Marvell Libertas 802.11b/g Wireless"
W8100PCIXP.DeviceDesc     = "Marvell Libertas 802.11b/g Wireless"
W8100PCIx64.DeviceDesc     = "Marvell Libertas 802.11b/g Wireless"
W8100PCI2K.Service.DispName = "Marvell Libertas 802.11b/g Driver for Windows 2000" 
W8100PCIXP.Service.DispName = "Marvell Libertas 802.11b/g Driver for Windows XP"
W8100PCIx64.Service.DispName = "Marvell Libertas 802.11b/g Driver for Windows XP x64"

ok will try them all out and get back to you.

---

### Post by kevdog on 2007-09-06
If you on 64 bit ubuntu, I really think this is the one you need:

W8100PCIx64

and not the others.  It looks like from your .inf file the other two drivers are for win2k and winxp (32 bit).

Can you post lspci -nn.  Maybe there is an alternative driver listed on the ndiswrapper website.

---

