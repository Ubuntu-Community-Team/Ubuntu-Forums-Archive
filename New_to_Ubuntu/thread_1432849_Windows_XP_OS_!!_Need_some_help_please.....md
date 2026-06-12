---
title: "Windows XP OS !! Need some help please...."
date: 2010-03-18
forum: New to Ubuntu
---

### Post by fathumthis on 2010-03-18
[SIZE=2][COLOR=Black]I have a problem..... The Windows XP OS wont start when selected and says that the file <Windows root>\system32\hal.dll. file is either missing or corrupt.
I have a recovery disc and would assume that this file could be copied over using recovery console, if I knew how to do it.
[/COLOR][/SIZE] 
[LIST]
[*][SIZE=2][COLOR=Black]Firstly I have to ask if the disc will know which is the partition with the XP[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Black]what exactly should I write in the recovery console, copy and paste would be good :-)![/COLOR][/SIZE]
[*][SIZE=2][COLOR=Black]is it possible to do this copying from the command line which you get with a 'c' at the' load which OS' stage (grub)[/COLOR][/SIZE]
[/LIST]
[SIZE=2][COLOR=Black]
Please, if you are kind enough to help then make it very simple to follow as Im not very good at these more tech tasks

I realise that this has nothing directly to do with ubuntu other than..... if it wasnt for the Jaunty freeze then I would probably not use the XP very much at all!

Regards to all and thanks in advance to anyone that can help
Martin[/COLOR][/SIZE]

---

### Post by Doctor Mike on 2010-03-18
> **fathumthis said:**
> [SIZE=2][COLOR=Black]I have a problem..... The Windows XP OS wont start when selected and says that the file <Windows root>\system32\hal.dll. file is either missing or corrupt.
I have a recovery disc and would assume that this file could be copied over using recovery console, if I knew how to do it.
[/COLOR][/SIZE] 
[LIST]
[*][SIZE=2][COLOR=Black]Firstly I have to ask if the disc will know which is the partition with the XP[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Black]what exactly should I write in the recovery console, copy and paste would be good :-)![/COLOR][/SIZE]
[*][SIZE=2][COLOR=Black]is it possible to do this copying from the command line which you get with a 'c' at the' load which OS' stage (grub)[/COLOR][/SIZE]
[/LIST]
[SIZE=2][COLOR=Black]
Please, if you are kind enough to help then make it very simple to follow as Im not very good at these more tech tasks

I realise that this has nothing directly to do with ubuntu other than..... if it wasnt for the Jaunty freeze then I would probably not use the XP very much at all!

Regards to all and thanks in advance to anyone that can help
Martin[/COLOR][/SIZE]My first question would be, have you changed any hardware around? If you have try to put everything back where it was. Hal contains information about your hardware setup replacing it would not be simple or desirable. If you have not made any hardware changes and can boot to command line (C:/) type, without the quotes, "chkdsk /f" make sure you have a space between chkdsk and the /f.

If the disk scan doesn't fix the problem boot from install disk and do a restore to a point (closest to today) when this problem was not occurring. If a restore is needed do a registry scan and repair and a chkdsk /f scan from the command line afterward.

Once you get up and running do a virus and malware scan. If you don't get up and running download a virus scanning cd image and boot from cd. Something may have damaged you file allocation table (record of file placement and size).

---

### Post by fathumthis on 2010-03-18
Thanks for your help so far, which I havent tried yet.....
I suppose there may be a connection.... I was trying to reload the 'Avira' free antivirus and I got a BSoD since when I cannot restart in XP with this problem....
No I have not changed any Hardware
I will try the chkdsk and see what happens but if that doesnt work then I am not sure about how to do the restore from diskboot...... chkdsk will not affect the Ubuntu instal will it? This is my only connection for now

---

### Post by VernonA on 2010-03-18
I see from Avira's web-site that they have been the victim of a serious spoofing attack (see [http://www.avira.com/en/security_news/fake_anti_virus_solutions_imitate_avira.html]("http://www.avira.com/en/security_news/fake_anti_virus_solutions_imitate_avira.html") for info). Are you sure you didn't download an infected version of the Avira s/w?

---

