---
title: "Poor performance in games"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by anotherdummhead on 2011-03-03
So i've finally managed to install Kubuntu 10.10 on my new pc, everything works flawlessly, just perfect except for one small thing. 

This is my PC :

MSI P45 Platinum
Intel Core2 Duo E8400 3.0GHz
XFX Radeon 4870 512MB / GDDR5 900MHz / 4.0GHz
Kingston HyperX DDR2 1333MHz 4GB
500GB HDD

Just tried to run WoW, i get about 10 FPS at best, same with the much older Frozen Throne. I'm ran update manager and installed "Additional Drivers", so should i download and install this :

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I had not so pleasant experience when i installed it last time, instead of fixing the performance, i got laggy Kubuntu with overall poor render.

So, any suggestions ? :)

---

### Post by mastablasta on 2011-03-03
remove current one first. yeah you should try to see if it fixes the issues. afterall it has release date: 2/15/2011
 
Also turn on any special effects you might be running as they can suck the life from virutalization. i am guessing you are running it all in wine. did you set it (wine) up propperly?

---

### Post by anotherdummhead on 2011-03-03
> **mastablasta said:**
> remove current one first.
 
Additional Drivers > Remove ? (sry, i'm a newbie :))
This may have been the problem last time, because i installed the latest proprietary drivers without removing these.

> **mastablasta said:**
> Also turn on any special effects you might be running as they can suck the life from virutalization. i am guessing you are running it all in wine. did you set it (wine) up propperly?

Yep, i'm running it up in WINE, WINE's working just fine, instalation went flawlessly. I also tried installing DirectX, but done more damage then helped, i lost all of my desktop effects and spent an hour getting them back.

---

### Post by seawolf167 on 2011-03-03
> **anotherdummhead said:**
> ...
so should i download and install this :

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Aye, I suggest removing any current video drivers you have installed, then installing the suite from AMD.

---

### Post by anotherdummhead on 2011-03-03
So basicaly how do i do that on **K**ubuntu ? 

Additional drivers > Remove ?

---

### Post by mastablasta on 2011-03-03
have a look here: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
 
see the purge fglrx (=proprietary driver) or the fully remove one. use Console to do this. Maybe print out the page. might come in handy later if you need to uninstall/remove the new driver.
 
What i ment is that Wine has plenty extra settings that you can do. some programmes require them.
 
another option would be to use play on linux to help you with the setup.
 
But if you have any special (no standard) Graphics card setup then this is what could be causing it (due to poor drivers).
 
BTW, Open source drivers for this card are no good? Well i guess they didn't catch up yet.

---

### Post by anotherdummhead on 2011-03-03
> **mastablasta said:**
> have a look here: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
 
see the purge fglrx (=proprietary driver) or the fully remove one. use Console to do this. Maybe print out the page. might come in handy later if you need to uninstall/remove the new driver.

Uff that's exactly what i need, thanks man. I'll be using this :

>  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 

and after that install proprietary drivers, right ?
 
> **mastablasta said:**
> What i ment is that Wine has plenty extra settings that you can do. some programmes require them.

Yeah i had a little experiment with skype, msn, yahoo :D  

> **mastablasta said:**
> But if you have any special (no standard) Graphics card setup then this is what could be causing it (due to poor drivers).

I can be more accurate if you can explain to me how can i see which version of drivers i have.

For now i can only tell you that i ran update manager when i installed kubuntu and after that i installed "Additional Drivers", so from my (really really newbie) point i have only source drivers, right ?
 
> **mastablasta said:**
> BTW, Open source drivers for this card are no good? Well i guess they didn't catch up yet.

Yeah they're real slow for games..every game.. :(

---

### Post by mastablasta on 2011-03-03
> **anotherdummhead said:**
>  
and after that install proprietary drivers, right ?

 
yes, this will remove the current proprietary drivers and it should put the open source ones back. then you can try it out with the new version of proprietary drivers. 
 
> 
Yeah i had a little experiment with skype, msn, yahoo :D 

Skype has it's own Linux client. It's behind a lot, but video and sound chat works. aMSN is sort of MSN client for linux. WHile yahoo the most compatible is Pidgin as well as GYache Improved (sort of attemt at yahoo for linux).
 
> 
I can be more accurate if you can explain to me how can i see which version of drivers i have.
For now i can only tell you that i ran update manager when i installed kubuntu and after that i installed "Additional Drivers", so from my (really really newbie) point i have only source drivers, right ?

 
Additional drivers are AMD proprietary drivers from end of Sept. 2010.
Opensource ones were the ones installed before that (they are the default ones). Otherwise drivers in Linux are part of kernel (core). Opensource ones (that are part of kernel) will get quite an update with new Ubuntu version. they fixed plenty issues, though i think mostly with older ATI cards (mobility chips and some others as well).
 
so yeah try to remove these adidtional drivers, purge them form the system and try to install the ones found on ATI site. maybe they fixed these issues you are having. aslo as i said be sure to set up wine propperly.
 
I had a huge lag running Diablo2. couldn't figure out what was causing it. until i noticed it happens after i pressed ALT key. apparently Alt key was connected with something in GNOME. so i disabled that shortcut and suddenly Diablo 2 worked fast.
 
moved to Kubuntu now, but didnt' have time to install Diablo 2 back yet.

---

### Post by anotherdummhead on 2011-03-03
> **mastablasta said:**
> 
I had a huge lag running Diablo2. couldn't figure out what was causing it. until i noticed it happens after i pressed ALT key. apparently Alt key was connected with something in GNOME. so i disabled that shortcut and suddenly Diablo 2 worked fast.
 
moved to Kubuntu now, but didnt' have time to install Diablo 2 back yet.

EDIT : Yes i know about skype, i tried the Windows version, because it's way newer, but i couldn't get it to work properly. Linux version is good, just sucking a lot more CPU than Windows version does.

LOL, i read this sentence 10 times. Kubuntu, Linux overall, is a fantastic system, and best of all, free..damn i hope Linux takes down Microsoft :D

Thanks a lot mate for the advices, i'll try all of this when i come home :)

---

### Post by anotherdummhead on 2011-03-03
So i've installed everything, everything went perfectly but still, POOR !

First thing that i noticed strange was the version of the driver, instead of 11.2 :

If you see properly it's 8, instead of 11...still laggy games :S

---

### Post by mastablasta on 2011-03-04
i am not sure about version. but i tend not to trust this info as it's often wrong even in windows. 
you have desktop effects turned on. did you turn them off before running the game?
Have you tried play on linux?

---

### Post by anotherdummhead on 2011-03-04
> **mastablasta said:**
> i am not sure about version. but i tend not to trust this info as it's often wrong even in windows. 
you have desktop effects turned on. did you turn them off before running the game?
Have you tried play on linux?

No, but i experimented now in WoW, DE have no whatsoever effect on the game performance :)

