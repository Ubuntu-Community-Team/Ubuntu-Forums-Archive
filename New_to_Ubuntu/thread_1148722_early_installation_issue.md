---
title: "early installation issue"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by KILLER RABBIT on 2009-05-04
trying to instal 9.04 i burned the iso to a disk, when i boot from the cd and click instal ubuntu after having just sitting for a while got stuck loading at a line that said * enabling bluetooth [ok]

i do not have blue tooth if that matters. 

on another try of just running it off the disk it got to a with the mouse working. the box had unknown characters.  showing just little squares, with one unknown clickable button. i clicked it and then itjust seemed to suspend the installation after refreshing the monitor a few times.

---

### Post by overdrank on 2009-05-04
> **KILLER RABBIT said:**
> trying to instal 9.04 i burned the iso to a disk, when i boot from the cd and click instal ubuntu after having just sitting for a while got stuck loading at a line that said * enabling bluetooth [ok]

i do not have blue tooth if that matters. 

on another try of just running it off the disk it got to a with the mouse working. the box had unknown characters.  showing just little squares, with one unknown clickable button. i clicked it and then itjust seemed to suspend the installation after refreshing the monitor a few times.

Hi and welcome, could you give us some specs on the system?
Have you checked the cd for errors?
You may have a look [here]("https://help.ubuntu.com/community/BurningIsoHowto") at burning the cd and HowToMD5SUM.

Moved to Absolute Beginner Talk

---

### Post by Panagiotis on 2009-05-04
:lolflag:> **overdrank said:**
> Hi and welcome, could you give us some specs on the system?
Have you checked the cd for errors?
You may have a look [here]("https://help.ubuntu.com/community/BurningIsoHowto") at burning the cd and HowToMD5SUM.

Moved to Absolute Beginner Talk I am in the process of burning the two new downloads to CDROM with 9.04 desktop server for 32-bit & 64-bit versions of ubuntu, I have Nero 9 installed on my XP home laptop, and want to know how to MD5SUM prior of burning the 1,4G double package download.

here are my spec. for the new ubuntu server double install deployment package:

I plan use two PCs test system setup: 1st a Tyan S475 Trinity (Lic. Award 2005 upd bios) Worstation Intel4\HT 875P MCH board, 1GB ECC kit DDR, 2LAN controlers, Via Fireware 2xport, IDE\SATA Intel ICH5 & one extra Promise Raid IDE\SATA, ATI-AGP\S3-PCI\NVidia-AGP/PCI?? VGA

2nd a new Asus AM2+ AMD Quad Phenom board (AMI 2008 bios) with onboard VGA from ATI HD3300 that supports HDMI projector,  2GB kit DDR2, Marvell GigLan, LSI Fireware 2xport, SATAII & eSATAII, as a backup card a NVidia 9600 VGA for use in case of trouble with onboard ATI chip    

thanks,:confused:

---

### Post by KILLER RABBIT on 2009-05-06
checked the cd. came back fine. also did the memory check. came back ok.  dell dimension 2200

---

### Post by Didius Falco on 2009-05-06
This may be worth a try - can't hurt, I'd say...