### Post by sandyd on 2010-03-18
boot up using a ubuntu livecd.
download
[http://www.mediafire.com/download.php?nmwmonzmmn4](http://www.mediafire.com/download.php?nmwmonzmmn4)

go to Places -> (your windows partition, whichever it is)
Open the "windows" folder.
Open the system32 folder.

drag and drop the file you just downloaded into there.

oh, and this is for sp2, but I dont think it matters.

---

### Post by lavinog on 2010-03-18
There should be a copy of all system files in windows/system32/dllcache

---

### Post by fathumthis on 2010-03-18
> **lavinog said:**
> There should be a copy of all system files in windows/system32/dllcache

Doctor Mike said "Hal contains information about your hardware setup replacing it would not be simple or desirable."

Is it possible to just replace the defective file and if so how do I get into the abovementioned cache and then how do I go from there?

I really am not experienced when it comes to it....sorry!

Thanks

---

### Post by fathumthis on 2010-03-18
> **carlee said:**
> boot up using a ubuntu livecd.
download
[http://www.mediafire.com/download.php?nmwmonzmmn4](http://www.mediafire.com/download.php?nmwmonzmmn4)

go to Places -> (your windows partition, whichever it is)
Open the "windows" folder.
Open the system32 folder.

drag and drop the file you just downloaded into there.

oh, and this is for sp2, but I dont think it matters.

Im working on a dual boot so I assume the live cd is not necessary...
downloaded the file
 went to places and this was the box it returned ....
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending           :(

Thanks

---

### Post by fathumthis on 2010-03-18
> **VernonA said:**
> I see from Avira's web-site that they have been the victim of a serious spoofing attack (see [http://www.avira.com/en/security_news/fake_anti_virus_solutions_imitate_avira.html](http://www.avira.com/en/security_news/fake_anti_virus_solutions_imitate_avira.html) for info). Are you sure you didn't download an infected version of the Avira s/w?

I think it was OK as I already had it on but the red box said that my subscription would expire soon and so I clicked on it and chose the free option of the 3 given.

Thanks

---

### Post by lavinog on 2010-03-18
> **fathumthis said:**
> Doctor Mike said "Hal contains information about your hardware setup replacing it would not be simple or desirable."

Is it possible to just replace the defective file and if so how do I get into the abovementioned cache and then how do I go from there?

I really am not experienced when it comes to it....sorry!

Thanks

dll files do not store information...they are system files.
hal.dll gets updated during some windows updates.  During the update process, the old file is saved in case the update fails.
there should be a hal.dll in your dllcache, this should be the most recent, and should be identical to the one in use.
The dllcache is part of the system file protection.  If a system file is modified, SFC checks the file signature, if it doesn't match, it replaces it with the one in the dllcache.  Some malware have been able to override the SFC.
There is some more information on SFC here: [http://support.microsoft.com/?kbid=310747](http://support.microsoft.com/?kbid=310747)

In my experience, some issues prevent you from running safemode, or installing the recovery console...in which case using ubuntu worked out for me.

The trick with using linux is to find all copies of hal.dll
```
find -iname 'hal.dll'
```
You do this in the windows folder, after mounting the partition.
After finding all copies, look at the modification dates, find the 3 most current ones.
do a md5sum on each one...the md5 for the current hal.dll should match one other copy, if not then it is corrupt and should be replaced with the 2nd most recent.

---

### Post by oldfred on 2010-03-18
This thread post #8 solved the issue with the XP repair disk.

[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Then I went back to Recovery Console and ran bootcfg /rebuild (fixes boot.ini which often causes hal.dll errors) and CHKDSK /r (which checks the drive for errors and fixes any).

---

### Post by fathumthis on 2010-03-19
[Sorry lavinog but I cannot mount the windows partition.....]("http://ubuntuforums.org/showthread.php?p=8988013#post8988013")

Post #8 this thread
**"Re: Windows XP OS !! Need some help please....**             
                                                                     Quote:
                                                                      [SIZE=1]Originally Posted by **carlee**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8988013#post8988013")[/SIZE]                 
                 [I][SIZE=1]boot up using a ubuntu livecd.
download
[http://www.mediafire.com/download.php?nmwmonzmmn4](http://www.mediafire.com/download.php?nmwmonzmmn4)

go to Places -> (your windows partition, whichever it is)
Open the "windows" folder.
Open the system32 folder.

drag and drop the file you just downloaded into there.

oh, and this is for sp2, but I dont think it matters.[/SIZE]    [/I]
                                 
Im working on a dual boot so I assume the live cd is not necessary...
downloaded the file
 went to places and this was the box it returned ....
[COLOR=Magenta]DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending[/COLOR]           :sad:"


 9.04 also suggested, in another box, that I do a chkdsk /f which I have now tried (using /r as /f is not permitted) and the result is that it gives up at 33% saying that 'the volume appears to contain one or more unrecoverable problems'

and ref. post # 11 this thread :

                                  **"Re: Windows XP OS !! Need some help please....**             
                                                                This thread post #8 solved the issue with the XP repair disk.

[COLOR=Magenta][http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)[/COLOR]
Then I went back to Recovery Console and ran bootcfg /rebuild (fixes boot.ini which often causes hal.dll errors) and CHKDSK /r (which checks the drive for errors and fixes any)."

I also tried to 'bootcfg /rebuild' ....
and the immediate return was  "Error - ....." ***basically*** unable to scan the disc.... failed _*maybe*_ due to corrupt file system.... ( sorry I cannot remember the exact wording)
I also gave the fixmbr command as suggested in this [COLOR=DarkOrchid][COLOR=Purple]1410696 thread[/COLOR] [/COLOR] but was warned by the system that it was a nonstandard or invalid master boot r. and so might damage the  partition 'something or other'


Going back to 'Doctor Mike' Post #2 this thread...

"Once you get up and running do a virus and malware scan. If you don't get up and running download a virus scanning cd image and boot from cd. Something may have damaged you file allocation table (record of file placement and size)."

Is this an option? Am I clutching at Straws?

Finally I have some sort of ghost type backup on an ext mem that I did a few months ago but I dont know what to do with it..... I think it is Windows deluxe backup or something..... Do I need an operating/working OS to reload from this Backup or maybe it can repair or what ever else I dont know......  Can 9.04 read it or would it load itself... ????? The disc is not connected to the computer so it should be clean, if all this may have been caused by some sort of virus or whatever

Thanks again to everyone for the help and advice....

---

### Post by fathumthis on 2010-03-23
Hello you lovely people out there.....
It's been 4 long days now and all quiet on the suggestions front, so does this mean that I should give up ????? Is there no hope of recovering?
I replied the results to previous suggestions and heard nothing....

I have been looking around, since I have freetime without the XP  :-k, and I found this thread [COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=1424322  [/COLOR]Now, I know Linux and Windows are not the same, before anyone says something, but from post #4 that thread.....  Is chkdsk the same as fsck only without the feedback? If not then is there a corresponding command in RConsole?
I dont know what to do next! I 
Can someone advise.... even if it's only to say 'Give it up and start again'! It's the waiting that's driving me mad. If I could just try something...

I look forward to hearing from one of you
thanks

---

### Post by lavinog on 2010-03-23
> **fathumthis said:**
> [Sorry lavinog but I cannot mount the windows partition.....]("http://ubuntuforums.org/showthread.php?p=8988013#post8988013")


Can you explain why you cant mount the windows partition?
are you getting an error message?

---

### Post by fathumthis on 2010-03-23
> **fathumthis said:**
> 
                                 
......Im working on a dual boot so I assume the live cd is not necessary...
I downloaded the file
 went to places and this was the box it returned ....
[COLOR=Magenta]DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending[/COLOR] 
 9.04 also suggested, in another box, that I do a chkdsk /f which I have now tried (using /r as /f is not permitted) and the result is that it gives up at 33% saying that 'the volume appears to contain one or more unrecoverable problems'
...............

I also tried to 'bootcfg /rebuild' ....
and the immediate return was  "Error - ....." ***basically*** unable to scan the disc.... failed _*maybe*_ due to corrupt file system.... ( sorry I cannot remember the exact wording)

I also gave the fixmbr command as suggested in this [COLOR=DarkOrchid][COLOR=Purple]1410696 thread[/COLOR] [/COLOR] but was warned by the system that it was a nonstandard or invalid master boot r. and so might damage the  partition 'something or other'



I've tried the above so far and got the results as described but the one error you ask for is
[COLOR=Magenta]DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending[/COLOR]
 and
"ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware, In the first case run chkdsk /f on Windows then reboot into Windows twice. The useage of the /f parameter is very important! If the device is a SoftRAID/ FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for nore details."

Sorry to have taken a while to answer but I couldnt copy and past the second so I did it longhand and I'm a slow typer
.......

---

### Post by oldfred on 2010-03-23
As long as there is an error in the NTFS parititon Ubuntu will not mount it. Windows chkdsk is supposed to solve it but you may have to run it multiple times until there are no errors and with whatever the parameter is for your version of windows /r /f ? to make it fix the errors.

---

### Post by fathumthis on 2010-03-23
> **oldfred said:**
> As long as there is an error in the NTFS parititon Ubuntu will not mount it. Windows chkdsk is supposed to solve it but you may have to run it multiple times until there are no errors and with whatever the parameter is for your version of windows /r /f ? to make it fix the errors.

So, from this, I gather that chkdsk may give up and not complete on one occasion and then continue past that point on another occasion! Am I understanding that OK?
I will try another few rounds of chkdsk /r and see if the % improves from the 33% I got last time.
If that works then perhaps I could retry the bootcfg /rebuild that you suggested before.....
and also the hal.dll comparison suggested by mr lavinog.

Thanks for that and welcome are any other suggestions, though I think I'll be busy for a while as the last chkdsk /r took about 2 hours.....!

---

### Post by mastablasta on 2010-03-23
> **fathumthis said:**
> So, from this, I gather that chkdsk may give up and not complete on one occasion and then continue past that point on another occasion! Am I understanding that OK?
I will try another few rounds of chkdsk /r and see if the % improves from the 33% I got last time.
If that works then perhaps I could retry the bootcfg /rebuild that you suggested before.....
and also the hal.dll comparison suggested by mr lavinog.
 
Thanks for that and welcome are any other suggestions, though I think I'll be busy for a while as the last chkdsk /r took about 2 hours.....!
 
 
Funny i also had this happen 2 or 3 weeks ago (also running AviraAntivir) after applying some updates computer rebooted and i go this error. thre is a very good article online with multiple solutions on this. google how to fix hal.dll similar to this one: [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
 
next if you can run chkdsk try running it with another parameter. i don't remember i think it's  /f
you can use both:
 
```
chkdsk /r /f 
```
 
more on commands here:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
 
Otherwise using the winXP cd you can repair it with recovery console. 
 
in my computer things went like this and a couple of reboots were needed (some in safe mode - note i don't have linux on this one).
 
I hear one of updates together with a known antivirus programe managed to screw up computer or crash the system. i think something like this also happened here.
 
The computer just wouldn't want to restar propperly. so next time i managed to somehow get into the windows (and not be in safe mode) i quickly created a restore point (before i turned them off). After that everything works normally as before. i never found out what actually crashed the system. was it avira or MS update or Filezilla (that's when the first system freeze occured) or just too cold computer?!
 
but point is CHKDSK managed to find the error and fix the disk. after that everything worked again. after creating a restore point i also did a virus check which didn't find anything. i was very close to install ubuntu on it (had the cd already in my hand) but i would loose too much data :-)
 
If you can not mount the partition in Ubuntu it may well be that partition table has crashed (also happened to me once after system crash). to repair it you will have to use a special programme which is quite costly. but an older version is available on torrent sites (if you don't mind doing some piracy). maybe it can also be repaired with one of ubuntu partition programmes like gparted. i do not know this....

---

### Post by Doctor Mike on 2010-03-23
> **mastablasta said:**
> Funny i also had this happen 2 or 3 weeks ago (also running AviraAntivir) after applying some updates computer rebooted and i go this error. thre is a very good article online with multiple solutions on this. google how to fix hal.dll similar to this one: [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
 
next if you can run chkdsk try running it with another parameter. i don't remember i think it's  /f
you can use both:
 
```
chkdsk /r /f 
```more on commands here:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
 
Otherwise using the winXP cd you can repair it with recovery console. 
 
in my computer things went like this and a couple of reboots were needed (some in safe mode - note i don't have linux on this one).
 
I hear one of updates together with a known antivirus programe managed to screw up computer or crash the system. i think something like this also happened here.
 
The computer just wouldn't want to restar propperly. so next time i managed to somehow get into the windows (and not be in safe mode) i quickly created a restore point (before i turned them off). After that everything works normally as before. i never found out what actually crashed the system. was it avira or MS update or Filezilla (that's when the first system freeze occured) or just too cold computer?!
 
but point is CHKDSK managed to find the error and fix the disk. after that everything worked again. after creating a restore point i also did a virus check which didn't find anything. i was very close to install ubuntu on it (had the cd already in my hand) but i would loose too much data :-)
 
If you can not mount the partition in Ubuntu it may well be that partition table has crashed (also happened to me once after system crash). to repair it you will have to use a special programme which is quite costly. but an older version is available on torrent sites (if you don't mind doing some piracy). maybe it can also be repaired with one of ubuntu partition programmes like gparted. i do not know this....I also had a problem going father back and not as severe. Problem is not all malware is detectable (when new) and can remove itself to leave no trace of it's start. Mucking with the file allocation table can help hide bad software bits. Some programs have been hiding from ati-virus and taking control. One hint, have you been using more than one ant-virus program at the same time? are you able (after all fixes) to uninstall an ati-virus program completely (checking system manager to be sure) and reinstall. May be an evil genius out there...

---

### Post by Doctor Mike on 2010-03-23
> **Doctor Mike said:**
> I also had a problem going father back and not as severe. Problem is not all malware is detectable (when new) and can remove itself to leave no trace of it's start. Mucking with the file allocation table can help hide bad software bits. Some programs have been hiding from ati-virus and taking control. One hint, have you been using more than one ant-virus program at the same time? are you able (after all fixes) to uninstall an ati-virus program completely (checking system manager to be sure) and reinstall. May be an evil genius out there... I had to completely disable Avira, because it doesn't like to be fully uninstalled (Software manager) and I believe it had been taken over by a sophisticated tool/program etc. I now use avast.

---

### Post by fathumthis on 2010-03-29
> **oldfred said:**
> As long as there is an error in the NTFS parititon Ubuntu will not mount it. Windows chkdsk is supposed to solve it but you may have to run it multiple times until there are no errors and with whatever the parameter is for your version of windows /r /f ? to make it fix the errors.

> **mastablasta said:**
> Funny i also had this happen 2 or 3 weeks ago (also running AviraAntivir) after applying some updates computer rebooted and i go this error. thre is a very good article online with multiple solutions on this. google how to fix hal.dll similar to this one: [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
 
next if you can run chkdsk try running it with another parameter. i don't remember i think it's  /f
you can use both:
 
```
chkdsk /r /f 
```more on commands here:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
 
Otherwise using the winXP cd you can repair it with recovery console. 
 
in my computer things went like this and a couple of reboots were needed (some in safe mode - note i don't have linux on this one).
 ..............


OK then ....
Well I tried multiple, 7 or 8 actually, chkdsk /r and always got the same, a 2 hour or so wait and then at 33% it always failed due to" one or more unrecoverable problem"

so then I started to follow the suggestions on the link [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm) ,which seems to be systematic and well put together thankyou for that, and at each stage got a big NO.....

end result is I got to the part on the list where it suggests a repair install....

and that ended in loosing grub :( and ultimately formatting the partition and reinstalling XP  Wow that was fun... took 6 hours to NTFS format and I had a 5 year old version without SP2 or 3.
But I do have the backup that I did some months ago so after getting ntbackup.exe, and finding out how to get grub back, both using the Ubuntu live CD as I cant get onto the internet with the XP without configuring the router etc., I am back here and have another problem....

I have done the backup recovery, which included system state and everything, and now I cannot start the XP and I don know if it is the backup or the grub that is at fault...
I can mount the XP partition from 9.04 now, and it seems that everything is there from the backup,,,
I note a couple of things....

[LIST]
[*]when I did the recovery the system warned of files that it did not recognise that might destablise but I might expect that from a 5 year old recovery disc so I overrode as it all worked fine when I took the backup.
[*]I now realise that it was not a straight ntbackup that I used but something called Enhanced windows backup and the .exe is a bit bigger ....
[/LIST]
could it just be the grub? the windows partition shows alongside the ubuntu and starts to load but doesnt get to the welcome screen before it flashes a bluescreen, too fast to see, restarts and then offers safemode etc, which also wont start....!
OK maybe its not the grub... :(
In which case it may be the different version of the backup but if I cannot start XP then I cannot recover again using the .exe that imaged the backup, can I?

Suggestions please :oops:

I realise that this has strayed a little from the original theme but the problem for me continues so if it would be preferable that I start a new thread .....

---

### Post by Mustard on 2010-03-29
[OFF TOPIC]

Reading this thread I remember the horrors of fixing Windows installs. The fact that the best tools to fix the problems, cost money, is a huge drawback.

[/OFF TOPIC]

---

### Post by shindou01 on 2010-03-29
> **fathumthis said:**
> OK then ....
Well I tried multiple, 7 or 8 actually, chkdsk /r and always got the same, a 2 hour or so wait and then at 33% it always failed due to" one or more unrecoverable problem"

so then I started to follow the suggestions on the link [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm) ,which seems to be systematic and well put together thankyou for that, and at each stage got a big NO.....

end result is I got to the part on the list where it suggests a repair install....

and that ended in loosing grub :( and ultimately formatting the partition and reinstalling XP  Wow that was fun... took 6 hours to NTFS format and I had a 5 year old version without SP2 or 3.
But I do have the backup that I did some months ago so after getting ntbackup.exe, and finding out how to get grub back, both using the Ubuntu live CD as I cant get onto the internet with the XP without configuring the router etc., I am back here and have another problem....

I have done the backup recovery, which included system state and everything, and now I cannot start the XP and I don know if it is the backup or the grub that is at fault...
I can mount the XP partition from 9.04 now, and it seems that everything is there from the backup,,,
I note a couple of things....

[LIST]
[*]when I did the recovery the system warned of files that it did not recognise that might destablise but I might expect that from a 5 year old recovery disc so I overrode as it all worked fine when I took the backup.
[*]I now realise that it was not a straight ntbackup that I used but something called Enhanced windows backup and the .exe is a bit bigger ....
[/LIST]
could it just be the grub? the windows partition shows alongside the ubuntu and starts to load but doesnt get to the welcome screen before it flashes a bluescreen, too fast to see, restarts and then offers safemode etc, which also wont start....!
OK maybe its not the grub... :(
In which case it may be the different version of the backup but if I cannot start XP then I cannot recover again using the .exe that imaged the backup, can I?

Suggestions please :oops:

I realise that this has strayed a little from the original theme but the problem for me continues so if it would be preferable that I start a new thread .....

I had that kind of problem multiple times before on many desktops at work and I did all sorts of stuff to fix it but it all came to one thing, reformatting the partition, so I ended up using FAT32 for the XP hard drives...weird as it may seem i think maybe NTFS partitions aren't so friendly with windows XP, especially the initial versions...if you want to stick to using NTFS, I suggest replacing or upgrading your windows installation...That's what I did anyway...As I no longer work there, I don't know whether or not the problem still occurs so I cant tell you anything more than that...

Right now I started my own shop and I'm using windows 7 and Ubuntu Lucid Lynx Beta 1 for my laptop and PC...I've never had that sort of problem anymore...So my suggestion would be the following :

- boot with your windows installation cd and try to do a recovery from there like all the others posted ( re-doing the whole thing to resolve your problem can be a hassle I know, but it's either that or do a fresh install on the windows)...
- restore your data and then create a fresh back up cd / dvd...( you might want to consider creating windows easy transfer images if you're going to update to something other than XP )
- update or upgrade your windows version...(if you don't mind piracy, there are many windows xp sp3, even windows 7 images available online from which you can upgrade your windows)
- after upgrading windows, use chkdsk to check disks for error from the newly installed windows
- reboot and update your Ubuntu ( to make sure everything is working )
- reboot and check your windows again
- restore your data from the fresh back up or use the easy transfer wizard if you've upgraded to other than XP...( I upgraded to 7 as it was a lot more stable than XP, I never had a B(lue)S(creen)O(f)D(eath) with 7 )
- don't forget to pray that everything works
- if you updated the XP and it still happens, try to delete the xp partition then re-partition the hard drive before re-installing and trying the whole damn thing from scratch...
- if you use other version of windows ( 7 as i don't recommend vista, delete the partition and re-partition before re-installing as well)
- should the problem persists then maybe your hard drive needs to be replaced...

---

### Post by fathumthis on 2010-03-29
> **shindou01 said:**
> 
Right now I started my own shop and I'm using windows 7 and Ubuntu Lucid Lynx Beta 1 for my laptop and PC...I've never had that sort of problem anymore...So my suggestion would be the following :

- [COLOR=Blue]boot with your windows installation cd and try to do a recovery from there like all the others posted[/COLOR] ( re-doing the whole thing to resolve your problem can be a hassle I know, but it's either that or do a fresh install on the windows)...
- restore your data and then create a fresh back up cd / dvd...( you might want to consider creating windows easy transfer images if you're going to update to something other than XP )
- update or upgrade your windows version...(if you don't mind piracy, there are many windows xp sp3, even windows 7 images available online from which you can upgrade your windows)
- after upgrading windows, use chkdsk to check disks for error from the newly installed windows
- reboot and update your Ubuntu ( to make sure everything is working )
- reboot and check your windows again
- restore your data from the fresh back up or use the easy transfer wizard if you've upgraded to other than XP...( I upgraded to 7 as it was a lot more stable than XP, I never had a B(lue)S(creen)O(f)D(eath) with 7 )
- don't forget to pray that everything works
- if you updated the XP and it still happens, try to delete the xp partition then re-partition the hard drive before re-installing and trying the whole damn thing from scratch...
- if you use other version of windows ( 7 as i don't recommend vista, delete the partition and re-partition before re-installing as well)
- should the problem persists then maybe your hard drive needs to be replaced...

Firstly congrats on your venture :D
I dont want to go through the whole reinstal again that is true :P [COLOR=Blue]but before I knew what I was trying to achieve in the Recovery Console i.e. missing hal.dll[/COLOR] ...
now I dont know what the problem is.... 
So far as I can see the backup was successful and the partition is accessible from 9.04, so it must be without errors, but I cannot boot it from the grub.....
All the tips you suggest will be useful when I can boot the XP

what am I trying to do in RC? or am I missing something obvious?
Thanks for your help

---

### Post by lavinog on 2010-03-29
> **fathumthis said:**
> 
could it just be the grub? the windows partition shows alongside the ubuntu and starts to load but doesnt get to the welcome screen before it flashes a bluescreen, too fast to see, restarts and then offers safemode etc, which also wont start....!
OK maybe its not the grub... :(

If you let the windows cd repair windows automatically, it will remove grub from the bootloader.

You may want to do a disk check with the harddrive manufacturers tools.  There might be a physical problem.
I worked on an old compaq that would bsod at boot up...using the disk check cd from the manufacturer (i think it was seagate) it found a bad sector and relocated it...and windows booted up just fine afterwards.

---

### Post by oldfred on 2010-03-29
It may be worthwhile to run this script as it usually shows missing files or reports errors.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by fathumthis on 2010-03-29
> **lavinog said:**
> If you let the windows cd repair windows automatically, it will remove grub from the bootloader.

OK but what will this achieve? Am I trying to prove that it is grub that is stopping XP from booting?
I lost grub when I did the XP reinstall yesterday and had to use the ubuntu live cd to replace it.....

 I replaced the grub at the _same_ time...
                              as I did the 'backup recovery', I had to do to update the 5year old XP instal that I got from the XP recovery disc, which happily seems to have been successful as I can now view the XP partition from >places>media> and so

I seem to have a perfectly good XP inside the partition ,only I cant boot it!

I dont understand the need to do a repair from RC now

sorry if I'm being dense :oops:

just found your edit lavinog and the new post 'oldfred'

This 'disc checker' is something different from chkdsk or....? Could I download it from their site? where will I find the manufacture details?

I will try the bootchecker if I can.... and post the result

Thanks for suggestions :)
I am doing so many new things and yet I still understand so little

---

### Post by fathumthis on 2010-03-29
> **oldfred said:**
> It may be worthwhile to run this script as it usually shows missing files or reports errors.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x55f5c5eb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    56,243,564    56,243,502   7 HPFS/NTFS
/dev/sda2          56,243,565    78,140,159    21,896,595   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5          56,243,691    72,083,654    15,839,964  83 Linux
/dev/sda6          72,083,718    72,902,969       819,252  82 Linux swap / Solaris
/dev/sda7          77,786,793    78,140,159       353,367  82 Linux swap / Solaris
/dev/sda3          72,903,033    77,786,729     4,883,697  83 Linux

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3E0068080067C60D                       ntfs                                     
/dev/sda3        19b21640-50ea-4974-81f0-002d234453d8   ext3                                     
/dev/sda5        81949c4c-e15c-4d20-b4ce-92d59b24438d   ext3                                     
/dev/sda6        c2c3d370-325b-453c-b26b-9c40ecee86ee   swap                                     
/dev/sda7        1dccb63d-34de-4095-b72b-1493ba2d9912   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=81949c4c-e15c-4d20-b4ce-92d59b24438d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        81949c4c-e15c-4d20-b4ce-92d59b24438d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=19b21640-50ea-4974-81f0-002d234453d8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=19b21640-50ea-4974-81f0-002d234453d8 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=81949c4c-e15c-4d20-b4ce-92d59b24438d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=c2c3d370-325b-453c-b26b-9c40ecee86ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  30.5GB: boot/grub/menu.lst
  30.4GB: boot/grub/stage2
  30.3GB: boot/initrd.img-2.6.28-11-generic
  30.2GB: boot/initrd.img-2.6.28-16-generic
  30.3GB: boot/initrd.img-2.6.28-17-generic
  30.3GB: boot/initrd.img-2.6.28-18-generic
  30.3GB: boot/vmlinuz-2.6.28-11-generic
  30.4GB: boot/vmlinuz-2.6.28-16-generic
  30.3GB: boot/vmlinuz-2.6.28-17-generic
  30.3GB: boot/vmlinuz-2.6.28-18-generic
  30.3GB: initrd.img
  30.3GB: initrd.img.old
  30.3GB: vmlinuz
  30.3GB: vmlinuz.old

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=19b21640-50ea-4974-81f0-002d234453d8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=19b21640-50ea-4974-81f0-002d234453d8

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        19b21640-50ea-4974-81f0-002d234453d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=19b21640-50ea-4974-81f0-002d234453d8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        19b21640-50ea-4974-81f0-002d234453d8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=19b21640-50ea-4974-81f0-002d234453d8 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        19b21640-50ea-4974-81f0-002d234453d8
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=19b21640-50ea-4974-81f0-002d234453d8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1dccb63d-34de-4095-b72b-1493ba2d9912 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  39.3GB: boot/grub/menu.lst
  39.3GB: boot/grub/stage2
  39.3GB: boot/initrd.img-2.6.28-11-generic
  39.3GB: boot/vmlinuz-2.6.28-11-generic
  39.3GB: initrd.img
  39.3GB: vmlinuz
```well there is the result.....

---

### Post by oldfred on 2010-03-29
Your grub points to a swap partition, but that is not the largest problem. 
Extended  partition  linking to another extended partition
is saying your partition table is messed up. 
Somehow when you inserted the windows partition or installed something the partition table was messed up.

I am not the best at solving partition problems. One solution I have seen is testdisk which is in the repositories and can be downloaded or is on most recovery CDs.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Others may know a way with fdisk.

---

### Post by fathumthis on 2010-03-29
> **oldfred said:**
> Your grub points to a swap partition, but that is not the largest problem. 
Extended  partition  linking to another extended partition
is saying your partition table is messed up. 
Somehow when you inserted the windows partition or installed something the partition table was messed up.........


when I did the instal of XP I lost the grub but I used the live cd to get to the forums and found how to put it back but
I have 2 Ubuntu instals... the first was a mistake as I allowed the installer to use the min partition space and so could not use it, but I never got rid of it as its only 2GB and I dont know how :(
when I replaced the grub I used (hd0,2) which is the one I cant use and then I went back and used the same commands
```
grub> root (hd0,5)
grub> setup (hd0)
```but it would not accept the "quit" or "sudo reboot" that I had used for the (hd0,2)

I think that it was after all this that I tried to boot the XP (this is my only computer so I need the internet for the info to fix it...), but I dont imagine that this is what has caused the problems with the Partition table though I dont know with the swap partition....

I'll start to look at the stuff you suggest but if there is a fdisk method that is straight forward enough for a beginner..... :) (though I am making progress, at least in my confidence, if not my compitence :D, thanks to everyones patience. =D> to all !!)

---

### Post by lavinog on 2010-03-29
> **fathumthis said:**
> 

This 'disc checker' is something different from chkdsk or....? Could I download it from their site? where will I find the manufacture details?

chkdsk only checks the filesystem...it doesn't really do any lowlevel disk checks.

Take a look at your harddrive lable...it should say who the manufacturer is there...or you might be able to tell from bios.

Typical manufacturers are: seagate, western digital, maxtor, hitachi, samsung, toshiba.

---

### Post by oldfred on 2010-03-29
This link uses sfdisk to make repairs but you have to manually calculate beginning and sizes.

[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by shindou01 on 2010-03-29
> **lavinog said:**
> If you let the windows cd repair windows automatically, it will remove grub from the bootloader.

You may want to do a disk check with the harddrive manufacturers tools.  There might be a physical problem.
I worked on an old compaq that would bsod at boot up...using the disk check cd from the manufacturer (i think it was seagate) it found a bad sector and relocated it...and windows booted up just fine afterwards.

True, but I don't think the manufacturers issued the software freely, at least not in my country...(only distributors are handed the softwares and they keep it really hush hush....

> **fathumthis said:**
> Firstly congrats on your venture :D
I dont want to go through the whole reinstal again that is true :P [COLOR=Blue]but before I knew what I was trying to achieve in the Recovery Console i.e. missing hal.dll[/COLOR] ...
now I dont know what the problem is.... 
So far as I can see the backup was successful and the partition is accessible from 9.04, so it must be without errors, but I cannot boot it from the grub.....
All the tips you suggest will be useful when I can boot the XP

what am I trying to do in RC? or am I missing something obvious?
Thanks for your help

Thank you...

> **oldfred said:**
> Your grub points to a swap partition, but that is not the largest problem. 
Extended  partition  linking to another extended partition
is saying your partition table is messed up. 
Somehow when you inserted the windows partition or installed something the partition table was messed up.

I am not the best at solving partition problems. One solution I have seen is testdisk which is in the repositories and can be downloaded or is on most recovery CDs.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Others may know a way with fdisk.

maybe you ought to try these fathumthis....

---

### Post by lavinog on 2010-03-30
> **shindou01 said:**
> True, but I don't think the manufacturers issued the software freely, at least not in my country...(only distributors are handed the softwares and they keep it really hush hush....

Not really, just look in the download sections of their sites...for instance seagates seatools can be downloaded here:[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD) (the dos version is a bootable disk)

---

### Post by fathumthis on 2010-03-30
Thanks for your continued help.... I am watching and have started to  read about the Partitioning etc and have 'testdisk' already, although I  couldn't find it at >Software Sources>Ubuntu Software but rather  in >Synaptics package manager....... but I have not the time at home  maybe until tomorrow evening to try it all out (if I have it sorted in  my head by that time :) )

regards to all

---

