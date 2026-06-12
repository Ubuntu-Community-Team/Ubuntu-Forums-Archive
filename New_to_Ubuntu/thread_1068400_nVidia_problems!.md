---
title: "nVidia problems!"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Toshibawarrior on 2009-02-12
Hello everyone! 

I might have post on the wrong section, but I'm desperate for answers, and I hope you're kind enough to read my post (which might become rather long).

First off, I'm installing Ubuntu on my best friend's computer, and she's very excited about it, and I promised her I will Ubuntufy her computer, and I CAN't fail.

Anyway, her computer is an **eMachines W3052 with an AMD Sempron 3000+, 512MB of RAM, 120GB HDD, and a darn nVidia GeForce4 MX integrated GPU**. Everything works in Ubuntu Intrepid Ibex (8.10) including the onboard card reader!!...except the video card. 

I have a Dell Dimension 4600 with an nVidia GeForce 440 MX card and it works very nicely with all Ubuntus (704-8.10). But when I installed the proprietary drivers on that eMachines computer, the darn card keeps pushing the display into a very low resolution. The computer can support up to 1024x768 or more but the only available resolutions are 640x480 and 320xsomething...

I've been trying to fix this for 2 days now, and I'm very frustrated. Usually nVidia cards work with the proprietary drivers for me, but this computer wants war.
[B]
WHAT I'VE TRIED SO FAR:[/B]

-I've added some resolutions other than the ones I specified above to xorg.conf on the display subsection and nothing happens.

-I've installed the drivers using EnvyNG and the Hardware Drivers tool and nothing happens (the driver (96) installs fine and then the crappy-resolution-madness begins).

- When I go to Preferences>Screen Resolution only 2 very low-res options are available.

- I've tried nvidia-settings and it's no help, it only allows me to use those 2 resolutions and nothing else, even if I add another resolution manually. I did manage to get the 1024x768 resolution, but the driver kept recognizing the monitor as a 640x480 monitor and everything look humongous! I had to move the cursor to the ends of the screen to scroll around the desktop, and it was horrible.

- I've tried to install the drivers from the nVidia website and it says that it can't continue the installation blah, blah. Even in command-line mode (CTRL+ALT+F2)

- I made a fresh install of Hardy Heron and it was the same problem.

- I've cursed and yelled at the computer numerous times.

What's bothering me the most is that when I try to click something the window moves around. For example, if I click on the "Close" button on the bottom of the window the mouse clicks something above it, because the windows move on each mouse click. That CAN'T be normal.

So to be clear: I'm using Ubuntu Intrepid Ibex 8.10 with the proprietary drivers on that computer and it has an nVidia GeForce4 MX Integrated GPU.

Right now it's 10:36pm and I'm exhausted, so I hope someone replies to this post and helps me. I'm posting right now from my laptop and I'm going to sleep in a few minutes, so any ideas, suggestions or fixes that you may have are more than welcome!

That computer's owner is not only my best friend, she's the cousin of the girl of my dreams and they believe in me, so I really want to go through this in piece.

Please note that I'm NOT a Linux noob, but when it comes down to compiling and tweaking intricate settings I'm kinda slow, so please be as simple as possible.

Thanks in advance! I'll be very grateful to all!

---

### Post by RomeReactor on 2009-02-12
Hi. Did you try running XFIX from the recovery mode? have you tried with another monitor to see if the problem is specific to the one the machine currently has?

---

### Post by Toshibawarrior on 2009-02-12
Thanks for the quick response. 

I tried XFIX and it reconfigured my xorg.conf and resolution nicely, but it disabled the nVidia driver therefore I couldn't use Desktop Effects. 

And as of right now I don't have any other monitor to test. But that's a pretty good suggestion. I'm using my Dell's (which uses Ubuntu Intrepid too) monitor right now; the computer's real monitor is on my friend's house, and I'm supposed to give it back to her tomorrow...and I really want to deliver it working 100%. If I can't find any other solution I might have to test it with her monitor.

Thanks again and keep the ideas coming! 

(Now I'm really going to sleep, I'll check back tomorrow morning, but don't stop posting!)

:)

---

