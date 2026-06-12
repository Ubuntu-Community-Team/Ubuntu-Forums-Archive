---
title: "separate home partition stopped working"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by dbuehler on 2010-01-05
By following the directions on another post here, I was able to get my system working for a short time using a separate home partition.  I removed my /home directory from the ubuntu partition and edited fstab to include the line:
/dev/sda8 /home ext3 nodev,nosuid 0 2
This worked for about a day or so, then, when I tried to log in, it went to a white screen.  

When I looked at /dev, I discovered that sda8 is not there.  In fact, there are no sda or sdb listed.  Any ideas what happened?

---

### Post by Methuselah on 2010-01-05
Do you have the ubuntu installation/live CD?

I don't really have a solution to your problem on hand but if you boot from the CD and execute **fidisk -l** 
in a terminal then post the output that will give some idea of your disk layout and maybe someone will be able to help.

---

### Post by dbuehler on 2010-01-05
Ok, here are the results of fdisk -l:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027aaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2   *        2433        4864    19535040   83  Linux
/dev/sda3            4865        7296    19535040   83  Linux
/dev/sda4            7297       24321   136753312+   5  Extended
/dev/sda5            7297        7539     1951866   82  Linux swap / Solaris
/dev/sda6            7540        9971    19535008+  83  Linux
/dev/sda7            9972       12403    19535008+  83  Linux
/dev/sda8           12404       24321    95731303+  83  Linux

Disk /dev/sdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027aaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9732    78172258+  83  Linux
```

sda8 is my home partition.  
sda3 is my main ubuntu hardy heron. (The one with the problem)
sda2 is another hardy installation that I am playing around with.  It does not use the separate home partition.
The other partitions are blank.  My intent was to use them to install other versions of linux so I can do some comparisons.

---

### Post by Grenage on 2010-01-05
Run the following on the partition in question, any issues?

```
fsck.ext3
```

---

### Post by dbuehler on 2010-01-05
fsck.ext3 on the home partition sda8 did not report any problems.

---

### Post by doas777 on 2010-01-05
weird.

what do you get from 
```

ls -al /dev/disk/by-uuid

```? 

I assume that you have turned it off and back on again, right? 

after you have your uuid's listed, try replacing "/dev/sda8" in your fstab with "UUID=<the disks uuid>" and reboot

/dev names can change if you plug in a a usb/esata volume, or add internal disks. if your fstab is using /dev names, this can ruin your boot. the UUIDs however do not change until you format the volume. 

you also may want to check the smart stats for your hdd. it may be on it's way out.

---

### Post by dbuehler on 2010-01-05
This is interesting!   I don't know how it happened, but /dev/disk is missing along with several others.  The only directories remaining in /dev are  fd  pts  and shm.

As for the smart stats, I an not sure how to get to them from hardy.

---

### Post by doas777 on 2010-01-05
just out of curiosity, does your BIOS see the disks?

here is some information on how to query SMART from ubuntu. you may wanna try a karmic livecd, as karmic has the new Disk utility (under system->adminstration) that has a graphical frontend for smartmon. 

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by dbuehler on 2010-01-05
Yes, bios is OK.  I am booting to another partition on the same drive.  

I loaded smartmontools and it DOES report errors as copied below.  Does this mean the drive is failing?  

```
SMART Error Log Version: 1
ATA Error Count: 34 (device log contains only the most recent five errors)
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

Error 34 occurred at disk power-on lifetime: 3594 hours (149 days + 18 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1f 51 a9 e0  Error: UNC 8 sectors at LBA = 0x00a9511f = 11096351

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 1f 51 a9 04 58      00:05:22.410  READ DMA EXT
  35 00 08 97 a0 9f 04 58      00:05:22.410  WRITE DMA EXT
  35 00 08 df 97 9f 04 58      00:05:22.410  WRITE DMA EXT
  35 00 08 e7 db 7d 04 58      00:05:22.410  WRITE DMA EXT
  25 00 08 0f f2 ae 04 58      00:05:22.410  READ DMA EXT

Error 33 occurred at disk power-on lifetime: 3594 hours (149 days + 18 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1f 51 a9 e0  Error: UNC 8 sectors at LBA = 0x00a9511f = 11096351

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 1f 51 a9 04 58      00:05:20.455  READ DMA EXT
  25 00 08 07 f2 ae 04 58      00:05:20.455  READ DMA EXT
  25 00 08 97 50 a9 04 58      00:05:20.445  READ DMA EXT
  25 00 08 2f 0a af 04 58      00:05:20.445  READ DMA EXT
  25 00 08 b7 3d a9 04 58      00:05:20.445  READ DMA EXT

Error 32 occurred at disk power-on lifetime: 3594 hours (149 days + 18 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1f 51 a9 e0  Error: UNC 8 sectors at LBA = 0x00a9511f = 11096351

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 1f 51 a9 04 58      00:05:17.280  READ DMA EXT
  35 00 05 0f 57 a3 04 58      00:05:17.280  WRITE DMA EXT
  35 00 05 87 68 a2 04 58      00:05:17.280  WRITE DMA EXT
  35 00 08 e7 db 7d 04 58      00:05:17.280  WRITE DMA EXT
  25 00 08 1f 51 a9 04 58      00:05:15.325  READ DMA EXT

Error 31 occurred at disk power-on lifetime: 3594 hours (149 days + 18 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1f 51 a9 e0  Error: UNC 8 sectors at LBA = 0x00a9511f = 11096351

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 1f 51 a9 04 58      00:05:15.325  READ DMA EXT
  25 00 08 97 50 a9 04 58      00:05:15.315  READ DMA EXT
  25 00 08 b7 3d a9 04 58      00:05:15.305  READ DMA EXT
  25 00 08 b7 35 a9 04 58      00:05:15.305  READ DMA EXT
  25 00 08 7f 4e a9 04 58      00:05:15.305  READ DMA EXT

Error 30 occurred at disk power-on lifetime: 3594 hours (149 days + 18 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 1f 51 a9 e0  Error: UNC 8 sectors at LBA = 0x00a9511f = 11096351

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 1f 51 a9 04 58      00:05:11.445  READ DMA EXT
  25 00 08 ef 35 af 04 58      00:05:11.445  READ DMA EXT
  25 00 08 8f 0e af 04 58      00:05:11.445  READ DMA EXT
  25 00 08 1f 51 a9 04 58      00:05:09.360  READ DMA EXT
  25 00 10 d7 35 af 04 58      00:05:09.360  READ DMA EXT

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

---

### Post by doas777 on 2010-01-05
hmm. can't really tell from the info provided. 
try running one of the tests that it recomends toward the bottom of the output (smartctl -t).

you are able to use other partitions on the drive, huh? wow, that is a head scratcher. I'll post back if I think of anything else

---

### Post by dbuehler on 2010-01-05
Hey, thanks for the help doas.  

I'm still a newbie here and guess I need to read  up on smartmon so I can figure out exactly what it is telling me.

---

