---
title: "ATI 9.3 Catalyst drivers now released, support for compositing!"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-27
Looks like we have better support for compositing in the new 9.3 drivers from AMD/ATI which were released today. (Yesterday for some!)

Hopefully this means that we don't have to use the Compiz-Fusion icon to switch to Metacity whenever we need to play video or use Google Earth!

[Phoronix article]("http://www.phoronix.com/scan.php?page=article&item=amd_catalyst93_composite&num=1")

[New drivers from ATI/AMD website]("http://ati.amd.com/support/driver.HTML")

---

### Post by TaTaE on 2009-03-28
How about including it in Jaunty, as it is the [COLOR="Red"]LAST VERSION TO SUPPORT R500 / R600 CHIPSETS ?[/COLOR]

---

### Post by ubersolid on 2009-03-28
That looks like significant improvement! :guitar:

---

### Post by humphreybc on 2009-03-29
> **ubersolid said:**
> That looks like significant improvement! :guitar:

Tell me about it! Now Google Earth works and I can play games (even windowed) without having to disable compiz! In fact I don't have to touch compiz ever again, just enjoy the sweet sweet effects AND the openGL playback :D

---

### Post by Pitboss on 2009-03-29
Hi. Am I the only one having problems with vlc player when using compiz. I don't get any picture. And I don't think that the memory problems from 9.1, 9.2 are fixed. Again I experience significant memory usage drop when I type
 
```
fglrxinfo; fglrxinfo 
```

in the terminal

---

### Post by kdreimiller on 2009-03-31
how do you see your mem useage?  i looked at my system monitor and all looks good.

i just upgraded to 9.3 and it works fantastic!  no more do i have to disable compiz with videos.  vlc and totem work great!

---

### Post by Pitboss on 2009-04-01
> **kdreimiller said:**
> how do you see your mem useage?  i looked at my system monitor and all looks good.

I mean, I start a system monitor and I open a firefox and nautilus and I start browsing my disk. After 5~10 minutes, I run a terminal, and type "fglrxinfo" twice, and magically an average of 10% mem usage has gone away... Or I just open an avi with mplayer (since vlc won't work with compiz on) I go to full screen mode after that back, the memory usage has gotten up, I type "fglrxinfo" twice, and it goes down again. Strange, huh. I've seen this problem since ati 9.1 catalyst, but it persists.

---

### Post by skymera on 2009-04-01
Is the 9.3 any better?

I believe i'm using 8.6 from EnvyNG on my 4870.
Buggy as hell! :(

---

### Post by kdreimiller on 2009-04-01
> **Pitboss said:**
>  Or I just open an avi with mplayer (since vlc won't work with compiz on) I go to full screen mode after that back, the memory usage has gotten up, I type "fglrxinfo" twice, and it goes down again. Strange, huh. I've seen this problem since ati 9.1 catalyst, but it persists.

i can use vlc / totem with very few issues with 9.3 even with compiz running.  weird.

i tried the fglrxinfo 2x and there was no change for me.  looks like i got lucky with this release?

---

### Post by billgoldberg on 2009-04-01
> **Pitboss said:**
> Hi. Am I the only one having problems with vlc player when using compiz. I don't get any picture. And I don't think that the memory problems from 9.1, 9.2 are fixed. Again I experience significant memory usage drop when I type
 
```
fglrxinfo; fglrxinfo 
```

in the terminal

You can always switch the video output from VLC to something else, less memory intensive like X11.

---

### Post by Yashiro on 2009-04-01
If you've previously tweaked your VLC output make sure you look into that thoroughly. 
X11 plain should work if you're using a GL overlay but you might have issues if you're using XV overlay instead.

Might be a good idea to post the version of VLC.

---

### Post by carrozza on 2009-04-02
This is GREAT news!
I'm on a laptop with ATI Mobility Radeon HD 2600.
Downloading this gem right now... :-)

---

### Post by Yashiro on 2009-04-02
It works quite well, generally. Old versions of totem are still choppy, seems vsync related. Newer apps are OK. 
There's some improvement over 9.2, although it comes at a very slight performance hit.

---

### Post by zika on 2009-04-02
> **carrozza said:**
> This is GREAT news!
I'm on a laptop with ATI Mobility Radeon HD 2600.
Downloading this gem right now... :-)
are You using 9.3 on Jaunty? do tell if it works ... it should not due to new X but ... do tell once You are done ...

---

### Post by keypox on 2009-04-03
On my 4870, i can no longer resume from suspend.  With compiz on or off.  And i still have tearing in VLC. 

I can deal with the tearing as i watch stuff through xbox anyways.  But I have to have suspend.  Anyone have a fix.

---

### Post by billgoldberg on 2009-04-03
> **keypox said:**
> On my 4870, i can no longer resume from suspend.  With compiz on or off.  And i still have tearing in VLC. 

I can deal with the tearing as i watch stuff through xbox anyways.  But I have to have suspend.  Anyone have a fix.

Revert back to the old drivers.

---

### Post by keypox on 2009-04-04
what is so hard about this? Why can't ati make a proper driver? 

I prob will revert as im not seeing much of an improvement.

---

### Post by MaindotC on 2009-04-04
> **keypox said:**
> what is so hard about this? Why can't ati make a proper driver?

Because of $$$$  I'm installing it now.  What I do is sudo rm -r /etc/ati, then I run the .bin and reboot.  I don't do all that stuff w/ generating the deb and so forth - that's never worked for me.  Here goes...

---

### Post by Yashiro on 2009-04-04
For me, on Hardy, the bin installer never installs the kernel module correctly. Generating the debian packages always works. No idea why.

---

### Post by MaindotC on 2009-04-05
I haven't noticed much difference after installing.  Second Life doesn't run properly - loads of random, vibrant colours - so I'll probably have to downgrade back to 9.1.

---

### Post by sdowney717 on 2009-04-05
works worse than 8.58 version for me
I am generating the package and then doing the install a second time.

the system is slower and glxgears performance is way down. Google earth is slow. Planet penguin racer cant even start.
I might have to go back to the other version.

ok, I did a reinstall and ran aticonfig --initial
seems better
this is on an x1300 256 mb agp card

scott@scott-desktop:~$ glxgears
12361 frames in 5.0 seconds = 2470.947 FPS
10890 frames in 5.0 seconds = 2177.995 FPS
10861 frames in 5.0 seconds = 2172.199 FPS
7383 frames in 5.0 seconds = 1476.596 FPS
11161 frames in 5.0 seconds = 2232.061 FPS
12964 frames in 5.0 seconds = 2592.708 FPS

true. now you can run compiz and google earth will no longer madly flash
which is nice.

I noticed the buildpkg for this driver lists jaunty. 
does this have any significance since jaunty is using the newer xserver?

---

### Post by sdowney717 on 2009-04-05
planet penguin racer still wont run, but it has been a while since I had tried it so who knows why

scott@scott-desktop:~$ ppracer
PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de) 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

