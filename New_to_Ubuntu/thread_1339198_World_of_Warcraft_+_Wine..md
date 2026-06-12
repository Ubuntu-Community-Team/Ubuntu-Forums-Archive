---
title: "World of Warcraft + Wine."
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Absolutnub on 2009-11-27
Hey guys, I'm brand new to Linux and on Ubuntu 9.04 right now.
I installed Wine just before without hassle and now I'm trying to install World of Warcraft.
I've just done the download/install through Blizzard's launcher with Wine, everything went well, and then the troubles came.
The folder's locked most the time, so every time I try I reset permissions (this reoccurs every time I try to start WoW), then I'll get to the start screen; general part that shows the menu, play, options, new stuff etc. I hit play, nothing happens, it all just disappears. I thought at the start it might be the Blizz updater going into action, but that's not showing up on the system monitor at all. So it seems now I can't get to update or anything it just shuts down and as mentioned before, I have to reset permissions each time I do it as it all locks up.
Anyone know what's happening here, or what I'm doing wrong?
If you need kernel information or something, I can grab it as long as I can be told the command to do it.:)

Thanks in advance.

---

### Post by Findarato on 2009-11-27
you might want to do this to provide us with a little more information :

- open terminal
- navigate to /home/USERNAME/.wine/dosdevices/c:/World of Warcraft/
- launch WoW (command => "wine WoW.exe" I think, but I am not sure about the file name)
- Once the program crashes, give us the errors in the terminal :)

---

### Post by Yanno on 2009-11-27
Well,I guess wine is not so stable as you expected.And the World Of Warcraft is such a large game,no doubt the process will crash!I recommend you to install a virtual machine like virtualbox and install Windows in it,then just install and run the game as you did in Windows.

---

### Post by lovemylady on 2009-11-27
[WineHq Games database etc...]("http://www.winehq.org/")

---

### Post by Absolutnub on 2009-11-27
Thanks for the replies guys.
Fin:

~/.wine/dosdevices/c:/World of Warcraft$ wine WoW.exe
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed70,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef6c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f280,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f550,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f54c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efc0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f100,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f49c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x189ec0) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39efc0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f100,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1b0ee8,0x1b0de8): stub
err:heap:HEAP_GetPtr Invalid heap 0x20011874!
err:heap:HEAP_GetPtr Invalid heap 0x2a882874!
failed to open C:/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Killed

Same thing as before I tried reinstalling both Wine and WoW. Resolution changed to game, lots of sounds, but no game image, just a grey desktop. P.S. what does one learn from such details, I'd like to know.. Slowly.. Eventually. ;)


Yanno: Direct download for virtualbox? Or available with apt-get install? I like the latter, doesn't hurt my brain as much.

Thanks again. :)

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]use the wine beta its better and more games run with it! noticed that too wine 1.01 is prety shitty get 1.131 if you didn'T already.. ^^[/COLOR]

---

### Post by Absolutnub on 2009-11-27
I might give an earlier version of Wine a try after. Right now seeing what I can do about Virtualbox and see if that does anything.

---

### Post by 311005901 on 2009-11-27
Another thing you can try before visualization is installing PlayOnLinux, a program that makes Wine really easy.

Just open up Terminal and type:
```
sudo apt-get install playonlinux
```

The program should be under "Applications>Games" and you can install WoW from there.

---

### Post by Grenage on 2009-11-27
If you're going to resort to VMs, you'll be better off with a dual boot to XP or the like.  Games in VMs are usually terrible.

---

### Post by Absolutnub on 2009-11-27
Thanks [311005901]("http://ubuntuforums.org/member.php?u=95587"), will try it while I wait for this.

Grenage - I must stay away from Windows. It irritates me to the point where at least a few years back, I fried my CPU and motherboard via overclocking just to show my hatred of it.
Of course I was migrating and had no use for that comp anymore, but that's not the story I'm sticking to.

---

### Post by Grenage on 2009-11-27
I understand; I once filled a hard drive with jam, just for Windows. ;)

It's really common for people to run WoW on wine (I did a long time ago), so you may find a lot of answers in the [Ubuntu wine]("http://ubuntuforums.org/forumdisplay.php?f=313") forum.

---

### Post by Absolutnub on 2009-11-27
[311005901]("http://ubuntuforums.org/member.php?u=95587"); I'm wondering if it's possible to install the online versions through Playonlinux.
I can download the full version from Blizzard (all my disks are on the other side of the world), and though it seems easier, it's just giving me the option to grab it from disk/DVD. Any chance links/setup downloads can go in there too?

---

