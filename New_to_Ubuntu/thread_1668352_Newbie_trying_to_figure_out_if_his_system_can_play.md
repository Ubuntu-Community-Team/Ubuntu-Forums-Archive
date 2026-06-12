---
title: "Newbie trying to figure out if his system can play 3D games with Ubuntu..."
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Trusty Mutsi on 2011-01-16
Hi everyone!

I've been using Ubuntu for about 6 months, but I've been barely using it for more than web browsing.

Now I'm beginning to wonder if I can actually play decent games on it. I tried using PlayOnLinux to use Steam, but when I installed, the Steam icon just shows up at the bottom bar, but does nothing when clicked on. PlayOnLinux also says I don't have 3D accelaration enabled.

Well, I tried using this method to install a driver for my Radeon 9600 video card, but it didn't seem to do anything.

**[COLOR=DimGray]*[SIZE=2]Problem:  Need to fully remove -fglrx and reinstall -ati from scratch[/SIZE]*[/COLOR]**

 [COLOR=DimGray]*[SIZE=2][/SIZE]*[/COLOR][COLOR=DimGray]*[SIZE=2]Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter: [/SIZE]*[/COLOR]
[COLOR=DimGray]*[SIZE=2][/SIZE]*[/COLOR]
[COLOR=DimGray][I][SIZE=2]  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg[/SIZE][/I][/COLOR]So I basically am trying to see what my system can do, why I can't seem to get a driver installed that works, and if I need to upgrade my hardware. I'm hoping to run games like Civ 4 or Civ 5, maybe some 2-3 year old 3D games?

Here's what I have:

