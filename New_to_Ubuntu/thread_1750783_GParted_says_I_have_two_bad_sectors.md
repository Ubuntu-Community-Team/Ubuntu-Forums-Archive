---
title: "GParted says I have two bad sectors"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by AnnS on 2011-05-05
Hello! I'll start by saying I have an HDD and three primary partitions (Windows XP, XP factory recovery disk, and Windows 7) and an extended partition in which I have Ubuntu 10.10.  Ok, now, my problem is that today I was checking my partitions with GParted and I noticed an exclamation mark next to my first partition (the one with XP). And it says this:    

[IMG]http://i283.photobucket.com/albums/kk314/EmilYN45/Pantallazo2.png[/IMG]

I noticed that appears when that drive is unmounted. If I mount it, it doesn't say anything and no exclamation mark shows.

I'm a little afraid of doing a chckdsk in case I lose my data, since it's not possible for me to do a backup. Now, I have done that in the past, but it never showed any problem in the disk so I don't know what would happen if it did. Do you think I'll lose something? And is it normal that GParted only shows that when the drive is unmounted?

I'm sorry if this is a silly question.^'

---

### Post by stmiller on 2011-05-05
Bad sectors happen. chkdsk (run in Windows, or better yet from a Windows recovery console) attempts to repair or work around bad sectors with spare ones a drive may have. This is good advice.

This is a sign the drive is on the way out, most say.

---

### Post by srs5694 on 2011-05-06
> **AnnS said:**
> I'm a little afraid of doing a chckdsk in case I lose my data, since it's not possible for me to do a backup.

Make it possible to do a backup. If you don't, you're risking your data no matter what you do.

You can run a SMART utility, such as GSmartControl or smartctl, to learn more about what sort of physical problems the disk is experiencing, but that will in no way correct the problems or reduce the likelihood of future problems occurring; that will just give you more information. Unless that warning is completely erroneous, though, my advice is to replace the drive ASAP. Go out and buy a new drive *today*. As the warning you posted says, drives can begin to fail and then deteriorate rapidly, so it's conceivable that the day after tomorrow you won't be able to recover a single byte from the disk. OTOH, it might also last another year. I don't want to make this out to be worse than it is, but that's the problem -- it's impossible to know with certainty just how bad it is.

---

### Post by 3rdalbum on 2011-05-06
You must do the backup ASAP. As the earlier poster says, "make it possible".

Ubuntu comes with the program "Disk Utility" which can read your disk's SMART data. I don't know if Gparted is telling you that there are two bad sectors that have been automatically remapped by your drive and don't pose a problem, or if your drive has run out of extra sectors to remap to and now you've got two MORE bad sectors. Disk Utility should be able to tell you this.

If it's the latter situation, then you need to put in a new hard disk and copy all your data to the new disk, and stop using the old one AT ALL. Get rid of the old disk once you know everything has been copied.

If it's the former situation (there's two bad sectors, but they have been remapped to the extra failsafe sectors of the drive) then you should still backup your data, and check the disk regularly. If the number of bad sectors goes up within the course of some weeks, then the disk needs replacing.

---

### Post by AnnS on 2011-05-06
First of all, I want to thank you all for taking the time to help me. :)
This is kind of sad to me, because the disk is 'quite' new. But I know this sort of thing can happen.

But anyway, I looked in Disk Utility, and It says this:

[IMG]http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho-1.png[/IMG]