[http://ubuntuforums.org/showpost.php?p=7220298&postcount=2](http://ubuntuforums.org/showpost.php?p=7220298&postcount=2)

Regards,

Didius

---

### Post by Panagiotis on 2009-05-07
> **KILLER RABBIT said:**
> checked the cd. came back fine. also did the memory check. came back ok.  dell dimension 2200
:confused: Nero 9 data verification fails after successfully finish the Ubuntu 9.04 ISO image (too many errors) burning, the Ubuntu install boot up screen shows OK but there is no way to tell if the files burned are correct ...

6.5.2009
CD Image
22:08:15    #1 Text 0 File SCSIPTICommands.cpp, Line 450
    LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
    
22:08:15    #2 Text 0 File Burncd.cpp, Line 3233
    _NEC DVD+-RW ND-6500A
    JustLink activated
    
22:08:16    #3 Text 0 File Burncd.cpp, Line 3563
    Turn on UltraRaw 96-Mode, using CD-R/RW media
    
22:08:17    #4 Text 0 File DlgWaitCD.cpp, Line 312
    Last possible write address on media:   366223 ( 81:24.73)
    Last address to be written:             357865 ( 79:33.40)
    
22:08:17    #5 Text 0 File DlgWaitCD.cpp, Line 324
    Write in overburning mode: NO (enabled: CD)
    
22:08:17    #6 Text 0 File DlgWaitCD.cpp, Line 2951
    Recorder: _NEC DVD+-RW ND-6500A;
       CDR code: 00 97 17 06; OSJ entry from: Moser Baer India Limited
       ATIP Data:
         Special    Info [hex] 1: D0 00 A0, 2: 61 11 06 (LI 97:17.06), 3: 4F 3B 4A (LO 79:59.74)
         Additional Info [hex] 1: 00 00 80 (invalid), 2: 00 00 00 (invalid), 3: 00 00 00 (invalid)
    
22:08:17    #7 Text 0 File DlgWaitCD.cpp, Line 499
    >>> Protocol of DlgWaitCD activities: <<<
    =========================================
    
22:08:17    #8 Text 0 File ThreadedTransferInterface.cpp, Line 756
    Setup items (after recorder preparation)
     0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
        2 indices, index0 (150) not provided
        original disc pos #0 + 357866 (357866) = #357866/79:31.41
        not relocatable, disc pos for caching/writing not required/not required
        -> TRM_ULTRARAW96_MODE1, 2448, config 4, wanted index0 0 blocks, length 357866 blocks [D: _NEC DVD+-RW ND-6500A]
    --------------------------------------------------------------
    
22:08:17    #9 Text 0 File ThreadedTransferInterface.cpp, Line 958
    Prepare [D: _NEC DVD+-RW ND-6500A] for write in raw writing
    DAO infos:
    ==========
     MCN: ""
     TOCType: 0x00; Session Closed, disc fixated
     Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
       1: TRM_ULTRARAW96_MODE1, 2448/0x04, FilePos             0        367200     876423168, ISRC ""
    DAO layout:
    ===========
     ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
         -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
         -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
            0 |        1 |   1 |    0x41 |   357866 |   357866 | 0x00
       357866 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
    
22:08:17    #10 Text 0 File SCSIPTICommands.cpp, Line 240
    SPTILockVolume - completed successfully for FSCTL_LOCK_VOLUME
    
22:08:17    #11 Text 0 File Burncd.cpp, Line 4362
    Caching options: cache CDRom or Network-No, small files-No (<64KB)
    
22:08:17    #12 Phase 36 File dlgbrnst.cpp, Line 1767
    Burn process started at 8x (1.200 KB/s)
    
22:08:17    #13 Text 0 File ThreadedTransferInterface.cpp, Line 2675
    Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
    
22:08:17    #14 Text 0 File MMC.cpp, Line 17849
    StartDAO : CD-Text - Off
    
22:08:17    #15 Text 0 File MMC.cpp, Line 22511
    Set BUFE: JustLink -> ON 
    
22:08:18    #16 Text 0 File ThreadedTransfer.cpp, Line 273
    Pipe memory size 83836800
    
22:18:42    #17 Text 0 File WriterStatus.cpp, Line 245
    <D: _NEC DVD+-RW ND-6500A> start writing Lead-Out at LBA 357866 (575EAh), length 375 blocks
    
22:18:44    #18 Text 0 File DVDPlusDualLayer.cpp, Line 1424
    SetDriveCaps: Set LAST LBA of layer 1 to 0
    
22:18:44    #19 Phase 37 File dlgbrnst.cpp, Line 1767
    Burn process completed successfully at 8x (1.200 KB/s)
    
22:18:45    #20 Phase 78 File dlgbrnst.cpp, Line 1767
    Data verification started
    
22:18:47    #21 Text 0 File ThreadedTransferInterface.cpp, Line 1029
    Removed 2 run-out blocks from end of track 1. Length: 357866 -> 357864.
    
22:18:47    #22 Text 0 File ThreadedTransfer.cpp, Line 273
    Pipe memory size 590400
    
22:18:47    #23 SPTI -1047 File SCSIPassThrough.cpp, Line 215
    CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
    CDB Data:   0x28 00 00 00 00 00 00 00 01 00 00 00 
    Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
    Sense Code: 0x64
    Sense Qual: 0x00
    Sense Area: 0x70 00 05 00 00 00 00 0A 00 00 00 00 64 
    Buffer x063b9f40: Len x800

........

22:18:47    #265 SPTI -1047 File SCSIPassThrough.cpp, Line 215
    CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1047)
    CDB Data:   0x28 00 00 00 00 F2 00 00 01 00 00 00 
    Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
    Sense Code: 0x64
    Sense Qual: 0x00
    Sense Area: 0x70 00 05 00 00 00 00 0A 00 00 00 00 64 
    Buffer x06440040: Len x800
    
22:18:48    #266 SectorVerify 20 File Cdrdrv.cpp, Line 11386
    Read errors from sector 0 to 1055
    
22:18:48    #267 CDR -1222 File Writer.cpp, Line 203
    Verification aborted, too much errors
    D: _NEC DVD+-RW ND-6500A
    
22:18:48    #268 Phase 81 File dlgbrnst.cpp, Line 1767
    Data verification failed
    
22:18:48    #269 Text 0 File SCSIPTICommands.cpp, Line 287
    SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
    
22:18:48    #270 Text 0 File Cdrdrv.cpp, Line 11444
    DriveLocker: UnLockVolume completed
    
22:18:48    #271 Text 0 File SCSIPTICommands.cpp, Line 450
    UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
    

Existing drivers:

Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon\AllocateCDROMs : 1 (Security Option) 


also there is n o way to exit the boot up welcome to Ubuntu screen but to restat the system and removing the boot cd so that windows boot will continue.

How do I do a MD5 sum check :confused:?? by the way the same problem I have with the MAC OS Leopard update 5.0.6

thanks,

---

### Post by carml on 2009-05-07
First of all I suggest you to retry to write the ISO file to a lower burn velocity.To check the md5 this SW should do the job: md5sum.exe. 
Let us know if you have got any more problems. :)

---

