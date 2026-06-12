---
title: "System no longer boots up after update"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by bamim2 on 2010-06-03
Please excuse that I'm probably using the wrong terminology for things, but I'll explain the best I can. Please ask more questions if I'm not clear or just don't make any sense at all. I'm running Ubuntu 9.10. This morning the Automatic Update program ran & did its thing & I believe it updated me from version 21 (of the kernel?) to version 22. When it ran I was in the middle of installing & setting up some things so I didn't reboot right away. 

One of the things I was installing was the web browser "Flock", which required that I install the Adobe Flash Player. The instructions on the web site are at the bottom. I did what the instructions say at the bottom, not realizing that it was going to do more than just update my Adobe stuff & now my system won't boot in version 22. It has a bunch of errors as it boots up & then finally it just stops.

I was able to boot to what I guess is my old kernel (?), version 21, so here I am. What can I do to fix this problem with version 22 so I can get back all the work I did to my system?

Thank you to anyone who can help me!!! Here's what Adobe had me do:
Adobe Flash Player Installation instructions via APT          
[LIST=1]
[*]Click the download link and follow the instructions to complete installation
[*]To verify the plugin is installed in Mozilla, launch Mozilla and choose Help > About Plug-ins from the browser menu.
[*]To get the most up-to-date Flash Player in the future, issue the following commands from the Terminal:
[LIST]
[*]sudo apt-get update
[*]sudo apt-get install adobe-flashplugin
[/LIST]
[/LIST]

---

### Post by varunendra on 2010-06-03
You should mention here upto what stage does the boot process reach before it halts.
Also, what is the output of final screen when it halts?

---

### Post by bamim2 on 2010-06-03
What log do I look in to get that info? It would take me an hour to write all of that down by hand, but it must me in a boot log someplace, right? I'm looking through the System Log Viewer program & there (as one but me knows) are a bunch of logs to view. I'm not sure which one has the info that would help though. What log is it in?

