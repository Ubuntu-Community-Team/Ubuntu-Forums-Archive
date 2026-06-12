---
title: "hdd temperature 67C high?"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by duruttye on 2010-01-26
Hey there!

I have a Dell Vostro A680 running ubuntu 9.10, and I just noticed that it became a little hot, so I run hddtemp and it shows 67Celsius. As I can remember I never saw it climb higher that 55Celsius.

Should I be concerned?

I don't do anything special, just browsing, and I already turned off compiz.

How is your temperature??

---

### Post by baltadt on 2010-01-26
My laptop runs at 48 degrees  with internet, OOo, and hulu desktop running at the same time. check that your fan is not clogged up and check fan setting in the BIOS settings.

---

### Post by SuperSonic4 on 2010-01-26
It is on the hot side, perhaps your fan needs a clean. How often do you power your laptop down?

---

### Post by duruttye on 2010-01-26
Thanx for the replies!

The cpu temperature is 51C so, the fan must work okay, right?
I power it off often, I mean twice a day, in case I'm not using it.
uptime
 00:18:40 up  3:31,  2 users,  load average: 0.01, 0.06, 0.03

Right now it is about 23C in the room, and the hdd temp went down to 64, because I lifted the front end of the laptop, putting a remote under it :)

Question: in case the temp is even higher, will the laptop shut down for safety reasons? or will it go on until it is damaged?

---

### Post by J V on 2010-01-26
I attach a plastic pen-casing to my hoover and suck the dust out of my fan every now and then, lowers temp by about 15 C every time and makes lots less noise :P

---

### Post by SuperSonic4 on 2010-01-26
Depends on your BIOS. My BIOS shuts down at around 85C I think but running it hot will reduce its life

---

### Post by Sir Jasper on 2010-01-26
Hi,

If you have important data and/or programs that you would hate to lose then seriously consider cloning or imaging or at least making a backup asap.

My regards

---

### Post by duruttye on 2010-01-26
Well, I shut down the laptop for a few minutes. Now is at 51C... I going to have to monitor the temperature more often, so I can see that this was a one time only case, or it is operating at higher temperatures.
Do you know any application that I might put in the notification area or on a panel so I can monitor the temperature at all times?

There is nothing I could find in the BIOS regarding the temperatures...

I already made some backup of the important stuff, but still...
Tomorrow I will open it up and make a fan clean, although it is't a year old, and I've careful with it, always using it on flat surfaces and such...

Thank you guys!
Take care

---

### Post by skymera on 2010-01-26
67c seems awfully hot for a hard drive.

I've never seen my desktop HDD go over 55c and that was with 3 hard drives packed next to each other with no fan and 3 defrags running.
The drive that got to 55c was a 10,000K Raptor.

They normally sit at 22-25c.

HDDtemp seems pretty accurate on my machine
```

scott@scott-desktop:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD1500ADFD-00NLR5: 31 C (10,000 RPM Raptor)
scott@scott-desktop:~$ sudo hddtemp /dev/sdb
/dev/sdb: SAMSUNG HD103SI: 23 C (5,400RPM Samsung F2)
scott@scott-desktop:~$ sudo hddtemp /dev/sdc
/dev/sdc: WDC WD1600JS-75NCB3: 33 C (7,200RPM old Caviar drive)

```

Is the HDD light on constant on your laptop?
If the CPU is cooled, something may be causing a hot HDD, maybe the graphics chip?

---

### Post by duruttye on 2010-01-26
Well, it's around 63C again. 
The light is barely blinking, nothing out of the ordinary.
I don't know about the graphics drive, but it isn't used excessively at all.
Although I had some troubles with the sound card for the past few days... Haven't had the time to look into it though... Can that be a reason for hdd temperature rising?

---

### Post by duruttye on 2010-01-26
domelaci@kucko:~$ sudo hddtemp /dev/sda
/dev/sda: WDC WD1200BEVT-75ZCT2: 65°C


domelaci@kucko:~$ uptime
 02:13:25 up 58 min,  3 users,  load average: 0.03, 0.07, 0.08


the load average is nowhere at all and it is a laptop! I guess laptops operate on higher temperatures, due to restricted space...

---

### Post by duruttye on 2010-01-28
Is there a diagnostic tool for hard drives?
And maybe someone who can interpret the results?

I run smartmontools, but there is nothing written in red:P, so as far as I can tell, nothing is wrong, but hey:

$ sudo hddtemp /dev/sda
/dev/sda: WDC WD1200BEVT-75ZCT2: 60°C

