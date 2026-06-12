---
title: "Cant copy a 2.7GB file to USB drive"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by moody_mark on 2009-01-08
I have a iso image that I want to copy to a USB drive. The image file is about 2.7GB. Im running 8.04 and can see the file on my ~/Desktop folder ok.

I have a 500GB network drive and another 500GB USB drive, both with plenty of free space. I cannot transfer the file to either of them, it always gets to 205MB then fails with a I/O read write error. I saw the following errors in my /var/log/messages log file

```

Jan  8 08:52:02 Barney kernel: [62858.328799] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan  8 08:52:02 Barney kernel: [62858.328834] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan  8 08:52:02 Barney kernel: [62858.328846] end_request: I/O error, dev sda, sector 57570220

```

Any ideas what this could be? perhaps i need to do something for USb / networking support of large files?

---

### Post by squaregoldfish on 2009-01-08
The error message you're getting is a read error, which implies that there's probably not a problem with either the network drive or the USB drive. It sounds more like an issue with the source hard drive. To test this, try copying the file to another folder on the hard drive. If you can't manage this, I'm afraid your hard drive is probably heading towards the dustbin.

Steve.

---

### Post by moody_mark on 2009-01-08
Oh oh! Your right.... I done a simple;

cp Desktop/<file> ~/Documents/

The cp operation didnt report any failure to the terminal but the /var/log/messages file shows;

```
Jan  8 09:44:07 Barney -- MARK --
Jan  8 10:00:57 Barney kernel: [64974.422813]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [64974.430683] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [64974.430700] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [64983.566349]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [64983.569514] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [64983.569535] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [64992.507160]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [64992.509940] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [64992.509962] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65001.519081]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65001.525808] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65001.525831] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65010.742723]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65010.749730] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65010.749752] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65020.169796]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65020.173413] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65020.173438] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan  8 10:00:57 Barney kernel: [65020.173446] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan  8 10:00:57 Barney kernel: [65020.173455] Descriptor sense data with sense descriptors (in hex):
Jan  8 10:00:57 Barney kernel: [65020.173460]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan  8 10:00:57 Barney kernel: [65020.173475]         03 6e 73 ac 
Jan  8 10:00:57 Barney kernel: [65020.173481] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan  8 10:00:57 Barney kernel: [65020.173494] end_request: I/O error, dev sda, sector 57570220
Jan  8 10:00:57 Barney kernel: [65020.173518] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65020.197444] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Jan  8 10:00:57 Barney kernel: [65020.220075] sd 0:0:0:0: [sda] Write Protect is off
Jan  8 10:00:57 Barney kernel: [65029.034951]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65029.037813] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65029.037835] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65038.415421]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65038.419675] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65038.419696] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65047.280939]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65047.284324] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65047.284346] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65057.410939]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65057.414431] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65057.414453] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [27842.312068]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [27842.314182] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [27842.314197] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65077.030009]          res 51/40:03:ac:73:6e/00:00:00:00:00/e3 Emask 0x9 (media error)
Jan  8 10:00:57 Barney kernel: [65077.039547] ata1.00: configured for UDMA/100
Jan  8 10:00:57 Barney kernel: [65077.039575] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan  8 10:00:57 Barney kernel: [65077.039583] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jan  8 10:00:57 Barney kernel: [65077.039592] Descriptor sense data with sense descriptors (in hex):
Jan  8 10:00:57 Barney kernel: [65077.039596]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan  8 10:00:57 Barney kernel: [65077.039611]         03 6e 73 ac 
Jan  8 10:00:57 Barney kernel: [65077.039618] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jan  8 10:00:57 Barney kernel: [65077.039630] end_request: I/O error, dev sda, sector 57570220
Jan  8 10:00:57 Barney kernel: [65077.039655] ata1: EH complete
Jan  8 10:00:57 Barney kernel: [65077.063044] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan  8 10:00:57 Barney kernel: [65077.115269] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Jan  8 10:00:57 Barney kernel: [65077.145609] sd 0:0:0:0: [sda] Write Protect is off
Jan  8 10:00:57 Barney kernel: [65077.145662] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
curtis@Barney:/var/log$ 
```

Is there any other tests I could do on my HDD to see how long I have left?

---

### Post by squaregoldfish on 2009-01-08
There's the SMART tests that are supposed to be able to spot a dying drive, but I've never used them to know how they work. You can try running fsck as well, although the partition has to be unmounted for that, so I'm not sure how you go about checking the root partition (a quick bit of Googling should help you there).

To be honest though, I'd do as full a backup as you can straight away, and replace the drive as soon as possible (today, preferably!). In my experience, once a drive starts to go, it's a slippery slope and there's no telling how long you've got before it packs up altogether. Could be a month, could be a year, could be a couple of hours.

Steve.

---

### Post by detroit/zero on 2009-01-08
> **squaregoldfish said:**
> There's the SMART tests that are supposed to be able to spot a dying drive, but I've never used them to know how they work.
```
sudo apt-get install smartmontools
```followed by ```
sudo smartctl -a /dev/sdX
```where sdX is, of course, your hard disk. The -a is the "all" switch. There are other specific tests. Use ```
smartctl --help
``` to get a usage summary.