Anyway, it displays a ton of stuff on the screen as it boots up now (it didn't used to display anything after Grub) & the last thing on the screen when it stops says something about TTY MIDI or something. But when I press Ctl-Alt-Del it displays a whole bunch more stuff & almost looks like it's going to boot up, then it says "rebooting" or "restarting" & reboots. 

If you let me know what log to get the info from, I'd actually be of some help. Thanks!

---

### Post by varunendra on 2010-06-03
I don't know myself where (& whether) it is logged. I meant the rough stages of booting (loading Grub, loading kernel, loading additional mods/drivers, starting Xserver,...etc.

If the messages are not too fast to read, you may get a rough idea of 'which of these stages have completed without problems', especially noticing the "Failed" (often very few, in contrast to many "OK") notations against each line.

I know that I'm talking more about experimenting than any to-the-point solution, but that's the level I am at!

If loading of Grub & kernel finishes successfully, then maybe booting with minimal configuration could help.
Now call me idiot or ignorant or whatever but I also don't actually remember how to bring up additional boot options of Grub2 (perhaps it is pressing Esc or just 'E' during loading of Grub) but that shouldn't be hard to find. It'll just take a little more search:)

---

### Post by bamim2 on 2010-06-03
Well, things are somehow getting weirder. I tried installing some updates to Firefox, installed some packages to help me try to troubleshoot the problem & when I rebooted everything I did is gone. The updates to Firefox needed to be installed again. The packages I added are gone from my system & I've had to install them again. 

When I boot & choose version 22 (the one with problems) it displays a bunch of things on the screen as it boots, but there are no errors or failures. It just gets to the TyMIDI part of loading & stops. I let it sit there for 20 minutes to see if would time out or something & maybe boot up, but it didn't. 

I tried as you suggested to press 'Esc' or 'e' (I did both, but I'm not sure which one worked) to get some boot options with Grub, but it stops for about 2 seconds & displays some message on the screen (that I don't have time to read) & then keeps going. It stops at a prompt that I can type something in. I typed "ls" & it showed me a list, but then left me at a login prompt. I typed in my username & it asked for my password. I typed in my password & it brought me to a prompt again. I can type in 1 thing & then it starts all over again. It doesn't seem to matter what username I enter, or what command I type, it just keeps going around & around until I reboot. 

Any useful suggestions would be greatly appreciated.

---

### Post by varunendra on 2010-06-03
Sorry about the Esc/'e' thing. As the things have been changed in recent versions, it now is the 'shift key'.
I just installed Lucid in VMware & tried it.

When the PC is booting (i.e., just as grub starts loading), press & hold shift key to bring up the conventional type grub menu showing additional options.
Choose 'Recovery Mode', then in recovery menu you can try different options. I'd suggest to select dpkg (repair broken packages) first.

As it is 2:40 am here, so that's it for now from me.


EDIT: Kick me now, I've been answering so many posts today that I forgot you are using 9.10. Nevertheless, since it also uses Grub2, so the 'shift' key should work the same way.

---

### Post by bamim2 on 2010-06-03
Actually holding down the Shift key doesn't do anything in the version I have (9.10), however Grub boots with the 'Recovery Mode' option all the time. The bad news is that I already tried what you suggested & it didn't help. 

Is there any way for me to remove version 22? or reload the update?

---

### Post by varunendra on 2010-06-05
Is this what you want?
[http://ubuntuforums.org/showthread.php?t=1415143](http://ubuntuforums.org/showthread.php?t=1415143)

You may need to replace packages that depend upon newer kernel.

By the way if it doesn't help, the more practical & smoother option would be to backup your data, & make a fresh install.

To avoid the frustration of re-downloading every package each time you install/reinstall Ubuntu on a system, make using AptOnCD a habit. Use it every time you update/download a package with 'Create a Metapackage' option enabled. You don't need to burn a cd/dvd every time, just save/update the iso. It's the most perfect offline repository alternative known to me.

---

### Post by bamim2 on 2010-06-05
That sounds like a good idea. I'll do that from now on. Thank you for all of your help with this.

Also, I did check out the link & it sounds like what I was asking about. Since I'm not very experienced with this stuff (hence the "Absolute Beginner Talk" category), is "The Packager" that they're referring to The Synaptic Package Manager? If so, I don't see any way to remove version 22 of the kernel in there. If there is a way to do that, I'm going to need more direction, please. 

Other things:
* If I do remove kernel version 22, will it also be removed from the Grub menu? 
* If I remove version 22 of the kernel, will I be able to 'reinstall' it? 
* If so, how?
* If I removing kernel version 22 doesn't remove it from Grub & I am able to reinstall that version of the kernel again, will it show up twice in Grub? 

Is upgrading to version 10 a good option?
Other things:
* Will that wipe out all of my current info?
* Will that change/wipe out all of my current apps & settings?
* What should I do to prepare for that upgrade?
* What things will working? 
* I have an older NVidia Graphics card that took me a LOT'm trying to do.  of fiddling around to get it to work correctly in 9.1. What about my NVidia in version 10?
* What about me using AptOnCD with 9.1 & moving things to 10?
* Any other advice?

I know that's a lot of stuff to ask. Any help would be greatly appreciated.

---

### Post by varunendra on 2010-06-07
Unfortunately, I'm not able to precisely answer most of your questions. But I'll try.


[LIST]
[*]The 'Packager' they're referring **should be** the 'Synaptic Package Manager'. Since alternatives to 'Synaptic' are also available, therefore 'packager' is something like a generic terminology for 'package-manager'. 'Synaptic' is the default one for Ubuntu.
[*]Your newer kernel, if it was installed through 'Update-Manager', **should be** listed in Synaptic as "linux-image<your version>" (where <your version> is the version installed). Since you are able to boot from older version, there should be two similar entries with only the versions being different. Both would be marked as 'installed'.
[*]If you can find an entry like "linux-image-x.x.xx-22-generic" with its size being around 90MB, then it **IS** the kernel image you want to remove. Make sure another similar entry with version being "x.x.xx-21-generic" is also installed- which will be used when you remove version....22. [to remove v22, you'll have to boot v21, find the entry for v22 in Synaptic, then select 'uninstall completely'.]
[*]Removing v.22 won't remove it from Grub list at once, but updating Grub **should**.
[*]You **should be** able to reinstall 22 after successfully removing it, **through** **'Update-Manager'**.
[*]As for displaying twice in Grub issue (or any issue related with correcting entries in Grub-menu), it all should be automatically corrected through this command:```
sudo update-grub
```
[*]There are mixed reactions about upgrading to Lucid (version 10.04). So whether it is good for you or not depends upon your hardware & your needs. You should try its liveCD before installing it.
[*]If you boot kernel ....21, remove kenel v22, run Update-Manager & select v.10.04 from there, then your settings (info) wouldn't be removed. But given your current circumstances, it can be tricky.
[*]If you install 10.04 from cd (if running 'live-session' was satisfactory) then your settings would be removed but it would be a easier transition. [if live-session is ok & you decide to switch to 10.04, I'd suggest to try the above option first (upgrading through 'Update-Manager). Try installing from CD only if the above option fails.]
[*]If you can restore kernel.....21, everything should be working as before. If you upgrade to Lucid, it'll depend.
[*]You can search the forum for support for your NVidia card in Lucid, or you can start a new thread asking the same.
[*]AptOnCD is supposed to create an offline repository for your current version. So it is helpful only when you migrate across machines using similar versions or reinstall the same version. However those packages would successfully install whose dependencies are satisfied on Lucid, but that may require a lot of manual effort.
[/LIST]
My advice:
first- try removing kernel...22, and getting your setup fully functional as before. If successful, then take a backup image of your root (/) partition with partimage (you can use "PING" bootable cd).
This will ensure you can return to the working condition anytime in case of problems.

Then try making a fresh install of Lucid (obviously if you are satisfied with its live session), reinstalling all the applications you need (through synaptic as much as possible) and then use AptOnCD to create offline repository for Lucid.

If, for any reason, you are not satisfied with Lucid, only then retry upgrading your kernel to version.......22. (if something goes wrong again, you can always restore the root partition from the image you made with "PING").

Hope it helps.:)

---

### Post by bamim2 on 2010-06-08
Thank you! This was very helpful. 

I right clicked on "**linux-image-2.6.31-22-generic**" & chose "**Remove Completely**" & rebooted. I've gone back in & found "**linux-image-2.6.31-22-generic**" & was going to install it again & the note says"**You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.**" I'm not sure what that means. I can't find anything that looks to me like a Meta version. Should I just installed this package, is there another package I need to install in addition to this one or in place of this? 

I'm getting close & I'd had to mess things up now. Thank you for all the help!

---

### Post by varunendra on 2010-06-09
> **bamim2 said:**
> Instead, install the** linux-generic meta-package, **which will ensure that upgrades work correctly, and that supporting packages are also installed."

Simply look for an entry named "linux-generic". **It should have already been installed** with installation size being around 32KB. It is actually a _meta-package (not mentioned in its name)- __means- it is not any application or kernel image in itself, but only contains info about certain installed/installable packages and their dependencies_**.**

Find it & right-click on it to see if install/upgrade options are available.

However, I'd again suggest to try it only as a third option. (see my previous post- 1st- try getting it fully functional again with older kernel, then take image; 2nd- try upgrading to Lucid; 3rd- (only if Lucid doesn't work) try upgrading kernel to ....22)