867AS Motherboard Specs can be found at: [http://www.sceusa.com/867as.htm](http://www.sceusa.com/867as.htm)
Athlon XP 1700+
Radeon 9600
512 MB RAM
(Kingston ValueRAM 512MB 184-Pin DDR SDRAM DDR 266 (PC 2100) Desktop Memory Model KVR266X64C25/512)

Please keep in mind, I am a complete newb, and have mostly been using "Ubuntu Software Center" to install things I need. I really don't use the terminal much, or even understand how it works.

Thanks so much for any help!

---

### Post by [Snc] on 2011-01-16
> **Trusty Mutsi said:**
> Hi everyone!

I've been using Ubuntu for about 6 months, but I've been barely using it for more than web browsing.

Now I'm beginning to wonder if I can actually play decent games on it. I tried using PlayOnLinux to use Steam, but when I installed, the Steam icon just shows up at the bottom bar, but does nothing when clicked on. PlayOnLinux also says I don't have 3D accelaration enabled.

Well, I tried using this method to install a driver for my Radeon 9600 video card, but it didn't seem to do anything.

**[COLOR=DimGray]*[SIZE=2]Problem:  Need to fully remove -fglrx and reinstall -ati from scratch[/SIZE]*[/COLOR]**

 [COLOR=DimGray]*[SIZE=2]Here is a more aggressive recipe which removes both -fglrx and -ati, and reinstalls the latter: [/SIZE]*[/COLOR]

[COLOR=DimGray][I][SIZE=2]  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg[/SIZE][/I][/COLOR]So I basically am trying to see what my system can do, why I can't seem to get a driver installed that works, and if I need to upgrade my hardware. I'm hoping to run games like Civ 4 or Civ 5, maybe some 2-3 year old 3D games?

Here's what I have:

867AS Motherboard Specs can be found at: [http://www.sceusa.com/867as.htm](http://www.sceusa.com/867as.htm)
Athlon XP 1700+
Radeon 9600
512 MB RAM
(Kingston ValueRAM 512MB 184-Pin DDR SDRAM DDR 266 (PC 2100) Desktop Memory Model KVR266X64C25/512)

Please keep in mind, I am a complete newb, and have mostly been using "Ubuntu Software Center" to install things I need. I really don't use the terminal much, or even understand how it works.

Thanks so much for any help!

so, did you reinstall fglrx?
have you got proprietary drivers enabled? (system->administration->additional drivers)

---

### Post by khelben1979 on 2011-01-16
In my opinion, you can forget about playing Civ4 or Civ5 with that graphic card (Radeon 9600), at least if you were to try this on your Ubuntu system. Of course you can try it, but... I would recommend playing it on a Windows system instead. Upgrading to a better video card would only make sense if it were a Windows system in this case and a low price, because clearly your processor won't be enough for the [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29") application.

Playing games which are less demanding on the hardware, that will be possible if you manage to get [AMD Catalyst]("http://en.wikipedia.org/wiki/ATI_Catalyst") 9.3 working with the provided OpenGL which is needed (it's part of the package). With your present video card, Catalyst 9.3 is the highest version which supports your video hardware.

I can tell that I got pretty desent performance with my Radeon 9800XT together with my Intel Pentium 4 @ 2.8ghz when using an older Linux distribution where [OpenGL]("http://en.wikipedia.org/wiki/Opengl") was working together with the provided AMD Catalyst driver package. Newer version of the [X server]("http://en.wikipedia.org/wiki/X_server") is sometimes not compatible with older versions of the AMD Catalyst driver software and that forces users to use an older version of Ubuntu.

---

### Post by Trusty Mutsi on 2011-01-16
> **'[Snc] said:**
> so, did you reinstall fglrx?
have you got proprietary drivers enabled? (system->administration->additional drivers)

**1.** Should I install fglrx? I'm not even sure what it is. Is it a driver for my card?

I tried finding the linux driver for my Radeon 9600, and all I could find was this:

"http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English"

It's a legacy driver, and it downloads a file called: ati-driver-installer-9-3-x86.x86_64.run

When I run it, I get this message: 

"==================================================
 ATI [[COLOR=blue][COLOR=blue ! important][FONT=inherit ! important][COLOR=blue ! important][FONT=inherit ! important]Technologies[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxquestions.org/questions/#") Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.easCmE"

So I'm kinda at a loss for how to get my graphics card working, let alone 3D enabled.

**2. **I don't have the "system->administration->additional drivers" option. I do, however, have "system->administration->hardware drivers". When I use that, it tells me "No proprietary drivers are in use on this system". And it doesn't list any drivers I can use.

> **khelben1979 said:**
> In my opinion, you can forget about playing  Civ4 or Civ5 with that graphic card (Radeon 9600), at least if you were  to try this on your Ubuntu system. Of course you can try it, but... I  would recommend playing it on a Windows system instead. Upgrading to a  better video card would only make sense if it were a Windows system in  this case and a low price, because clearly your processor won't be  enough for the [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29") application.

Playing games which are less demanding on the hardware, that will be possible if you manage to get [AMD Catalyst]("http://en.wikipedia.org/wiki/ATI_Catalyst")  9.3 working with the provided OpenGL which is needed (it's part of the  package). With your present video card, Catalyst 9.3 is the highest  version which supports your video hardware.

I can tell that I got pretty desent performance with my Radeon 9800XT  together with my Intel Pentium 4 @ 2.8ghz when using an older Linux  distribution where [OpenGL]("http://en.wikipedia.org/wiki/Opengl") was working together with the provided AMD Catalyst driver package. Newer version of the [X server]("http://en.wikipedia.org/wiki/X_server")  is sometimes not compatible with older versions of the AMD Catalyst  driver software and that forces users to use an older version of  Ubuntu.

Okay, so for now we forget Civ 5. I figured as much. I'd still like to see what my machine CAN do ;)

Now we go back to my other question: Where do I get the driver for my Radeon 9600 video card? How do I install it? How do I enable 3D acceleration? Do I WANT fglrx, or is there something else I should use?

I hope my questions make sense. I really appreciate everyone's help.

---

### Post by khelben1979 on 2011-01-17
You got the right version of the Catalyst software, and as it says: your linux kernel version is not supported. However, it should be something which can get fixed if you have **linux-source-2.6.28-11-generic** package installed (the exact name can be a little different, not 100% sure). The reason is because the installer is going to try and build a binary package and it gathers information from the source tree which should be in your Ubuntu system if the kernel sources are correctly installed.

I suspect that some versions of the Linux kernel is not supported by the Catalyst driver package, and in this case you haveto use the open source video driver, and that can be enabled by telling the X configuration file (/etc/X11/xorg.conf) to use RADEON as your video driver. Slower graphics, but it works!

[Ubuntu Wiki X Configuration]("https://wiki.ubuntu.com/X/Config").

---

### Post by mastablasta on 2011-01-17
> **Trusty Mutsi said:**
>  
Now we go back to my other question: Where do I get the driver for my Radeon 9600 video card? How do I install it? How do I enable 3D acceleration? Do I WANT fglrx, or is there something else I should use?

 
FGLRX (Linux Catalyst) are not supported in latest Ubuntu so you are going to have to do with opensource drivers.
 
For starteds (to try what it can do) i would try some quake2 engine based games with native linux support. maybe Smokin' guns? or go to play deb and try if you can run RTCW: Enemy territory or osme other 3D games found there.
 
I have 9600XT. i haven't played arround with games much (especially under WINE), but i know diablo 2 works fine under wine using openGL :-D
 
also some simpler 3D games work nicely. i haven't tried any more complex ones, however i plan to.
 
I wanted to install jDoom (doomsday engine) to try it out with 3D models, but for some reason i am too dumb to do it. the thing didn't work.
 
WINE needs quite a bit of processing so CPU could be your bottleneck.
 
 
My card ran Oblivion on medium-high settings (tweaked medium) on XP, but i am not sure if it oculd do the same in Linux under WINE.

---

### Post by cascade9 on 2011-01-17
You wont get Catalyst 9.3 going with ubuntu 10.10. Even if you sorted out the kernel issues. 

Catalyst 9.3 only supports up to xorg 7.4 (xorg-xserver 1.5.1) and ubuntu has a later version.

---

### Post by khelben1979 on 2011-01-17
Since he is using kernel 2.6.28, that indicates that he most likely are using Ubuntu Karmic.

So the question is, does Ubuntu Karmic support Catalyst 9.3?

---

### Post by cascade9 on 2011-01-17
AFAIK, the last version to support Catalyst 9.3 would have been ubuntu 8.10. E.g.- 

[http://ubuntuforums.org/showthread.php?t=1109768](http://ubuntuforums.org/showthread.php?t=1109768)

---

