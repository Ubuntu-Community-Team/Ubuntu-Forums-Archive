---
title: "ata1: failed due to HW bug"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by BugBuster on 2009-06-15
Hello I have three linuxes running on my computer.
Ubuntu Jaunty 64-bit
Ubuntu Hardy 32-bit
Centos 5.3 Final 32-bit

The problem here is that now I am getting an error:

ata1: failed due to HW bug

I get this error in Jaunty and Centos and not in Hardy.I get this error while booting from a 32-bit Jaunty livecd as well.
Any ideas??

I am worried as this is a 250GB Seagate SATA 2 disk and I have quite a lot of stuff on it.
Does this error essentially mean disk (hardware) failure.
I there a tool that can scan and report a failing hard disk?

Thanks.

---

### Post by tomszyszko on 2009-06-15
No, it is a common problem with Jaunty. I get the exact same thing. Im not sure exactly what it is but its probably some sort of driver timeout?

Your drive is fine, don't worry.

---

### Post by BugBuster on 2009-06-16
Thank you for your concern tomszyszko.

Out of curiosity I downloaded the Fedora 11 x86_64 livecd as well.
I get this error on it as well.So that increases my concern even more.
Is this an issue with the newer linux kernels itself..(ofcourse specific to my set of hardware) is what I am starting to wonder.

And this rules out the assumption that this is Jaunty-specific issue.

And what actually do ata1:, ata2:, ata3: and ata4: stand for.I get this listed in my logfiles.Would like to dig deep in order to trace the issue.

Would this in one way be related to a BIOS update?

Thanks once again.

---

### Post by Iowan on 2009-06-16
> **tomszyszko said:**
>  I get the exact same thing.Ditto here - Dual-boot from SATA drive.  Machine works fine - just a boot-up annoyance (so far).

---

### Post by mgranet on 2009-06-16
If you are worried about the state of the drive, make sure SMART is enabled in the bios, then ```
sudo apt-get install smartmontools
```

It's a command line tool, so ```
sudo smartctl -*options* /dev/sd*x*
```

with x being the drive you want to view the report on.

---

### Post by BugBuster on 2009-06-17
> **mgranet said:**
> If you are worried about the state of the drive, make sure SMART is enabled in the bios, then ```
sudo apt-get install smartmontools
```

It's a command line tool, so ```
sudo smartctl -*options* /dev/sd*x*
```

with x being the drive you want to view the report on.

Thank you mgranet, following is the output that I get when I run this command;

```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST3250310SV
Serial Number:    9RY1YE6L
Firmware Version: 3.ACC
User Capacity:    250,059,350,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jun 17 09:40:44 2009 IST
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
data collection: 		 ( 430) seconds.
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
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       79262795
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2195
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   079   060   030    Pre-fail  Always       -       84173423
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2642
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2167
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   061   054   045    Old_age   Always       -       656408615
194 Temperature_Celsius     0x0022   039   046   000    Old_age   Always       -       39 (Lifetime Min/Max 0/22)
195 Hardware_ECC_Recovered  0x001a   078   063   000    Old_age   Always       -       65532917
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2608         -
# 2  Short offline       Completed without error       00%       313         -

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

Now what do you guys make of it??

---

### Post by mgranet on 2009-06-17
Your drive is perfectly fine. Nothing is near threshold, and you only have 2600 hours on it. It has a long life ahead of it.

---