---

### Post by bamim2 on 2010-06-09
Ok, "**linux-image-2.6.31-21-generic**"is where things are currently, now that I've removed "**linux-image-2.6.31-22-generic**". Version 21 works fine except that Grub still shows that "**linux-image-2.6.31-22-generic**" is a possible boot option. I've run the "**sudo update-grub**" comand, but it still shows version 22, although version 22 doesn't show up as installed in Package Manager. 

Package Manager shows that linux-generic is not currently installed though, so right-clicking only shows Mark for Installation & Properties. 

I did install APTonCD though & I'm ready to make a "backup" of version 21 as soon as I can get version 22 out of the Grub list. 

Thanks again for all this help.

---

### Post by bamim2 on 2010-06-09
Ok. I'm not exactly sure what happened, but I'm pretty sure it's me. Version 22 is back in the Package Manager showing installed & 'linux-generic'  now showing that it's installed. I did rerun 'sudo update-grub' & it showed several older versions & version 21 (which I'm currently booted to) as being installed. 

Anyway, version 22 is back. The thing is that when I right click on version 22 & choose "Remove Completely" it only shows that "linux-generic" & 'linux-image-generic' will be removed. It still shows that the headers for version 22 will be left in place. Shouldn't the headers get removed also? 

Also, APTonCD is no longer installed, even though I just installed it & rebooted, now it's gone. I'll install it again....

To summarize: 
I have right-clicked "**linux-image-2.6.31-22-generic**" (now this is highlighted in blue) & choosing **Remove Completely** now shows that it & "**linux-generic**" (this is now highlighted in RED, obviously marking DANGER) will be also removed. I have stopped to await further instructions so I don't make more problems than I've already made.

When I move passed the point of being "more trouble than I am worth" (assuming I am not already passed that point), please just tell me you've had enough of me. I will understand. However, I TRULY appreciate all of your time & help & I AM learning a great deal. THANK YOU!

---

### Post by varunendra on 2010-06-09
> **bamim2 said:**
> When I move passed the point of being "more trouble than I am worth" (assuming I am not already passed that point), please just tell me you've had enough of me. I will understand.
Here's all I can say: lol, lol, lol....... & I feel a bit sorry for you, again..... lol, lol,......
> I AM learning a great deal.That's the prime reason we're all here. We (& later you will) help because 1)it helps us to learn what we don't know, 2)to perfect what we know a little, & 3)to get satisfaction of doing good to what we know perfectly.