Segmentation fault

---

### Post by locksley on 2009-04-06
May be this isn't the place but sounds like some of you guys have gotten the ati 9.3 to run on Jaunty. How?

I have a brand new install running Jaunty x64 on ATI 3300 and  dual 4850's and i get all kinds of glx errors and X server mismatch can anyone point me in the right direction.

I will reboot into jaunty and get the specific errors later on if needed.

9.04 ran fine against my cards with the Ubuntu Propriety fglrx install though but i need the latest cc and drivers as im trying to get multiple monitors going.

---

### Post by locksley on 2009-04-06
Ati 9.3 and jaunty 

the xorg.conf 
```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0" 
        Device     "aticonfig-Device[0]-0" 
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24   
        SubSection "Display"  
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```
[    0[    0.030107] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.4.99.906, module version = 8.59.2
        Module class: X.Org Video Driver
[atiddxSetup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.4.-
[    0.030375] (II) UnloadModule: "fglrx"
[    0.030380] (II) Unloading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.030387] (EE) Failed to load module "fglrx" (module requirement mismatch,
[    0.030399] (EE) No drivers available.
.024869] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVi
[    0.025025] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.025035] (II) UnloadModule: "glx"
[    0.025039] (EE) Failed to load module "glx" (loader failed, 7)
The errors from the log are:

```

```

Any guesses it must configs or something not installed as i said everything worked with the Ubuntu supplied drivers?

---

