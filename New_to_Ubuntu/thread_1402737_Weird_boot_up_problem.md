---
title: "Weird boot up problem"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2010-02-09
I have Ubuntu 9.10 in an Acer Aspire 5000. Some time ago, I started having to turn it on twice to get it running. The first time it would do nothing, and then when I shut it down and turn it on again, it would boot up without a problem. At the time, I opened a thread about it, and it was said to me that it was a hardware problem, which is not surprising, given that I know I at least have a hard drive issue.

Now, in the last few days, the problem changed. It still doesn't boot up at the first try, but it does start to do so, right until the drum thing.
It seems to be loading ok, and then when the little drum introduction sounds, the screen goes black, and that's it. Then I have to turn it off, and when I turn it on again, it boots up normally and keeps running perfectly.

Is this still a hardware problem? Does anybody have the same issue?

Thanks in advance. :)

---

### Post by Morimando on 2010-02-09
Do you use ext4? Is there an I/O error?
Have you run tests of your hd with smartctl/smartmon?
You can for example use smartctl -t long /dev/sda to run a long test on the drive :)
smartctl --all /dev/sda will show you the results :)

---

### Post by Inodoro Pereyra on 2010-02-09
Thanks Morimando for the reply, but all you just said is Chinese for me..

I'm as beginner a they come. I didn't run anything, as I don't have a clue what to do. If you can explain it to me, I'll do it. Thank you. :)

---

### Post by Morimando on 2010-02-09
> **Inodoro Pereyra said:**
> Thanks Morimando for the reply, but all you just said is Chinese for me..

I'm as beginner a they come. I didn't run anything, as I don't have a clue what to do. If you can explain it to me, I'll do it. Thank you. :)

Okay... to check your hd health, you can use SMART, at least if it's enabled in the BIOS (which it should be with a newer computer). To use SMART with Linux, install smartmontools via Synaptic.
After installation is complete, you can test your drives and inspect the results of these tests using 'smartctl' in a terminal.
```
smartctl -t long /dev/sda
```
for example will run a 30 minute test on your drive sda (first scsi or sata drive). Now that depends on which kind of drive you use as your primary drive, IDE or SATA/SCSI. If it's IDE, try smartctl -t long /dev/hda.
To collect the results, run
```
smartctl --all /dev/sda
```
Hopefully, that will tell you that all's okay. You can copy and paste the report here, but please remember to use the code tags to set off the copied output in your reply :)

edit: In case you're told about missing permissions, use "sudo" before smartctl (thus making it "sudo smartctl -t long /dev/sda" for example).

---

### Post by sameden on 2010-02-09
What i would do is use a old HD (if you have one) and try to run ubutnu on that, if the problem is still happening then it is most likely to be your motherboard, if it does work then it will be the hard drive. to try and fix the HD i would reformat it and reinstall ubuntu and see if that does the job.
If it is the motherboard then it sound like you need a new laptop.  

sam

---

### Post by Inodoro Pereyra on 2010-02-09
Thank you both. I'm running the test right now. Will report when it's done.

---

### Post by Inodoro Pereyra on 2010-02-09
Ok, here it is...

```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD600UE-22HCT0
Serial Number:    WD-WXE905491498
Firmware Version: 09.07D09
User Capacity:    60,011,642,880 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Feb  9 16:52:10 2010 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (3600) seconds.
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
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  50) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   198   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   190   186   021    Pre-fail  Always       -       1475
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5539
  5 Reallocated_Sector_Ct   0x0033   150   150   140    Pre-fail  Always       -       395
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       8641
 10 Spin_Retry_Count        0x0012   100   099   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   096   096   000    Old_age   Always       -       4060
192 Power-Off_Retract_Count 0x0032   195   195   000    Old_age   Always       -       3976
193 Load_Cycle_Count        0x0032   027   027   000    Old_age   Always       -       520513
194 Temperature_Celsius     0x0022   105   099   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   185   185   000    Old_age   Always       -       15
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 944 (device log contains only the most recent five errors)
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

Error 944 occurred at disk power-on lifetime: 6256 hours (260 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 94 b0 d0 e2  Error: UNC at LBA = 0x02d0b094 = 47231124

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 d8 01 94 b0 d0 02 58      00:28:02.600  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:28:02.600  READ DMA
  40 d8 01 93 b0 d0 02 58      00:27:59.500  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:59.500  READ DMA
  40 d8 02 99 b0 d0 02 58      00:27:59.480  READ VERIFY SECTOR(S)

Error 943 occurred at disk power-on lifetime: 6256 hours (260 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 93 b0 d0 e2  Error: UNC at LBA = 0x02d0b093 = 47231123

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 d8 01 93 b0 d0 02 58      00:27:59.500  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:59.500  READ DMA
  40 d8 02 99 b0 d0 02 58      00:27:59.480  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:59.480  READ DMA
  40 d8 02 97 b0 d0 02 58      00:27:55.525  READ VERIFY SECTOR(S)

Error 942 occurred at disk power-on lifetime: 6256 hours (260 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 02 98 b0 d0 e2  Error: UNC at LBA = 0x02d0b098 = 47231128

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 d8 02 97 b0 d0 02 58      00:27:55.525  READ VERIFY SECTOR(S)
  40 d8 02 95 b0 d0 02 58      00:27:52.790  READ VERIFY SECTOR(S)
  c8 d8 01 f4 5d aa 03 58      00:27:52.790  READ DMA
  40 d8 02 93 b0 d0 02 58      00:27:50.240  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:50.240  READ DMA

Error 941 occurred at disk power-on lifetime: 6256 hours (260 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 02 95 b0 d0 e2  Error: AMNF at LBA = 0x02d0b095 = 47231125

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 d8 02 95 b0 d0 02 58      00:27:52.790  READ VERIFY SECTOR(S)
  c8 d8 01 f4 5d aa 03 58      00:27:52.790  READ DMA
  40 d8 02 93 b0 d0 02 58      00:27:50.240  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:50.240  READ DMA
  40 d8 04 9b b0 d0 02 58      00:27:50.225  READ VERIFY SECTOR(S)

Error 940 occurred at disk power-on lifetime: 6256 hours (260 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 02 93 b0 d0 e2  Error: UNC at LBA = 0x02d0b093 = 47231123

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  40 d8 02 93 b0 d0 02 58      00:27:50.240  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:50.240  READ DMA
  40 d8 04 9b b0 d0 02 58      00:27:50.225  READ VERIFY SECTOR(S)
  c8 d8 01 00 00 00 00 58      00:27:50.225  READ DMA
  40 d8 04 97 b0 d0 02 58      00:27:46.675  READ VERIFY SECTOR(S)

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      8641         -
# 2  Extended offline    Completed without error       00%      8058         -

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

```Now...what does it mean??? :))

---

### Post by Morimando on 2010-02-09
It means that your drive gets an error sometimes about 27 minutes after power on. So that could mean that there are bad sectors that cause the boot problems or it could be problems with power management (27m is awfully close to 30m, but it's improbable).
I'd suggest you back up your data, as a precaution. Then try running Ubuntu from a new (or at least different) harddisk.
It really seems to be a physical/hard disk problem :( I was wondering (and thus asked about ext4), since I have the occasional unsuccessful boot but no errors on both drives. But seems to be a different issue.

---

### Post by Inodoro Pereyra on 2010-02-09
Thank you again.
I knew the hard drive was bad, because I get an error message every time I boot, but I didn't think a HD problem would cause that kind of error...:(

Anyways, looks like I'm gonna have to get a new HD...:(

---

### Post by sameden on 2010-02-22
hi
 
can i ask, what are the speaks of your computer?
 
sam

---

