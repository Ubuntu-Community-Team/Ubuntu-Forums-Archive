---
title: "Recent Data got deleted?!"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-06-15
I found out a couple of directories became missing a while ago, and now I'm missing some more, all of the folders that have disappeared I opened not to long ago... It's very strange... I ran testdisk and photorec and got a whole bunch of recovered data, but all of it is in this kind of format:

```
f710676496.asf  f720900112.asf  f735842320.asf  f747325272.asf  f757338132.mpg  f758937196.mpg  f759722956.mpg  f760327624.mpg
f711200784.asf  f720900160.mpg  f735859296.mpg  f747331256.asf  f757600272.mpg  f758951612.mpg  f759737928.mpg  f760344816.mpg
f712405065.mpg  f721424400.asf  f736366608.asf  f747376656.asf  f757862416.mpg  f758971632.mpg  f759766760.mpg  f760374592.mpg
f713035792.asf  f721424448.mpg  f736380810.mpg  f747464520.asf  f758124576.mpg  f758986704.mpg  f759790976.mpg  f760394056.mpg
f713179173.mpg  f721743900.mpg  f737153040.asf  f747560872.asf  f758324488.mpg  f759001852.mpg  f759800440.mpg  f760447840.mpg
```

Most of the stuff was in .avi and DVD file format (VOB IFO etc). Is there any log I can check to see what happened to my files?! How is this possible in the first place?

---

### Post by tomszyszko on 2009-06-15
> **dvdhaar said:**
> I found out a couple of directories became missing a while ago, and now I'm missing some more, all of the folders that have disappeared I opened not to long ago... It's very strange... I ran testdisk and photorec and got a whole bunch of recovered data, but all of it is in this kind of format:

```
f710676496.asf  f720900112.asf  f735842320.asf  f747325272.asf  f757338132.mpg  f758937196.mpg  f759722956.mpg  f760327624.mpg
f711200784.asf  f720900160.mpg  f735859296.mpg  f747331256.asf  f757600272.mpg  f758951612.mpg  f759737928.mpg  f760344816.mpg
f712405065.mpg  f721424400.asf  f736366608.asf  f747376656.asf  f757862416.mpg  f758971632.mpg  f759766760.mpg  f760374592.mpg
f713035792.asf  f721424448.mpg  f736380810.mpg  f747464520.asf  f758124576.mpg  f758986704.mpg  f759790976.mpg  f760394056.mpg
f713179173.mpg  f721743900.mpg  f737153040.asf  f747560872.asf  f758324488.mpg  f759001852.mpg  f759800440.mpg  f760447840.mpg
```

Most of the stuff was in .avi and DVD file format (VOB IFO etc). Is there any log I can check to see what happened to my files?! How is this possible in the first place?

Are you using EXT4, as files are lost if interupted while being written to, mainly because the files arnt filled with 0s like EXT3

---

### Post by dvdhaar on 2009-06-15
> **tomszyszko said:**
> Are you using EXT4, as files are lost if interupted while being written to, mainly because the files arnt filled with 0s like EXT3

Hmm I don't really know actually the files are on my server which is running 9.04 but afaik the attached disks are still ext3.. I use the files via Samba basicly. I'll check the filesystem.

How would I go about checking the filesystem? I thought fdisk -l would show me. And I can't run gparted because I'm 'sshing' into the machine.

---

### Post by Azrael3000 on 2009-06-15
sorry can't help you on the vanishing file thing, but for a list of partitions you can also try
```
sudo parted -l
```

---

### Post by dvdhaar on 2009-06-15
> **Azrael3000 said:**
> sorry can't help you on the vanishing file thing, but for a list of partitions you can also try
```
sudo parted -l
```

Ah thanks. I've got all ext3 partitions.

---

### Post by dvdhaar on 2009-06-17
Anyone has any idea what might have caused this? Or how I can get my data back in a right format?

---

### Post by Martje_001 on 2009-06-17
You said you're running a server. Is it connected to the Internet? Who has access to it? Is it secure? Have you updated it?

---

### Post by dvdhaar on 2009-06-17
> **Martje_001 said:**
> You said you're running a server. Is it connected to the Internet? Who has access to it? Is it secure? Have you updated it?

Yes it is, and now that you mention it, I recently ran:

```
sudo apt-get update
sudo apt-get upgrade
```

I'm the only one that has access to it, it has some open ports for bittorent and port 22 for ssh. I haven't done anything concerning extra security, I've got a pretty heavy password but thats about it.

---

### Post by Martje_001 on 2009-06-17
Check if you didn't accidentally ran a command lately which erased the files:
```
cat .bash_history
```

---

### Post by dvdhaar on 2009-06-17
> **Martje_001 said:**
> Check if you didn't accidentally ran a command lately which erased the files:
```
cat .bash_history
```

Not that I can see, how far does it go back? I can only see very recent commands from today and yesterday pretty much. The strange thing is that the files missing are within a folder which has like 400+ directories, some of them disappeared. And the ones that disappeared are directories which I opened quite recently.

---

### Post by dvdhaar on 2009-06-25
Does anyone have an idea? Can it have something to do with file permissions? It's realy bugging me.. will this happen again? How did it happen? How can I check?

---

### Post by niteshifter on 2009-06-25
Hi,

