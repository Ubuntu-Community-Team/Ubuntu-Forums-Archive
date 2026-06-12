---
title: "World of Warcraft won't work on Lucid Lynx 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by mirrordave on 2010-05-01
I just installed Ubuntu 10.04 Lucid Lynx (the netbook version) on my computer. I just went to try a trial of WoW since I'm actually waiting on my full copy and BC that I just ordered. Can someone help through the process on Lynx? All the ones I saw were for older builds on Linux.

---

### Post by xumuk37 on 2010-05-01
BC (if you mean Bad Company) won't work in ubuntu...

---

### Post by mirrordave on 2010-05-01
> **xumuk37 said:**
> BC (if you mean Bad Company) won't work in ubuntu...

No lol my bad. WoW = World of Warcraft, BC = Burning Crusade (an expansion pack)

---

### Post by Wiebelhaus on 2010-05-01
I'm about to do this , so if I have any problems I'll report back here but basically you just install wine and configure wow via the how to [here]("https://help.ubuntu.com/community/WorldofWarcraft").

---

### Post by Wiebelhaus on 2010-05-01
> **Wiebelhaus said:**
> I'm about to do this , so if I have any problems I'll report back here but basically you just install wine and configure wow via the how to [here]("https://help.ubuntu.com/community/WorldofWarcraft").

Works perfect with vanilla wine (the one in the repositories) No issues.

---

### Post by mirrordave on 2010-05-01
> **Wiebelhaus said:**
> Works perfect with vanilla wine (the one in the repositories) No issues.

lol thanks. I guess I'll have to wait until my game actually arrives and install using the disc. I was trying to get the TryWoW thing to work just to see if the computer could handle it but I can't follow that guideline with TryWoW. Of course I'm an uber-n00b when it comes to Linux ^^' My game should be here on Monday or Tuesday, I'll let you know if I can get it installed then, thanks for the feedback.

---

### Post by nick_geetar on 2010-05-05
Alright wow runs great until i get in the world. Then it bugs. Gives me the whole wine bug report and stuff. It's literally anywhere from 3-10 seconds of loading the game. Any Ideas.

---

### Post by Wiebelhaus on 2010-05-07
Need to see the report , wrap it up and attach it to your post please , thanks.

---

### Post by ngoc on 2010-06-19
Hi,

I might have an issue. Wow starts and load the character but few seconds later, it crashs and says:

> wine: Unhandled page fault on write access to 0x00000000 at address 0x642c40 (thread 0009), starting debugger...


Any ideas?

---

### Post by lkjoel on 2010-06-20
Ok run this
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine wine1.2-gecko wine1.2-dev winetricks wine-doors wine1.2 wine1.2-dbg gnome-exe-thumbnailer playonlinux
```That should fix it

---

### Post by ken631 on 2010-06-20
Why wait for the discs and not just use the installer to d/l the game for you.   Actually its a good idea to run wow under wine with all the keyloggers who want to steal your account and take your gold.   I tried using the installer using wine and it worked however It was on a windows partition with Wubi and it wasn't large enought to download (the installer downloeaded the game could not)but it worked nicely in the Wine C: directory. I tried using by mounting the Windows directory and load WoW that way but it was slow, FPS was really low. 
 
There are actually tutorials on youtube of WoW working in ubuntu with wine. Ventrilo works.

---

### Post by ngoc on 2010-06-20
Hi,

Ubuntu doesn't find the package winetricks and wine-doors.

It's downloading the rest...

Wait and see

But i have new issue from nowhere (I promise :D)
> 
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\data\\World of Warcraft\\Wow.exe" failed, status c0000005


It's come when i do "wine Wow.exe"

---

### Post by lkjoel on 2010-06-20
Just add these lines to your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/wine-doors-dev-team/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main
```
Then redo.

---

### Post by themusicalduck on 2010-06-20
> **ngoc said:**
> Hi,

I might have an issue. Wow starts and load the character but few seconds later, it crashs and says:



Any ideas?

Looking at your screenshot, it looks a bit like how my install looked when it was being run in DirectX mode (with the action bars looking strange).

Have you set WoW to use OpenGL? If you find the World of Warcraft folder in Program Files on the wine C drive, then go to WTF and open Config.wtf in a text editor then add the line ```
SET gxAPI "OpenGL"
``` It'll make it run in OpenGL and most likely run a lot better.

---

### Post by J V on 2010-06-20
Chances are all these problems would be fixed using playonlinux... It even has an automated installation procedure: If it needs something extra it will do it...

---

### Post by ngoc on 2010-06-21
Here's my config.rtf 

> 
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET installType "Retail"
SET locale "frFR"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET hwDetect "0"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "3"
SET movie "0"
SET mouseSpeed "1.25"
SET Gamma "1.000000"
SET showToolsUI "0"
SET accounttype "LK"
SET VoiceActivationSensitivity "0.39999997615814"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MasterVolume "0.20000000298023"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "727"
SET specular "1"
SET groundEffectDensity "24"
SET projectedTextures "1"
SET gameTip "23"
SET timingTestError "0"
SET EnableMicrophone "0"
SET EnableVoiceChat "1"
SET Sound_OutputQuality "2"
SET Sound_NumChannels "64"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET uiScale "0.81999999284744"
SET useUiScale "1"
SET realmName "Krasus"
SET Sound_EnableAmbience "0"
SET watchFrameWidth "1"
SET gxWindow "1"
SET gxApi "opengl"
SET M2UseShaders "0"
SET UIFaster "2"
SET ffxGlow "0"
SET ffxSpecial "0"


