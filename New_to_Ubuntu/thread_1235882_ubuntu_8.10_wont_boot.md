---
title: "ubuntu 8.10 wont boot"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by homerwookey on 2009-08-09
Hi all, after using ubuntu pretty happily for a year now, Ubuntu wont boot, Gets to grub loading stage 2, then nothing for ages, then the grub command line. not sure what to do from here, have tried using an old 7.10 install disk but after loading the kernel, the ubuntu start page with scroling orange bar comes up and it wont do anything, then I get a number of recurring error messages.
these are: (gotta write them as cant take screen shot)

[206.165.756] ata1.00: exception emask 0x0 SAct 0x0 Serr 0x0 action 0x0

[different numbers, same message] ata1.00: (BMDMA stat 0x25)

[ditto] ata1.00: cmd c8/00:08:55:08:a2/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in

and occasionally:
[ditto] Buffer I/O error on device sda 3, logical block 0

not sure how to get any more info, please help!!
Thanks loads  in advance

---

### Post by jauntyjackalope on 2009-08-09
Have you tried reinstalling GRUB? Thats what i would do first.

---

### Post by homerwookey on 2009-08-09
Thanks for getting back to me so quickly.
No I haven't, and how do I do that?

---

### Post by jauntyjackalope on 2009-08-09
Here are some pretty easy instrutions:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by homerwookey on 2009-08-09
Yeah I found that earlier but I cant get to the desktop! 
Is there a way round this?

---

### Post by jauntyjackalope on 2009-08-09
Did you boot from the CD?

---

### Post by homerwookey on 2009-08-09
Just tried find /boot/grub/stage1 at the grub command line and says error 15 file not found

---

### Post by homerwookey on 2009-08-09
wont boot from cd (see original thread)
starting to wonder if hard drive has died....

---

### Post by Yvan300 on 2009-08-09
Hard drive failure would not affect your ability to boot from a live cd. Try booting from a more recent live cd and see what is the outcome. Oh and are you getting any hd activity when you turn on your computer?

---

### Post by homerwookey on 2009-08-09
Have just tried with a 8.10 install disk downloaded off ubuntu.com
I'm getting the same thing when I try to install, just the ubuntu download screen with the moving orange bar.
I think theres action from the harddrive but cant be 100% sure

---

### Post by homerwookey on 2009-08-09
Managed to get the 8.10 disk to work, so followed the instruction from the link jaunty jackalope gave me, and after typing in 
sudo grub,
then find /boot/grub/stage1 
All it returned was Error 15: File not found

Tried find /boot 
and still the same
So where do I go next?
Thanks for your help so far guys

EDIT
In Grub typed 
root (hd0.0)
setup (hd0)
and got the reply
Error 17: Cannot mount selected partition

Is that a hard drive issue?

---

### Post by Yvan300 on 2009-08-10
There are some boot options that are available when using the live cd. Try playing around with them, it worked for me.

---

### Post by mikechant on 2009-08-10
You might have a failing hard drive. Is grub on a different disc to Ubuntu? (the fact that grub is getting somehwere indicates that the disc it is on is at least partly working).

Also, when running from the live CD could you post the output of the terminal command
```
sudo fdisk -l 
```

