---
title: "Can't Uninstall Ubuntu from Dual Boot Vista"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by L-hibou on 2009-04-12
A friend of mine installed Ubuntu onto my Vista Home premium x64 machine and told me all I had to do to uninstall it was to use Add/remove programs in my vista.  However, I tried that and only received a notification saying something called "wubi" was removed.  He had used his disc so I have no copy of a disc for Ubuntu, so I'm unsure of if I need one or not.

I decided to uninstall it after hitting a huge chain of problems in Ubuntu that just got worse and worse. Now I don't know how to both uninstall it completely, give Vista back the space, AND remove it from my boot menu.

I've already tried running a command prompt in my Vista install CD under "Repair my computer" and running the command prompt "bootrec.exe /fixmbr" that my research led me to remove the boot list. However this did not work, despite the command prompt reading that the action was performed successfully. 

I am at a loss here. i plan on reinstalling Vista for a separate issue, however would this return my Vista to its original state and uninstall Ubuntu completely and restore my boot menu? If not, what options would I have even after reinstalling Vista to completely remove the Ubuntu from my machine?

Any help would be greatly appreciated. I'm a complete beginner so it would help me best to be as detailed as possible in any possible solutions.

Thank you,
L-Hibou.

---

### Post by jfbooth on 2009-04-12
Are you sure Ubuntu is still installed?  The 'glory' of Wubi is that it installs Ubuntu 'inside windows'.  Not in a separate partition per se.  Here is a quote on uninstalling a WUBI install of Ubuntu:

"How do I uninstall it?
You uninstall it as any other applications. In Windows go to the control panel and select "Add or Remove Programs", then select Wubi/Ubuntu and uninstall it. You can also use the uninstaller that you find in the installation folder."

[http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)

going to add/remove programs and selecting uninstall results in a pretty quick uninstall.  It may be you think you simply uninstalled Wubi.  It happens fast.

Wubi installs Ubuntu not on a physical partition on your HD but in a huge folder within Windows.  If you do not find such a folder, Ubuntu is probably uninstalled and disk space returned to Vista.

"How does Wubi work?
Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk."

If you have a boot screen that shows Ubuntu as a OS choice, but you know Ubuntu is GONE, you may need to consult with the following:

http://msdn.microsoft.com/en-us/library/aa468626.aspx[/url]

You might want to hold off until you get some more anwers.  I am anything but a Linux expert.

---

### Post by nandemonai on 2009-04-12
Wubi uses the Windows boot menu if I'm not mistaken.

If it's uninstalled yet still showing the option to boot you'll need to edit your c:\boot.ini file and remove the line for Ubuntu.

That's for XP mind you, I've not been able to stomach using Vista long enough to know whether this still holds true.

---

### Post by Craige4107 on 2009-04-12
If you're reinstalling Vista anyway, then just do a full erasure, if you're concerned, before you reinstall Vista.  This will remove everything, including the partitions.  You can d/l utility programs for your specific hd or google for a some type of sw that does this.  I use Acronis, mainly for backing up, but the sw wasn't free.  Good luck.

---

### Post by L-hibou on 2009-04-12
@jfbooth

I have one "ubuntu" file remaining on my "C:\ubuntu". It is full of items still.  I ran the uninstaller in there too, but it is still full of items and I am unsure whether it is safe to delete it. I fear if I do, I may freeze up without the boot info listed in that file and never get into Vista again. 

Nonetheless, I'm not sure if the space still belongs to vista. How would I go and check to see if Vista owns it or if it was partitioned somehow?

Thank you for your response. =]

@nandemonai

Thank you for your response. I'm not sure at all how to remove it from boot.ini., regardless of operating systems. But thank you. 

If anyone knows how to do this in Vista, detailed descriptions on how would be appreciated. 

Thank you all for your responses thus far. =]

---

### Post by L-hibou on 2009-04-12
> **Craige4107 said:**
> If you're reinstalling Vista anyway, then just do a full erasure, if you're concerned, before you reinstall Vista.  This will remove everything, including the partitions.  You can d/l utility programs for your specific hd or google for a some type of sw that does this.  I use Acronis, mainly for backing up, but the sw wasn't free.  Good luck.