### Post by Toshibawarrior on 2009-02-13
BUMP?...I still need help on this, and my deadline is almost up...:(!

---

### Post by overdrank on 2009-02-13
> **Toshibawarrior said:**
> BUMP?...I still need help on this, and my deadline is almost up...:(!

One issue maybe the amount of memory that is shared with the integrated nvidia graphics. You may check in bios to see if you can increase the amount shared.

---

### Post by Toshibawarrior on 2009-02-13
Hi! Thanks for your reply! Sadly that didn't work, because those settings are grayed-out on the BIOS. I went to Advanced Chipset Settings/Options and everything that had anything to do with video was grayed out, 

It had something that said AGP Aperture and it was set and grayed out, and something else called Frame Buffersomething and it was also grayed out.

I still need help on this! :'(

---

### Post by avtolle on 2009-02-13
I don't have the link, but IIRC, in the release notes for 8.10 there is a discussion of "legacy" drivers for nVidia not being supported in 8.10 (including 96), and the system defaults to the nv driver (open source). Go to [www.ubuntu.com](www.ubuntu.com) and look for the release notes for more information.

---

### Post by 4Orbs on 2009-02-13
You need to install the nvidia 96.43.10 beta driver which is available [ON THIS PAGE.]("ftp://download.nvidia.com/XFree86/Linux-x86/96.43.10/") Right click on the pkg0 version and "save link as" to your desktop. Then follow [THESE INSTRUCTIONS]("http://ubuntuforums.org/showthread.php?t=971103") to compile and install the driver, being sure to substitute 96.43.10 for 96.43.09

Before installing the driver, you need to deactivate whatever you have now in the Hardware Drivers, then uninstall EnvyNG.

After you compile and install the beta driver, you should be good to go. But don't try to activate the driver with the Hardware Drivers tool, because its already activated (even though the Hardware Drivers tool says it isn't).

---

### Post by Hospadar on 2009-02-13
you might try having nvidia ignore the edid (monitor info) sent by your laptop, it might be mis-recieving it, and garbling stuff up in the process.
There might be a graphical way to do this, but I kinda doubt it

Here's nvidia's page describing xorg.conf options:
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-b.html)

As per those options, maybe try adding ```
Option "UseEDIDDpi" "FALSE"
``` to the device or screen section of your /etc/X11/xorg.conf