---

### Post by lkjoel on 2010-06-21
If any of you wants to install it via PlayonLinux, just add these lines to you /etc/apt/sources.list file:
```
deb http://deb.playonlinux.com/ lucid main
```
Then in a new Terminal (Applications->Accessories->Terminal) window, type:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install playonlinux
```
I hope this helps!

---

### Post by ngoc on 2010-06-21
I get everything.

%wine wow.exe:

> 
wine: configuration in '/home/user/.wine' has been updated.
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\data\\World of Warcraft\\Wow.exe" failed, status c0000005


I still have the dll's error :( it's weird because before i got the game started until getting the character and then few sec later, it crashed. Now nothing.. 

I'm on 64bit

---

### Post by lkjoel on 2010-06-21
Ok, just follow the instructions from my last post, then in a terminal window, type
```
playonlinux
```
Click install, then click on world of warcraft.
Follow the instructions.

---

### Post by ngoc on 2010-06-21
Ho ho

I just remove glrx, glrx-amdccl and restart.

Now, the game start until the crash.

Here is the log until the crash (wine wow.exe):

> 
fixme:advapi:SetSecurityInfo stub
archive Data\frFR\patch-frFR.MPQ opened
archive Data\patch.MPQ opened
archive Data\frFR\patch-frFR-2.MPQ opened
archive Data\frFR\patch-frFR-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\frFR\locale-frFR.MPQ opened
archive Data\frFR\speech-frFR.MPQ opened
archive Data\frFR\expansion-locale-frFR.MPQ opened
archive Data\frFR\lichking-locale-frFR.MPQ opened
archive Data\frFR\expansion-speech-frFR.MPQ opened
archive Data\frFR\lichking-speech-frFR.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed14,0x00000000), stub!
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x39e9e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f358,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0a8,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x140190,0x140090): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f790): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39f790): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x39eef8): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39de50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de88,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
archive data\frFR\agreements.mpq opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39da18,0x00000000), stub!
failed to open Z:/media/data/World of Warcraft/Data/Interface/Icons
failed to open Z:/media/data/World of Warcraft/Interface/Icons
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...


Here is my system:

> Your system : GNU/Linux
Your kernel : Linux 2.6.32-22-generic
System language : en_US.utf8
Your user login : user
Your computer's name : buntu
Your video card : Mesa DRI R300 (R580 724B) 20090101  TCL DRI2
Your distribution : Ubuntu
Your distribution version : 10.04
Wine version installed : wine-1.2-rc4
Wine version used by PlayOnLinux : wine-1.2-rc4

It crashs even i have compiz actived or not.

Nota: i have an ATI X1900 but it says "Mesa DRI R300 (R580 724B)" ??

Thanks for help by the way.

Edit: i do have already wow's folder from windows' installation. I don't need to install again via playonlinux right?

---

### Post by eriktheblu on 2010-06-21
ATI video card? The white minimap is a classic indicator.

WoW should need no modifications to your wine settings. I use it constantly and have never touched PlayOnLinux or winewricks.

I bet the problem is with your drivers.

---

### Post by Mark Phelps on 2010-06-22
> **eriktheblu said:**
> ATI video card? The white minimap is a classic indicator.

WoW should need no modifications to your wine settings. I use it constantly and have never touched PlayOnLinux or winewricks.

I bet the problem is with your drivers.

OP has an ATX X1900 -- there are NO fglrx drivers that will work with this card and recent Ubuntu versions, period.  If they are getting a graphical desktop display, they already have the open source video drivers installed -- and those are the ONLY drivers available that will work with their card and recent Ubuntu versions.

---

### Post by eriktheblu on 2010-06-22
Ouch.

How recent do you mean? Do you think it could work on Hardy?

Even with the best drivers and severe tweaking, my Xpress 200 never equaled it's performance in XP. I eventually got tired of messing with my integrated ATI card and purchased an Nvidia card a while back.

---

### Post by Mark Phelps on 2010-06-22
> **eriktheblu said:**
> Ouch.

How recent do you mean? Do you think it could work on Hardy?
Should work fine on Hardy, might even work OK on Intrepid.  Stopped working early in the Karmic days.

> Even with the best drivers and severe tweaking, my Xpress 200 never equaled it's performance in XP. I eventually got tired of messing with my integrated ATI card and purchased an Nvidia card a while back.
I'll probably do that as well, as I'm now stuck with a "legacy" card and have decided against replacing it -- after seeing post after post after post with folks unable to get their NEW ATI cards to work properly with the fglrx drivers.

---

### Post by ngoc on 2010-06-22
On the Hardware drivers, there is nothing. I can activate Extra visual effect.

What should i do now?

---

### Post by lkjoel on 2010-06-28
Do you have OpenGL properly installed?

---

### Post by lkjoel on 2010-06-28
I just found this link [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

---

