---
title: "Hard disk clicks"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by hmo on 2009-03-20
I have Ubuntu 8.04 with Gnome 2.22.3 in a laptop Sony Vaio VGN-SZ770FN. After I installed Ubuntu, I realized that every 3 to 5 seconds there is a click that seems come from my hard disk. I was searching in internet and I'm a bit worried because this maybe decreasing the life of my hard disk. I tried a workaround shown in this link ([Ubuntu tweaks]("(http://wiki.msiwind.net/index.php/Ubuntu_8.04_Tweaks#Fixing_Suspend_.26_Hard_Drive_Clicking")) but even after I did it, still is happening. 

Is there an effective workaround? By the way I have also Windows Vista(no clicking if I'm using it)

---

### Post by cariboo on 2009-03-20
Have a look at this [thread=331418]thread[/thread], there seems to be  a solution to your problem.

Jim

---

### Post by HermanAB on 2009-03-20
You are hearing the system logs being written to disk.

$ sudo service syslog stop

or something like that.

Cheers,

Herman

---

### Post by 123456789123456789123456 on 2009-03-20
try a hard drive test from live cd.  usually hard drive clicks indicate disk failure, or possible failure.  If disk comes back damaged or not working properly.  Recover all data you need, and replace drive.

---

### Post by hmo on 2009-03-21
I did this:

hmo@ares:~$ sudo smartctl --attributes --log=selftest /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       66478
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       52756480
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       685
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3134
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       2109
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       665
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       49
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       2319
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       39 (Lifetime Min/Max 21/51)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       23
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       450035712
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       25458
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       1533217148407
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2109         -
# 2  Extended offline    Aborted by host               20%      2109         -



Also this:

 sudo smartctl -l error /dev/sda
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
No Errors Logged




Does this mean that my hard disk is ok?

---

