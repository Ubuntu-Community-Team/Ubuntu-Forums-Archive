---
title: "Recover partition"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by txobie on 2011-07-06
I was setting up Ubuntu on an external drive and managed to delete my partitions on my internal hard drive and created new ones ones by mistake.  (I thought I was on the external drive)  I did this using Ubuntu GParted Partition Editor.  

How can I recover the original partitions.  It is a Dell laptop.  One partition was a Recovery partition FAT? I think, and I don't know the size.  The other was an NTFS partition.  I think there was some unused space too. 

Any ideas how I can recover this?  I have Ubuntu on another external drive so I can boot with that and see the internal drive.  

It is a Dell Studio 1555 with a 500 GB hard drive, if that matters.

Thanks.

---

### Post by seawolf167 on 2011-07-06
You'll want to try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). Here is their Step-by-Step [guide]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

Good luck!

---

### Post by txobie on 2011-07-06
Thanks.  I'll read over that and get going.

---

### Post by Mark Phelps on 2011-07-06
You may be lucky -- and testdisk may actually work.  I've never had it work for me when trying to recovery MS Windows partitions.  And even when it partially worked, it was unable to reconstruct the actual filenames -- rendering the process completely useless (for me).

If you have the same results, you'll probably have to contact DELL.  Tell them your hard drive crashed and you need optical media in order to reinstall Windows.  They will most likely charge you for it, but the cost will be a lot less than buying MS Windows retail.

---

### Post by txobie on 2011-07-09
Using TestDisk I recovered my partition.  

Using TestDisk I changed the DellUtility partition to de as  instructed here under Recovery of a Dell computer.   [http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)

I can see the files and have recovered them.  Yea.  

I tried booting in Windows but it goes into recovery mode instead of starting....and it won't recover.  Here's what my partitions look like from Ubuntu GParted:

_**Partition     File System         Label          Size                Used         Unused      Flags**_
/dev/sda1    fat16                     DellUtility     133.32 MiB      9.27 MiB    124.05 MiB  diag
/dev/sda2    ntfs                       RECOVERY 15.00 GiB      7.48 Gib        7.52 GiB
/dev/sda3    ntfs                       OS               450.63 GiB 288.44 Gib    162.19 GiB   boot
unallocated  unallocated                                   1.02 MiB             --                     --

I feel like I'm close to having it working.  Any ideas what I should do?  Thanks.

---

### Post by westie457 on 2011-07-09
Welcome to the forums.

A few suggestions to restore Windows.

Select Windows from the Grub Menu and immediately start tapping - about once a second - the F8 key.
This will bring up a screen of options. If I remember correctly the first option is Repair your computer. Take that one and wait until a pop up says select your keyboard layout, do so click ok/continue. Enter your password next if asked then in the next screen select Command Prompt - a cli.

  At the command line input these commands one at a time:- 

```
bootrec /fixmbr

bootrec /fixboot

bootrec /rebuildbcd
```

Exit the command prompt then reboot. You might have to restore Grub from a LiveCD afterwards

---

### Post by txobie on 2011-07-09
Thanks for your help.  That sure seems like the right steps, but it didn't work.  
1. bootrec /fixmbr 
response: The operation completed successfully
2. bootrec /fixboot
response: The operation completed successfully
3. bootrec /rebuildbcd
response: Successfully scanned windows installations
Total identified windows installations: 0
response: The operation completed successfully

So it doesn't recognize the windows installation and seems that all three commands didn't actually do anything.  I can go to the c: drive and see the files, but windows doesn't recognize it.  Any more ideas?

---