---

### Post by duruttye on 2010-01-28
Just for the fun of it, and in case someone is wondering

sudo smartctl -s on -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1200BEVT-75ZCT2
Serial Number:    WD-WXE908PH4846
Firmware Version: 11.01A11
User Capacity:    120,034,123,776 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Jan 28 12:38:35 2010 EET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (4800) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  59) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   159   159   021    Pre-fail  Always       -       1033
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       906
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2900
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       897
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       67
193 Load_Cycle_Count        0x0032   198   198   000    Old_age   Always       -       6065
194 Temperature_Celsius     0x0022   082   072   000    Old_age   Always       -       61
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   097   097   000    Old_age   Always       -       2886
241 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       2138446911
242 Unknown_Attribute       0x0032   200   200   000    Old_age   Always       -       2186458488

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%      2880         -
# 2  Short offline       Completed without error       00%      2880         -
# 3  Short offline       Interrupted (host reset)      80%       360         -
# 4  Short offline       Completed without error       00%       101         -
# 5  Short offline       Completed without error       00%         0         -

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


I'm the best:guitar:

---

### Post by skymera on 2010-01-28
Western Digital says this about the drive

```
 Temperature (Metric)
	Operating	-0° C to 60° C
	Non-operating	-40° C to 65° C

```

So they suggest 60c being max, which means something seems wrong with yours. But it's figuring out what :)

Personal note: backup :)

---

### Post by duruttye on 2010-01-28
where did you get that?

---

### Post by skymera on 2010-01-28
[http://www.wdc.com/en/products/products.asp?driveid=514](http://www.wdc.com/en/products/products.asp?driveid=514)

Under the "Specs" tab further down.

---

### Post by cascade9 on 2010-01-28
> **SuperSonic4 said:**
> Depends on your BIOS. My BIOS shuts down at around 85C I think but running it hot will reduce its life

AFAIK, BIOS will only shutdown if your CPU temp hits 85C, it doesnt care about HDD temps. 

From the specs that skymera posted, I would be doing a through check on that machine. Maybe think about taking the HDD cover off, and check that it is not full of dust? Or you could get a 'laptop cooler', some laptops will always have hot drives, it really depends on the layout and how much, if any, ventilation there is for the HDD.

---

### Post by duruttye on 2010-01-31
Hey there!

Thank you all for your replies.
I posted this problem on the Dell forums, and there were two guys, who agreed, that I will have to start backing up data as of yesterday. 
Right now I'm writing dvd-s like mad, hoping that it will last until I'm finished. The good news is, that the laptop is still in warranty, but I will have to send it in another town and wait for a few weeks. It is sad that the drive will fail after a year of use.
When I finish backing up my data, I will format the drive and install an XP on it (for the first time since 2006) just to see the temperatures using windows.

Take care, and thank you for your support!
Long live the ubuntu forums!

---

### Post by nhasian on 2010-01-31
i have two 7200rpm 2.5" hard disks in my 17" HP laptop.  I use the Palimpsest Disk Utility in System->Administration to check the status of my drives (installed by default in 9.10 karmic)
my primary hard disk temp is 53C but since your WD Scorpio Blue hard disk is only 5400rpm it should run even cooler.

I dont see why you have to send your laptop anywhere.  One of my drives failed after only 2 months and HP mailed me an advanced replacement hard disk (they had to hold onto my credit card number till i returned the defective drive) but then i just replaced the drive myself.  two screws at the bottom of the case.  easy as cake.  Hopefully you never have to replace the fan in your laptop.  that requires some major surgery.

PS maybe you can pay the difference and get a solid state drive that would be worth the upgrade :)

> **duruttye said:**
> The good news is, that the laptop is still in warranty, but I will have to send it in another town and wait for a few weeks. It is sad that the drive will fail after a year of use.

---

### Post by duruttye on 2010-01-31
In the following days I will contact the local representatives of DELL to see what I have to do, maybe they will ship me a replacement drive too, I don't know yet.
Anyway, the drive is performing as normal, no problems yet... Although it doesn't hurt to be prepared, right? I wonder what happens to people who don't care, or don't know how to check stuff on their machines...

Right now, the drive is in heavy usage, due to dvd writing, but the temp is not rising above 56C.
And I'm gonna take the laptop apart tomorrow, to see what's inside, maybe there is some dusk piled up in there, or something...

Anyway, I'm gonna have to wait it out.
Thank you guys!

---