Smartctl does provide a LOT of info, and might help OP figure out if his HDD is going bad. Here's a report on my hard drive:```
$zero@zero-laptop:~$ sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K160 series
Device Model:     Hitachi HTS541612J9SA00
Serial Number:    SB3D04E5JLJEXE
Firmware Version: SBDOC7DP
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Thu Jan  8 11:18:13 2009 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 645) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  73) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   230   230   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       942
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   072   072   000    Old_age   Always       -       12591
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       698
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       258
193 Load_Cycle_Count        0x0012   016   016   000    Old_age   Always       -       845198
194 Temperature_Celsius     0x0002   157   157   000    Old_age   Always       -       35 (Lifetime Min/Max 15/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       6
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 18 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 18 occurred at disk power-on lifetime: 11275 hours (469 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 10 1f cb e3  Error: UNC 1 sectors at LBA = 0x03cb1f10 = 63643408

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 09 1f cb e3 08   4d+18:08:31.400  READ DMA
  27 00 00 00 00 00 e0 08   4d+18:08:31.400  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08   4d+18:08:31.400  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08   4d+18:08:31.400  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08   4d+18:08:31.400  READ NATIVE MAX ADDRESS EXT

Error 17 occurred at disk power-on lifetime: 11275 hours (469 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 10 1f cb e3  Error: UNC 1 sectors at LBA = 0x03cb1f10 = 63643408

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 09 1f cb e3 08   4d+18:08:27.500  READ DMA
  27 00 00 00 00 00 e0 08   4d+18:08:27.500  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08   4d+18:08:27.400  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08   4d+18:08:27.400  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08   4d+18:08:27.400  READ NATIVE MAX ADDRESS EXT

Error 16 occurred at disk power-on lifetime: 11275 hours (469 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 10 1f cb e3  Error: UNC 1 sectors at LBA = 0x03cb1f10 = 63643408

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 09 1f cb e3 08   4d+18:08:23.500  READ DMA
  27 00 00 00 00 00 e0 08   4d+18:08:23.500  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08   4d+18:08:23.500  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08   4d+18:08:23.500  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08   4d+18:08:23.500  READ NATIVE MAX ADDRESS EXT

Error 15 occurred at disk power-on lifetime: 11275 hours (469 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 10 1f cb e3  Error: UNC 1 sectors at LBA = 0x03cb1f10 = 63643408

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 09 1f cb e3 08   4d+18:08:19.500  READ DMA
  27 00 00 00 00 00 e0 08   4d+18:08:19.500  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08   4d+18:08:19.500  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08   4d+18:08:19.500  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08   4d+18:08:19.500  READ NATIVE MAX ADDRESS EXT

Error 14 occurred at disk power-on lifetime: 11275 hours (469 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 10 1f cb e3  Error: UNC 1 sectors at LBA = 0x03cb1f10 = 63643408

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 09 1f cb e3 08   4d+18:08:15.500  READ DMA
  27 00 00 00 00 00 e0 08   4d+18:08:15.500  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08   4d+18:08:15.400  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 08   4d+18:08:15.400  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08   4d+18:08:15.400  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by bryncoles on 2009-01-08
I'm gonna wade in with a simple question - what file type are the drives using? are the NTFS/fat32, for windows compatibility, or are they ext2 or ext3? 

i ask because back in the day, when i first switched to ubuntu i kept my external drive in NTFS for windows compatibility, and i had this same issue. 

turns out, the problem was fragmentation. if the drive is fragmented (which happens to NTFS and Fat partitions), linux cant write data to it. 

so, if you have windows available, try booting into that and defragging your external drives. 

that might fix the problem (if you're lucky!)

---

### Post by detroit/zero on 2009-01-08
> **bryncoles said:**
> turns out, the problem was fragmentation. if the drive is fragmented (which happens to NTFS and Fat partitions), linux cant write data to it. 

so, if you have windows available, try booting into that and defragging your external drives. 

that might fix the problem (if you're lucky!)
That's a good point, and more likely than a hardware failure if the drive isn't all that old.

---

### Post by squaregoldfish on 2009-01-08
But we've already seen that this is a read error, and the file can't be copied on its own drive. This is why I think it's the source drive that's faulty.

---

### Post by moody_mark on 2009-01-09
Heres the output of the smartmon tools, my load cycle count, is that quite high?

```

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD series (30-60 GB)
Device Model:     TOSHIBA MK4018GAP
Serial Number:    62GA0572T
Firmware Version: M0.03 A
User Capacity:    40,007,761,920 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jan  9 09:23:06 2009 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 421) seconds.
Offline data collection
capabilities: 			 (0x1b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  47) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1693
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4253
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       8
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   071   071   000    Old_age   Always       -       11670
 10 Spin_Retry_Count        0x0033   185   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2276
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       130
193 Load_Cycle_Count        0x0032   053   053   000    Old_age   Always       -       476136
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       8
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       167
222 Loaded_Hours            0x0032   079   079   000    Old_age   Always       -       8415
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       138
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       15

SMART Error Log Version: 1
ATA Error Count: 365 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 365 occurred at disk power-on lifetime: 11657 hours (485 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 ac 73 6e e3  Error: UNC 3 sectors at LBA = 0x036e73ac = 57570220

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a7 73 6e e3 00   1d+02:25:49.169  READ DMA
  f8 00 00 00 00 00 e0 00   1d+02:25:49.168  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 00   1d+02:25:49.160  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+02:25:49.153  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00   1d+02:25:49.152  READ NATIVE MAX ADDRESS

Error 364 occurred at disk power-on lifetime: 11657 hours (485 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 ac 73 6e e3  Error: UNC 3 sectors at LBA = 0x036e73ac = 57570220

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a7 73 6e e3 00   1d+02:25:40.413  READ DMA
  f8 00 00 00 00 00 e0 00   1d+02:25:40.412  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 00   1d+02:25:40.404  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+02:25:40.397  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00   1d+02:25:40.396  READ NATIVE MAX ADDRESS

Error 363 occurred at disk power-on lifetime: 11657 hours (485 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 ac 73 6e e3  Error: UNC 3 sectors at LBA = 0x036e73ac = 57570220

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a7 73 6e e3 00   1d+02:25:31.620  READ DMA
  f8 00 00 00 00 00 e0 00   1d+02:25:31.620  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 00   1d+02:25:31.613  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+02:25:31.612  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00   1d+02:25:31.612  READ NATIVE MAX ADDRESS

Error 362 occurred at disk power-on lifetime: 11657 hours (485 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 ac 73 6e e3  Error: UNC 3 sectors at LBA = 0x036e73ac = 57570220

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a7 73 6e e3 00   1d+02:25:22.929  READ DMA
  f8 00 00 00 00 00 e0 00   1d+02:25:22.928  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 00   1d+02:25:22.920  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+02:25:22.912  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00   1d+02:25:22.912  READ NATIVE MAX ADDRESS

Error 361 occurred at disk power-on lifetime: 11657 hours (485 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 ac 73 6e e3  Error: UNC 3 sectors at LBA = 0x036e73ac = 57570220

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 a7 73 6e e3 00   1d+02:25:14.168  READ DMA
  f8 00 00 00 00 00 e0 00   1d+02:25:14.168  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 00   1d+02:25:14.160  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+02:25:14.153  SET FEATURES [Set transfer mode]
  f8 00 00 00 00 00 e0 00   1d+02:25:14.152  READ NATIVE MAX ADDRESS

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging

```

---

### Post by squaregoldfish on 2009-01-09
It does seem high, yes. However, the hard drive power saving modes may well spin your drive up and down quite frequently. This is a whole different discussion, however.

Although I don't claim to be an expert on hard drive operation, the power cycling shouldn't affect the integrity of your disk - the disk heads are always parked in a safe place on power down. Much more likely is that the surface of the disk itself is damaged in some way.

I think the next step is to run a full check on the partition. Boot your machine in Recovery Mode (from the Grub menu on startup), and then run fsck at the resulting prompt. Make a note of any errors you get, and we'll see where we stand then.

Steve.

---

### Post by lazyart on 2009-01-09
Back up your data QUICKLY.  Use a live cd, mount your disk and copy it off to another drive.

When a drive starts to go I consider the revolutions precious.  You don't know how many you have left. Backup first, then start with the disk checks.

---

### Post by moody_mark on 2009-01-09
Im wondering if I really do have problems, although Im not doubting a read error as indicative of some problem on the horizon. I booted into the live CD and didnt mount the HDD, I ran a fsck command and got the following;

```
ubuntu@ubuntu:~$ sudo fsck -V /dev/sda1
fsck 1.40.8 (13-Mar-2008)
[/sbin/fsck.ext3 (1) -- /dev/sda1] fsck.ext3 /dev/sda1 
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 218337/2342912 files, 6312052/9355846 blocks

```

Also my Load_Cycle_Count wasnt increasing that much, I think it upped by 2 over the period of about 3 hours today.

If fsck says "clean" does that mean my HDD is ok?

---

### Post by niteshifter on 2009-01-09
Hi,

fsck saying clean means the *file system* is OK. Not at all the same as saying the HD is OK.

About that Load_Cycle_Count: The real value of the S.M.A.R.T. tools is historical, that is comparing values read over time in use. A one-time look at some of the parameters isn't at all useful. It's been noted in these forums and elsewhere the Load_Cycle_Count gives "bogus" info on some drives and systems.

IOW, I wouldn't worry about Load_Cycle_Count. Where I you, I would pay attention to the logged read errors: backup, verify the backup and replace the drive.

---

### Post by squaregoldfish on 2009-01-09
It doesn't look as though fsck actually performed any tests, which is a bit odd. Unfortunately my fsck knowledge is minimal, so I don't really know why it didn't do anything.

Anyway, as others have said, you definitely have a broken hard drive, and it needs to be backed up and replaced as quickly as possible. Once that's done, you can mess around with the old drive at your leisure.

---