### Post by zika on 2009-04-07
> **locksley said:**
> ...
[atiddxSetup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.4.-
...
Any guesses it must configs or something not installed as i said everything worked with the Ubuntu supplied drivers?
somehow X.org does not report proper version.

---

### Post by MaindotC on 2009-04-08
Sorry I'm still using Hardy :(  I know it doesn't help the community for me to stay on Hardy but I need a machine that works!

---

### Post by CLomax on 2009-04-08
Upgraded to Jaunty yesterday and attempted to install this driver. It didn't work but I must have been doing something wrong.

When I boot up the top of the screen was garbled with lines of RGB.
Rolled back to Ibex and tried again, same thing. :P

I was looking forward to a decent ATI driver too.

:KS

---

### Post by MaindotC on 2009-04-08
Did you follow the documentation?  All you should do is execute the file, accept all default options, then aticonfig --initial (or you may add the -f option) and reboot.  Granted I went back to  9.1 but if you want 9.3 then that is how you do it.

---

### Post by Kosimo on 2009-04-08
we (NVIDIA users) have been doing this since looong time ago :KS

---

### Post by balcis on 2009-04-09
it doesn't support anything for me, for 9.2; it was just flapping the video and i was turning the compiz off, but now it crashes my computer, so i restart my machine? ati hd3650, intrepid ibex.

---

### Post by MaindotC on 2009-04-09
I can't believe I'm using an x850 with minimal issues and people using a HD3650 are having problems.  I was thinking of getting a new video card - nothing lavish but just something better than my x850 - but it seems like it might be a bad investment.  Balcis did you follow the guide on [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide?](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide?)

---

### Post by markbuntu on 2009-04-09
Well, I just installed 9.3 on my hardy i386 with the automatic installer and it is just great with my HD3650. VLC and Totem both play just fine in windowed or full screen with compiz. I can watch them from behind when I spin the cube. I will try it now on my Intrepid amd64 install, stand by.

EDIT: Works the same on Intrepid amd64, no tearing with compiz etc cpu usage is much lower with full screen.

EDIT: Same on Hardy amd64. I don't know what problems anyone else is having but I am not having any problems at all with this driver and video playback and compiz. I can have totem and vlc both playing at the same time in full screen while spinning the cube. Some frame drops when they are both playing but geeze what more could you want.

---

### Post by MaindotC on 2009-04-11
Can you put your hardware specs in your sig like mine?

---

### Post by markbuntu on 2009-04-11
No, I don't want to put them in my sig, but since you asked

PC1, (built by me)
Biostar TA790GX A2+ mobo, AMD6000X2 CPU, 6GB DDR2 800 ram, HD36501GB, 2 360GB WD SATA, 250GB WD SATA, 160GB WD SATA, 1 Samsung DVD writer SATA, 1 Samsung DVD writer EIDE, SIIG Surround 7.1PCI sound card, SOYO 24 inch widescreen lcd, ACER 20inch widescreen lcd, Plantronics usb headest, logitech quickcam communicate stx usb webcam. Korg nano-control, Korg nano-key.
Hardy i386, Hardy Ubuntustudio amd64, Intrepid Ubuntustudio amd64, Jaunty Ubuntustudio amd64.

PC2
HP1330n media center w/ 19" Samsung 930B, Intrepid amd64,XP(to do my taxes)
Netbook
ACER Aspire One AOA-150 XP (soon to have Jaunty Ubuntustudio)

Belkin wireless router
Trendnet Ethernet switch
Briteport DSL modem

---

### Post by odoketa on 2009-04-11
> **billgoldberg said:**
> Revert back to the old drivers.

Hi,

I'm relatively new at this game. I had suspend working before on my t61 with the 8400. I noticed when I installed the new drivers the changes I had made in 

 /etc/default/acpi-support
 /etc/hal/fdi/information/lenovo.fdi 

went away (or maybe those weren't the changes I had made - I should have taken notes when I made the changes!). I went back in, and they didn't fix whatever is wrong. Could someone help me with the syntax to roll back to the driver that worked for me?

Thanks a bunch!
David

---

### Post by MaindotC on 2009-04-13
The important stuff is really your o/s, motherboard, video card, network card and memory.  The other stuff is really irrelevant, especially the router/modem because they are run on open communication standards that are irrelevant of the machine connected to it.

---

### Post by MaindotC on 2009-04-13
> **odoketa said:**
> Hi,

I'm relatively new at this game. I had suspend working before on my t61 with the 8400. I noticed when I installed the new drivers the changes I had made in 

 /etc/default/acpi-support
 /etc/hal/fdi/information/lenovo.fdi 

went away (or maybe those weren't the changes I had made - I should have taken notes when I made the changes!). I went back in, and they didn't fix whatever is wrong. Could someone help me with the syntax to roll back to the driver that worked for me?

Thanks a bunch!
David

If you want to go back to a previous driver, remove the /etc/ati directory, then install the driver you need - I suggest the 9.1

---

### Post by markbuntu on 2009-04-13
> **strAlan said:**
> If you want to go back to a previous driver, remove the /etc/ati directory, then install the driver you need - I suggest the 9.1

That will not remove the driver kernel modules and a whole bunch of other stuff and will give you problems at the next kernel update. The correct way to remove a driver you got from the ati web site is to go to usr/share/ati and run the uninstaller script. 

fglrx-uninstall.sh

---

### Post by zika on 2009-04-13
> **markbuntu said:**
> that will not remove the driver kernel modules and a whole bunch of other stuff and will give you problems at the next kernel update. The correct way to remove a driver you got from the ati web site is to go to usr/share/ati and run the uninstaller script. 

Fglrx-uninstall.sh
**+1**

---

### Post by Jakey_TheSnake on 2009-04-13
Question: how will this help me under Jaunty, seeing as it does not use ATI/AMD proprietary drivers? Or is it already implemented? 

I am confused. 

Thanks, 

- Jake

---

### Post by MaindotC on 2009-04-13
> **markbuntu said:**
> That will not remove the driver kernel modules and a whole bunch of other stuff and will give you problems at the next kernel update. The correct way to remove a driver you got from the ati web site is to go to usr/share/ati and run the uninstaller script. 

fglrx-uninstall.sh

Thank you, Mark.  I wish you were replying to my thread months ago asking the same question.  All this time all I've been doing is removing the /etc/ati directory and installing new drivers.  I'll uninstall like you suggested and reinstall and perhaps it will fix some issues I've had.

---

### Post by markbuntu on 2009-04-14
So many people get themselves in trouble because they did not read the release notes or installer instructions. 

Those directions have been in the installer instructions forever.

I suspect that thousands will install the 9.4 driver only to find out after they recover from the black screen of death that it does not support their card.  These people will have saved themselves a lot of trouble by reading the release notes that will tell them their rv200-500 card is no longer supported. 

Don't feel so bad, they are dropping support for rv200-500 from the windows driver at the same time.

---

### Post by skymera on 2009-04-14
Have had nothing but trouble with 9.3 and my HD4870.
Erros freezes and couldn't get to GUI.

8.6 is working fine for the moment :)

---

### Post by zika on 2009-04-14
> **strAlan said:**
> Thank you, Mark.  I wish you were replying to my thread months ago asking the same question.  All this time all I've been doing is removing the /etc/ati directory and installing new drivers.  I'll uninstall like you suggested and reinstall and perhaps it will fix some issues I've had.
I think I've made such a suggestion in a thread You've been involved in ... ;)
You might want also to read a thread I started long time ago ([http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)) which might be even more interesting now that xorg.conf is depreciated (I even do not have xorg.conf any more ... :) (but I'm using open-source driver so that is not relevant to the thread we are in ... are there any news about progress of radeon ... ?)) ...

---

### Post by ssri on 2009-04-19
Kubuntu 08.10, x86_64, KDE 4.2.2.  I ran into random hard screen freezes after a successful install of 9.3 (8.593 or 8.594?).  This after I removed ubuntu's 8.543 package prior to running ATI's installer.  I can tell you that it was hell reinstalling 8.543.  Namely, from the fact that the ATI's uninstall bash script did not work.  I had to reinstall 8.543, run the uninstaller to remove 8.593, purge 8.543 and then reinstall it *whew*.  I never had any luck with ATI's drivers.  Mostly with random freezes.  This comes on the heels of 9.2 being unable to power off the screen, failure to understand dpms commands.  In terms of stability, I'll stick with Ubuntu's original package.  The only thing I hoped to gain from ATI's drivers was to use the S-Video and Monitor ports on my laptop.  I guess I have to continue to dual-boot into Windows to give presentations.  :(

---

### Post by redtom on 2009-04-19
I'm getting this error message when I try to install the ATI driver:

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.RLgZtF



Anyone know what's going wrong? I have a Radeon X700 Pro card on an A8N-SLI motherboard and an Athlon 64 processor...

Ta for any help

p.s.

Oh, and I'm trying to get this running on Ubuntu 9.04

---

### Post by MaindotC on 2009-04-20
Who said anything about default_policy.sh ?!  Follow the directions on the release notes or the wiki!

---

### Post by redtom on 2009-04-20
But I downloaded the driver from here and followed their instructions exactly:

[ATI]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.18&lang=English")

:(

---

### Post by MaindotC on 2009-04-20
Yes and it doesn't say anything in the installation instructions, the release notes, or the wiki about autopolicy.sh so please stop using it.

---

### Post by redtom on 2009-04-20
I don't know what this autopolicy is - I opened a terminal, navigated to the folder I have the driver in and typed in their line - this is what came up...

---

### Post by MaindotC on 2009-04-20
DEFAULT POLICY WHATEVER.  default_policy.sh is not mentioned in any of the instructions.

---

### Post by caravel on 2009-04-20
I don't think the OP is running it, I think it's part of the installation script.  It probably gets unpacked and run at some point during the installation.  If you google you'll see that there are a few others having the same problem.

---

### Post by redtom on 2009-04-20
Thanks caravel, strAlan mentioned autopolicy, and further confused the matter with the default_policy thing in my error message and now needs to take a chill pill...

I'm not choosing to run this default_policy thing, full stop. I don't know where its coming from - I'm just following ATI's instructions.

Yes, a few others are having this problem as well. I thought it might have been that Ubuntu didn't support xOrg 7.4, but it does.

Will keep looking

---

### Post by slm020 on 2009-04-29
I have a quick question, my graphics card is now classed as Legacy by ATI as well. As far as I can tell, the 9.3 ATI Drivers cannot be installed on Jaunty, so which would be the best option? Wait for some drivers to be created that will enable 3D support in the X1250 card or revert back to the Ubuntu 8.10 where the 9.3 drivers work?

Any help would be appreciated.

---

### Post by MaindotC on 2009-04-29
I'm probably going to get a better video card.  The other option is to use the open-source ATI driver for your card and so far I've found very little help in properly configuring it for my x850.  It's probably all documented and written somewhere but when you weigh the cost of time to read all the documentation versus the cost of getting one of the supported cards it just seems like a better option in my humble opinon.

---

### Post by Didius Falco on 2009-04-29
> **slm020 said:**
> I have a quick question, my graphics card is now classed as Legacy by ATI as well. As far as I can tell, the 9.3 ATI Drivers cannot be installed on Jaunty, so which would be the best option? Wait for some drivers to be created that will enable 3D support in the X1250 card or revert back to the Ubuntu 8.10 where the 9.3 drivers work?

Any help would be appreciated.

That really is up to you to decide.

If 3D is a high priority for you, and can't/won't buy a newer card, then definitely go back to 8.10. Just keep an eye on the forums and other linux news sites - there should be plenty of fanfare when the Open Source driver gets 3D working reliably, though at this stage there is no telling when that will be happen.

If, on the other hand 3D is in the "Nice to have, bit not Required" category, install the Open Source driver and be patient.

---

### Post by slm020 on 2009-04-29
You raise a fair point there, unfortunately I have a laptop otherwise I would have upgraded the gfx card instantly. Only downer is this is the first time I have installed Ubuntu and not partitioned to dual boot to force myself to learn. Is there a way to downgrade or would I need to reformat?

Thanks for your advise guys/gals

---

### Post by MaindotC on 2009-04-29
You need to either re-install or remove fglrx and install the open-source ATI driver [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  This is what I did and so far I can get back into the graphical desktop, but anything graphics-intensive causes a crash and reboot.  You can do simple web browsing, flash video, and gnome-games but anything beyond that may cause issues.

My card probably just needs configuration but I don't know if I'll have time to read all the docs and tutorials to configure it .

---

### Post by MockY on 2009-04-29
Why is it that a relatively new cards such as X850XT doesn't work in Jaunty? Or should I say, is not supported by ATi? I find it very bizarre.

---

### Post by MaindotC on 2009-04-29
I guess they expect us to make $100 within 5 years to buy a new one :D  Like I said earlier, I'm in the same boat and I think I'd rather just get a new video card then re-install Hardy.

---

### Post by markbuntu on 2009-04-29
Well they did it to windows too so it is not like they are picking on linux. Besides the open source drivers are in very good shape for the great majority of RV200-500 cards and are improving in leaps and bounds. A lot of people are very happy with them and report performance better than they ever got with fglrx.

Far too many people have convinced themselves that they can only get performance with proprietary drivers and so dismiss the open source drivers out of hand.

---

### Post by Didius Falco on 2009-04-29
> **slm020 said:**
> You raise a fair point there, unfortunately I have a laptop otherwise I would have upgraded the gfx card instantly. Only downer is this is the first time I have installed Ubuntu and not partitioned to dual boot to force myself to learn. Is there a way to downgrade or would I need to reformat?

Thanks for your advise guys/gals

If you have data you need to save, back it up to cd/dvd, then burn a copy of the 8.10 iso and boot up and install it. To make future reinstalls/upgrades/backups easier, when you reinstall, delete the partition and set up a /Home partition, a / (root) partition and a linux swap file.

Personally, I also make a Data partition (you can call it whatever you like) to store my own data and downloads on. This is optional, though. Then install 8.10 and choose the / and /Home partitions in the partitioner and mark them appropriately. 

An alternate way to go about it is to make a separate /Home partition now and move your data to it, then install 8.10 to the partition you want Ubuntu in, and choose the /Home partition but do not let it format it.

This will preserve your current data and 8.10 will use it as the /Home folder. It will appear seamlessly in Ubuntu, just as if it were still part of the same partition.

A good tutorial on how to create a separate /Home directory from an existing installation can be found here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you do not have a lot of data saved, I'd recommend going the backup what you need to save and reinstall method. That will start you off with a clean, fresh install. The downside to that is that all your configuration settings will need to be done over.

Two options to choosefrom, but in the end, go with what works the best for you.

I hope this helps...

---

### Post by MaindotC on 2009-04-29
> **markbuntu said:**
> Well they did it to windows too so it is not like they are picking on linux. Besides the open source drivers are in very good shape for the great majority of RV200-500 cards and are improving in leaps and bounds. A lot of people are very happy with them and report performance better than they ever got with fglrx.

Far too many people have convinced themselves that they can only get performance with proprietary drivers and so dismiss the open source drivers out of hand.

Thanks for making that known because I certainly didn't know that ATI did it platform-wide.  I wonder though if those people reporting great success with the open-source drivers are developers - people that understand operations of the video card and driver at the electrical-level and on up - and not the typical user.  I'm still looking for a decent guide on how to properly configure my x850 using the open-source ati driver.  I'm googling, but if anyone wants to throw me a link I'd appreciate it.

---

### Post by ssri on 2009-04-30
> **strAlan said:**
> I wonder though if those people reporting great success with the open-source drivers are developers - people that understand operations of the video card and driver at the electrical-level and on up - and not the typical user.


I share your sentiments.  The one thing preventing me from upgrading to jaunty is the fact that my 1.5 yr old mobility radeon (dropped into the market 2 years ago) is now deemed legacy.  Unfortunately, my xorg.conf kung-fu is not strong enough yet to unlock the potential of opensource drivers.  Furthermore, upcoming deadlines prevent me from rolling up my sleeves to play around with it.  Not something I want to waste a Saturday or Sunday on, especially with the nice sun outside :D.

From all of this, I am afraid that many potential switchers with laptops will be in for a rude awakening when trying out jaunty.  Staying with intrepid for the time being.

---

### Post by markbuntu on 2009-04-30
The open source ati drivers in Jaunty are vastly improved and should configure themselves without the need for any tweaking by you. Just be sure to remove fglrx before upgrading or you could have a really bad time.

I am using the automatically configured "radeon" open source driver with my HD3650 and it works great except for no 3D which should not be a problem for earlier cards that will be using either the ati or raden driver. The 9.4 driver from ati is all screwed up anyway so I am just skipping it and will wait for 9.5 or maybe just keep using this driver. 3D is not that big of a deal for me anyway and 2D acceleration is great.

It is a huge improvement over the radeon driver in Hardy and Intrepid

---

### Post by MaindotC on 2009-05-01
mark - I used the configuration instructions from [the Open Source ATI Driver](https://help.ubuntu.com/community/RadeonDriver) which goes into removing fglrx but not installing the ATI driver and I had problems booting into the desktop.  I used the following instructions to start over:
> 
sudo apt-get remove &#8211;purge xorg-driver-fglrx xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install &#8211;reinstall libgl1-mesa-glx libgl1-mesa-dri
dpkg-reconfigure -phigh xserver-xorg

per [this blog post](http://is.gd/vLpD).  Now I am able to boot into the desktop but there is clearly a degradation in performance.  I'm using an older card, but applications like Second Life or Torcs are way slower and choppier than before. I can't even run wine'd games like Counterstrike, and they ran very smoothly with 8.04 and the proprietary driver.  Can you help me configure my settings to get at least SOME decent performance from what I have?

---

### Post by Demonizer on 2009-05-02
I'm gonna try to install 9.3 driver now.. hope it works.
(doesn't matter now)

---