I'm here for reasons 1)& 2). But now I really have begun to think that probably I shouldn't have had answered you.:-k Because then some real experienced guy would have had picked it up & maybe could have had it solved by now.
By the way, to me there seem to be only three reasons why you are still trying:
[LIST=1]
[*]You are just trying to honour my efforts,
[*]You like R&D,
[*]You really love your current installation & don't want to lose it.
[/LIST]Now if it is reason 1, I'd say leave it, it's worthless. I do it mostly out of habit. However if it is any of reasons 2 or 3, I'm here as long as you wish - enjoying all the while (after all, it is YOU who is having troubles:lolflag:)

Now we better get to the point.
Now that kernel ver.22 is back, is the current situation any different to that when you made your first post or is it all the same (the boot-fail, errors with 22, etc.)?
If it is same, then take a backup image of your root partition using PING cd and then try upgrading to Lucid through Update Manager.

**I strongly recommend to take the backup image** because it'll give you freedom to try whatever comes to your mind without having to worry about anything getting worse. In any such case, you can always safely revert back to the current situation. (Obviously, It'll be safer to keep the backup on an external media like USB disk or a DVD etc.)

---

### Post by bamim2 on 2010-06-09
Again, thank you for all of this & the humor too. 
Well, I am an actual University educated Electronics Engineer, so R&D is quite near & dear to me. There's a possible #4 & that is I am a gluten for punishment. :mad:

When I try to boot to version 22, it still fails at the same spot (TiMIDI tty or something similar). 

I don't know what PING CD is. Is that what APTonCD does? I'm trying to get APTonCD to write to a blank CD, but that drive doesn't show up as a choice for the destination, only my home directory shows up. What do I need to do to get it to write to the blank disc?

---