And I was thinking, when I installed Ubuntu, I did the partitioning manually (using an unallocated space I had), and everything went fine, but I noticed I have two unallocated spaces (I don't know why, I thought I did it right and from what I remember, I allocated 2048 MB to swap, but it has 1.91 GB), and maybe that's the problem? Maybe that's what Disk Utility and GParted see as bad sectors? Is that a possibility? This is what my disk looks like:

[http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho.png](http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho.png)

And also, when I mount my second partiton (with Windows 7, and the one named 'Sky OS'), it shows a warning sign that says:

[http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho-2.png](http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho-2.png)

It only happens with that one. When I mount the other one ('Preload', with Windows XP and the one with the bad sectors), it doesn't show any warning sign.

I hope you know more than me about this. But thank you either way for your answers. :)
And I will follow your advice and make it possible to do a backup. In fact, I should do backups even if my HDD is fine, since one never knows when it can fail. :(

*Sorry for my bad english, by the way, and for the long post, haha.

---

### Post by srs5694 on 2011-05-06
The unallocated space in your partitioning scheme did not cause your sectors to go bad, and were almost certainly not caused by bad sectors; the two are unrelated. For the record, there's little or nothing you can do in software to make sectors go bad on a spinning hard disk; the only possibility that occurs to me is reading or writing the same track repeatedly. I'm not even sure that would do it, and if it did it would take *many* reads/writes. Bad sectors are more likely to result from physical trauma, like dropping a disk, particularly while it's running. They also inevitably occur with time, of course, entropy being what it is.

If the disk is new, as you say, then it's probably under warranty. Contact the manufacturer for a replacement. With any luck they'll cross-ship, so that you'll get the replacement before you have to return the defective unit. That will let you transfer your data over. If not, I recommend buying another drive to replace the current one, and then you can use the replacement drive for backups.

---

### Post by Fraoch on 2011-05-06
> **AnnS said:**
> And also, when I mount my second partiton (with Windows 7, and the one named 'Sky OS'), it shows a warning sign that says:

[http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho-2.png](http://i283.photobucket.com/albums/kk314/EmilYN45/Screensho-2.png)

This is saying you're trying to mount an NTFS-formatted partition and you don't have the required Linux package to read NTFS ("ntfsprogs").

Install ntfsprogs using Ubuntu Software Centre, Synaptic or apt-get.

---

### Post by AnnS on 2011-05-06
I see. Well, thank you so much for your answer.

I'll do what you say.
And well, I guess the constant energy issues (low voltage, high voltage and sudden power cut) we've been having around here for years can be part of the cause.

Thanks again! :)

> **Fraoch said:**
> This is saying you're trying to mount an  NTFS-formatted partition and you don't have the required Linux package  to read NTFS ("ntfsprogs").

Install ntfsprogs using Ubuntu Software Centre, Synaptic or apt-get.

I see, but Ubuntu can read perfectly my other NTFS partition, that just appears with that one. And if I mount "Sky OS", it lets me and I can access it with no problems. I don't know why the message appears. =/

---

### Post by Dutch70 on 2011-05-06
If it's any consolation, I've had 9 bad sectors on one of my hdd's for about 6-8 months and it hasn't gotten any worse. I still use it, but I keep my data backed up on my other hdd.
The problem is, I can't depend on that hdd at all for important data that I don't want to lose. As SRS said, it may not boot the very next time I try.

It's a good possibility that the power outages had a lot to do with it. What happens when your hdd is not shut down properly is the arm/needle (if I'm saying this right) that reads the disk drops down onto the hdd and the hdd continues to spin from momentum, causing it to scratch the hdd's surface.

---

### Post by AnnS on 2011-05-06
> **Dutch70 said:**
> If it's any consolation, I've had 9 bad sectors on one of my hdd's for about 6-8 months and it hasn't gotten any worse. 
The problem is, I can't depend on that hdd at all for important data that I don't want to lose. As SRS said, it may not boot the very next time I try.

It's a good possibility that the power outages had a lot to do with it. What happens when your hdd is not shut down properly is the arm/needle (if I'm saying this right) that reads the disk drops down onto the hdd and the hdd continues to spin from momentum, causing it to scratch the hdd's surface.
Thank you for your explanation.
I certainly didn't expect this, it's the first time it happens to me. Now I'll buy an UPS, so it will give me time to shut down the computer properly, because that's a serious problem we have here.

I think I'll buy a new HDD and use this as a backup replacement, as [srs5694]("http://ubuntuforums.org/member.php?u=1032238") suggested.
I'll still do the chkdsk in Windows (though I don't know if that will do anything), I'm just looking to make a backup first.

---