I've installed winetricks and from there i typed :

> sh ./winetricks droid fontfix fontsmooth-rgb gdiplus gecko vcrun2005 vcrun2008 allfonts d3dx9 dinput winxp

I get this error when trying to install vcrun2008 :

> 
Using native,builtin override for following DLLs: msvcr90
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Executing wine /home/nemacx/.cache/winetricks/vcrun2008-ms09-035/vcredist_x86.exe
fixme:clusapi:GetNodeClusterState ((null),0x32ec24) stub!
fixme:advapi:DecryptFileA "y:\\23e0d105fbc5947ea2c0d246\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:LsaOpenPolicy ((null),0x33f324,0x00000001,0x33f34c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"nemacx" (nil) 0x7addcc (nil) 0x7addd0 0x7addc4 - stub
fixme:advapi:LookupAccountNameW (null) L"nemacx" 0x199478 0x7addcc 0x18e768 0x7addd0 0x7addc4 - stub
fixme:advapi:LookupAccountNameW (null) L"nemacx" (nil) 0x7add98 (nil) 0x7add9c 0x7add90 - stub
fixme:advapi:LookupAccountNameW (null) L"nemacx" 0x1bdd28 0x7add98 0x1c3d88 0x7add9c 0x7add90 - stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
------------------------------------------------------
Note: command 'wine /home/nemacx/.cache/winetricks/vcrun2008-ms09-035/vcredist_x86.exe' returned status 91. Aborting.

And this is an SS of working WoW, still poor textures in game (even on ultra) but i'm hoping to get that repaired soon :popcorn:

---

