---
title: "modem"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by tounsi1988 on 2007-06-15
HOW  TO INSTAL **_Urmet Speed Access USB_**  :confused::confused::confused:?[IMG]http://www.lineatel.it/lineatel.it/immagini/urmet.gif[/IMG]

---

### Post by jhenager on 2007-06-15
You will get more responses if you enter more information, but if this is a controllerless (winmodem, aka softmodem), you might as well enter this in a terminal:

$ sudo forget_it

I have been working two weeks with three internal, two external modems, GPPP, KPPP, wvdial, pon, poff, linuxant, and everything else I can think of.
Linux does not support dialup.

---

### Post by 3nder on 2007-09-27
Hello !

I installed ubuntu yesterday and I'm just starting to look into the messy problem of getting my modem work

I have an URMET Speed Access USB ADSL Modem
I know it's shitty, but it's already paid for in the ISP bill....
is there any way to make it work ?

I'll paste herebelow the setup info for xp, any effective help will make me your slave for life !!!  :-P


;-------------------------------------------------------------------
; Installation file for STMicroelectronics ATM/ADSL miniport drivers
;
; Copyright (C) F.H.L.P. 2000-2002, (C) STMicroelectronics 2000-2002
;-------------------------------------------------------------------

[Version]
Signature   = "$CHICAGO$"
Compatible  = 1
Class       = Net
ClassGUID   = {4D36E972-E325-11CE-BFC1-08002BE10318}
Provider    = %ProviderName%
DriverVer   = 02/07/2003,1.8.0.1

[ControlFlags]
ExcludeFromSelect = *

[Manufacturer]
%Manuf% = Devices

[Devices]
%StmAtm.Description% = StmAtm.ndi, STM-ATMADSL
%StmLan.Description% = StmLan.ndi, STM-ATMADSL
%StmWan.Description% = StmWan.ndi, STM-ATMADSL

[StmAtm.ndi]
AddReg = StmAtm.ndi.reg, Stm.ndi.reg, StmAtm.win9x.reg, Stm.win9x.reg
CopyFiles = Stm.Files.Sys, Stm.Files.Co9x
DriverVer   = 02/07/2003,1.8.0.1

[StmLan.ndi]
AddReg = StmLan.ndi.reg, Stm.ndi.reg, StmLan.win9x.reg, Stm.win9x.reg
CopyFiles = Stm.Files.Sys, Stm.Files.Co9x
DriverVer   = 02/07/2003,1.8.0.1

[StmWan.ndi]
AddReg = StmWan.ndi.reg, Stm.ndi.reg, StmWan.win9x.reg, Stm.win9x.reg
CopyFiles = Stm.Files.Sys, Stm.Files.Co9x
DriverVer   = 02/07/2003,1.8.0.1

[StmAtm.ndi.NT]
Characteristics = 0x0081 ; NCF_HAS_UI | NCF_VIRTUAL
AddReg = StmAtm.ndi.reg, Stm.ndi.reg, StmAtm.win2k.reg, Stm.win2k.reg
CopyFiles = Stm.Files.Sys

[StmLan.ndi.NT]
Characteristics = 0x0081 ; NCF_HAS_UI | NCF_VIRTUAL
AddReg = StmLan.ndi.reg, Stm.ndi.reg, StmLan.win2k.reg, Stm.win2k.reg
CopyFiles = Stm.Files.Sys

[StmWan.ndi.NT]
Characteristics = 0x0081 ; NCF_HAS_UI | NCF_VIRTUAL
AddReg = StmWan.ndi.reg, Stm.ndi.reg, StmWan.win2k.reg, Stm.win2k.reg
CopyFiles = Stm.Files.Sys

[StmAtm.ndi.NT.Services]
AddService = stmatm, 2, StmAtm.AddService, StmAtm.AddEventLog

[StmLan.ndi.NT.Services]
AddService = stmatm, 2, StmAtm.AddService, StmAtm.AddEventLog

[StmWan.ndi.NT.Services]
AddService = stmatm, 2, StmAtm.AddService, StmAtm.AddEventLog

[StmAtm.ndi.NT.CoInstallers]
AddReg = StmAtm.CoInstall.win2k
CopyFiles = Stm.Files.Co2k

[StmLan.ndi.NT.CoInstallers]
AddReg = StmLan.CoInstall.win2k
CopyFiles = Stm.Files.Co2k

[StmWan.ndi.NT.CoInstallers]
AddReg = StmWan.CoInstall.win2k
CopyFiles = Stm.Files.Co2k

[StmAtm.CoInstall.win2k]
HKR,,CoInstallers32,0x00010000,"stmcfg32.dll,CoAtmInstall"

[StmLan.CoInstall.win2k]
HKR,,CoInstallers32,0x00010000,"stmcfg32.dll,CoLanInstall"

[StmWan.CoInstall.win2k]
HKR,,CoInstallers32,0x00010000,"stmcfg32.dll,CoWanInstall"

; Common part
; -----------
[Stm.ndi.reg]
HKR,Ndi,DeviceID,,STM-ATMADSL
HKR,Ndi\Interfaces,LowerRange,,"adsl"

[StmAtm.ndi.reg]
HKR,Ndi\Interfaces,UpperRange,,"ndisatm"

[StmLan.ndi.reg]

[StmWan.ndi.reg]
HKR,Ndi\Interfaces,UpperRange,,"ndiswan"

; Windows 2000 specific
; ---------------------
[Stm.win2k.reg]
HKR,Ndi,Service,0,"stmatm"
HKR,,DebugFlags,0x00010001,"17"

