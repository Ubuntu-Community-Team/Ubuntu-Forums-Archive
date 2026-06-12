---
title: "Ubuntu has stop booting.. Need help"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by joelNr on 2008-12-10
Hi people.  Ive been using Ubuntu 8.10 i386 for around 2 months now with no problems at all.

this morning when I turned my PC on it booted to the Ubuntu loading screen and then gave me this error:

Gave up waiting for root device. Common Problems:

 -Boot args (cat/proc/cmdline)
    -Check rootdelay= (did the system wait long enough)
    -Check root= (did the system wait for the right device)
-missing modules (cat/proc/modules ; ls /dev)

ALERT! dev/disk/by-uuid/20b711a5 - fd37 - 4849 - a9aa - b5579daf1247 DOES NOT EXIST. DROPPING TO A SHELL!


So thats what has happend all but 1 time, where it booted properly but ran so slow it wasn't funny.

As far as I know none of the settings have been changed software/hardware wise.

Please help me sort this out as most of that warning I do not understand.

---

### Post by az on 2008-12-10
> **joelNr said:**
> Hi people.  Ive been using Ubuntu 8.10 i386 for around 2 months now with no problems at all.

this morning when I turned my PC on it booted to the Ubuntu loading screen and then gave me this error:

Gave up waiting for root device. Common Problems:

 -Boot args (cat/proc/cmdline)
    -Check rootdelay= (did the system wait long enough)
    -Check root= (did the system wait for the right device)
-missing modules (cat/proc/modules ; ls /dev)

ALERT! dev/disk/by-uuid/20b711a5 - fd37 - 4849 - a9aa - b5579daf1247 DOES NOT EXIST. DROPPING TO A SHELL!


So thats what has happend all but 1 time, where it booted properly but ran so slow it wasn't funny.

As far as I know none of the settings have been changed software/hardware wise.

Please help me sort this out as most of that warning I do not understand.

Your hard disk is failing or there is another hardware problem that is preventing your computer to read the hard disk.  By the fact that you are getting that far into the boot process, your drive is still recognised by your computer and you may still be able to recover data from it before it dies completely.

I suggest you boot a live cd and try to copy your important data onto another disk.  If that fails, see this:

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by joelNr on 2008-12-10
> **az said:**
> Your hard disk is failing or there is another hardware problem that is preventing your computer to read the hard disk.  By the fact that you are getting that far into the boot process, your drive is still recognised by your computer and you may still be able to recover data from it before it dies completely.

I suggest you boot a live cd and try to copy your important data onto another disk.  If that fails, see this:

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

Thankyou for the quick reply, and I think you are probably right. It is a very old Hdd. I have all important files backed up already. Time to fish out another hard drive from the pile I think.

Thanks again

---

### Post by caljohnsmith on 2008-12-10
If you want to get a better confirmation of whether your HDD is failing, you can run a "SMART" HDD test from Ubuntu by doing:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please post the contents of the two files on your desktop so I can see the results. 

Also, have you by chance tried booting with a different kernel yet? If you have another kernel in your Grub menu, how about trying that and see if it gives you the same results. Let me know how it goes.

---

### Post by turkdavid on 2008-12-10
caljohnsmith - Sorry I dont mean to hijack you thread, But I have a similar problem.

I was given a laptop that was droped on the floor and vista would not load correctly. So I attempted to load Mandriva fist but the same outcome installed fine but would not load correct got froze on the start screen. So installed Ubuntu and it installed fine and works flawless. "That I am aware of"

I ran the same code you recomended and I got:
```

david@david-laptop:~$ sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
david@david-laptop:~$ sudo smartctl -t long /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 58 minutes for test to complete.
Test will complete after Wed Dec 10 15:21:25 2008

Use smartctl -X to abort test.
david@david-laptop:~$ sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
david@david-laptop:~$ sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
david@david-laptop:~$ 
```

Have I done something wrong.. it say the test failed

---

### Post by turkdavid on 2008-12-10
Before test
```

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD1200BEVS-60UST0
Serial Number:    WD-WXE907241352
Firmware Version: 01.01A01
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Dec 10 14:23:01 2008 CST
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
data collection: 		 (4560) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  58) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   160   159   021    Pre-fail  Always       -       1000
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3299
  5 Reallocated_Sector_Ct   0x0033   169   169   140    Pre-fail  Always       -       248
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1692
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1517
187 Reported_Uncorrect      0x0032   100   001   000    Old_age   Always       -       425
188 Unknown_Attribute       0x0032   100   095   000    Old_age   Always       -       4295032837
190 Airflow_Temperature_Cel 0x0022   065   047   040    Old_age   Always       -       35
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       84
193 Load_Cycle_Count        0x0032   176   176   000    Old_age   Always       -       74309
194 Temperature_Celsius     0x0022   108   090   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   189   189   000    Old_age   Always       -       11
197 Current_Pending_Sector  0x0012   200   198   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 392 (device log contains only the most recent five errors)
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

Error 392 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:37.428  READ DMA
  ec 00 00 00 00 00 00 00      00:17:37.428  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:37.428  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:37.427  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:33.566  READ DMA

Error 391 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:33.566  READ DMA
  ec 00 00 00 00 00 00 00      00:17:33.566  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:33.566  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:33.565  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:29.685  READ DMA

Error 390 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:29.685  READ DMA
  ec 00 00 00 00 00 00 00      00:17:29.684  IDENTIFY DEVICE
  ef 10 03 00 00 00 00 00      00:17:29.684  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 00 00      00:17:29.683  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:29.683  SET FEATURES [Set transfer mode]

Error 389 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:24.146  READ DMA
  ec 00 00 00 00 00 00 00      00:17:24.146  IDENTIFY DEVICE
  ef 03 44 00 00 00 00 00      00:17:24.146  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:24.145  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:20.286  READ DMA

Error 388 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:20.286  READ DMA
  ec 00 00 00 00 00 00 00      00:17:20.285  IDENTIFY DEVICE
  ef 03 44 00 00 00 00 00      00:17:20.285  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:20.284  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:16.426  READ DMA

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

```