Check the log files - in /var/log folder. Also when reviewing look for items (errors) pertaining to the disk, power failure / restart times, etc.

Check the hard disk, if it's SMART-capable:
```
sudo smartctl -a /dev/sda
```
Replace /dev/sda with the device name of the offending drive. You may need to install smartmontools:
```
sudo apt-get install smartmontools
```

---

### Post by dvdhaar on 2009-06-25
Thanks for your reply, I've already done a quicktest and it seems OK. I could try and run the original Samsung tool, but I don't think the disk is faulty. 

```
daniel@server:~$ sudo smartctl -l selftest /dev/sdd
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       423         -
# 2  Short offline       Completed without error       00%         0         -


```

And which logs are worth checking out? I guess the syslog?

---

### Post by niteshifter on 2009-06-25
Hi,

kernel logs - kern.log, kern.log.0 and the archived ones (ending in .gz).
Mostly look for error / status messages, made easy with grep since these lines will have the string "drive_cmd" in them:

```
grep drive_cmd /var/log/kern.log
grep drive_cmd /var/log/kern.log.0

```
```
gzip -dc /var/log/kern.log.1.gz | grep drive_cmd
gzip -dc /var/log/kern.log.2.gz | grep drive_cmd

```

```
ls -al /var/log/kern*
```
to see the dates, go back to when the drive was working.

By "quicktest" I take it you invoked smartctl like this?
```
sudo smartctl -t short /dev/sdd
```

Try the long test. This can take awhile. How long? Use:
```
sudo smartctl -c /dev/sdd
```
and look at the end of the output. Then do:
```
sudo smartctl -t long /dev/sdd
```
Wait for the time given above (plus a few minutes) and do:
```
sudo smartctl -t conveyance /dev/sdd
```
wait, then do
```
sudo smartctl -a /dev/sdd
```

Even though the drive shows a small amount of hours, it won't be the first to die young ;)

Last, with it still unmounted do a fsck. First see what e2fsck would do if you let it run interactive:
```
sudo e2fsck -fn /dev/sdd
```
next a preening:
```
sudo e2fsck -p /dev/sdd
```
or just let it run (be prepared to work with it for awhile):
```
sudo e2fsck /dev/sdd
```

The idea is let's make sure (as best we can) that the hardware really is good before turning fsck loose on it. Flaky hardware + fsck = FUBAR, big time.

Also, just to save typing sudo over and over if you like, give yourself a root session to work in:
```
sudo -i
```
Note that you'll be user "root", not "daniel". Should you or the system create any files they will be in /root, not /home/daniel.

---

### Post by dvdhaar on 2009-06-29
Thanks alot for your reply. Here's what came up:

Apparently no errors in the logs:

```
daniel@server:~$ grep drive_cmd /var/log/kern.log
daniel@server:~$ grep drive_cmd /var/log/kern.log.0
daniel@server:~$ gzip -dc /var/log/kern.log.1.gz | grep drive_cmd
daniel@server:~$ gzip -dc /var/log/kern.log.2.gz | grep drive_cmd
daniel@server:~$ ls -al /var/log/kern*
-rw-r----- 1 syslog adm 136271 2009-06-29 21:41 /var/log/kern.log
-rw-r----- 1 syslog adm  10298 2009-06-28 22:57 /var/log/kern.log.0
-rw-r----- 1 syslog adm  13011 2009-06-22 01:04 /var/log/kern.log.1.gz
-rw-r----- 1 syslog adm    619 2009-06-14 09:06 /var/log/kern.log.2.gz
-rw-r----- 1 syslog adm    365 2009-06-07 11:25 /var/log/kern.log.3.gz
daniel@server:~$ gzip -dc /var/log/kern.log.3.gz | grep drive_cmd
daniel@server:~$

```

And no errors concerning the driver either, still have to do the samsung estool test though.
```
daniel@server:~$ sudo smartctl -a /dev/sdd
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD103UJ
Serial Number:    S13PJ1MS201027
Firmware Version: 1AA01113
User Capacity:    1,000,204,886,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Mon Jun 29 21:37:04 2009 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection: 		 (11825) seconds.
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
recommended polling time: 	 ( 198) minutes.
Conveyance self-test routine
recommended polling time: 	 (  21) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   076   076   011    Pre-fail  Always       -       8080
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       55
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       10002
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       519
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       55
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   073   073   000    Old_age   Always       -       27 (Lifetime Min/Max 15/27)
194 Temperature_Celsius     0x0022   073   071   000    Old_age   Always       -       27 (Lifetime Min/Max 15/29)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       4205903
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%       519         -
# 2  Extended offline    Completed without error       00%       518         -
# 3  Short offline       Completed without error       00%       423         -
# 4  Short offline       Completed without error       00%         0         -

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

And this is the output of e2fsck:

```
daniel@server:~$ sudo e2fsck -fn /dev/sdd
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdd

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

daniel@server:~$ 

```

---

### Post by dvdhaar on 2009-07-01
:) Just a small bump if nobody minds

---

### Post by dvdhaar on 2009-07-31
Strange thing is I ran fsck and got this message:

```
daniel@server:~$ sudo fsck -p /dev/sdc
[sudo] password for daniel: 
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc
/dev/sdc: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

Already done some searches, don't know what it means.. Haven't gotten around to diagnosing the harddrive with the Samsung tool yet o_O

---