[StmAtm.win2k.reg]
HKR,,Medium,0x00010001,"8"
HKR,,WanEndPoints,0x00010001,"1"
HKR,,AtmSignalling,0x00010001,"1"
HKR,,MaxTransferUnit,0x00010001,"1500"

[StmLan.win2k.reg]
HKR,Ndi\Interfaces,UpperRange,,"ndis5"

HKR,,Medium,0x00010001,"0"
HKR,,PvcVpi,0x00010001,"0"
HKR,,PvcVci,0x00010001,"800"
HKR,,PvcEncapsulation,0x00010001,"2"
HKR,,MaxTransferUnit,0x00010001,"1500"

[StmWan.win2k.reg]
HKR,,Medium,0x00010001,"3"
HKR,,WanEndPoints,0x00010001,"1"
HKR,,MaxBuffers,0x00010001,"50"
HKR,,BufferLength,0x00010001,"1532"
HKR,,MaxTransferUnit,0x00010001,"1492"

; Windows 98/Me specific
; ----------------------
[Stm.win9x.reg]
HKR,,DevLoader,,"*ndis"
HKR,,DeviceVxDs,,"stmatm.sys"
HKR,,EnumPropPages,,"netdi.dll,EnumPropPages"

HKR,NDIS,MajorNdisVersion,1,3
HKR,NDIS,MinorNdisVersion,1,0A
HKR,NDIS,LogDriverName,,"STM-ATMADSL"

HKR,Ndi\Interfaces,DefLower,,"adsl"

HKR,,DebugFlags,,"17"
HKR,,MaxBuffers,,"50"
HKR,,BufferLength,,"1532"

[StmAtm.win9x.reg]
HKR,Ndi\Interfaces,DefUpper,,"ndisatm"
HKR,Ndi,NdiInstaller,,"stmcfg16.dll,AtmNdiProc"
HKR,Ndi\Compatibility,RequireAll,,"ATMUNI,WANATM,*PNP8387,MSTCP,VREDIR"

HKR,,Medium,,"8"
HKR,,WanEndPoints,,"1"
HKR,,MaxTransferUnit,,"1492"

[StmLan.win9x.reg]
HKR,Ndi\Interfaces,DefUpper,,"ndis3"
HKR,Ndi\Interfaces,UpperRange,,"ndis3"
HKR,Ndi,NdiInstaller,,"stmcfg16.dll,LanNdiProc"
HKR,Ndi\Compatibility,RequireAll,,"MSTCP,VREDIR"

HKR,,Medium,,"0"
HKR,,PvcVpi,,"0"
HKR,,PvcVci,,"800"
HKR,,PvcEncapsulation,,"2"
HKR,,MaxTransferUnit,,"1500"

[StmWan.win9x.reg]
HKR,Ndi\Interfaces,DefUpper,,"ndiswan"
HKR,Ndi,NdiInstaller,,"stmcfg16.dll,WanNdiProc"
HKR,Ndi\Compatibility,RequireAll,,"NDISWAN,*PNP8387,MSTCP,VREDIR"

HKR,,Medium,,"3"
HKR,,WanEndPoints,,"1"
HKR,,MaxTransferUnit,,"1492"

HKR,TAPI,ConfigFlags,1,00,00,00,00
HKR,TAPI,DeviceCaps,1,14,00,00,00, 00,00,00,00, 00,00,00,00, 01,00,00,00, 01,00,00,00
HKR,TAPI\Line0,ConfigFlags,1,00,00,00,00
HKR,TAPI\Line0,LineCaps,1,1c,00,00,00, 00,00,00,00, 00,00,00,00, 00,00,00,00, 00,00,00,00, 01,00,00,00, 01,00,00,00
HKR,TAPI\Line0\Channel0,ConfigFlags,1,00,00,00,00
HKR,TAPI\Line0\Channel0,Properties,1,00,00,00,00, 00,00,00,00, 00,00,00,00
HKCU,RemoteAccess,Wizard,1,80,00,00,00

; stmatm service installation
; ---------------------------
[StmAtm.AddService]
DisplayName    = %Stm.DisplayName%
ServiceType    = 1 ; SERVICE_KERNEL_DRIVER
StartType      = 3 ; SERVICE_DEMAND_START
ErrorControl   = 1 ; ERROR_CONTROL_NORMAL
ServiceBinary  = %12%\stmatm.sys
LoadOrderGroup = NDIS

[StmAtm.AddEventLog]
;AddReg = StmAtm.AddEventLog.reg
;[StmAtm.AddEventLog.reg]
;HKR,,EventMessageFile,0x00020000,"%%SystemRoot%%\System32\netevent.dll"
;HKR,,TypesSupported,0x00010001,"7"

; Copy Files Sections
; -------------------
[Stm.Files.Sys]
;stmatm.sys

[Stm.Files.Co2k]
;stmcfg32.dll

[Stm.Files.Co9x]
;stmcfg16.dll
;stmc1632.dll

[SourceDisksNames]
1 = %InstallDisk%,Disk1,,

[SourceDisksFiles]
stmatm.sys   = 1,,
stmcfg32.dll = 1,,
stmcfg16.dll = 1,,
stmc1632.dll = 1,,

[DestinationDirs]
DefaultDestDir = 11
Stm.Files.Co9x = 11
Stm.Files.Co2k = 11
Stm.Files.Sys  = 10,System32\Drivers

[Strings]
Manuf              = "BeWAN systems"
ProviderName       = "BeWAN systems"
InstallDisk        = "ADSL Modem installation Disk"
Stm.DisplayName    = "ATM/ADSL miniport"
StmAtm.Description = "ATM/ADSL miniport"
StmLan.Description = "LAN/ATM/ADSL miniport"
StmWan.Description = "WAN/ATM/ADSL miniport"

---