### Post by themusicalduck on 2009-11-27
This is a bug that was introduced in the last wow patch - [http://bugs.winehq.org/show_bug.cgi?id=20643](http://bugs.winehq.org/show_bug.cgi?id=20643)

One way to workaround it is to bypass the launcher and just run Wow.exe.

You could make a launcher on the panel or desktop with this as the command ```
wine "/home/*username*/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"
``` (that's assuming you installed Wow in the default location)

you need to replace *username* with your actual username.

Also there's this post on the bugreport which is another workaround > Here is a dirty workaround that allows me to run the game through the Launcher
for now.

Start the Launcher with this bash script:


#!/bin/bash

nohup env WINEPREFIX="/home/sean/.wine" wine "C:\Games\World of
Warcraft\Launcher.exe" &
sleep 1
chmod 770 -v ~/.wine/drive_c/Games/World\ of\ Warcraft
echo "Exiting"
exit 0



You need to change the directory names to match your own, but this should set
the proper permissions to your WoW folder 1 second after starting the
Launcher(you may have increase this if you have a slow computer), and then exit
the script. This should make the game launchable through the Launcher, and
hopefully allow the installation of future patches through the
launcher(hopefully the future patches fix this)

If you want to use the script and need help implementing it then post here and we can help with it.

---

### Post by 311005901 on 2009-11-27
> **Absolutnub said:**
> [311005901]("http://ubuntuforums.org/member.php?u=95587"); I'm wondering if it's possible to install the online versions through Playonlinux.
I can download the full version from Blizzard (all my disks are on the other side of the world), and though it seems easier, it's just giving me the option to grab it from disk/DVD. Any chance links/setup downloads can go in there too?

I'm pretty sure you can. If you've already tried installing through PlayOnLinux's menu, then try this: when you open up the PlayOnLinux program, click on the bottom left of the window and follow the prompts to install the game. :)

[IMG]http://img130.imageshack.us/img130/9089/polt.jpg[/IMG]

---

### Post by lovemylady on 2009-11-27
> **311005901 said:**
> I'm pretty sure you can. If you've already tried installing through PlayOnLinux's menu, then try this: when you open up the PlayOnLinux program, click on the bottom left of the window and follow the prompts to install the game. :)

[IMG]http://img130.imageshack.us/img130/9089/polt.jpg[/IMG]

[COLOR=Magenta]
I already watched for cadega and this crossover **** and both are totally commercial downloaded the trails and things wich work with wine doesn't work with them LoL ..


However does LINUX ONPLAY or however its called again cost something?![/COLOR]

---

### Post by ed-koala on 2009-11-27
Anyone installing WoW since the latest patch is having problems with the launcher.  It's WoW's fault, not Wine's.  WoW made some sort of change and now each time the launcher runs it changes the file permissions and locks the files, making it unable to run.

During the install, this means going in several times and changing permissions back as each part of the update process downloads and launches ... a real pain, but what can ya do?  If you need help how to change permissions let me know.

Also, run the game (once you get it installed) using wow.exe, not launcher.exe (as it'll lock up those permissions, again ... wine might come up with a fix for that, who knows).

I've installed WoW a dozen times lately as I hosed my system getting Karmic, and Windows games, working.  My final solution?  3 tiered - Ubuntu, Wine, and VirtualBox in that order.

Any WoW problems, feel free to ask, I've been around the block with WoW and Wine.

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]then do not play the original WoW.. can't understand people who pay for wow anyway i'd never pay to play just buying premium once or twice when im really interested in but not well forget it ^^ [/COLOR]

---

### Post by Absolutnub on 2009-11-27
Awesome, thanks heaps everyone. Have a few things to try and see how the downloader goes overnight. Hopefully the update process doesn't kill me too much.
In any case, thanks again, shall see how it goes by tomorrow. :)

---

### Post by lovemylady on 2009-11-27
> **Absolutnub said:**
> Awesome, thanks heaps everyone. Have a few things to try and see how the downloader goes overnight. Hopefully the update process doesn't kill me too much.
In any case, thanks again, shall see how it goes by tomorrow. :)


[COLOR=Magenta]What are you talking about o.O?[/COLOR]

---

### Post by Absolutnub on 2009-11-27
Have to download WoW from Blizzard. Takes a while with this connection being zapped by the German guys that live here too. ;)

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]Heh i see, well i never played and will never play WoW.. nono ^^[/COLOR]

---

### Post by Yanno on 2009-11-28
> **Absolutnub said:**
> Thanks for the replies guys.
Fin:

~/.wine/dosdevices/c:/World of Warcraft$ wine WoW.exe
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:advapi:SetSecurityInfo stub
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed70,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ef6c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f280,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f550,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f54c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39efc0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f100,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f49c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x189ec0) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39efc0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f100,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1b0ee8,0x1b0de8): stub
err:heap:HEAP_GetPtr Invalid heap 0x20011874!
err:heap:HEAP_GetPtr Invalid heap 0x2a882874!
failed to open C:/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Killed

Same thing as before I tried reinstalling both Wine and WoW. Resolution changed to game, lots of sounds, but no game image, just a grey desktop. P.S. what does one learn from such details, I'd like to know.. Slowly.. Eventually. ;)


Yanno: Direct download for virtualbox? Or available with apt-get install? I like the latter, doesn't hurt my brain as much.

Thanks again. :)

Why not use UbuntuTweak?It just like Wopti Utilities in windows.You can find softwares you want graphically and download them. To get Ubuntu Tweak,you can google it.

---

### Post by Absolutnub on 2009-11-28
Just might do, thanks Yanno.
Got WoW in, seems installed at least. Now I just have to work out this fatal error I keep getting and throw in the two expansions.

---

### Post by lovemylady on 2009-11-28
[COLOR=Magenta]wich error?


btw already gone to color correction? also for brightness ;)[/COLOR]

---