### Post by Dutch70 on 2011-05-06
Edit: It's also best to go to the manufacturers website to verify that it is bad & see if it is still under warranty. I'm not sure what kind of hdd you have, but for an example, here is Seagate's website. I'm going to check mine now...lol.
[[COLOR="Red"]http://www.seagate.com/www/support/warranty_&_returns_assistance/verify_warranty_&_submit_rma[/COLOR]]("http://www.seagate.com/www/support/warranty_&_returns_assistance/verify_warranty_&_submit_rma")

Have a look at mine. As I said, I still use it with no problems, other than the fact that I can't shrink it to give Ubuntu more space & the impending failure that is sure to come...who knows when.

---

### Post by Paqman on 2011-05-06
A small number of bad sectors is not a big problem, and normal for any drive that's been in use for a while. As long as the drive is reallocating them and the numbers aren't rising there's no cause for alarm. Your system will alert you if the number of bad sectors is reaching a dangerous level.

A bulletproof backup & redundancy plan is a good thing to set up though. Personally I don't trust hard drives at all. It's good to be a bit paranoid with important data.

---

### Post by BertN45 on 2011-05-06
DON't Buy a new disk, stop worrying. bad sectors are a completely normal on a disk, it can be a small fabrication error detected during formatting. That is why there are spare sectors. Only worry if the number of bad sectors reaches that limit of 200 or if the number increases fast. I wrote formatting software in the past and we really tried hard to find the bad sectors during the formatting to avoid the problems during normal operation.

---

### Post by srs5694 on 2011-05-06
> **BertN45 said:**
> DON't Buy a new disk, stop worrying. bad sectors are a completely normal on a disk

I don't think that's true, at least not for modern disks and as reported by SMART utilities. I've got about a dozen hard disks in use on computers I use, ranging in age from a couple months old to several years old, and not one of them has a single bad sector as reported by SMART utilities, as of the last time I checked them (which has varied from today to months ago). That said, there may be bad sectors on the platters that are mapped out at a low enough level that they don't even show up in SMART utilities. (I don't know enough about the low-level disk workings to say for sure.)

I *have* had disks fail catastrophically on me. Most of these drives weren't SMART-capable (they were bought and failed years ago), so I don't know what, if any, hints of impending failure SMART would have provided.

---

### Post by Paqman on 2011-05-07
> **srs5694 said:**
> I've got about a dozen hard disks in use on computers I use, ranging in age from a couple months old to several years old, and not one of them has a single bad sector

That's a bit unusual. In my experience I would expect any disk over a year old to have a pretty good chance of a bad sector.

---

### Post by tkelito on 2011-05-07
As someone who deals in repair work I can honestly say you should always be expecting the worst.  Always be proactive about the things you couldn't live without if your drive completely failed and make regular backups.  HDDs seem to have much higher failure rates now than they did 10 years ago.

---

### Post by AnnS on 2011-05-07
Thank you all for your answers!

I'll try not to be too concern about this. I did make a backup of my important data, so I'm a bit relieved.

By the way, I ran DSKCHK C: /f on Windows and in the report it says there's 8KB of bad sectors but apparently it didn't do anything, since in Disk Utility (now Ubuntu) it still said the same and I because I saw a lot of recommendations, I used a bootable CD of HDD Regenerator (now on Windows) to see if it could repair the bad sectors. It did find the same two bad sectors and it said it repaired them, even though in GParted (Ubuntu) still says the same thing (about the two bad sectors).

*--- **Edit:** Oh, ignore this part, haha, mysteriously, it workes now ---* But now... in Disk Utility, in SMART state it now says "Not sopported". And I was wondering why? It was 'sopported' before, so I wonder what changed. Oh, this is too confusing for me, haha. Does anyone know why it says that now? I'm about to give up, haha, I think I obsessed too much about everything computer-related and end up making the problem worse, haha.

I'm sorry if I'm being too annoying, by the way.

---

### Post by 3rdalbum on 2011-05-07
> **Paqman said:**
> That's a bit unusual. In my experience I would expect any disk over a year old to have a pretty good chance of a bad sector.

My early-2008 500 GiB hard disk still has zero bad sectors, according to Disk Utility.

Laptop HDDs may well vary.

---

### Post by demilord on 2011-05-07
I have a external drive for a year with a bad sector, a 1.5TB drive..
Im not worried, I switched it off once accidently while doing something and a power failure once while running.. it happends and most probably hittted the surface shortly...

---

### Post by srs5694 on 2011-05-07
AnnS, have you told a SMART utility to run a full test? In GSmartControl, for instance:


[list=1]
[*]Double-click your drive.
[*]In the resulting "Device Information" dialog box, click the Perform Tests tab.
[*]Select "Extended Self-Test" as the "Test Type."
[*]Click Execute.
[*]Wait. (You'll get an ETA timer. Such tests can take well over an hour, depending on the drive.)
[*]Check the results on the "Self-Test Logs" tab.
[/list]


The 8 KiB of bad sectors that Windows is reporting is 16 bad sectors. If Windows is detecting actual bad sectors (as in, it's tried to read or write a sector and gotten an error), then that means that they are *not* being remapped by the drive's firmware, which suggests that there's some sort of serious problem -- maybe the drive's reserved sectors have already all been used or some other issue is preventing the firmware from remapping those bad sectors. Alternatively, if the Windows report is based on the same type of SMART data you reported earlier, then your bad sector count has jumped from 2 to 16, which is disturbing in such a short period of time.

---

### Post by psusi on 2011-05-07
I have several corrections to things that have been said here:

1)  Bad sectors certainly are not "normal".  I have a pair of first gen 36 gb raptors still in this machine that have been in operation since 2004 with none.  I have a dozen disks in other server systems that are about the same age have zero bad sectors.  While they are not normal, a few can be lived with, and often times corrected.

2)  Chkdsk does not attempt to repair bad sectors and has no idea what SMART is.  All it does is flag the entire cluster as bad and avoid using it in the future.  The default cluster size is 4kb so each of those two 512 byte bad sectors caused windows to flag two 4kb clusters as bad, hence why it reports 8kb of bad sectors.

Power failure in the middle of a write can sometimes cause the sector to be incompletely written, which causes it to show up as bad when you try to read it.  In this case, there is nothing physically wrong with the disk; you just need to write valid data to the sector to repair it.  The SMART Pending count means that it is waiting for you to do that.  Once you try to write to that sector, the drive with either successfully write to it, or determine that it is physically damaged and reallocate the sector from the spare pool.

Run badblocks -b 512 on the drive to locate the bad sectors.  Once you have the sector numbers, use dd first verify that you have the right one, and then write zeros to it:

sudo dd if=/dev/sda iflag=direct of=/dev/null bs=512 count=1 skip=sector_number

If you have the right sector number, this should fail.  If it does, then run:

sudo dd if=/dev/zero of=/dev/sda oflag=direct bs=512 count=1 seek=sector_number

It is imperative that you enter the command exactly.  Note the difference between skip and seek, iflag and oflag, if and of.

After this, check the SMART numbers and the pending count should drop, and the reallocated count may go up.  If reallocated increases, then it was physically defective and has been reallocated from the spare pool.  If this is the case, then you should run the long self test about once a week for a few months to make sure no new bad sectors develop.  If reallocated does not increase, then there was nothing wrong with the medium and everything is fine.

---

### Post by BertN45 on 2011-05-08
I have been involved in a project that did a lot of research to improve the reliability of the computers (and disks) we used at that time. 
- _Bad sectors are norma_l. If you are in a very controlled static environment with professional equipment and professional service you will not have very much problems. BUT
- At home in the Dominican Republic most of my 5 disk have between 2 and 20 bad sectors. Partly because  I brought the equipment here by plane stored in my suitcase, because I bought the disks cheap on a computer fair in Belgium with a fair chance that it was B quality or because somebody moved the desktop or laptop abruptly, while the disk was in use.
- _Never try to repair a bad sector_. A bad sector indicates that something is wrong with the magnetic layer of the disc in that location and sooner or later the error may re-appear and you might loose data. It is not always right or wrong, but more something like there is e.g a 90% chance tat it is right and 10% that it cannot be read anymore.
= Power-fails should not cause a bad sector, since there is enough energy left in the power supply to complete the operation on the current sector and to retract the heads afterwards.

_If you cannot read the smart data anymore with the Disk Utility, you almost surely have a fast developing problem. Try to save everything, while the disk still works.._

---

### Post by AnnS on 2011-05-08
> **srs5694 said:**
> AnnS, have you told a SMART utility to run a full test? In GSmartControl, for instance:


[LIST=1]
[*]Double-click your drive.
[*]In the resulting "Device Information" dialog box, click the Perform Tests tab.
[*]Select "Extended Self-Test" as the "Test Type."
[*]Click Execute.
[*]Wait. (You'll get an ETA timer. Such tests can take well over an hour, depending on the drive.)
[*]Check the results on the "Self-Test Logs" tab.
[/LIST]
(...)

Hi, thank you for your answer. I did what you told me to, but I don't understand the log, haha. I think it's the same that says in Disk Utility. This is what it says:

```
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
data collection:          (6960) seconds.
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
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  84) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       5
  3 Spin_Up_Time            0x0027   153   151   021    Pre-fail  Always       -       1350
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       728
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4594
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       725
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       92
193 Load_Cycle_Count        0x0032   181   181   000    Old_age   Always       -       58028
194 Temperature_Celsius     0x0022   099   093   000    Old_age   Always       -       44
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged
```> **psusi said:**
>  (...)

Run badblocks -b 512 on the drive to locate the bad sectors.  Once you have the sector numbers, use dd first verify that you have the right one, and then write zeros to it:

sudo dd if=/dev/sda iflag=direct of=/dev/null bs=512 count=1 skip=sector_number

If you have the right sector number, this should fail.  If it does, then run:

sudo dd if=/dev/zero of=/dev/sda oflag=direct bs=512 count=1 seek=sector_number

It is imperative that you enter the command exactly.  Note the difference between skip and seek, iflag and oflag, if and of.

(...)

I find your post very informative, it helps me understand more about this. Thank you. :)

I tried doing what you told me, I copied "badblocks -b 512 /dev/sda" *(and I had to copy sudo at the beginning,  since it told me "Permission denied while trying to determine device  size")* but after one-two hours (more or less),  it didn't show anything, just the command line prompt and nothing else. It was like:

my@username:~$: sudo badblocks -b 512 /dev/sda
[sudo] password for my:
*(after one-two hours)*
my@username:~$: 

Did I do it wrong?

> **BertN45 said:**
> I have been involved in a project that did a lot of research to improve  the reliability of the computers (and disks) we used at that time. 
- _Bad sectors are norma_l. If you are in a very controlled static  environment with professional equipment and professional service you  will not have very much problems. BUT
- At home in the Dominican Republic most of my 5 disk have between 2 and  20 bad sectors. Partly because  I brought the equipment here by plane  stored in my suitcase, because I bought the disks cheap on a computer  fair in Belgium with a fair chance that it was B quality or because  somebody moved the desktop or laptop abruptly, while the disk was in  use.
- _Never try to repair a bad sector_. A bad sector indicates that  something is wrong with the magnetic layer of the disc in that location  and sooner or later the error may re-appear and you might loose data. It  is not always right or wrong, but more something like there is e.g a  90% chance tat it is right and 10% that it cannot be read anymore.
= Power-fails should not cause a bad sector, since there is enough  energy left in the power supply to complete the operation on the current  sector and to retract the heads afterwards.

_If you cannot read the smart data anymore with the Disk Utility, you  almost surely have a fast developing problem. Try to save everything,  while the disk still works.._

Thank you for your answer. :)

Well, I don't know why, but now it can read SMART data with Disk Utility again. I don't understand why before it said "Not supported". But just in case, I already backed up almost everything.

I'm not trying to repair the bad sectors, well, actually I am, haha, but because I was thinking that maybe it's not that serious. Like I said, it's the first time this happens to me, before I bought this HDD, I had the one that came with my laptop for three years and it's fine, no bad sectors. But I think I'll still replace it with another HDD, and maybe use this as an external disk.

I really appreciate your help. Thanks to all of you, I understand this better. :)

