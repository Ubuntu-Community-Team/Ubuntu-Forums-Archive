---
title: "unable to start windows xp after ubuntu 7.10 live cd use"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by paulgill on 2010-04-04
i had windows xp and after trying ubuntu 7.10 live cd neither i can start windows xp nor i can use ubuntu 7.10 live cd.

1. "NTLDR is missing. press ctrl+alt+del to restart" message shows up. it simply gives no option to start windows xp or any other os.

2. if i try to boot from ubuntu 7.10 live cd - "error reading boot cd. reboot". massage shows up while i was able to boot from the same cd before without any problem.

3. how can i restore my windows xp back again?

4. right now i am using ubuntu 7.04 live cd without any problem, it works just fine but i need my windows xp back as there are some absolutely important programs that i can't run in linux atall

---

### Post by quinnten83 on 2010-04-04
I don't know what you did, but you messed up your bootloader.
you need an XP install disc and have to perform a fix of your master boot record. I don't know the instructions from the top of my head, so google for fix xp master boot record.

Edit: I think that CD you were using got damaged. Try using a more recent live cd, like 9.10.

---

### Post by NightwishFan on 2010-04-04
Both of those Ubuntu editions are depricated and are no longer supported. Do as the above poster suggests and use a newer edition. You can download Ubuntu here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

To fix the boot of Windows you should use a Windows Recovery CD or a SuperGrubDisk.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by houseworkshy on 2010-04-04
Search for "fixmbr" it is a utility which fixes the master boot record and should be on your windows installation disc.  I haven't used windows for a while so you'll probably find better advise on how to use it via google.  
You would certainly be better off with a more recent Ubuntu, the current long term support one is 8.04.4 lts.  Though the next lts ( 10.04)  comes out this month the 8.04 still has a year of updates to go and as it has been around long enough for bugs to be ironed out and the makers of proprietory drivers to catch up I'd recomend 8.04 as the best bet for a trouble free out of the box experiance.

---

### Post by Gone fishing on 2010-04-04
The live cd will not have done any damage it is more likely that damage was done by hard rebooting.

However, to your problem:

Boot on the Windows CD and choose recover console (I think you need to click r). First I'd simply run ```
chkdsk C:/f
``` have a look at [http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265) if chdsk finds errors then reboot and all shoud be fine.

If not try running the live CD again and running fixboot and fixmbr

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixboot.mspx?mfr=true)

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

You could also have a look at

[http://articles.techrepublic.com.com/5100-10878_11-6031733.html](http://articles.techrepublic.com.com/5100-10878_11-6031733.html)

Once fixed do yourself a favour and try the 9.10 live CD

---

### Post by lkraemer on 2010-04-04
Paulgill,
Go to this website and download Supergrub:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can use a Floppy, CDROM, or USB device to boot from.  Just make
sure your BIOS has CDROM and/or USB Boot Devices available and ENABLED.

Go to this site and read how to use Supergrub:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Just replace the Master Boot Record with the one contained in Supergrub.

You can't boot the Ubuntu LiveCD and run the Windows software as suggested
in "If not try running the live CD again and running fixboot and fixmbr".

BE VERY CAREFUL if you boot the Windows Recovery CDR, because you will
overwrite all your data files you are wanting if you aren't VERY CAREFUL
what you do.  I'll try to find my bookmark and post it when I locate it.

Just use Supergrub, and replace the MBR and you should be up and running.

Here is a link to using the Recovery Console to repair XP.
[http://tech.icrontic.com/articles/repair_windows_xp](http://tech.icrontic.com/articles/repair_windows_xp)

REF: "Getting to the Windows Recovery Console"

You don't need anything except the last two commands, chkdisk & fixboot.
BUT BE VERY CAREFUL because wrong choices in RECOVERY CONSOLE can be the end of your data. 

Here is another posting that is very similar:
[http://ubuntuforums.org/showthread.php?t=1446181](http://ubuntuforums.org/showthread.php?t=1446181)
Posting #4.

lk

---

### Post by paulgill on 2010-04-06
Thanks everybody,


when i get into windows recovery console, it asks me for administrator's password and i do not remember ever signing a password to it, but have tried a few without success. i can't get passed this for now and don't know how to go around it. help please.

---

### Post by IndyGunFreak on 2010-04-06
> **paulgill said:**
> Thanks everybody,


when i get into windows recovery console, it asks me for administrator's password and i do not remember ever signing a password to it, but have tried a few without success. i can't get passed this for now and don't know how to go around it. help please.

Were you accessing your hard drive from the Live CD?  Deleting files, etc..?  The Live CD simply cannot do anything to a hard drive, unless the person using the live CD does so intentionally.  Did you attempt to install, and stopped midway through?

Something isn't adding up.

Also, 7.04 and 7.10 are well past their supported life.. is there any reason you were using a disk as old as 7.10?

---

### Post by mastablasta on 2010-04-06
> **paulgill said:**
> Thanks everybody,
 
 
when i get into windows recovery console, it asks me for administrator's password and i do not remember ever signing a password to it, but have tried a few without success. i can't get passed this for now and don't know how to go around it. help please.
 
 
uh, o... i think it's nothing just enter or 1234. you will have to google this but is not uncommon especially if you ranthe computer as only one user. however it might be that the system already locked down in which case reinstalling windows is the easiets way to go. can you do a repair from Windows live CD? Choosing repair instead of install?
 
If not you are in trouble as you will need to format the drive. Or find another way in getting the fixmbr to run (maybe a system recovery floppy disk if you have one of those...).
 
Things that happened to you were because as one suggested you canceled in the middle of some instalation while in Live Linux session. Another option is that you have some hardware problem (e.g bad cables, bad disk...)

---

### Post by pastalavista on 2010-04-06
I once felt I had a similar problem but what I had really done was disable HDD boot in the BIOS when I enabled CD boot. I replaced HDD boot in the boot order with CD but forgot to add HDD to the boot list after it. Just thinkin'.... recheck BIOS?

---