After test
[CODE]smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD1200BEVS-60UST0
Serial Number:    WD-WXE907241352
Firmware Version: 01.01A01
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Dec 10 14:40:28 2008 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (4560) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  58) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   160   159   021    Pre-fail  Always       -       1000
  4 Start_Stop_Count        0x0032   097   097   000    Old_age   Always       -       3299
  5 Reallocated_Sector_Ct   0x0033   169   169   140    Pre-fail  Always       -       248
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1692
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1517
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       424
188 Unknown_Attribute       0x0032   100   095   000    Old_age   Always       -       4295032837
190 Airflow_Temperature_Cel 0x0022   064   047   040    Old_age   Always       -       36
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       84
193 Load_Cycle_Count        0x0032   176   176   000    Old_age   Always       -       74348
194 Temperature_Celsius     0x0022   107   090   000    Old_age   Always       -       36
196 Reallocated_Event_Count 0x0032   189   189   000    Old_age   Always       -       11
197 Current_Pending_Sector  0x0012   200   198   000    Old_age   Always       -       3
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 392 (device log contains only the most recent five errors)
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

Error 392 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:37.428  READ DMA
  ec 00 00 00 00 00 00 00      00:17:37.428  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:37.428  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:37.427  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:33.566  READ DMA

Error 391 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:33.566  READ DMA
  ec 00 00 00 00 00 00 00      00:17:33.566  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:33.566  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:33.565  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:29.685  READ DMA

Error 390 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:29.685  READ DMA
  ec 00 00 00 00 00 00 00      00:17:29.684  IDENTIFY DEVICE
  ef 10 03 00 00 00 00 00      00:17:29.684  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 00 00      00:17:29.683  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:29.683  SET FEATURES [Set transfer mode]

Error 389 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:24.146  READ DMA
  ec 00 00 00 00 00 00 00      00:17:24.146  IDENTIFY DEVICE
  ef 03 44 00 00 00 00 00      00:17:24.146  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:24.145  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:20.286  READ DMA

Error 388 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:20.286  READ DMA
  ec 00 00 00 00 00 00 00      00:17:20.285  IDENTIFY DEVICE
  ef 03 44 00 00 00 00 00      00:17:20.285  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:20.284  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:16.426  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1692         7333886

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

### Post by caljohnsmith on 2008-12-10
> ```
SMART Error Log Version: 1
[COLOR="Red"]ATA Error Count: 392[/COLOR] (device log contains only the most recent five errors)
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

Error 392 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:37.428  READ DMA
  ec 00 00 00 00 00 00 00      00:17:37.428  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:37.428  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:37.427  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:33.566  READ DMA

Error 391 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:33.566  READ DMA
  ec 00 00 00 00 00 00 00      00:17:33.566  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:33.566  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:33.565  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:29.685  READ DMA

Error 390 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:29.685  READ DMA
  ec 00 00 00 00 00 00 00      00:17:29.684  IDENTIFY DEVICE
  ef 10 03 00 00 00 00 00      00:17:29.684  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 00 00      00:17:29.683  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:17:29.683  SET FEATURES [Set transfer mode]

Error 389 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:24.146  READ DMA
  ec 00 00 00 00 00 00 00      00:17:24.146  IDENTIFY DEVICE
  ef 03 44 00 00 00 00 00      00:17:24.146  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:24.145  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:20.286  READ DMA

Error 388 occurred at disk power-on lifetime: 1641 hours (68 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 00 fe e7 6f e0  Error: AMNF at LBA = 0x006fe7fe = 7333886

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 f7 e7 6f 00 00      00:17:20.286  READ DMA
  ec 00 00 00 00 00 00 00      00:17:20.285  IDENTIFY DEVICE
  ef 03 44 00 00 00 00 00      00:17:20.285  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 00 00      00:17:20.284  IDENTIFY DEVICE
  c8 00 08 f7 e7 6f 00 00      00:17:16.426  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1692         7333886

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
Unfortunately, your HDD test reported 392 errors, and also the HDD was not able to even complete its own internal self-test; looks like your HDD did not survive being dropped. I suppose there is a remote possibility the HDD is still OK, but the problem is that a cable connection is loose or something like that. Either way, it looks like you will have to open up the computer if you want to do anything about it. Sorry I can't be of any further help, good luck though. :|

---

### Post by turkdavid on 2008-12-10
I saw the errors hopefuly it just the hdd and nothing else. I would hate to have to put money into something that I didn't even pay for. :lolflag:

---

### Post by donkyhotay on 2008-12-10
I'd try booting to a liveCD to confirm the problem is only with the HD and if that works try salvaging what you can.

---

### Post by turkdavid on 2008-12-12
donkyhotay .. what should I do. Should I run the same code as before? I took the computer apart and the hard drive is a sata and there were no loose wires or anything out of place. I will prob. just use it till it fails but I would like to make sure that its just the HDD

---

### Post by turkdavid on 2008-12-15
I have it resolved. I contacted HP costumer support.. The computer is still under warrenty and they are sending me a new hdd. lol I still have yet to put money into the computer:lolflag:

---