---

### Post by psusi on 2011-05-08
> **BertN45 said:**
> 
- _Bad sectors are norma_l.

You have a strange definition of normal.  Scratches and dings frequently happen to cars and usually people just live with them if they are small, but most people do not consider them to be "normal".

> **BertN45 said:**
> - _Never try to repair a bad sector_. A bad sector indicates that something is wrong with the magnetic layer of the disc in that location and sooner or later the error may re-appear and you might loose data.

No, it does not.  It is a fairly common occurrence for them to develop during power failure and to be correctable and never relapse.  Furthermore, drives are built with a pool of spare sectors for the express purpose of repairing bad sectors by remapping them.  Since the drives are designed to handle repairs, it hardly makes sense to advise never doing so.

> **BertN45 said:**
> = Power-fails should not cause a bad sector, since there is enough energy left in the power supply to complete the operation on the current sector and to retract the heads afterwards.


I used to believe this too, but after seeing numerous drives develop a single bad sector after a power failure that is easily repaired, it seems this is not always the case.  The medium actually being defective almost certainly would cause multiple bad sectors that could not be written to again.

---

### Post by srs5694 on 2011-05-08
AnnS, your SMART output shows 0 reallocated sectors (ID# 5) and the two "pending" sectors (ID# 197). This seems much less dire than might have been the case -- say if you already had a bunch of bad (reallocated) sectors and more had been detected but not yet reallocated.

---

### Post by Paqman on 2011-05-08
> **psusi said:**
> You have a strange definition of normal.  Scratches and dings frequently happen to cars and usually people just live with them if they are small, but most people do not consider them to be "normal".


I think he means "normal" in the sense of "routine" or "to be expected". As in, it's not necessarily a sign of a serious fault.

---

### Post by BertN45 on 2011-05-08
> **psusi said:**
> You have a strange definition of normal.  Scratches and dings frequently happen to cars and usually people just live with them if they are small, but most people do not consider them to be "normal".

No, it does not.  It is a fairly common occurrence for them to develop during power failure and to be correctable and never relapse.  Furthermore, drives are built with a pool of spare sectors for the express purpose of repairing bad sectors by remapping them.  Since the drives are designed to handle repairs, it hardly makes sense to advise never doing so.

I used to believe this too, but after seeing numerous drives develop a single bad sector after a power failure that is easily repaired, it seems this is not always the case.  The medium actually being defective almost certainly would cause multiple bad sectors that could not be written to again.

For me it is normal that an old car has scratches.

For me remapping is OK, the word repair confused me because it sounded like re-write/re-use the same physical sector. In general I do not think the consumer should try to intervene. It is best left to the firmware.

Just read the next article:

[http://static.googleusercontent.com/external_content/untrusted_dlcp/labs.google.com/en//papers](http://static.googleusercontent.com/external_content/untrusted_dlcp/labs.google.com/en//papers)

After developing the first bad sector there is a 15% chance that the drive will fail during the next 9 month and a 85% chance that it will survive.

Mains power fail can develop very strange effects. I lost a couple of motherboards after power fails and that should not happen either. It stopped, when I installed a surge protector. Problems after power failure depend on the quality of the design of the power supply.

---

### Post by psusi on 2011-05-08
> **BertN45 said:**
> 
For me remapping is OK, the word repair confused me because it sounded like re-write/re-use the same physical sector. In general I do not think the consumer should try to intervene. It is best left to the firmware.

The way that you cause the remapping to take place is to attempt to write to it.  That is the point where the firmware decides if the media is actually defective or not and remaps if it chooses to.  I have yet to see a case where a single bad sector that crops up after a power failure actually gets remapped; it is usually when you have a dozen or two consecutive bad sectors that you actually have media damage and they get remapped.

> **BertN45 said:**
> After developing the first bad sector there is a 15% chance that the drive will fail during the next 9 month and a 85% chance that it will survive.

Most likely that is because 15% of those "bad sectors" are actual media defects, which do tend to grow worse and ultimately kill the drive entirely, and the other 85% are just power loss errors.

---

### Post by BertN45 on 2011-05-08
> **psusi said:**
> The way that you cause the remapping to take place is to attempt to write to it.  That is the point where the firmware decides if the media is actually defective or not and remaps if it chooses to.  I have yet to see a case where a single bad sector that crops up after a power failure actually gets remapped; it is usually when you have a dozen or two consecutive bad sectors that you actually have media damage and they get remapped.

Most likely that is because 15% of those "bad sectors" are actual media defects, which do tend to grow worse and ultimately kill the drive entirely, and the other 85% are just power loss errors.

Please read the report :)

---

### Post by psusi on 2011-05-09
> **BertN45 said:**
> Please read the report :)

Bad link: 404.

---