### Post by westie457 on 2011-07-09
Try it again using this info [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by txobie on 2011-07-09
Thanks for your help Westie457.

I followed the steps.  Did the stuff to rename and replace the BCD file.  

After doing it I rebooted and got the error:
Windows failed to start. A recent hardware or software change might be the case.  
File: \windows\system32\drivers\vdrvroot.sys
status: 0xc0000098

I tried recovering as the message instructed further. No success.  

When I then renamed the BCD.old back to BCD.  Then it was back where it was before.

---

### Post by westie457 on 2011-07-09
It is possible that somehow I gave you wrong information, if that is the case I am sorry.

Now what I am about to suggest is a bit radical and I have never tried it but it might work.

If it goes wrong everything will need to be done again including using 'testdisk' to recover your partitions. I am trying to help and not deliberately BORK (technicl term) your system. Are you willing to try this? ..... Yes

use testdisk to rewrite the mbr for Windows. If it works and you can boot Windows CHEER very loudly.
If it fails and you cannot get Windows running try the repair procedure again. This time starting Let Windows repair itself. The repair procedure can take a long time and several reboots depending on the problems found. This is a looping process until Windows is happy.Check the report when this has finished. When the report says something along the lines of 'No errors found and the system reports that it has booted correctly' exit from this and you should go back to the options screen I think. If the options screen is available now is the time to use the command-line and input those commands from earlier.

Good luck.

---

### Post by westie457 on 2011-07-09
After all that typing i found what could be a simple more elegant solution _[here]("http://ubuntuforums.org/showthread.php?t=622828")_.
It is old but might still work.

---

### Post by txobie on 2011-07-10
I managed to mess up the drives trying to put mbr on it.  I tried to do it using windows bootsect commands.  No luck.  I'm using ddrescue to copy the drive on my external hard drive back to the internal so I can try again.  At least I have my data recovered.

---

### Post by westie457 on 2011-07-10
Thank heavens for back ups. Not sure if this question is going to be relevant now. Before starting ddrescue did you complteley wipe the borked disk and put a new partition table in it? I personally have no idea whether ddrescue .  Scrub most of what I have typed. Of course ddrescue writes byte for byte from the back up to the destination. It does not need a clean partition.

The last link I gave you had a very likely solution in the very last post on page 7.

Good Luck.

---

### Post by txobie on 2011-07-10
I didn't wipe out the disk.  I think ddrescue clears out everything it its byte by byte copy.  

Questions while ddrescue is running.  In case it wasn't clear earlier.  I do not have Grub.  My Ubuntu is on an external hard disk I boot from.  So I am trying to recover my internal windows drive as it came from Dell.  My mistake was when trying to create a new external Ubuntu drive I deleted my internal partitions and created new Linux ext2 partitions.  

1. Dell has two partitions that are for recovery.  In my previous attempt at fixing my partitions I changed them both to Dell Utility partitions using testdisk.  I think this may have been a mistake.  I'm thinking of not changing anything to begin with.  Does that matter?  I think it will only matter if I wanted to do a Dell recovery.  
2. In my earlier repair attempt.  Once I started windows for the first time it went through a very long repair attempt that failed.  Did that mess up the hard drive so that all my future attempts were pointless?
3. I'm reading the threads pointed out and if I'm following them right, under the section[SIZE=3] [/SIZE][SIZE=3][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE] they are saying to use the commands Westie457 said to use previously.  bootrec.exe /fixboot and bootrec.exe /fixmbr  Maybe those will work if I start from the Windows 7 cd and go right into the command line without windows trying to recover.

I think ddrescue will be running for quite a while so I'll plan my attack.

---

### Post by txobie on 2011-07-10
I think I may have found what I missed.  At the bottom of this page [http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples) is the following.  
**  Recovery of reformatted partition **

 If the partition has been reformatted to another file system (FAT32 formatted as NTFS or vice-versa), 
 
[LIST]
[*] run [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"),
[*] select the hard disk and the partition type
[*] choose Advanced
[*] select the partition
[*] choose Type,
[*] enter the value corresponding to the previous filesystem
[*] choose Boot
[*] choose RebuildBS
[*] List
[*] If you can see your files, choose Write and confirm
[*] In Analyse, choose to rewrite the partition with the correct partition type.
[/LIST]
 Return to [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") main page 

What do you think?

---

### Post by westie457 on 2011-07-10
> **txobie said:**
> I think I may have found what I missed.  At the bottom of this page [http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples) is the following.  
**  Recovery of reformatted partition **

 If the partition has been reformatted to another file system (FAT32 formatted as NTFS or vice-versa), 
 
[LIST]
[*] run [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"),
[*] select the hard disk and the partition type
[*] choose Advanced
[*] select the partition
[*] choose Type,
[*] enter the value corresponding to the previous filesystem
[*] choose Boot
[*] choose RebuildBS
[*] List
[*] If you can see your files, choose Write and confirm
[*] In Analyse, choose to rewrite the partition with the correct partition type.
[/LIST]
 Return to [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") main page 

What do you think?

It is possible that could be your answer. I missed that too.

If that does not work properly you still have the fall-back of the Windows commands. Also as a reminder in the link I sent the very last post has another likely solution. That thread was started late 2007 and this answer came through last week. Sometimes persistence does pay off. The post with the answer is [here]("http://ubuntuforums.org/showpost.php?p=10999954&postcount=61").

Yet another option is if you can remember exactly which partition contained the Dell Recovery and you have a SuperGrubDisk or SGD2 you could use That disk to boot the recovery partition to restore that hard drive to how it left the Dell factory.

A short while ago with the help of Google I found another thread that explains how to repair Windows boot from an Ubuntu LiveCD.

Back to the bit where you said "In my earlier repair attempt. Once I started windows for the first time it went through a very long repair attempt that failed. Did that mess up the hard drive so that all my future attempts were pointless". That probably did not mess up the hard drive. However it certainly messed up something. In hindsight you could have run the recovery again to check if it had actually repaired with the "the operating system reports it has booted successfully" comment. The correct procedure then is to reboot into Windows and see if you were successful or not IE you get to see the Windows logo (hooray) or just a blank screen (boo). With just a blank screen hit Ctrl+Alt+Del at the same time to restart Hitting the F8 key immediately after the POST screen going through the repair options to input those commands to repair the MBR.


There is an extra option that cannot be discussed in the open of the forum. For that you will have to PM me to get the details.

---

### Post by txobie on 2011-07-10
Well, I tried doing the rebuildbs and more but cannot get the drive to reboot normalliy in windows.  So I'm going to give up and reinstall windows.  Thanks to info on ddrescue and testdisk I was able to recover my data so that's most important.  

Thanks for the help.

---

### Post by westie457 on 2011-07-11
> **txobie said:**
> Well, I tried doing the rebuildbs and more but cannot get the drive to reboot normalliy in windows.  So I'm going to give up and reinstall windows.  Thanks to info on ddrescue and testdisk I was able to recover my data so that's most important.  

Thanks for the help.

No problem, always happy to help.

If the reinstall to factory default will not start for you you will need to burn a SuperGrub2 Disk available from here
[http://www.supergrubdisk.org/super-grub2-disk/]("http://www.supergrubdisk.org/super-grub2-disk/") to a CD. Then alter bios settings if necessary to boot from the CD.

The first option in the menu will be the right one to use.
Detect any OS will list all available boot-able partitions. Select the one that will restore and press enter.


Good Luck and Be Happy

---