### Post by varunendra on 2010-06-09
PartImage is a disk/partition imaging software (freeware) that can handle Linux partitions with compression facility.
PING is just a live CD that holds this software with a user-friendly interface. You can download its iso (25.3MB) from here:
[http://ping.windowsdream.com/ping/doc-2.01/burniso.html](http://ping.windowsdream.com/ping/doc-2.01/burniso.html)

Burn it to a CD then boot your computer from it to take the image of your root partition.

---

### Post by alien878 on 2010-06-09
This may or may not be related....

My system stopped booting with the installation of .22, so you aren't the only one with problems with this version.

I have reset my default kernel in grub2 to .21 (apt-get install startupmanager and run it).  I'll just wait until another version comes out and try again.

btw:  I highly recommend clonezilla to clone the boot partition.

---

### Post by 98cwitr on 2010-06-09
Why are you using such an old kernel? Upgrade to the latest stable version 2.6.34

[https://help.ubuntu.com/community/Kernel/Upgrade?action=show&redirect=UpgradeKernel](https://help.ubuntu.com/community/Kernel/Upgrade?action=show&redirect=UpgradeKernel)

you don't want to upgrade to 10.04?

---

### Post by bamim2 on 2010-06-09
Uhhhmmm, I would say, ignorance. Mostly. Or maybe completely. THANK YOU for any help you could provide me.

I'm using the most current version of the kernel that's listed in my Package Manager. I don't have any "linux-image-2.6xxx" in my Package Manger when I do a search in there, so how do I get them? 

Learning is good. I hate being a bonehead. 

Thanks also to alien878. I would bet it IS related & we've been wasting our time trying to fix a problem that's actually a problem with the kernel or something.

---

### Post by bamim2 on 2010-06-11
> **alien878 said:**
> This may or may not be related....

My system stopped booting with the installation of .22, so you aren't the only one with problems with this version.

I have reset my default kernel in grub2 to .21 (apt-get install startupmanager and run it).  I'll just wait until another version comes out and try again.

btw:  I highly recommend clonezilla to clone the boot partition.

I've used Startup Manager to set my default kernel to .21 also, but Grub still tries to load .22 on startup. What's the trick to getting it to choose .21 automatically? 

Which Clonezilla do you recommend? I have 32 bit AMD & Ubuntu 9.1.

---

### Post by varunendra on 2010-06-11
> **bamim2 said:**
> I've used Startup Manager to set my default kernel to .21 also, but Grub still tries to load .22 on startup. What's the trick to getting it to choose .21 automatically?Post here the contents of:

[LIST=1]
[*]**/etc/default/grub**  (may need to be edited)
[*]**/boot/grub/grub.cfg**  (only for info, DO NOT EDIT!)
[/LIST]


(Self-help tutorials):> Grub2 quick help [here]("http://ubuntuforums.org/showthread.php?t=1302743").
Grub2 complete (& updated) guide [here]("http://ubuntuforums.org/showthread.php?t=1195275").
Grub2 community's official Guide [here]("https://help.ubuntu.com/community/Grub2"). More? [Here]("http://ubuntuforums.org/showthread.php?t=1287602"). 



> **bamim2 said:**
> Which Clonezilla do you recommend? I have 32 bit AMD & Ubuntu 9.1.
Download [[COLOR=Black]clonezilla-live-1.2.5-17-i486.iso[/COLOR]]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_stable/clonezilla-live-1.2.5-17-i486.iso/download")
([sourceforge page]("http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php"))

[Tutorial for using Clonezilla/Partimage live cd]("http://www.dedoimedo.com/computers/free_imaging_software.html").

---

### Post by bamim2 on 2010-06-11
Thank you. 

I just burned PING to CD, booted from it & was going to copy my /root slice. However, after getting to that point in the process I was not clear as to where it would put my /root slice & how big it would be etc. I guess I should break down & actually read the documentation on PING. LOL. 

Since I'm already here, maybe I'll throw a few questions out anyway. Since PING is not going to be able to burn my /root slice to a CD, I will probably have to put it on a USB drive. That being said, here are a few questions:

* Does PING just make one file out of my /root slice or does it do a ufsdump (Solaris UNIX term)?
* Is there a way to know (since I didn't venture passed the point of "what to backup", not on to "where to put it") how big the file(s) will be?
* If I choose a USB drive does it write over what's already on that drive?
* If I choose a USB drive does it give me a choice of where to put it on the drive or just write it to the drive?

Thanks. Now I'm off to read the PING documentation.

---

### Post by varunendra on 2010-06-11
> **bamim2 said:**
> Now I'm off to read the PING documentation.

Instead, read the tutorial (second half- about Partimage) I gave the link of in the previous post.

I didn't know about that tutorial earlier otherwise I would have had suggested 'SystemRescueCD' instead.
Nevermind, the methods & interface are same in both the CDs after Partimage starts. So the linked tutorial should answer most of your questions.


**EDIT:**
1) Partimage or Clonezilla (AFAIK) can not directly save (burn) images to CD/DVD. Therefore it must be saved on a different partition or a separate drive (another attached HDD, USB drive, etc.)
2) It **TRIES **to save the image in **ONE SINGLE FILE**, but depending upon resultant file-size, the image may split into parts as per file-system limitations.
3) The resultant image file **CAN BE compressed **(**None**, **Gzip **(default), **Bzip2 **options are provided before starting the actual process).
4) Resultant file's **estimated size is displayed** after the process starts. **Final size depends** upon how much compressible your data is.
**5) IT DOES NOT OVERWRITE** anything already existing on the destination drive (**WHILE IMAGING**).
6) You have the freedom to choose a pre-existing path to save the image. It MUST BE located on a drive/partition other than the Source drive/partition (the one that has to be imaged)
**7) IT WILL OVERWRITE** everything on the destination drive/partition **WHILE RESTORATION** of an image.

---

### Post by bamim2 on 2010-06-11
Thank you. Will do.

---