I'm going to just back up all my documents manually onto an external HD once I get one. 

So what exactly is meant by a full erasure? Does that mean deleting my "C:\ubuntu" file manually in Vista before reinstalling?

And will Vista return my boot menu and everything back to normal once I reinstall it?

thank you for your response. =]

---

### Post by nandemonai on 2009-04-12
> **L-hibou said:**
> @jfbooth

I have one "ubuntu" file remaining on my "C:\ubuntu". It is full of items still.  I ran the uninstaller in there too, but it is still full of items and I am unsure whether it is safe to delete it. I fear if I do, I may freeze up without the boot info listed in that file and never get into Vista again. 

Nonetheless, I'm not sure if the space still belongs to vista. How would I go and check to see if Vista owns it or if it was partitioned somehow?

Thank you for your response. =]

@nandemonai

Thank you for your response. I'm not sure at all how to remove it from boot.ini., regardless of operating systems. But thank you. 

If anyone knows how to do this in Vista, detailed descriptions on how would be appreciated. 

Thank you all for your responses thus fer. =]

If you can see it in Vista, it's under Vista not a separate partition.

To edit boot.ini (assuming it's still used in Vista) then Start -> Run -> notepad c:\boot.ini

It _should_ look something like this:

```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Of course it would have one line for Vista and one for Ubuntu.

Simple delete the Ubuntu one and save the file (Don't mess with the Vista one obviously).

If Wubi/Ubuntu is not showing in add/remove anymore then just delete the whole c:\ubuntu directory.

Again though I have little to no experience with Vista so this is coming from an XP mindset.

---

### Post by nandemonai on 2009-04-12
> **L-hibou said:**
> I'm going to just back up all my documents manually onto an external HD once I get one. 

So what exactly is meant by a full erasure? Does that mean deleting my "C:\ubuntu" file manually in Vista before reinstalling?

And will Vista return my boot menu and everything back to normal once I reinstall it?

thank you for your response. =]

A clean re-install of Vista would format the drive anyway, thereby removing everything on the disc. If in doubt with my previous post just do that.

---

### Post by L-hibou on 2009-04-12
Thank you for your response. 

I tried the notepad thing, but it reads that the file doesn't exist. Guess it is just an XP thing.

However, it would be good to know that I can still fix this with a reinstallation of Vista.  I already have an updates issue in Vista, so I figure if this is possible, I can just kill two birds with one stone and do a complete reinstall of Vista.

Thank you for your time. Greatly appreciated. =]

---

### Post by jfbooth on 2009-04-12
vista doesn't use boot.ini

[http://msdn.microsoft.com/en-us/library/aa468626.aspx](http://msdn.microsoft.com/en-us/library/aa468626.aspx)

---

### Post by L-hibou on 2009-04-12
Thank you for the link. 
Unfortunately, I cannot access BCDEdit.exe. It flashes a command-prompt looking window at me for a split second then it vanishes.

Thank you for the time though. At least I know why I don't have boot.ini.

---

### Post by jfbooth on 2009-04-13
Are you running bcedit from Start Run or are you first opening a cmd window and then running it?  Try Start, Run, CMD and get a cmd window open to a c: prompt.  THEN run bcedit.

more info on bcedit:

[http://www.vistaforums.com/FORUM/Topic587-9-1.aspx](http://www.vistaforums.com/FORUM/Topic587-9-1.aspx)

---

### Post by L-hibou on 2009-04-13
Thank you for the help! I couldn't get in through command prompt, but I tried out to right click command prompt and run it as administrator and I got in! I see it listed, however I'm not sure how to go about removing it. It shows it as stored in my C:\ubuntu" folder, but I'm afraid to delete that. I'm not sure how to use the command prompts to delete it from my boot menu through bcdedit. 

I would need further assistance in what to do, but this has been a great help thus far. =]

---

### Post by Jakey_TheSnake on 2009-04-13
Small question out of curiosity, why are you bothering with all this if you're going to reinstall Vista anyway? Seems like a waste of time to me.

---

### Post by L-hibou on 2009-04-13
I'm not sure if it WILL get rid of it. I looked up if reinstalling Vista will remove it, and I get mixed results. 

Sometimes, people say that it gets rid of it, other times people say their Ubuntu remained intact. I'm not precisely sure of the differences between their installations, however I still am concerned... 

Yeah, silly, I know, but I figure it's best for me to try to get rid of it first in case I end up like the latter cases. =\ With a reinstalled Vista, and 30 GB off my hard drive from a still-installed Ubuntu. (That doesn't even work anymore. =[ )

In addition, I'm not sure why and how just reinstalling Vista would work. It IS technically a separate operating system, right...? 

Sorry, I'm pretty new, obviously. =\

---

### Post by L-hibou on 2009-04-14
I apologize for posting again so soon, but I ran across a place on my computer that would supposedly tell me if my computer was accidentally partitioned by the Ubuntu installation. I'm not enturely sure if I'm reading this correctly, but it looks like maybe my Vista remained intact, partition-wise at least? I still see C: and my recovery (D: ), but I don't see a third option. So, does this mean that I don't have to worry about partitions?

If so, how do I go about just removing it from the boot menu and restoring my directly-into-Vista boot and remove the ubuntu file from my "C:\ubuntu"?

Or is this setup enough for me to just re-install my Vista and return everything to a normal Vista machine?

Thank you all for your time.

EDIT: Added a screenshot of the folder I'm talking about in Vista. The Ubuntu one. That remains after "wubi" uninstall.

---

### Post by SunnyRabbiera on 2009-04-14
Any reasoning behind dumping Ubuntu?
Personally I take Ubuntu anyday over Vista, I mean yes some hardware and software is not available in ubuntu yet but we have many workarounds.

---

### Post by L-hibou on 2009-04-14
> **SunnyRabbiera said:**
> Any reasoning behind dumping Ubuntu?
Personally I take Ubuntu anyday over Vista, I mean yes some hardware and software is not available in ubuntu yet but we have many workarounds.

Well, I couldn't get my microphone or Webcam to work, I sort of gave up on that and decided to go on without it. Then I wanted some fonts that weren't available in Ubuntu readily (like Lucida), one required me to install Java, which crashed mid-install. THEN, my add remove programs in Ubuntu crashed, then everything went downhill form there. I don't have the time to figure out how to fix all of it, just want to get rid of it. I MAY come back someday, but I was sort of talked into trying it out by a friend. Little did I know how complicated it really was.... Lost of codes and such... It's just not for me. Plus, I grew fast to miss lots of my programs on Vista and such but yeah...... I also didn't like all the smooth font stuff they had. Really hard to read on a laptop screen. 

Also, I MAY have to take it to Geek Squad, and I heard they don't allow Ubuntu or anything to be on the computers they fix. Not sure if that's true but I heard it. =\

But all in all, it's not really for me. ^^;

---

### Post by SunnyRabbiera on 2009-04-14
Hardware is win some loose some, actually the main reason why so many give you codes in thier post as usually its faster to type in a command like sudo apt-get install package then to give out a full explanation of how to install something via synaptic.
Given more time you could have solved most of your issues.

---

### Post by L-hibou on 2009-04-14
> **SunnyRabbiera said:**
> Hardware is win some loose some, actually the main reason why so many give you codes in thier post as usually its faster to type in a command like sudo apt-get install package then to give out a full explanation of how to install something via synaptic.
Given more time you could have solved most of your issues.

Eh, it's just not really for me. I tried looking up help for my issues but there were just so many I didn't know where to start and little bits of it just were talking about things I never heard of and couldn't figure out where to start. I'm looking to uninstall it and just get my Vista back completely. I just hope that I didn't do too much damage, and that my Vista machine still owns all of the space on the computer. I have an update issue in Vista, so I NEED to reinstall Vista anyway. I just need to know will this reinstall remove the ubuntu folder completely and restore my boot menu to what it was before. If so I would give it a shot and report back with my results.

---

### Post by WhiskyChris on 2009-04-14
As you can see in the screenshots you've posted above the physical partitions on your computer remian completely vista's - C: & D: only. What has been explained previously is that wubi installs ubuntu _inside_ windows, and it can be uninstalled just like a normal windows program.

If you have gone through the normal motions of add/remove - ubuntu and it has been removed then it should have gone. Any files left over are normally things that the uninstaller thinks you might want to keep (things like configuration details and what not), so long as there's nothing you actually want (like music/documents you've saved) then your C:\ubuntu folder is safe to delete it you want.

Alternatively reinstalling vista will wipe everything on C: (including C:\ubuntu) so this will also remove any trace.

Hopefully this answers your questions, and we'll hopefully see you back here when you want to reinstall ubuntu again :D

---

### Post by L-hibou on 2009-04-14
> **WhiskyChris said:**
> As you can see in the screenshots you've posted above the physical partitions on your computer remian completely vista's - C: & D: only. What has been explained previously is that wubi installs ubuntu _inside_ windows, and it can be uninstalled just like a normal windows program.

If you have gone through the normal motions of add/remove - ubuntu and it has been removed then it should have gone. Any files left over are normally things that the uninstaller thinks you might want to keep (things like configuration details and what not), so long as there's nothing you actually want (like music/documents you've saved) then your C:\ubuntu folder is safe to delete it you want.

Alternatively reinstalling vista will wipe everything on C: (including C:\ubuntu) so this will also remove any trace.

Hopefully this answers your questions, and we'll hopefully see you back here when you want to reinstall ubuntu again :D

That was my guess regarding my partitions, but i just wanted another opinion to make sure. I'm not the most tech-savvy person in the world. xD Thank you for shedding some light on this for me. :D

When I had to go into my boot thing in the command prompt earlier, it showed the boot for Ubuntu path going into the ubuntu folder. Would deleting the ubuntu folder remove this automatically and restore Vista's automatic boot? Or would I end up freezing my computer at boot and be unable to boot Windows?

I have no configuration or files in my Ubuntu I want to keep. However it's just the boot now giving me concern. I sort of fear deleting it at risk of perhaps freezing my boot loader with it being unable to find the boot option for Ubuntu anymore. 

A may just be paranoid, but bear with me please. It's a new computer and I'm really nervous over it. xD I just need a little more light shed on the boot issue before I can feel safe to delete the ubuntu folder? Or is there a way to delete the item from the boot list in Vista to ensure proper access to vista so I can delete the ubuntu folder with no fear? I otherwise have no way to get into my computer if I mess it up, so yeah....

But it is nice to hear form many sources that a Vista re-installation can also solve the issue. I'd like to get it off first, as I'd be more apt to maybe try Ubuntu again someday if I can get it off and not resort to a Vista re-installation to take it off completely, but if push comes to shove I'll try that.

---

### Post by halitech on 2009-04-14
deleting the folder will not remove the entry from vista's boot menu, you will still need to do that manually. 

If you use WUBI, reinstalling windows will remove ubuntu. if you do a true dual-boot, then depending on how you reinstall, it may or may not remove ubuntu (usually not) and you would have to use vista's builtin disk management tools to remove the partition and format into NTFS or fat32 to be usable in windows. 

Try removing the entry in the windows tool, then reboot and make sure it boots if you want to be cautious. When it works, then delete the c:\ubuntu folder.

---

### Post by L-hibou on 2009-04-14
> **halitech said:**
> deleting the folder will not remove the entry from vista's boot menu, you will still need to do that manually. 

If you use WUBI, reinstalling windows will remove ubuntu. if you do a true dual-boot, then depending on how you reinstall, it may or may not remove ubuntu (usually not) and you would have to use vista's builtin disk management tools to remove the partition and format into NTFS or fat32 to be usable in windows. 

Try removing the entry in the windows tool, then reboot and make sure it boots if you want to be cautious. When it works, then delete the c:\ubuntu folder.

My issue is it didn't show it as a partition in my disk management. It showed it all as NTFS Vista... =\ So does that mean that this was just a remnant that never got deleted? Because I even looked at how much memory Vista thinks it has and it was the exact same number as before installing ubuntu. I believe I have used that wubi, it told me that it was uninstalled. Only issue left is that I cannot remove the boot, as far as I know... I'm not sure HOW to remove anything from the boot itself in Vista.

Thank you,
L'Hibou

---

### Post by halitech on 2009-04-14
with using WUBI you won't see a Linux partition, it installs as a quasi-file system inside windows (basically a loop back filesystem) but the drive will still be ntfs (or whatever format it was previously). the c:\ubuntu "folder" is where the "partition" was created so if WUBI has been uninstalled, you can safely delete the folder. 

Someone gave you the steps previously by going to Start - Run and typing in CMD to get a command prompt and then run the command they gave you (sorry, don't remember it off the top of my head) and delete the lines regarding Ubuntu.

---

### Post by L-hibou on 2009-04-14
> **halitech said:**
> with using WUBI you won't see a Linux partition, it installs as a quasi-file system inside windows (basically a loop back filesystem) but the drive will still be ntfs (or whatever format it was previously). the c:\ubuntu "folder" is where the "partition" was created so if WUBI has been uninstalled, you can safely delete the folder. 

Someone gave you the steps previously by going to Start - Run and typing in CMD to get a command prompt and then run the command they gave you (sorry, don't remember it off the top of my head) and delete the lines regarding Ubuntu.

I had a feeling that was what i had to use, (cmd under admin>bcdedit) however, I'm not sure how to delete it from there. I looked at all viable commands, "/delete" seems the most promising, however I'm not sure how to go about using it, or if it even IS the one I need to use. I fear screwing something up worse if I accidentally delete the wrong thing/mess something up...

I'll edit a screen capture of what I see in a moment.

EDIT: Added screen cap. of CMD

---

### Post by halitech on 2009-04-14
well I can't help you much there, I have only had limited access to using vista and that was months ago and never used the bcdedit program so not sure but if the link they gave you previous has the information, I would read it again to find out what to do. that or just reinstall vista and be done with it.

ps. this is another reason why I don't like WUBI

---

### Post by L-hibou on 2009-04-14
> **halitech said:**
> well I can't help you much there, I have only had limited access to using vista and that was months ago and never used the bcdedit program so not sure but if the link they gave you previous has the information, I would read it again to find out what to do. that or just reinstall vista and be done with it.

ps. this is another reason why I don't like WUBI

Thank you for your time nonetheless. I am being pointed in the right direction I feel so this is good. =]

---

### Post by L-hibou on 2009-04-14
This is officially [COLOR="DarkRed"]SOLVED[/COLOR]! =D I'll now put down exactly what I did so anyone else in this scenario can potentially find a solution: (All this is done AFTER I uninstalled "wubi" and it did NOT remove the start menu boot, but it was not listed in "Add/Remove Programs" under Vista anymore):
[COLOR="DarkSlateGray"]
1: I downloaded a free program called [EasyBCD]("http://neosmart.net/dl.php?id=1").

2: I installed it and ran the program.

3: I clicked on Add/Remove Entries on the left list.

4: I highlighted Ubuntu and hit Delete, and also approved the action when a dialog box showed up asking if I was sure.

5: I restarted the computer and it restarted like it used to.

6: I deleted the C:\ubuntu folder. (This I could not go back on, as it was too big for the recycle bin and had to be automatically deleted. I swallowed my guts and hit delete).

7: Then I restarted again and all my hard drive IS still on Vista as I regained my room, and now my computer starts up like normal into Vista with no boot list.[/COLOR]


That's what I did. Just posting this in case anyone else runs across an issue like this and happens upon this thread.

Thank you all for your help and time though. Definitely pointed me in the right direction in finding out what kind of installation I had and removed my worries on that "*too* quick wubi uninstall". xD

---

### Post by lamda on 2009-04-29
L-hibou man u rock the place! tnx for this gr8 info! i run on Vista Ultimate x64 and it worked 100% smooth!! tnx again bro!

P.S. Ubuntu should let us users know that without the use of third-party Software (EasyBCD) we cannot remove Ubuntu entry from dual boot!!

---

### Post by qamelian on 2009-04-29
> **lamda said:**
> L-hibou man u rock the place! tnx for this gr8 info! i run on Vista Ultimate x64 and it worked 100% smooth!! tnx again bro!

P.S. Ubuntu should let us users know that without the use of third-party Software (EasyBCD) we cannot remove Ubuntu entry from dual boot!!
If Windows PCs always came with real installation media instead of restore images, the third-party software would not be needed. That is not Ubuntu's fault.

---

