---
title: "Crashing HD"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by stktek on 2010-07-07
Just got a disk is falling.
 This is a new Seagate Barracuda SATA 1TB 7200rpm 32mb cache
Been running for about a month learning Ubuntu 10.04 (new Bee) how can i back up the install so as not to loose all my setting and programes. i have a external HD with space and a extra internal drive formatted NTFS which has saved stuff from my win XP days.

---

### Post by k3lt01 on 2010-07-07
If you have the space your backup can be as simple as copying your files over to your other hard drive, whatever one you choose to use. This is how I do it.

One question though, how do you know your hdd is failing? It can happen I had a Western Digital that failed when it was brand new.

---

### Post by stktek on 2010-07-07
Icon appeared on desk top top right side.
1.0 TB Hard Disk - ATA ST31000528AS Disk Failure is Imminent

Click on icon goes to Disk Utility
Smart Status - Disk Failure Imminent
Smart Data - item 5 Reallocation Sector Count - Failing

I am so new to Linux and it took me a while to set every thing up all my files are saved on an external drive. Its just all software and email accounts I dont want to loose. Really don't want to have to reload everything on a new drive like i had to do with Win XP.
I hoped that Ubuntu would have an easy way to image the whole drive and restore it on a new one.

Thank for the help

---

### Post by k3lt01 on 2010-07-07
That icon can give false positive alarms, your disk might actually be fine.

---

### Post by philinux on 2010-07-07
stktek,

Install gsmartcontrol and compare the results with Disk Utility (palimpsest).

---

### Post by warfacegod on 2010-07-07
> **philinux said:**
> stktek,

Install gsmartcontrol and compare the results with Disk Utility (palimpsest).

Helps if you post the command:biggrin:

```
sudo apt-get install gsmartcontrol
```

---

### Post by philinux on 2010-07-07
Click this. Even easier. I missed the bit in post #3 about being so new to linux.

[gsmartcontrol]("apt:gsmartcontrol") :mrgreen:

---

### Post by stktek on 2010-07-07
I compared Disk Utility and gsmart and get the same thing.

MART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   115   099   006     Pre-fail Always       -       95416476
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       16
  5 Reallocated_Sector_Ct   0x0033   030   030   036    Pre-fail  Always   FAILING_NOW 2887
  7 Seek_Error_Rate         0x000f   066   060   030    Pre-fail  Always       -       4111205
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       538
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       8
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       13
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   067   059   045    Old_age   Always       -       33 (Lifetime Min/Max 26/33)
194 Temperature_Celsius     0x0022   033   041   000    Old_age   Always       -       33 (0 25 0 0)
195 Hardware_ECC_Recovered  0x001a   046   024   000    Old_age   Always       -       95416476
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       254236294119982
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       464640965
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       3442670257

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed: unknown failure    90%       538         -
# 2  Short offline       Completed: unknown failure    90%       538         -
# 3  Short offline       Completed: unknown failure    90%       536         -

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

---

### Post by philinux on 2010-07-07
Time to back up and get new disk.

---

### Post by k3lt01 on 2010-07-07
I'm surprised the BIOS hasn't alerted the OP to the problem. Maybe it isn't set to SMART control. As it is a SATA drive you could get another one preferably the same size or bigger, don't go smaller, and setup a RAID 1 profile and that would write your data over to the new disk. Doing this would save you setting up Ubuntu all over again as everything is copied over.

---