(that's lower case L, not number 1)

---

### Post by homerwookey on 2009-08-10
I only have 1 internal hard drive, not partitioned, so grub must be on the same drive as ubuntu
With the installer disk I typed sudo fsdisk -l and got the reply
command not found

I also cant get ubuntu to recognise my hard drive running from the live cd, is this normal? (no icon in 'places')

---

### Post by mikechant on 2009-08-10
> With the installer disk I typed sudo fsdisk -l and got the reply
command not found

It's fdisk, not fsdisk.

---

### Post by homerwookey on 2009-08-10
Sorry, really tired still after being up most of the night trying to find solutions!

heres the results, 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9         661     5245222+   b  W95 FAT32
/dev/sda3   *         662       59573   473210640   83  Linux
/dev/sda4           59574       60801     9863910    5  Extended
/dev/sda5           59574       60801     9863878+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Linux000 on 2009-08-10
Maybe the partition went bad?

---

### Post by homerwookey on 2009-08-10
How do I find that out?

---

### Post by Linux000 on 2009-08-10
Do you have any other OSes(windows, other linux) on your computer? If you do try to boot into that.

---

### Post by homerwookey on 2009-08-10
no just ubuntu

---

### Post by Linux000 on 2009-08-10
When you boot into the live cd, can you store a file to the HDD?

---

### Post by LarsW_Tierp on 2009-08-10
Looks like a hardware problem. Do you have a spare drive that you can try?

---

### Post by homerwookey on 2009-08-10
Cant find an icon for it so dont think so

---

### Post by homerwookey on 2009-08-10
Ihave an external, will that do?

---

### Post by homerwookey on 2009-08-10
Ok so I decided to reinstall 8.10
It took about an hour to complete, then after I rebooted got past the grub stage, then flashing cursor in top left hand corner for about a minute then
Error 15: File not found
press any key to continue

tried all the options but to no avail
Any ideas?

---

### Post by Linux000 on 2009-08-10
This is odd. The harddrive's MBR can be read, but the partition can't... What did you select in the install menu when you partition the drive, i.e. use whole disk etc.

---

### Post by homerwookey on 2009-08-10
Didnt use whole drive, just 1 partition.
after running the livecd again, a 9.6 gb partition of the drive appeared on the desktop but I couldn't access any of the restof the drive

A few extra notes, also after upgrade, running the livecd,
typed fdisk -l 
got message
cannot open /dev/sda

Whilst checking the partition editor, it stayed on the scanning all devices screen for a few minutes, then at /dev/sda3 (I think where my hard drive originally was) it stated unknown file system (451.29 GiB) and had 'boot' in the flags column.

ALSO A WARNING FLAG:
unable to detect filesystem! Possible reasons are: the filesystem is damaged,  The filesystem is unknown to GParted,  There is no filesystem available (unformatted)

SOOOOO... Guessing that indeed there is an issue with my hard drive. Can somebody point me in the right direction to confirm this, and suggest the next course of action?

Thankyou again to all

---

### Post by Linux000 on 2009-08-10
Okay, thats more likely, what is on your entire Hard drive that you would want to keep? (software, files, licensees, etc.) It doesn't look like a hardware problem or grub wouldn't boot and Ubuntu wouldn't install.

---

### Post by homerwookey on 2009-08-10
I have backed up my work stuff, my music and pictures but there are a few things I would like to keep so if possible to recover them that would be great

---

### Post by Linux000 on 2009-08-10
Could you post a screenshot of PartEd from the live CD?

---

### Post by homerwookey on 2009-08-10
trying to by cutting and pasting to email but wont work
heres manual input

sda1 is fat32, 62,72mb, used 8.52 unused 54.21
sda2 is fat32, os label, 5 GiB, used 4.98, unused 25.60 mb
sda3 is unknown with warning flag, 451.29 GiB, used ?, unused ? boot flag also
sda4 has key symbol, extended, 9.41 GiB, used ?, unused?
sda5 has key symbol, linux-swap, 15.66 mb, used? unused?
sda6 is ext3, 8.95GiB, used 2.27GiB, unused 6.68GiB
sda7 is linux swap, 454.94mb, used?, unused?
hope this will help

---

### Post by Linux000 on 2009-08-10
I am guessing sda3 the 491 GB partition is ubuntu?

---

### Post by homerwookey on 2009-08-11
think so

---

### Post by Linux000 on 2009-08-11
Looks like your main ubuntu partition is not properly formatted, which would cause the errors.

---

### Post by homerwookey on 2009-08-11
Wierd its been fine for a year now.
So I take it I have to format the drive, would it be better to do the whole thing or just the dodgy partition?
Is there any way I can recover the stuff on there first or have I lost it?

---

### Post by Linux000 on 2009-08-11
Formatting that partition should do it, but you would lose everything on it, also what happens when you try to boot into ubuntu from the HDD.

---

### Post by homerwookey on 2009-08-11
After the grub loading, I get flashing cursor top left for a minute then Error 15 File not found, press anykey to continue.
It then gives options for booting ubuntu but the same thing happens with each- error 15 file not found

---

### Post by Cato2 on 2009-08-11
I think your main drive has problems and you should back up any data you'd like to keep as soon as possible.   It could fail completely at any time I think...

Looking at /var/log/messages for errors would help confirm this, but the messages you posted early on seem to show disk or controller errors.

A backup of /home would be a good start.   Also try to grab a copy of /etc, it really helps in re-configuring your new setup to look like the old one.

Reinstalling on the same hard disk isn't going to cure anything - the disk will remap the bad blocks but if it's failing you will just get new ones. 

Here's what I would do:

1. Connect your external drive

2. Boot from the Ubuntu Live CD that you have

3. Run "apt-get install sbackup" - this is a really good but simple backup tool.  

4. Mount your external drive - may happen automatically if you re-connect it after step 3.  Note the pathname, usually /media/something.

5. Run the sbackup (Simple Backup) config tool under System menu - tell this to back up to /media/something, and to include backup of /home and /etc.  If for some reason the drive isn't mounted, do an fdisk -ul to find the partition and then do "mount /dev/sdXY /media/external".

6. Within this config tool, tell it to Backup Now

7. Wait for the backup to complete - maybe look in Gnome System Monitor or do "ps -ef | grep sbackup" until it's finished.

8. Check the backup is OK - try "grep sbackup /var/log/*" to find any errors.

9. If there are errors, install gddrescue and read up on how to use that.  It's more complex to use than sbackup but works well on failing hard disks.

You have got a chance of recovering your stuff, but some data may be gone.   If your sbackup backup works well, this can be restored quite easily within your new setup on a new hard drive.

Just because Ubuntu installed OK again doesn't mean the drive is OK.

Also, note that it could be a disk controller error (IDE/PATA if it's an old PC, SATA on newer PCs) - this might explain some of the errors with booting a live CD.

Before you buy a new hard drive, I'd recommend burning a copy of StressLinux, and leaving that running for a day or two - it might help flush out where the hardware problems are.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) is a really good resource.

Also, try the Ubuntu Rescue Remix live CD - it's got some great tools and the forums are good, with a real data recovery expert answering questions.  Parted Magic is another good rescue disk with a larger community.

Once you know the new PC is OK, you can install Ubuntu, then install sbackup and use it to recover your files into temporary directories, then move them back into the right places.  The /etc files won't work directly but you can compare them to your new /etc files.

Above all, make sure you have GOOD backups - sbackup is not only easy to use, it automatically configures itself to run backups every day, and will never run out of disk space!  

Good luck!

---

### Post by Linux000 on 2009-08-11
Yeah, pretty much that. Forgot disks can have bad sectors...

---

### Post by Cato2 on 2009-08-11
Something I forgot to say is that using the Live CD is recommended even if Ubuntu is bootable, because new package installs are then done in RAM, without writing to the hard disk at all.  The less you write to a failing disk, the better.

---

### Post by homerwookey on 2009-08-11
Thanks for the info Cato2,
Unfortunately I fall at the first hurdle, 
sudo apt-get install sbackup gets me
 Couldn't find package sbackup


Tried to find with synaptic package manager but to no avail
Also fdisk -ul gives me
cannot open /dev/sda

---

### Post by compucon on 2009-08-11
it could be your BIOS, the oldest you can have yours bios is from the year 2000.

also, to get to synaptic package manager, go to the terminal and log in as the root user (su) then type, or copy and paste : gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic

(i'm running ubuntu 9.04 so it might be a bit different)

---

### Post by homerwookey on 2009-08-11
My BIOS is up to date,
I can get to synaptic, it just doesnt find sbackup

---

### Post by LewRockwell on 2009-08-11
I've read through all the posts on this thread

Now I'm going to offer my personal actions as if the machine was on my tech bench

[http://www.puppylinux.org/downloads/official-releases/latest-production-release](http://www.puppylinux.org/downloads/official-releases/latest-production-release)

Load up my Puppy Linux LiveCD, mount the desired partitions, recover any desired data

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

[http://partedmagic.com/programs.html](http://partedmagic.com/programs.html)

Load up my Parted Magic LiveCD and do a complete drive Secure Erase via the hard drive's onboard secure erasure function and also perform a GSmartControl analysis of the drive health

and go from there based on the results of above actions

keep us posted on your progress and discoveries!

.

---

### Post by homerwookey on 2009-08-11
Ok, running puppylinux livecd
mount options only show sda1, sda2, and sda6.
all my stuff I believe is on sda3,
is there any way I can access?

---

### Post by Linux000 on 2009-08-11
Well, sda3 is of an unknown(or corrupted) format so not really.

---

### Post by Cato2 on 2009-08-12
sbackup is definitely in the Ubuntu repositories for 8.10 - [http://packages.ubuntu.com/intrepid/sbackup](http://packages.ubuntu.com/intrepid/sbackup) - check that the universe repository is enabled in Synaptic.

Also, are you booting from the Live CD and with an Internet connection?  If so, sbackup should definitely install, so check your connection (use the Network configuration stuff perhaps to set an IP address).  You should not boot from your hard disk as that will involve writing to it.

To recover sda3, you will need to read the DataRecovery link - try testdisk which can recover partition tables (in case that's the problem), and perhaps try 'data carving' tools (e.g. PhotoRec which will scan the disk blocks to recognise images and recover those).  Best to get it into a mountable state first of course but data carving may be the only option if not.

---

### Post by homerwookey on 2009-08-12
Well, I have done all that LewRockwell suggested,
So far so good in that I have managed to get the hard drive wiped and have successfully reinstalled ubuntu.

I am attaching the output from the GSmart control analysis, so If someone can make any sense of it for me that would be fantastic

The only other thing I have noticed is that instead of having 500G of space on my hard drive, that has been reduced by about 50G, wheteher that has something to do with corrupted files or not I don't know but its a bit strange. I have just 1 partition (sda1)

So I am going to carry on using as normal (and making backups every day!), as I said before any feedback on the Gsmart control analysis would be great,
And just to say a big big thankyou to all for helping me through this
cheers


smartctl version 5.38 [i486-slackware-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDP725050GLA360
Serial Number:    GEA550RE37VKEN
Firmware Version: GM4OA5BA
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Wed Aug 12 08:23:50 2009 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (7890) seconds.
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
recommended polling time: 	 ( 131) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   133   133   054    Old_age   Offline      -       138
  3 Spin_Up_Time            0x0007   141   141   024    Pre-fail  Always       -       297 (Average 246)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       770
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   129   129   020    Old_age   Offline      -       30
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       3518
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       770
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       779
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       779
194 Temperature_Celsius     0x0002   193   193   000    Old_age   Always       -       31 (Lifetime Min/Max 8/40)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 3150 (device log contains only the most recent five errors)
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

Error 3150 occurred at disk power-on lifetime: 3511 hours (146 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 59 08 a2 e0  Error: UNC 4 sectors at LBA = 0x00a20859 = 10618969

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 55 08 a2 e0 08      00:28:33.500  READ DMA
  27 00 00 00 00 00 e0 08      00:28:33.500  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08      00:28:33.500  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:28:33.500  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      00:28:33.500  READ NATIVE MAX ADDRESS EXT

Error 3149 occurred at disk power-on lifetime: 3511 hours (146 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 59 08 a2 e0  Error: UNC 4 sectors at LBA = 0x00a20859 = 10618969

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 55 08 a2 e0 08      00:28:29.200  READ DMA
  27 00 00 00 00 00 e0 08      00:28:29.200  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08      00:28:29.200  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:28:29.200  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      00:28:29.200  READ NATIVE MAX ADDRESS EXT

Error 3148 occurred at disk power-on lifetime: 3511 hours (146 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 59 08 a2 e0  Error: UNC 4 sectors at LBA = 0x00a20859 = 10618969

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 55 08 a2 e0 08      00:28:24.900  READ DMA
  27 00 00 00 00 00 e0 08      00:28:24.900  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08      00:28:24.900  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:28:24.900  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      00:28:24.900  READ NATIVE MAX ADDRESS EXT

Error 3147 occurred at disk power-on lifetime: 3511 hours (146 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 59 08 a2 e0  Error: UNC 4 sectors at LBA = 0x00a20859 = 10618969

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 55 08 a2 e0 08      00:28:20.600  READ DMA
  27 00 00 00 00 00 e0 08      00:28:20.600  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08      00:28:20.600  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:28:20.600  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      00:28:20.600  READ NATIVE MAX ADDRESS EXT

Error 3146 occurred at disk power-on lifetime: 3511 hours (146 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 59 08 a2 e0  Error: UNC 4 sectors at LBA = 0x00a20859 = 10618969

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 55 08 a2 e0 08      00:28:16.300  READ DMA
  27 00 00 00 00 00 e0 08      00:28:16.300  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 08      00:28:16.300  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:28:16.300  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      00:28:16.300  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      3511         10618969
# 2  Short offline       Completed without error       00%      3511         -
# 3  Short offline       Completed without error       00%         0         -

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

