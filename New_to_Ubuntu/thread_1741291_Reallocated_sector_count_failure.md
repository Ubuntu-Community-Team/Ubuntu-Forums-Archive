---
title: "Reallocated sector count failure"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-04-27
I am testing my hard disk health by using Ultimate Boot cd  and i got the following error and i shows that reallocated sector count failure! Pls help

Thank you

[B]complete error log:

SMART Error Log Version: 1
ATA Error Count: 11167 (device log contains only the most recent five errors)
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

Error 11167 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  a1 00 00 00 00 00 a0 00      00:23:44.833  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:44.828  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:23:44.661  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00      00:23:39.677  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.672  IDENTIFY DEVICE

Error 11166 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


[/B]
[HTML]smartctl 5.39.1 2010-01-28 r3054 [i486-slackware-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12 family
Device Model:     ST3250318AS
Serial Number:    9VY1LMLV
Firmware Version: CC35
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Apr 28 03:02:13 2011 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 600) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  48) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   104   092   006    Pre-fail  Always       -       37857001
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   096   096   020    Old_age   Always       -       4597
  5 Reallocated_Sector_Ct   0x0033   002   002   036    Pre-fail  Always   FAILING_NOW 4049
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       83087597
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4804
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2278
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       208
188 Command_Timeout         0x0032   100   094   000    Old_age   Always       -       287767265476
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   062   054   045    Old_age   Always       -       38 (Lifetime Min/Max 37/38)
194 Temperature_Celsius     0x0022   038   046   000    Old_age   Always       -       38 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   036   025   000    Old_age   Always       -       37857001
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       183369333745968
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2327276534
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       555781216

SMART Error Log Version: 1
ATA Error Count: 11167 (device log contains only the most recent five errors)
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

Error 11167 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  a1 00 00 00 00 00 a0 00      00:23:44.833  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:44.828  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:23:44.661  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00      00:23:39.677  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.672  IDENTIFY DEVICE

Error 11166 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:23:44.828  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:23:44.661  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00      00:23:39.677  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.672  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:23:39.505  NOP [Abort queued commands]

Error 11165 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  a1 00 00 00 00 00 a0 00      00:23:39.677  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.672  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:23:39.505  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00      00:23:39.481  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.436  IDENTIFY DEVICE

Error 11164 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:23:39.672  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:23:39.505  NOP [Abort queued commands]
  a1 00 00 00 00 00 a0 00      00:23:39.481  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.436  IDENTIFY DEVICE
  c8 00 00 58 65 2a e2 00      00:23:32.320  READ DMA

Error 11163 occurred at disk power-on lifetime: 4803 hours (200 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  a1 00 00 00 00 00 a0 00      00:23:39.481  IDENTIFY PACKET DEVICE
  ec 00 00 00 00 00 a0 00      00:23:39.436  IDENTIFY DEVICE
  c8 00 00 58 65 2a e2 00      00:23:32.320  READ DMA
  c8 00 a0 b8 64 2a e2 00      00:23:32.299  READ DMA
  c8 00 60 c0 fa b0 e4 00      00:23:32.298  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%      4132         0
# 2  Short offline       Completed: unknown failure    90%      4132         0
# 3  Conveyance offline  Completed without error       00%      2613         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.[/HTML]

---

### Post by Hedgehog1 on 2011-04-28
[SIZE="4"]**Backup any data you need from this drive RIGHT AWAY!**[/SIZE] 


```
Drive failure expected in less than 24 hours. SAVE ALL DATA.
```

The drive is failing **very quickly**.  It will need to be replaced right away.


***The Hedge***

:KS

p.s. If you were having problems with this PC, this may well explain them...

---

### Post by Paqman on 2011-04-28
Yep, that drive is as good as dead. I don't think i've ever seen one with over 4000 bad sectors. Back up and replace it asap!

---

### Post by 1991sudarshan on 2011-04-28
> **Paqman said:**
> Yep, that drive is as good as dead. I don't think i've ever seen one with over 4000 bad sectors. Back up and replace it asap!

How about doing the full format of the disk and check for the error again? The data re totally safe and I got the same error four months back when i was suing ubuntu 10.04 live cd!

---

### Post by 1991sudarshan on 2011-04-28
> **Hedgehog1 said:**
> [SIZE=4]**Backup any data you need from this drive RIGHT AWAY!**[/SIZE] 


```
Drive failure expected in less than 24 hours. SAVE ALL DATA.
```The drive is failing **very quickly**.  It will need to be replaced right away.


***The Hedge***

:KS

p.s. If you were having problems with this PC, this may well explain them...

the drive is failing very qucikly? But i am able to use the system normally but at times the icons turns into question marks for during first login and if i restart everything comes back to normal!

---

### Post by 1991sudarshan on 2011-04-28
??

---

### Post by Paqman on 2011-04-28
> **1991sudarshan said:**
> How about doing the full format of the disk and check for the error again? The data re totally safe and I got the same error four months back when i was suing ubuntu 10.04 live cd!

Formatting won't make any difference. It's the hardware that is faulty, not the filesystem. Back up your data and replace the drive.

---

### Post by seeker5528 on 2011-04-28
> **1991sudarshan said:**
> the drive is failing very qucikly? But i am able to use the system normally but at times the icons turns into question marks for during first login and if i restart everything comes back to normal!

The failing sectors could be on an unused part of the disk. 4000 sectors is a lot but only a small amount in terms of stored data, if files are affected it could be only a single file, but since it is a lot of sectors, it could potentially affect a lot of files, could be in an area used by the swap partition or where some temporary file is stored.

> **1991sudarshan said:**
> How about doing the full format of the disk and check for the error again?

If it was a read failure on a single sector or a couple of sectors, formatting might help because sectors are only re-allocated when the bad sector is attempted to be written to.

I believe the typical threshold before the SMART system will start reporting that the disk is failing is 5, 4000+ is definitely way too many.

Later, Seeker

---

