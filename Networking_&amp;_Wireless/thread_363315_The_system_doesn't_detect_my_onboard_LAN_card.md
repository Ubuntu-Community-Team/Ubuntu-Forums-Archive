---
title: "The system doesn't detect my onboard LAN card"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Abadia on 2007-02-16
Hello,

I've been a Windows user for many years, but now I want to escape from the dark side and experience an alternative like Ubuntu. I've installed it and now I have a problem: I need to install the drivers for the 3Com 3C940 Gbit LAN of my motherboard (an Asus P4C800), but I don't know how to do it. The readme.txt file that comes with the drivers explains these steps in order to install them:

[I]Loading the driver
------------------
1) Make sure that the kernel source is installed in /usr/src/linux
   or /usr/src/linux-2.4.
2) Copy the file /Linux/3c2000.tar.gz from the 3Com driver CD to 
   your hard drive.
3) Change to the directory containing 3c2000.tar.gz
4) Type 'tar zxvf 3c2000.tar.gz'
5) Type 'cd 3c2000'
6) Type 'make load' to load the driver.[/I]

Well, when I type 'make load' it appears the following message:

```
skge.c:3266: error: SK_AC has no member named RlmtNets
skge.c:3268: error: SK_EVPARA has no member named Para32
skge.c:3269: error: incompatible type for argument 2 of SkEventQueue
skge.c:3269: error: too many arguments to function SkEventQueue
skge.c:3270: error: SK_EVPARA has no member named Para32
skge.c:3271: error: incompatible type for argument 2 of SkEventQueue
skge.c:3271: error: too many arguments to function SkEventQueue
skge.c:3273: error: incompatible type for argument 2 of SkEventQueue
skge.c:3273: error: too many arguments to function SkEventQueue
skge.c:3276: error: SK_AC has no member named IoBase
skge.c:3278: error: SK_GEINIT has no member named GIMacsFound
skge.c:3280: error: SK_AC has no member named TxPort
skge.c:3281: error: SK_AC has no member named dev
skge.c:3290: error: SK_GEINIT has no member named GIMacsFound
skge.c:3292: error: SK_GEINIT has no member named GIMacsFound
skge.c:3293: error: SK_AC has no member named RlmtNets
skge.c:3294: error: SK_AC has no member named RxPort
skge.c:3295: error: SK_AC has no member named RxDescrPerRing
skge.c:3297: error: SK_AC has no member named ActivePort
skge.c:3298: error: SK_AC has no member named RxPort
skge.c:3299: error: SK_AC has no member named RxDescrPerRing
skge.c:3301: error: SK_AC has no member named RxPort
skge.c:3302: error: SK_AC has no member named RxDescrPerRing
skge.c:3308: error: SK_GEINIT has no member named GIMacsFound
skge.c:3310: error: SK_GEINIT has no member named GIMacsFound
skge.c:3311: error: SK_AC has no member named RlmtNets
skge.c:3312: error: SK_AC has no member named RxPort
skge.c:3314: error: SK_AC has no member named ActivePort
skge.c:3315: error: SK_AC has no member named RxPort
skge.c:3317: error: SK_AC has no member named RxPort
skge.c:3318: error: SK_AC has no member named RxDescrPerRing
skge.c:3323: error: SK_AC has no member named IoBase
skge.c:3330: error: SK_GEINIT has no member named GIPortUsage
skge.c:3333: error: SK_GEINIT has no member named GIMacsFound
skge.c:3334: error: SK_AC has no member named RlmtNets
skge.c:3335: error: SK_GEINIT has no member named GIPortUsage
skge.c:3337: error: SK_GEINIT has no member named GIPortUsage
skge.c:3341: error: SK_AC has no member named IoBase
skge.c:3342: error: SK_AC has no member named IoBase
skge.c:3343: error: SK_AC has no member named IoBase
skge.c:3344: error: SK_AC has no member named IoBase
skge.c:3345: error: SK_AC has no member named IoBase
skge.c:3346: error: SK_AC has no member named IoBase
skge.c:3347: error: SK_AC has no member named IoBase
skge.c:3355: error: SK_AC has no member named IoBase
skge.c:3356: error: SK_AC has no member named IoBase
skge.c:3357: error: SK_AC has no member named IoBase
skge.c:3358: error: SK_AC has no member named IoBase
skge.c:3359: error: SK_AC has no member named IoBase
skge.c:3360: error: SK_AC has no member named IoBase
skge.c:3361: error: SK_AC has no member named IoBase
skge.c:3366: error: SK_GEINIT has no member named GIMacsFound
skge.c:3367: error: SK_AC has no member named RxPort
skge.c:3367: error: too many arguments to function ReceiveIrq
skge.c:3368: error: SK_AC has no member named RxPort
skge.c:3369: error: SK_AC has no member named RxPort
skge.c:3372: error: SK_AC has no member named IoBase
skge.c:3372: error: too many arguments to function SkGePollTxD
skge.c:3373: error: SK_AC has no member named RxPort
skge.c:3376: error: SK_AC has no member named IoBase
skge.c:3382: error: SK_AC has no member named IoBase
skge.c:3383: error: SK_AC has no member named IoBase
skge.c:3384: error: SK_AC has no member named IoBase
skge.c:3388: warning: implicit declaration of function netif_start_queue
skge.c:3388: error: SK_AC has no member named dev
skge.c:3389: error: SK_GEINIT has no member named GIMacsFound
skge.c:3390: error: SK_AC has no member named TxPort
skge.c:3395: error: SK_GEINIT has no member named GIValIrqMask
skge.c:3395: error: SK_AC has no member named IoBase
skge.c:3396: error: SK_AC has no member named IoBase
skge.c:3398: error: incompatible type for argument 2 of SkEventQueue
skge.c:3398: error: too many arguments to function SkEventQueue
skge.c:3399: error: SK_AC has no member named IoBase
skge.c:3402: error: SK_GEINIT has no member named GIMacsFound
skge.c:3403: error: SK_AC has no member named RlmtNets
skge.c:3405: error: SK_EVPARA has no member named Para32
skge.c:3405: error: SK_AC has no member named RlmtNets
skge.c:3406: error: SK_EVPARA has no member named Para32
skge.c:3408: error: incompatible type for argument 2 of SkEventQueue
skge.c:3408: error: too many arguments to function SkEventQueue
skge.c:3411: error: SK_EVPARA has no member named Para32
skge.c:3412: error: SK_EVPARA has no member named Para32
skge.c:3413: error: incompatible type for argument 2 of SkEventQueue
skge.c:3413: error: too many arguments to function SkEventQueue
skge.c:3416: error: SK_EVPARA has no member named Para32
skge.c:3418: error: incompatible type for argument 2 of SkEventQueue
skge.c:3418: error: too many arguments to function SkEventQueue
skge.c:3421: error: incompatible type for argument 2 of SkEventQueue
skge.c:3421: error: too many arguments to function SkEventQueue
skge.c:3424: error: SK_AC has no member named IoBase
skge.c:3425: error: SK_AC has no member named SlowPathLock
skge.c: At top level:
skge.c:3443: error: conflicting types for SkGeStats
skge.c:412: error: previous declaration of SkGeStats was here
skge.c: In function SkGeStats:
skge.c:3444: error: dereferencing pointer to incomplete type
skge.c:3454: error: SK_AC has no member named PnmiStruct
skge.c:3455: warning: implicit declaration of function memset
skge.c:3455: warning: incompatible implicit declaration of built-in function memset
skge.c:3456: error: SK_AC has no member named SlowPathLock
skge.c:3458: error: SK_AC has no member named IoBase
skge.c:3458: error: too many arguments to function SkPnmiGetStruct
skge.c:3459: error: SK_AC has no member named SlowPathLock
skge.c:3460: error: SK_PNMI_STRUCT_DATA has no member named Stat
skge.c:3461: error: SK_PNMI_STRUCT_DATA has no member named Conf
skge.c:3463: error: SK_AC has no member named stats
skge.c:3463: error: u32 undeclared (first use in this function)
skge.c:3463: error: expected ; before pPnmiStruct
skge.c:3464: error: SK_AC has no member named stats
skge.c:3464: error: expected ; before pPnmiStat
skge.c:3465: error: SK_AC has no member named stats
skge.c:3465: error: expected ; before pPnmiStruct
skge.c:3466: error: SK_AC has no member named stats
skge.c:3466: error: expected ; before pPnmiStat
skge.c:3469: error: SK_AC has no member named stats
skge.c:3469: error: expected ; before pPnmiStruct
skge.c:3471: error: SK_AC has no member named stats
skge.c:3471: error: SK_PNMI_STRUCT_DATA has no member named InErrorsCts
skge.c:3472: error: SK_PNMI_STAT has no member named StatRxTooLongCts
skge.c:3476: error: SK_GEINIT has no member named GP
skge.c:3476: error: SK_AC has no member named HWRevision
skge.c:3477: error: SK_AC has no member named stats
skge.c:3477: error: SK_AC has no member named stats
skge.c:3477: error: SK_PNMI_STAT has no member named StatRxShortsCts
skge.c:3479: error: SK_AC has no member named stats
skge.c:3479: error: expected ; before pPnmiStat
skge.c:3480: error: SK_AC has no member named stats
skge.c:3480: error: expected ; before pPnmiStruct
skge.c:3481: error: SK_AC has no member named stats
skge.c:3481: error: expected ; before pPnmiStruct
skge.c:3482: error: SK_AC has no member named stats
skge.c:3482: error: expected ; before pPnmiStat
skge.c:3483: error: SK_AC has no member named stats
skge.c:3483: error: expected ; before pPnmiStat
skge.c:3486: error: SK_AC has no member named stats
skge.c:3486: error: expected ; before pPnmiStat
skge.c:3487: error: SK_AC has no member named stats
skge.c:3487: error: expected ; before pPnmiStat
skge.c:3488: error: SK_AC has no member named stats
skge.c:3488: error: expected ; before pPnmiStat
skge.c:3489: error: SK_AC has no member named stats
skge.c:3489: error: expected ; before pPnmiStat
skge.c:3490: error: SK_AC has no member named stats
skge.c:3490: error: expected ; before pPnmiStat
skge.c:3491: error: SK_AC has no member named stats
skge.c:3491: error: expected ; before pPnmiStat
skge.c:3494: error: SK_AC has no member named stats
skge.c:3494: error: expected ; before numeric constant
skge.c:3495: error: SK_AC has no member named stats
skge.c:3495: error: expected ; before pPnmiStat
skge.c:3496: error: SK_AC has no member named stats
skge.c:3496: error: expected ; before pPnmiStat
skge.c:3497: error: SK_AC has no member named stats
skge.c:3497: error: expected ; before pPnmiStat
skge.c:3498: error: SK_AC has no member named stats
skge.c:3498: error: expected ; before numeric constant
skge.c:3500: error: SK_AC has no member named stats
skge.c: At top level:
skge.c:3517: warning: struct ifreq declared inside parameter list
skge.c:3518: error: conflicting types for SkGeIoctl
skge.c:413: error: previous declaration of SkGeIoctl was here
skge.c: In function SkGeIoctl:
skge.c:3529: error: dereferencing pointer to incomplete type
skge.c:3532: warning: implicit declaration of function copy_from_user
skge.c:3532: error: dereferencing pointer to incomplete type
skge.c:3533: error: EFAULT undeclared (first use in this function)
skge.c:3537: error: SIOCDEVPRIVATE undeclared (first use in this function)
skge.c:3539: warning: implicit declaration of function capable
skge.c:3539: error: CAP_NET_ADMIN undeclared (first use in this function)
skge.c:3539: error: EPERM undeclared (first use in this function)
skge.c:3541: error: SK_AC has no member named PnmiStruct
skge.c:3542: error: SK_AC has no member named PnmiStruct
skge.c:3543: error: SK_AC has no member named PnmiStruct
skge.c:3547: warning: implicit declaration of function copy_to_user
skge.c:3547: error: SK_AC has no member named PnmiStruct
skge.c:3552: error: dereferencing pointer to incomplete type
skge.c:3557: error: EOPNOTSUPP undeclared (first use in this function)
skge.c: In function SkGeIocMib:
skge.c:3592: error: SK_AC has no member named SlowPathLock
skge.c:3594: error: SIOCDEVPRIVATE undeclared (first use in this function)
skge.c:3595: error: SK_AC has no member named IoBase
skge.c:3595: error: SK_AC has no member named PnmiStruct
skge.c:3596: error: too many arguments to function SkPnmiGetStruct
skge.c:3599: error: SK_AC has no member named IoBase
skge.c:3599: error: SK_AC has no member named PnmiStruct
skge.c:3600: error: too many arguments to function SkPnmiPreSetStruct
skge.c:3603: error: SK_AC has no member named IoBase
skge.c:3603: error: SK_AC has no member named PnmiStruct
skge.c:3604: error: too many arguments to function SkPnmiSetStruct
skge.c:3609: error: SK_AC has no member named SlowPathLock
skge.c: In function GetConfiguration:
skge.c:3630: error: s32 undeclared (first use in this function)
skge.c:3630: error: expected ; before Port
skge.c:3635: error: u8 undeclared (first use in this function)
skge.c:3635: error: expected ; before AutoSet
skge.c:3636: error: expected ; before DupSet
skge.c:3663: error: SK_AC has no member named Index
skge.c:3664: error: SK_AC has no member named Index
skge.c:3665: warning: implicit declaration of function strcmp
skge.c:3665: error: SK_AC has no member named Index
skge.c:3668: error: SK_AC has no member named Index
skge.c:3671: error: SK_AC has no member named Index
skge.c:3674: error: SK_AC has no member named Index
skge.c:3677: error: SK_AC has no member named Index
skge.c:3681: error: SK_AC has no member named dev
skge.c:3686: error: SK_GEINIT has no member named GIChipId
skge.c:3687: error: SK_GEINIT has no member named GICopperType
skge.c:3692: error: SK_AC has no member named dev
skge.c:3695: error: SK_GEINIT has no member named GP
skge.c:3699: error: AutoSet undeclared (first use in this function)
skge.c:3700: error: SK_AC has no member named Index
skge.c:3701: error: SK_AC has no member named Index
skge.c:3703: error: SK_AC has no member named Index
skge.c:3706: error: SK_AC has no member named Index
skge.c:3709: error: SK_AC has no member named Index
skge.c:3712: error: SK_AC has no member named Index
skge.c:3716: error: SK_AC has no member named dev
skge.c:3720: error: DupSet undeclared (first use in this function)
skge.c:3721: error: SK_AC has no member named Index
skge.c:3722: error: SK_AC has no member named Index
skge.c:3724: error: SK_AC has no member named Index
skge.c:3727: error: SK_AC has no member named Index
skge.c:3730: error: SK_AC has no member named Index
skge.c:3733: error: SK_AC has no member named Index
skge.c:3737: error: SK_AC has no member named dev
skge.c:3743: error: SK_AC has no member named dev
skge.c:3748: error: SK_AC has no member named dev
skge.c:3760: error: SK_AC has no member named dev
skge.c:3765: error: SK_GEINIT has no member named GP
skge.c:3768: error: SK_GEINIT has no member named GP
skge.c:3769: error: SK_AC has no member named Index
skge.c:3770: error: SK_AC has no member named Index
skge.c:3771: error: SK_AC has no member named Index
skge.c:3773: error: SK_AC has no member named Index
skge.c:3774: error: SK_GEINIT has no member named GP
skge.c:3777: error: SK_AC has no member named Index
skge.c:3778: error: SK_GEINIT has no member named GP
skge.c:3781: error: SK_AC has no member named Index
skge.c:3782: error: SK_GEINIT has no member named GP
skge.c:3785: error: SK_AC has no member named Index
skge.c:3786: error: SK_GEINIT has no member named GP
skge.c:3791: error: SK_GEINIT has no member named GP
skge.c:3795: error: SK_AC has no member named dev
skge.c:3796: error: SK_GEINIT has no member named GP
skge.c:3800: error: SK_AC has no member named Index
skge.c:3801: error: SK_AC has no member named Index
skge.c:3802: error: SK_AC has no member named Index
skge.c:3804: error: SK_AC has no member named Index
skge.c:3807: error: SK_AC has no member named Index
skge.c:3810: error: SK_AC has no member named Index
skge.c:3814: error: SK_AC has no member named dev
skge.c:3816: error: SK_GEINIT has no member named GP
skge.c:3822: error: SK_AC has no member named Index
skge.c:3823: error: SK_AC has no member named Index
skge.c:3824: error: SK_AC has no member named Index
skge.c:3827: error: SK_AC has no member named Index
skge.c:3830: error: SK_AC has no member named Index
skge.c:3833: error: SK_AC has no member named Index
skge.c:3836: error: SK_AC has no member named Index
skge.c:3840: error: SK_AC has no member named dev
skge.c:3845: error: SK_GEINIT has no member named GIChipId
skge.c:3846: error: SK_GEINIT has no member named GICopperType
skge.c:3851: error: SK_AC has no member named dev
skge.c:3854: error: SK_GEINIT has no member named GP
skge.c:3859: error: SK_AC has no member named Index
skge.c:3860: error: SK_AC has no member named Index
skge.c:3862: error: SK_AC has no member named Index
skge.c:3865: error: SK_AC has no member named Index
skge.c:3868: error: SK_AC has no member named Index
skge.c:3871: error: SK_AC has no member named Index
skge.c:3879: error: SK_AC has no member named Index
skge.c:3880: error: SK_AC has no member named Index
skge.c:3882: error: SK_AC has no member named Index
skge.c:3885: error: SK_AC has no member named Index
skge.c:3888: error: SK_AC has no member named Index
skge.c:3891: error: SK_AC has no member named Index
skge.c:3900: error: SK_AC has no member named dev
skge.c:3905: error: SK_AC has no member named dev
skge.c:3917: error: SK_AC has no member named dev
skge.c:3922: error: SK_GEINIT has no member named GP
skge.c:3925: error: SK_GEINIT has no member named GP
skge.c:3926: error: SK_AC has no member named Index
skge.c:3927: error: SK_AC has no member named Index
skge.c:3928: error: SK_AC has no member named Index
skge.c:3930: error: SK_AC has no member named Index
skge.c:3931: error: SK_GEINIT has no member named GP
skge.c:3934: error: SK_AC has no member named Index
skge.c:3935: error: SK_GEINIT has no member named GP
skge.c:3938: error: SK_AC has no member named Index
skge.c:3939: error: SK_GEINIT has no member named GP
skge.c:3942: error: SK_AC has no member named Index
skge.c:3943: error: SK_GEINIT has no member named GP
skge.c:3948: error: SK_GEINIT has no member named GP
skge.c:3952: error: SK_AC has no member named dev
skge.c:3953: error: SK_GEINIT has no member named GP
skge.c:3957: error: SK_AC has no member named Index
skge.c:3958: error: SK_AC has no member named Index
skge.c:3959: error: SK_AC has no member named Index
skge.c:3961: error: SK_AC has no member named Index
skge.c:3964: error: SK_AC has no member named Index
skge.c:3967: error: SK_AC has no member named Index
skge.c:3971: error: SK_AC has no member named dev
skge.c:3973: error: SK_GEINIT has no member named GP
skge.c:3977: error: SK_AC has no member named ActivePort
skge.c:3978: error: SK_AC has no member named Index
skge.c:3979: error: SK_AC has no member named Index
skge.c:3980: error: SK_AC has no member named Index
skge.c:3981: error: SK_AC has no member named ActivePort
skge.c:3982: error: SK_RLMT has no member named Net
skge.c:3983: error: SK_RLMT has no member named Net
skge.c:3985: error: SK_AC has no member named Index
skge.c:3990: error: Port undeclared (first use in this function)
skge.c:3991: error: SK_RLMT has no member named Net
skge.c:3992: error: SK_RLMT has no member named Net
skge.c:3994: error: SK_AC has no member named Index
skge.c:4000: error: SK_RLMT has no member named Net
skge.c:4001: error: SK_RLMT has no member named Net
skge.c:4004: error: SK_AC has no member named dev
skge.c:4007: error: SK_AC has no member named RlmtNets
skge.c:4009: error: SK_AC has no member named Index
skge.c:4010: error: SK_AC has no member named Index
skge.c:4011: error: SK_AC has no member named Index
skge.c:4012: error: SK_AC has no member named RlmtMode
skge.c:4014: error: SK_AC has no member named Index
skge.c:4015: error: SK_AC has no member named RlmtMode
skge.c:4017: error: SK_AC has no member named Index
skge.c:4018: error: SK_AC has no member named RlmtMode
skge.c:4021: error: SK_AC has no member named Index
skge.c:4022: error: SK_AC has no member named RlmtMode
skge.c:4026: error: SK_AC has no member named Index
skge.c:4027: error: SK_GEINIT has no member named GIMacsFound
skge.c:4028: error: SK_AC has no member named RlmtMode
skge.c:4029: error: SK_AC has no member named RlmtNets
skge.c:4033: error: SK_AC has no member named dev
skge.c:4034: error: SK_AC has no member named RlmtMode
skge.c:4038: error: SK_AC has no member named RlmtMode
skge.c: In function ProductStr:
skge.c:4062: error: SK_AC has no member named SlowPathLock
skge.c:4063: error: SK_AC has no member named IoBase
skge.c:4063: error: SK_AC has no member named DeviceStr
skge.c:4065: error: SK_AC has no member named SlowPathLock
skge.c:4070: error: SK_AC has no member named DeviceStr
skge.c: In function SkDrvAllocRlmtMbuf:
skge.c:4104: error: GFP_ATOMIC undeclared (first use in this function)
skge.c:4104: warning: assignment makes pointer from integer without a cast
skge.c:4108: error: dereferencing pointer to incomplete type
skge.c:4111: error: SK_MBUF has no member named pOs
skge.c:4112: error: SK_MBUF has no member named pData
skge.c:4112: error: dereferencing pointer to incomplete type
skge.c:4113: error: SK_MBUF has no member named Size
skge.c:4114: error: SK_MBUF has no member named Length
skge.c: In function SkDrvFreeRlmtMbuf:
skge.c:4144: error: SK_MBUF has no member named pOs
skge.c: At top level:
skge.c:4162: error: expected =, ,, ;, asm or __attribute__ before SkOsGetTime
skge.c:4183: error: expected declaration specifiers or ... before u32
skge.c: In function SkPciReadCfgDWord:
skge.c:4185: warning: implicit declaration of function pci_read_config_dword
skge.c:4185: error: SK_AC has no member named PciDev
skge.c:4185: error: pVal undeclared (first use in this function)
skge.c: At top level:
skge.c:4205: error: expected declaration specifiers or ... before u16
skge.c: In function SkPciReadCfgWord:
skge.c:4207: warning: implicit declaration of function pci_read_config_word
skge.c:4207: error: SK_AC has no member named PciDev
skge.c:4207: error: pVal undeclared (first use in this function)
skge.c: At top level:
skge.c:4227: error: expected declaration specifiers or ... before u8
skge.c: In function SkPciReadCfgByte:
skge.c:4229: warning: implicit declaration of function pci_read_config_byte
skge.c:4229: error: SK_AC has no member named PciDev
skge.c:4229: error: pVal undeclared (first use in this function)
skge.c: At top level:
skge.c:4249: error: expected declaration specifiers or ... before u32
skge.c: In function SkPciWriteCfgDWord:
skge.c:4251: warning: implicit declaration of function pci_write_config_dword
skge.c:4251: error: SK_AC has no member named PciDev
skge.c:4251: error: Val undeclared (first use in this function)
skge.c: At top level:
skge.c:4272: error: expected declaration specifiers or ... before u16
skge.c: In function SkPciWriteCfgWord:
skge.c:4274: warning: implicit declaration of function pci_write_config_word
skge.c:4274: error: SK_AC has no member named PciDev
skge.c:4274: error: Val undeclared (first use in this function)
skge.c: At top level:
skge.c:4295: error: expected declaration specifiers or ... before u8
skge.c: In function SkPciWriteCfgByte:
skge.c:4297: warning: implicit declaration of function pci_write_config_byte
skge.c:4297: error: SK_AC has no member named PciDev
skge.c:4297: error: Val undeclared (first use in this function)
skge.c: At top level:
skge.c:4320: error: expected declaration specifiers or ... before u32
skge.c: In function SkDrvEvent:
skge.c:4330: error: u8 undeclared (first use in this function)
skge.c:4330: error: expected ; before DualNet
skge.c:4332: error: Event undeclared (first use in this function)
skge.c:4336: error: SK_AC has no member named dev
skge.c:4338: error: SK_AC has no member named IoBase
skge.c:4342: error: SK_EVPARA has no member named Para32
skge.c:4346: error: SK_AC has no member named dev
skge.c:4348: error: SK_AC has no member named dev
skge.c:4354: error: SK_EVPARA has no member named Para32
skge.c:4357: error: SK_EVPARA has no member named Para64
skge.c:4358: error: incompatible type for argument 3 of SkPnmiEvent
skge.c:4358: error: too many arguments to function SkPnmiEvent
skge.c:4360: error: SK_AC has no member named TxPort
skge.c:4363: error: SK_AC has no member named dev
skge.c:4363: error: SK_EVPARA has no member named Para32
skge.c:4363: error: IFF_RUNNING undeclared (first use in this function)
skge.c:4365: error: SK_AC has no member named TxPort
skge.c:4369: error: SK_AC has no member named RxPort
skge.c:4369: error: too many arguments to function ReceiveIrq
skge.c:4371: error: SK_AC has no member named TxPort
skge.c:4373: error: SK_AC has no member named TxPort
skge.c:4379: error: SK_AC has no member named dev
skge.c:4381: error: SK_AC has no member named dev
skge.c:4384: error: too many arguments to function SkAddrMcUpdate
skge.c:4386: error: too many arguments to function SkGePollTxD
skge.c:4389: error: SK_AC has no member named TxPort
skge.c:4394: error: SK_EVPARA has no member named Para32
skge.c:4398: error: SK_AC has no member named dev
skge.c:4398: error: SK_EVPARA has no member named Para32
skge.c:4398: error: SK_EVPARA has no member named Para32
skge.c:4401: error: SK_GEINIT has no member named GP
skge.c:4412: error: SK_GEINIT has no member named GP
skge.c:4427: error: SK_GEINIT has no member named GP
skge.c:4442: error: SK_GEINIT has no member named GICopperType
skge.c:4443: error: SK_GEINIT has no member named GP
skge.c:4445: error: SK_GEINIT has no member named GP
skge.c:4458: error: SK_GEINIT has no member named GIChipId
skge.c:4467: error: SK_EVPARA has no member named Para32
skge.c:4467: error: SK_AC has no member named ActivePort
skge.c:4468: error: SK_AC has no member named RlmtNets
skge.c:4469: error: SK_EVPARA has no member named Para32
skge.c:4469: error: SK_AC has no member named ActivePort
skge.c:4470: error: SK_EVPARA has no member named Para32
skge.c:4470: error: SK_EVPARA has no member named Para32
skge.c:4472: error: incompatible type for argument 2 of SkEventQueue
skge.c:4472: error: too many arguments to function SkEventQueue
skge.c:4476: error: SK_AC has no member named dev
skge.c:4476: error: SK_EVPARA has no member named Para32
skge.c:4483: error: SK_AC has no member named dev
skge.c:4483: error: SK_EVPARA has no member named Para32
skge.c:4484: error: SK_AC has no member named dev
skge.c:4484: error: SK_EVPARA has no member named Para32
skge.c:4491: error: SK_AC has no member named dev
skge.c:4492: error: SK_EVPARA has no member named Para32
skge.c:4494: error: SK_EVPARA has no member named Para32
skge.c:4495: error: SK_EVPARA has no member named Para32
skge.c:4499: error: SK_EVPARA has no member named Para64
skge.c:4500: error: incompatible type for argument 3 of SkPnmiEvent
skge.c:4500: error: too many arguments to function SkPnmiEvent
skge.c:4501: error: SK_EVPARA has no member named Para64
skge.c:4502: error: incompatible type for argument 3 of SkPnmiEvent
skge.c:4502: error: too many arguments to function SkPnmiEvent
skge.c:4504: error: SK_AC has no member named TxPort
skge.c:4507: error: SK_AC has no member named TxPort
skge.c:4511: error: SK_AC has no member named TxPort
skge.c:4513: error: SK_AC has no member named TxPort
skge.c:4516: error: SK_AC has no member named RxPort
skge.c:4516: error: too many arguments to function ReceiveIrq
skge.c:4517: error: SK_AC has no member named RxPort
skge.c:4517: error: too many arguments to function ReceiveIrq
skge.c:4519: error: SK_AC has no member named TxPort
skge.c:4520: error: SK_AC has no member named TxPort
skge.c:4522: error: SK_AC has no member named TxPort
skge.c:4525: error: SK_AC has no member named TxPort
skge.c:4526: error: SK_AC has no member named ActivePort
skge.c:4531: error: DualNet undeclared (first use in this function)
skge.c:4532: error: SK_AC has no member named RlmtNets
skge.c:4538: error: SK_AC has no member named ActivePort
skge.c:4539: error: too many arguments to function SkGeInitAssignRamToQueues
skge.c:4541: error: SK_AC has no member named TxPort
skge.c:4543: error: SK_AC has no member named TxPort
skge.c:4552: error: SK_AC has no member named dev
skge.c:4558: error: too many arguments to function SkAddrSwap
skge.c:4559: error: too many arguments to function SkAddrMcUpdate
skge.c:4560: error: too many arguments to function SkAddrMcUpdate
skge.c:4563: error: too many arguments to function SkGePollTxD
skge.c:4564: error: too many arguments to function SkGePollTxD
skge.c:4568: error: SK_AC has no member named TxPort
skge.c:4570: error: SK_AC has no member named TxPort
skge.c:4577: error: SK_MBUF has no member named pOs
skge.c:4578: error: SK_MBUF has no member named Length
skge.c:4579: error: SK_AC has no member named TxPort
skge.c:4579: error: SK_MBUF has no member named PortIdx
skge.c:4580: warning: passing argument 3 of XmitFrame from incompatible pointer type
skge.c: In function SkErrorLog:
skge.c:4616: warning: implicit declaration of function strcpy
skge.c:4616: warning: incompatible implicit declaration of built-in function strcpy
skge.c:4637: error: KERN_INFO undeclared (first use in this function)
skge.c:4637: error: expected ) before string constant
make: *** [skge.o] Error 1
```

Does anybody know what am I doing wrong?

Thank you.

---

### Post by Floppyjoe on 2007-02-16
Possibly use the sudo prefix command:
```
sudo make load
```

---

### Post by Abadia on 2007-02-17
> Possibly use the sudo prefix command:
I've tried with the sudo prefix command, but unfortunately it appears the same error :(
Any other solution?

---