Make sure you backup the file first, and after you change it, you'll need to restart the xserver (or your machine).  If it dies, you can Ctrl-Alt-F1 while ubuntu is starting up (or any time thereafter) and get to a terminal and restore your backup ```
sudo cp /etc/X11/whatever.yourbackup.was /etc/X11/xorg.conf
```

There may be some other useful options in that readme I linked you, take a look around.

Also perhaps:
Option "ModeValidation" "NoEdidModes"

Scroll down to the edid section, there's a few others.  There's also some depricated ones you might need since you are using an older version of the driver.

---

### Post by Toshibawarrior on 2009-02-13
> **4Orbs said:**
> You need to install the nvidia 96.43.10 beta driver which is available [ON THIS PAGE.]("ftp://download.nvidia.com/XFree86/Linux-x86/96.43.10/") Right click on the pkg0 version and "save link as" to your desktop. Then follow [THESE INSTRUCTIONS]("http://ubuntuforums.org/showthread.php?t=971103") to compile and install the driver, being sure to substitute 96.43.10 for 96.43.09

Before installing the driver, you need to deactivate whatever you have now in the Hardware Drivers, then uninstall EnvyNG.

After you compile and install the beta driver, you should be good to go. But don't try to activate the driver with the Hardware Drivers tool, because its already activated (even though the Hardware Drivers tool says it isn't).

The situation went from bad to worse...I did everything you told me to, and now I have crappy resolution AND not a single window border or tooltip. The borders are gone and the tooltips (and Cairo Dock) show as a big light brown square...What is going on here?...

I read the release notes and it says the Legacy stuff will not be supported...but I have a Dell with a GeForce 440 MX and it runs fine :(!!!...

I'm even more frustrated now...

---

### Post by 4Orbs on 2009-02-13
First of all, did you see a green nvidia logo while booting up after compiling and installing the beta driver? If you did, then the install worked. The disappearing window borders suggest to me that you still have the desktop effects enabled. If you disable the effects, for now, the window borders should reappear. If the driver install was successful you should be able to change your screen resolution as you normally would.

---

### Post by Toshibawarrior on 2009-02-13
> **4Orbs said:**
> First of all, did you see a green nvidia logo while booting up after compiling and installing the beta driver? If you did, then the install worked. The disappearing window borders suggest to me that you still have the desktop effects enabled. If you disable the effects, for now, the window borders should reappear. If the driver install was successful you should be able to change your screen resolution as you normally would.

Nope...screen resolution options were still cut down to 2: 640x480 and 320x240... 

Here's my xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@palmer)  Thu Jun 26 06:22:40 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

I don't know where to add the options that someone mentioned above me...And I didn't see any logo...the xorg.conf had the NOLOGO set to True. Right now I uninstalled the drivers you told me because the resolution was crappy and the effects were null...so I'm back to the Hardware Drivers tool version...:(!

---

### Post by 4Orbs on 2009-02-13
When you did the beta driver installation, did you answer yes to all the questions when it was compiling the driver? Does the nvidia settings tool show any options for screen resolution (even if the wrong ones)? If so, you need to just stay away from the Hardware Drivers tool because it doesn't work with the beta driver. If the driver installation was successful you will use only the nvidia settings tool, and probably edit the xorg.conf file to add your preferred resolutions.

---

### Post by Toshibawarrior on 2009-02-13
> **4Orbs said:**
> When you did the beta driver installation, did you answer yes to all the questions when it was compiling the driver? Does the nvidia settings tool show any options for screen resolution (even if the wrong ones)? If so, you need to just stay away from the Hardware Drivers tool because it doesn't work with the beta driver. If the driver installation was successful you will use only the nvidia settings tool, and probably edit the xorg.conf file to add your preferred resolutions.

Ok, I uninstalled everything again and reinstalled the BETA driver you pointed me to, and now it's a bigger disaster...I have to reformat everything and start over...Maybe I omitted something and something was left behind and ran over by the BETA drivers...:'( I guess I'll make a clean install...Don't stop replying! ;)!

---

### Post by 4Orbs on 2009-02-13
Installing the beta driver doesn't automatically fix the resolution. But it is the first, most important step. Are you sure the beta driver really installed? If it worked, you should be able to open the  nvidia settings manager and see some options (even if they are the wrong options). You should have desktop effects turned off before doing anything else.

---

### Post by 4Orbs on 2009-02-13
OK, I'm guessing that you just did a fresh re-install of Ubuntu. If that's correct, then:
1. Don't change any settings other than disabling the desktop effects. Leave the resolution as-is if it is sufficient enough to work with. But do the updates so you'll have the most recent kernel.
2. Go through the beta driver install process answering yes to all the questions it asks.
3. Come back here and tell me what happened.

---

### Post by 4Orbs on 2009-02-13
Is this a wubi install of Ubuntu, or a physical install on real partitions?

---

### Post by 4Orbs on 2009-02-13
I put the whole how-to on one page that will hopefully make it more understandable.

[Install nVidia Legacy beta driver on Ubuntu 8.10]("http://guitarchasers.org/guchmain/archives/290")

---

### Post by Toshibawarrior on 2009-02-13
Thanks a ton 4Orbs! I went to her house and tried the drivers with her monitor, etc...but nothing worked (Her internet connection was down, so you can imagine the pain it was to get packages...I had to move them from the Intrepid partition to the Hardy one...)...In fact I did a fresh install of Hardy and everything was the same. So I took the computer back with me and I'm going to make a fresh install of Intrepid (deleting all partitions and stuff). I always make fresh installs on partitions as God wants us to :p!...I don't like nor do I endorse Wubi or Virtual Machines...

I guess I'll do everything tomorrow...

As for right now, she told me that she could buy a new video card in case that GPU was too hard to configure...so which video card is nearly perfect for Linux?...I'd like a simple and inexpensive card that can run Compiz and preferably be easy to install/configure. I really want that computer to run Ubuntu and work smoothly and as problem-less as possible.

Thanks again for everything! I'll post back my findings tomorrow! :)

---

### Post by RomeReactor on 2009-02-13
> **Toshibawarrior said:**
> As for right now, she told me that she could buy a new video card in case that GPU was too hard to configure...so which video card is nearly perfect for Linux?...I'd like a simple and inexpensive card that can run Compiz and preferably be easy to install/configure. I really want that computer to run Ubuntu and work smoothly and as problem-less as possible.

Hi again. For the moment, nVidia cards seem to work best; anything from the 6000 range and above will work even with the newest drivers--my system has a 6200, and Compiz works very well, even playing 720p video while the effects are on, and it's a moderately adequate (albeit low-end) gaming card.

---

### Post by Toshibawarrior on 2009-02-13
> **RomeReactor said:**
> Hi again. For the moment, nVidia cards seem to work best; anything from the 6000 range and above will work even with the newest drivers--my system has a 6200, and Compiz works very well, even playing 720p video while the effects are on, and it's a moderately adequate (albeit low-end) gaming card.

Thanks! I'll take a look around my local computer store and check nvidia cards then...She's not into gaming or high-end graphics, so any card would do as long as it plays nice with Ubuntu. :)!

I'll give reinstalling the drivers a whirl tomorrow, but if that doesn't work then I'm off to the store to check prices and let her know.

Thanks again man! ;)!

---

### Post by Toshibawarrior on 2009-02-14
Ok, new problem...It turns out I can't make a fresh install of Intrepid...I've been trying all afternoon long and it gets stuck at 76%, when it says "Installing System" and "Copying System Files (Less than a minute remaining)"...It just gets stuck there and there's no way to do anything...except push the power button until the computer turns off.

Does this have anything to do with me installing multiple drivers, or making 2 partitions, one for Hardy and one for Intrepid?.....

I've had to turn it off violently a few times...

The CD integrity check went fine without erros and the Memtest finished without errors too...So what does this mean?...Does it mean I have to reinstall WIndows on this thing?...:(

I feel like a total noob...:(

---

### Post by Toshibawarrior on 2009-02-14
Problem solved! I had to rewrite the whole partition table and not just the partition where Intrepid was sitting...I had to wipe the RECOVERY Partition that eMachines stuck in there, so I hope I don't need that.

Now I'm off to follow 4Orbs nice guide to install these cursed drivers.

;)!

---

### Post by oldsoundguy on 2009-02-14
8.04 works better with NVidia right now and since it is LONG TERM SUPPORT, you should consider installing IT vs 8.10 (Envy (the NVida 3rd party installer) supports 8.04 with the EnvyNG in your repositories, where as it does NOT support 8,10)

I am in the process of doing just that on 3 desktop units as I want the screen rotate feature in order to do full page displays (portrait) and 8.10 does not allow that for some stupid reason.

---

### Post by 4Orbs on 2009-02-14
I agree that 8.04 may be a better choice for some people, mostly because it is hassle-free compared to 8.10. In my case, however, 8.10 with the nvidia beta driver is an improvement over 8.04, most noticeable with games using wine, that Ibex is worth the extra effort. If you want easy and never have to mess with it, then choose 8.04 Heron. I'm looking forward to the Jaunty release and hoping things get better with nvidia legacy drivers. Maybe I should get a new graphics card?

---

### Post by Toshibawarrior on 2009-02-14
WHOO HOO!!!!!!!!! SUCCESS!!!!!!!!!! partially.....................

I followed your (4Orb's) guide and I finally got the freaking driver working and with tons of available resolutions...

But I have one problem...

When I start up Ubuntu window borders are missing and every pop-up or tooltip (including Terminal output) is blank...Just a huge sqyare in the place where said things were supposed to be.

So...I went into the Terminal and typed: ```
metacity --replace
``` And it worked...but I don't know if I'll be able to use COmpiz effects then...Each time I reboot the computer the blank-madness starts...

What do you guys suggest?...

Thanks for all your help!

P.S.

I don't like Hardy very much because it's kinda problematic with power management in some computers...For example my laptop got up to 50+ C degrees with it...while it feels ice-cold with Intrepid...

---

### Post by 4Orbs on 2009-02-14
You might try installing the compiz fusion icon, which provides a few options that seem to fix some people's problems. And maybe install Emerald theme manager and use the fusion icon to choose Emerald as the default theme manager. Don't know if this will work with the nvidia beta driver, but it's worth a try. Besides, there are some very cool emerald themes available.

Toshibawarrior, if you go to your Sessions manager and tick the option to remember this session at next startup, you won't need to reactivate the metacity thing.

---

### Post by Toshibawarrior on 2009-02-14
> **4Orbs said:**
> You might try installing the compiz fusion icon, which provides a few options that seem to fix some people's problems. And maybe install Emerald theme manager and use the fusion icon to choose Emerald as the default theme manager. Don't know if this will work with the nvidia beta driver, but it's worth a try. Besides, there are some very cool emerald themes available.

Toshibawarrior, if you go to your Sessions manager and tick the option to remember this session at next startup, you won't need to reactivate the metacity thing.

Thank you very much! Right now I'm installing some apps she wanted and I'm using my laptop, while her comp installs stuff...I guess I'll try Fusion Icon, as I've used it before.

I'll let you know if something comes up. I hope everything gets solved today :)!

---

### Post by 4Orbs on 2009-02-14
Don't go bananas trying to solve all your compiz problems while still using the beta nvidia driver. With some luck, nvidia will release the final version driver in the near future and it might be the remedy we seek.

---

### Post by Toshibawarrior on 2009-02-14
Well...Compiz effects don't work...So I guess she has to stay cube-less for a while...:)...

Thanks a lot for all your help ;)!!

---

### Post by 4Orbs on 2009-02-14
Just a suggestion, only because it's Valentine's Day. On my old computer, The Cube and compiz all worked especially well when I had Linux Mint 5 (8.04) installed for a few weeks. But, you know, Ubuntu rules.

---

### Post by 4Orbs on 2009-02-14
Also, I think on Ubuntu 8.10 you need to install the compiz settings manager as a separate package. Not that installing it will fix your problems, just another maybe.

---

### Post by oldsoundguy on 2009-02-14
Earlier Ubuntu actually had real entries describing what hardware devices you loaded in the xorg.conf file that you could EDIT and it would make the necessary changes.  Not so with 8.10.

---

### Post by 4Orbs on 2009-02-14
Ain't progress weird? My cable guy crossed the cable line with the gas line last week. The television exploded, but I get great reception on the stove.

---

