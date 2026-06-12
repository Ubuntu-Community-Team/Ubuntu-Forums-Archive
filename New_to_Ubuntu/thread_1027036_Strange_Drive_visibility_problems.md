---
title: "Strange Drive visibility problems"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-12-31
my neighbor brought over a Maxtor OneTouch 4 Mini external hard drive. her son loaded it with a bunch of pics of him and his friends stationed out in iraq, but somehow the mini-usb jack broke off and is rattling inside. i disassembled the unit (no screws or nothing, i used a credit card to pop the seams lol) and took the hard drive off the SATA to USB board.

i figured i'd throw the Maxtor drive in my laptop, boot from a live CD, and copy the files to a spare thumbdrive. sounds easy right?

well i'm posting a thread here, so you can assume it wasn't easy.

i dual boot, so i have Hardy on one partition, and XP on the other. neither OS could see the drive, but GSmartControl can.

```
ryan@ryan-desktop:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00060268

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda2            4570       19697   121515660   83  Linux
/dev/sda3           19698       20023     2618595   82  Linux swap / Solaris

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x879b879b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       20023   160834716   83  Linux
```
notice how there isn't a /dev/sdb listed? look at the mount point listed on the pic below

[IMG]http://dl.getdropbox.com/u/285667/Pictures/GSmartControl.png[/IMG]

I ran the GSmartControl extended test and it came back with no errors, so according to GSmartControl the drive is working perfectly, but tell that to ubuntu or XP.
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST9250827AS
Serial Number:    5RG3PPXM
Firmware Version: 3.CTC
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Dec 31 17:13:07 2008 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
Offline data collection
capabilities: 			 (0x53) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.
SCT capabilities: 	       (0x0001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   099   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       121
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   061   060   030    Pre-fail  Always       -       4296410017
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       39
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       84
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   094   094   000    Old_age   Always       -       6
190 Airflow_Temperature_Cel 0x0022   076   049   045    Old_age   Always       -       24 (Lifetime Min/Max 10/51)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       5
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       76
193 Load_Cycle_Count        0x0022   100   100   000    Old_age   Always       -       861
194 Temperature_Celsius     0x001a   024   051   000    Old_age   Always       -       24 (0 10 0 0)
195 Hardware_ECC_Recovered  0x0012   074   060   000    Old_age   Always       -       139533293
197 Current_Pending_Sector  0x0010   100   100   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x003e   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 TA_Increase_Count       0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        39         -
# 2  Extended offline    Completed without error       00%        36         -

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

according to GSmartControl, the drive is fine, according to Ubuntu and XP, the drive doesn't exist. how can i get the pics off the drive?

---

### Post by Michael.Godawski on 2008-12-31
hi,

have you tried the applications PhotoRec and TestDisk?


[LIST]
[*][http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[*][http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[/LIST]

---

### Post by mikewhatever on 2008-12-31
What is the mount point, I don't see any. What version of Ubuntu do you use? Did you try manually mounting the drive?

---

### Post by Sonic Reducer on 2008-12-31
> **mikewhatever said:**
> What is the mount point, I don't see any. What version of Ubuntu do you use? Did you try manually mounting the drive?

i'm running Hardy 32-Bit, and it says the mount point in the top left of the picture (/dev/sdb)

and manually mounting it produces this:
```
ryan@ryan-desktop:/media$ sudo mount /dev/sdb1 /media/disk
[sudo] password for ryan: 
mount: special device /dev/sdb1 does not exist
```

---

### Post by handydan918 on 2008-12-31
The screenie you posted shows /dev/sdb, not sdb1. Have you tried just mounting /dev/sdb?

---

### Post by mikewhatever on 2008-12-31
I don't know. Hopefully photorec will save the day. And by the way, /media/disk is a mount point, /dev/sdb is a device name.

---

### Post by Sonic Reducer on 2008-12-31
> **handydan918 said:**
> The screenie you posted shows /dev/sdb, not sdb1. Have you tried just mounting /dev/sdb?

the device is /dev/sdb, the partition i'd want to mount is /dev/sdb1 (the first partition on that drive). i tried mounting /dev/sdb hoping it was a trick i didn't know, and this got returned:

```
**ryan@ryan-desktop:~$** sudo mount /dev/sdb /media/disk
[sudo] password for ryan: 
mount: you must specify the filesystem type
**ryan@ryan-desktop:~$** sudo mount -t ntfs /dev/sdb /media/disk
Error reading bootsector: Input/output error
Failed to mount '/dev/sdb': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
```

---

