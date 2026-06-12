---
title: "Dual-booting partitions"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by salgala2000 on 2011-08-13
Hello,
I've been running Ubuntu on Wubi for about a month now and decided to do a real dual-boot. I downloaded ubuntu onto a USB drive and am now running Ubuntu from there. When I tried "Install Ubuntu 11.04" an "Allocate hard drive" screen comes up and I'm not sure what to do. I can't erase Windows, I don't need much memory for it. I share this computer with my parents (underage here) so I'd rather go on the conservative side and keep using Wubi rather than dual-booting if there is a risk of losing Vista. Any help will be greatly appreciated.

Here's the pic.
[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Screenshot.png[/IMG]

---

### Post by oldfred on 2011-08-13
Safest to use Vista's tools to shrink the Vista partition. NTFS does need about 30% free so do not shrink too much. Do not create partitions in windows, it does not know Linux.

Then come back to gparted.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by salgala2000 on 2011-08-13
The problem for me is that there is no option to keep both.
[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Screenshot-1.png[/IMG]




EDIT: The second link seems to have what I want. Sorry for posting before reading all links. Let's hope I can get this to work.

---

### Post by salgala2000 on 2011-08-13
Okay, when I try to "change" the Windows partition (I'm assuming that's it since it's 198.5GB) it doesn't give the option to resize it. It just lets me "Use as" something different. In the screenshots on the second link, his computer lets him edit the size of the partition to make free space. What should I do?
[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Screenshot-2.png[/IMG]




















Sorry for the double post. I tried using Gparted to shrink the Vista partition but it won't let me. I (strongly) suspect it has something to do with this error that shows up on that partition.  I've already tried and Vista is working fine, so I'm not sure what this error means.
[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Screenshot-3.png[/IMG]

---

### Post by oldfred on 2011-08-13
I believe I said it was safer to use Vista's MMC to shrink Vista.

You have to run chkdsk from Vista. Ubuntu & gparted will not use a NTFS partition that needs chkdsk or was not shutdown properly as that could cause damage that chkdsk then could not fix.

---

### Post by salgala2000 on 2011-08-14
Sorry, I misread your earlier post. I will try using MMC to shrink Vista.

When I run "chkdsk" this is what I get.
[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Capture.jpg[/IMG]


EDIT: Sorry for all the questions; as you can tell, I'm new to this.



EDIT2: MMC appears to be working to shrink Vista. However, it's only letting me shrink Vista by 5094MB. Any ideas how i could remedy this?

[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Capture1.jpg[/IMG]

---

### Post by bcbc on 2011-08-14
You need to run chkdsk with the /f or /r parameter. /f means chkdsk will fix errors automatically. /r means chdsk will scan the disk surface for bad blocks (and also fixes automatically).

You can also do this from Computer, right click on the drive you want to scan, properties, tools, check disk for errors - select option(s) - and (if it's the C: drive or it cannot obtain a lock on the drive) you need to reboot to complete.

---

### Post by salgala2000 on 2011-08-14
Thank you for the help.

I've done this now. The process was completed and I rebooted. MMC is still only letting me shrink Vista by 5GB, but I'm going to try to use GParted to see what it can do.

---

### Post by spiky001 on 2011-08-14
not a good idea using Gparted to shrink windows

---

### Post by Triblaze on 2011-08-14
I remember I had trouble repartitioning as well, Vista wasn't cooperative when it came to allocating space for Ubuntu.

I eventually got it, but something must've gone wrong, because now Vista seems to not exist. I don't really use it though, but still.

Good luck to OP, sorry I don't have anything to contribute.

---

### Post by spiky001 on 2011-08-14
In the box where it sayes ENTER AMOUNT YOU WANT TO SHRINK DID YOU PUT ANYTHING??? You should state the amount in MB

---

### Post by YesWeCan on 2011-08-14
A few defrags may help create more shrinkability.

---

### Post by salgala2000 on 2011-08-14
Even though I haven't gone through with it yet, GParted seems to be  allowing me to shrink the partition by the amount I want (60GB). MMC is  still only letting me shrink Vista by 5GB. Should I go through  with the  GParted shrinking, or should I try to do something in Vista which will  allow me to shrink Vista by more?

---

### Post by spiky001 on 2011-08-14
Try setting the amount in the box i pointed out 1st

---

### Post by salgala2000 on 2011-08-14
If you're referring to MMC: It will only let me type up to 5094MB. Anything else and it just goes back down to 5094.

If you're referring to GParted: Yes, I typed in 60,000MB but I didn't finalize the operation because of the warnings on here.

So should I go ahead with GParted, or is there a way to change the MMC settings to allow me shrink the partition more?

---

### Post by spiky001 on 2011-08-14
read this ALL [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

partition magic [http://www.soft32.com/Download/free-trial/Partition_Magic/4-151-1.html](http://www.soft32.com/Download/free-trial/Partition_Magic/4-151-1.html)

---

### Post by salgala2000 on 2011-08-14
Thank you for the links, reading now.

EDIT: Would you recommend downloading Auslogics Disk Defrag which is linked to in the first link?

---

### Post by spiky001 on 2011-08-14
Defrag is always good  As mention by "yes we can"

---

### Post by salgala2000 on 2011-08-14
I did a Defrag and now the memory available for shrinking went from 5GB to 2.5GB :(

EDIT: I'm not sure why GParted (and the computer) shows 65GB free and MMC only lets me shrink by <5GB. Is shrinking with GParted a sure fire way to ruin Vista?

---

### Post by YesWeCan on 2011-08-14
Good grief. You may need to run the defrag several times...its whole purpose is to compact the existing data. 
What does Windows report for the partition/drive capacity and the free space?

---

### Post by salgala2000 on 2011-08-15
> **YesWeCan said:**
> Good grief. You may need to run the defrag several times...its whole purpose is to compact the existing data. 
What does Windows report for the partition/drive capacity and the free space?

First of all, I went ahead and shrank the Vista partition by the 2.5GB that it would let me, I figured I can shrink more later if it lets me.

I've run the defrag several times and now it will only let me shrink the Vista partition by 0MB. I'm currently running the "Optimize" feature on the Auslogics Disk Defrag program to see if that will help.

---

### Post by oldfred on 2011-08-15
How much space is used in your Vista partition. Windows works best with at least 30% free space in the NTFS partition. At about 10% free it slows so much as to be unusable.

It used to be old versions of gparted (and many other tools) started all partitions at sector 63 which was correct for XP and Linux. Then Vista & 7 changed to start at sector 2048, but many tools were not updated and moved the start of Vista or 7 to sector 63. It often could be repaired with a fixBoot command as the boot sector has to match partition size/location. Gparted added a checkbox to not move the start but no one knew what the checkbox was for, so the issue continued. Now Linux starts partitions at sector 2048. If you have a new gparted it should work without issue, but we have many users who have an old CD laying around and still create problems. So we still suggest using windows MMC for changes to windows. 

If you do use gparted or any other partition tool to resize windows be sure to have a windows repair CD, immediately reboot windows at least twice, as it will run chkdsk and may make other auto repairs. You should also have an Ubuntu liveCD as sometimes other tools have made partition table entires that are not valid (not sure why) and then fixparts, testdisk or other Linux tools are needed to repair partition table. 

Or it still is best to use Windows to resize windows. And have good backups as any partition changes can cause problems and require reinstalls.

---

### Post by salgala2000 on 2011-08-15
> **oldfred said:**
> How much space is used in your Vista partition. Windows works best with at least 30% free space in the NTFS partition. At about 10% free it slows so much as to be unusable.

It used to be old versions of gparted (and many other tools) started all partitions at sector 63 which was correct for XP and Linux. Then Vista & 7 changed to start at sector 2048, but many tools were not updated and moved the start of Vista or 7 to sector 63. It often could be repaired with a fixBoot command as the boot sector has to match partition size/location. Gparted added a checkbox to not move the start but no one knew what the checkbox was for, so the issue continued. Now Linux starts partitions at sector 2048. If you have a new gparted it should work without issue, but we have many users who have an old CD laying around and still create problems. So we still suggest using windows MMC for changes to windows. 

If you do use gparted or any other partition tool to resize windows be sure to have a windows repair CD, immediately reboot windows at least twice, as it will run chkdsk and may make other auto repairs. You should also have an Ubuntu liveCD as sometimes other tools have made partition table entires that are not valid (not sure why) and then fixparts, testdisk or other Linux tools are needed to repair partition table. 

Or it still is best to use Windows to resize windows. And have good backups as any partition changes can cause problems and require reinstalls.

Unfortuneatly, I can't find my Windows repair CD at the moment :( Here are two screenshots which show how much memory I have left (69.23GB) as well as the Defrag screenshot.

[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/Auslogicsdefrag.jpg[/IMG]

[IMG]http://i922.photobucket.com/albums/ad67/salgala2000/ConsoleMMC.jpg[/IMG]






EDIT: I just moved 6GB of data from my computer to my external hard drive and deleted the data from my computer (and the recycle bin). I tried running MMC, and it still says that the shrink capacity is 0MB.

---

### Post by oldfred on 2011-08-15
Not sure if the repair CD is in Vista but these are instructions on how to make one:

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by salgala2000 on 2011-08-15
> **oldfred said:**
> Not sure if the repair CD is in Vista but these are instructions on how to make one:

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)



Thank you very much. I'm currently running Defrag and Optimize, as well as cleaning up my disk and backing everything up. As soon as this is done I'll do try what Mark Phelps posted and report back with results.




EDIT: The macrium.com link says that the download is not currently available due to copyright issues, so Mark Phelps post doesn't help me :(

All my files (music, pictures, documents) are already backed up (i did that manually) onto an external hard drive. I don't care about losing my personal files, I just don't want to lose the system files that allow Vista to run. I'm creating a "System Recovery Disk" as per the 4th link you posted. If I use GParted to shrink the windows partition (from what I've heard, Vista will most likely not be bootable) can I use this disk to repair Vista?

EDIT2: I installed the program in the 2nd link and when i try to run it, it just says "Fatal error during installation."

---

### Post by oldfred on 2011-08-15
It is the neogrub site that is down due to copyright issues. Not sure why as all it downloaded was the recovery software, not a full install. Not sure where else to get a Windows repairCD if you have not made one before your system crashes.

You are saying the macruim backup software is not working? I have not tried it.

---

### Post by salgala2000 on 2011-08-15
I've tried installing and reinstalling the macrium backup software multiple times and whenever I try to use it for the first time it gives me the error "Fatal error during installation".

I've tried torrenting the vista recovery iso CD from here [http://www.techrepublic.com/blog/window-on-windows/creating-a-windows-vista-recovery-cd/622](http://www.techrepublic.com/blog/window-on-windows/creating-a-windows-vista-recovery-cd/622) (hyperlink under the second heading). I downloaded it to a disk and tried to boot my computer off it. However, I got a message that said > Windows is loading files...The bar loaded about 10% and then I got an error message saying 

> Windows has encountered a problem communicating with a device connected to your computer.

This error can be caused by unplugging a removable storage device such as an external USB drive while the device is in use., or by faulty hardware such as a hard drive or CD-ROM drive that is failing. Make sure any removable storage is properly connected and then restart your computerI'm unsure if this is because my CD/DVD drive (which sometimes fails, presumably randomly), because of an error copying the ISO file onto the CD (the only options were 3x and 9x, but my CD is 12x rewritable), or if it's because I have to use a DVD (which I have none of at the moment).


This is what I'm going to do next:

1) Run the macrium backup software from the administrator account (I right-clicked and selected "run as administrator" but i didn't actually run it from the administrator account).

2) Try rewriting the CD and see if it works.

3) As a last resort, I'll try downloading a vista recovery cd ISO file from thepiratebay.




**EDIT:** The Macrium program works when run from the administrator account, but not from another user account and pressing "Run as administrator" for some reason. Now I have Macrium open, but I'm not sure what to do. Should I "Create a backup image of an entire disk or selected partition" or "Create a bootable rescue CD" ?
[B]
EDIT2[/B]: I tried the "Create a bootable rescue CD" and then "Create a linux-based recovery system". Now I'm going to try the other option. With the linux-based recovery, i booted off the CD and an installation wizard started, but it said that there was no valid image file on the CD. I will try again.

---

### Post by salgala2000 on 2011-08-17
Sorry for the double post here. I'm not sure how much attention (if any) this problem gets on these forums, but I'll leave the information here of how I solved the problem for any future references.

Since Vista wouldn't let me shrink the partition by more than 2.5GB, I backed up Vista and shrank the Vista partition using GParted in Ubuntu. So here are the steps I took to dual-boot.
  
...............................................................................................................................

1) Download Ubuntu on a USB drive.

2) (In Windows) Used Macrium's software ([http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)) to create a bootable disk (I chose the Linux based CD option).

3) I again used Macrium's software to backup up my Vista partition in case anything went wrong. I backed up the Vista onto an external hard drive that I have.

4) I used GParted (from Ubuntu on the USB) to shrink the Vista partition.

5) I rebooted and ran chkdsk a couple times. Windows had no problems after a couple reboots, so I didn't need to use my backup.

6) Installed Ubuntu in the free space.  
................................................................................................................................

Thanks to everyone in this thread that helped me successfully install Ubuntu on my computer. I'll be sure to mark the thread as solved.

---

### Post by oldfred on 2011-08-17
Glad it worked and it helps to know what works.

Even though we recommend using Windows tools for Winodws, most of the time you can shrink with gparted if you have the newer version, but having the backup saves you in those cases where there are issues.

---

