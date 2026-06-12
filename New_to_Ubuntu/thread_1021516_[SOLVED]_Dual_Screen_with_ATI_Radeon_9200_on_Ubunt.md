---
title: "[SOLVED] Dual Screen with ATI Radeon 9200 on Ubuntu 8.10"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by DarkGekko on 2008-12-25
Hi,

I recently converted from XP to Ubuntu 8.10 (Intrepid Ibex) and have been very impressed by Ubuntu.

I have a dual head graphics card (ATI Radeon 9200) and two monitors, and would like to run a dual monitor setup as I used to in XP. I'm using the open source drivers for the card. 

When I plugged the second monitor into the card I did for a while have a clone display, and if I recall correctly this was the case until just after login today. However the second monitor has remained blank and in standby mode since then. I'd like to have the second monitor displaying an extended desktop rather than just a clone.

Any help would be appreciated, I'm willing to use any program it takes to get this working!

Cheers, 

James

---

### Post by ELF_O8 on 2008-12-25
Have you tried the "Screen Resolution" App in the Preferences Tab?
I've used that to create an extended desktop.

---

### Post by DarkGekko on 2008-12-25
Hi, thanks for the quick response!

Just tried what you suggested, but I can't seem to set the res any higher than the maximum for my primary (VGA) monitor, 1024*768. It also only appears to detect this monitor, not the second.

James

---

### Post by ELF_O8 on 2008-12-25
Yeah, for some reason you can't have a greater resolution on one than the next. Alternatively, you could use Envy; its a neat little app you can get from Synaptic/Adept, automatically detects and installs necessary hardware for most video cards.

---

### Post by DarkGekko on 2008-12-25
Hi,

Tried installing Envy. A friend suggested I try this earlier but it failed and we couldn't understand what to do. Here's a copy of the output:

james@CRYSTAL:~$ sudo aptitude install envyng-core
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following partially installed packages will be configured:
  fglrx-6-8-0 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up fglrx-6-8-0 (8.28.8-2) ...
/var/lib/dpkg/info/fglrx-6-8-0.postinst: 156: Bad substitution
dpkg: error processing fglrx-6-8-0 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 fglrx-6-8-0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up fglrx-6-8-0 (8.28.8-2) ...
/var/lib/dpkg/info/fglrx-6-8-0.postinst: 156: Bad substitution
dpkg: error processing fglrx-6-8-0 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 fglrx-6-8-0
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

Something that might interest you though: When I realised a moment ago that there was now a "Configure Display Settings" icon on my top 'taskbar' I clicked it, and down came a menu with options for BOTH monitors. Clicked one of the options for the CRT (my second monitor), and all of a sudden it burst into life, cloning the first display. And everything was at 90 degrees! Rotated back to normal orientation, and the monitor is still cloning, which is an apparent improvement! This was before trying to install Envy by the way.

James

---

### Post by ELF_O8 on 2008-12-25
Well, that is a rather interesting output, though I can't seem to understand the 
> /var/lib/dpkg/info/fglrx-6-8-0.postinst: 156: Bad substitution
dpkg: error processing fglrx-6-8-0 (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
fglrx-6-8-0

You may try uninstalling completely and then reinstalling as it seems your previous install may have become corrupted. I would also recommend a reboot after this; it'll clear the system cache and let you reinstall without fuss. Let me know if this helps.

---

### Post by DarkGekko on 2008-12-25
Hi,

In trying to uninstall envyng-core (which I think is what you suggested) via Synaptic I got an error with this:

E: fglrx-6-8-0: subprocess post-installation script returned error exit status 2

Any thoughts?

James

---

### Post by DarkGekko on 2008-12-25
Interesting...despite the previously mentioned error, which also came with a message saying that no packages had been altered, it's now no longer marked as installed in Synaptic...

James

---

### Post by ELF_O8 on 2008-12-25
Alright, I've been doing my homework for this one.
The file /var/lib/dpkg/info/fglrx-6-8-0.postinst is corrupt.
Find the file in question, make a copy, and then use this code.
```
sudo rm /var/lib/dpkg/info/fglrx-6-8-0.postinst
```
I know it's one of those dreaded "rm" codes, and you don't have to do it if you don't want to. That's why I advise the backup copy.
After that, you should be able to un/reinstall the package.

---

### Post by moredhel on 2008-12-25
Well, dreaded in so far as don't do rm -rf /

If people actually look at what they are copying and pasting, then they are safe :)

---

### Post by DarkGekko on 2008-12-25
Hi again,

Well, thanks to your suggestions Envy appears to have installed with no issues! :) What's the next step?

James

---

### Post by ELF_O8 on 2008-12-25
Just ask it to locate whatever automatically and it will install the driver that your computer needs. If you're lucky, it may install the ATI Catalyst Control Center for Linux, which, quite handily, is exactly the same as the windows version.

---

### Post by DarkGekko on 2008-12-25
Well, mixed success. Mostly failure. Success in that I got it to run the thing, failure in that it failed. Below is a copy of the terminal:

> james@CRYSTAL:~$ envyng
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend (Not yet available)
   "-k" for the QT4 frontend
   "--uninstall-all" to completely remove what EnvyNG has done
james@CRYSTAL:~$ envyng -t
[sudo] password for james: 


 +-------------------------------------------------+
 |                                                 |
 |             Welcome to EnvyNG                   |
 |    Developed by Alberto Milone (aka tseliot)    |
 |                                                 |
 +-------------------------------------------------+


 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

3
 +---------------------------------------------------------------------------+
 | Number | Candidate Version | Installed Version | Compatible | Recommended |
 |---------------------------------------------------------------------------|
 | 0      | 8.552-0ubuntu0.1  | -                 | -          | -           |
 +---------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
0

Dowloading the packages...
[==================================100.0%======================================]Selecting previously deselected package dkms.
(Reading database ... 130552 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.0.20.4-0ubuntu2_all.deb) ...
dkms: Installing dkms

dkms: Preparing dkms

Selecting previously deselected package fakeroot.
dkms: Unpacking dkms

Unpacking fakeroot (from .../fakeroot_1.9.5ubuntu1_i386.deb) ...
dkms: Preparing to configure dkms

fakeroot: Installing fakeroot

Selecting previously deselected package fglrx-kernel-source.
fakeroot: Preparing fakeroot

Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.552-0ubuntu0.1_i386.deb) ...
fakeroot: Unpacking fakeroot

fakeroot: Preparing to configure fakeroot

fglrx-kernel-source: Installing fglrx-kernel-source

fglrx-kernel-source: Preparing fglrx-kernel-source

fglrx-kernel-source: Unpacking fglrx-kernel-source

Selecting previously deselected package xorg-driver-fglrx.
fglrx-kernel-source: Preparing to configure fglrx-kernel-source

Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb) ...
xorg-driver-fglrx: Installing xorg-driver-fglrx

xorg-driver-fglrx: Preparing xorg-driver-fglrx

dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man8/atieventsd.8.gz', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.552-0ubuntu0.1_i386.deb) ...
fglrx-amdcccle: Installing fglrx-amdcccle

fglrx-amdcccle: Preparing fglrx-amdcccle

Processing triggers for man-db ...
fglrx-amdcccle: Unpacking fglrx-amdcccle

fglrx-amdcccle: Preparing to configure fglrx-amdcccle

man-db: Running post-installation trigger man-db

Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb
Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 303, in mainMenu
    a.driverMenu('fglrx')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.5/site-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 206, in install
    self.cacheUi.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText)) 
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 226, in commit
    res = self.installArchives(pm, installProgress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 201, in installArchives
    res = installProgress.run(pm)
  File "/usr/lib/python2.5/site-packages/apt/progress.py", line 216, in run
    res = pm.DoInstall(self.writefd)
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 303, in mainMenu
    a.driverMenu('fglrx')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.5/site-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.5/site-packages/Envy/packagemanager.py", line 206, in install
    self.cacheUi.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText)) 
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 230, in commit
    raise SystemError, "installArchives() failed"
SystemError: installArchives() failed
james@CRYSTAL:~$ 

Shortly after this I got a flag at the top of the screen saying that there was a broken package and that I should go to the Package Manager for more details. Synaptic reports that there is one broken package, titled fglrx-amdcccle which it says is the current version. Other info given about this package is as follows:

> Catalyst Control Center for the ATI graphics accelerators
Catalyst Control Center for the ATI Radeon and FireGL graphics accelerators.

This package provides the Catalyst Control Center, Linux Edition

Options in Synaptic are Reinstall, Removal and Complete Removal.

First instinct would tell me to go with a complete removal, reboot, installation, and then try running Envy again. However I may be entirely wrong! Gah, nothing ever seems to work on this system does it?!

Thanks for all the help so far, really appreciate it!

James

---

### Post by ELF_O8 on 2008-12-25
I would go for your first instinct. Completely remove, reboot, then try to use the Envy Graphical Interface, it's a lot less confusing than the terminal.

---

### Post by DarkGekko on 2008-12-25
Well this is turning out to be a moderately scary evening/morning...

I removed the broken package, restarted the PC, reinstalled it (I think with an error message, I unfortunately forgot to write it down), but it appeared installed in Synaptic). I then ran envyng. To try and do any of the graphical options I had to install envyng-qt. I was then able to run the GUI for EnvyNG, and selected the ATI driver. It then prompted me to reboot, which I did.

Upon restart it appears that something is pretty majorly wrong. I'm presented with an error message that is followed by options headed by "run ubuntu in low graphics mode for this session only", the others being troubleshoot and configure IIRC. The low graphics mode (which appears to be completely normal oddly enough) is how I'm online now. 

And that package fglrx-amdccce is broken again.

There is an option to get envyNG to undo everything it's done which I am tempted by, simply to get this thing working properly. Any thoughts?

James

---

### Post by moredhel on 2008-12-25
Do that I think - It seems that your card and envy (or rather, the drivers it is getting) do not mix.

---

### Post by ELF_O8 on 2008-12-26
I agree with moredhel.
This is turning out to be a nightmare, sorry about this.
Ubuntu is usually much more flexible. It's all these darn proprietary drivers.

---

### Post by DarkGekko on 2008-12-26
Ah don't worry about it, it's been pretty useful anyway as a learning experience if nothing else!

OK, I've undone anything done by Envy. I'm now just going through the package manager looking for drivers. Hopefully then it'll boot properly without this "Low graphics" issue.

James

EDIT: OK, through the course of fiddling with the package manager I've now managed to reduce the number of low graphics error causes at startup to just "EE: No device detected". This then gave me the option to restore to default settings, backing up my settings, which I did. After restart the error message now tells me that I just need to configure the monitor/display devices myself. So it appears we're on the way to fixing it, but I don't know how to configure these. As always, any/all help appreciated! 

Cheers,

James

---

### Post by moredhel on 2008-12-26
try 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DarkGekko on 2008-12-26
Followed that through, saved the location of the backup to a text file and rebooted. Problem appears to be unchanged, but did copy down the text of the error message:

> Your screen, graphics card and input device settings could not be detected correctly. You will need to configure them yourself.

[http://rafb.net/p/pdFPxN31.html](http://rafb.net/p/pdFPxN31.html) << A link to the paste of my xorg.conf file.

James

EDIT: Gah, xrandr is now no longer showing both monitors. Any ideas on how to resolve it?

Cheers,

James

---

### Post by ELF_O8 on 2008-12-26
You could check out this [thread]("http://ubuntuforums.org/showthread.php?t=1019822&highlight=ATI+radeon+9200"). It provides some useful information. Also [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) is the official Ubuntu guide for installing non-open source drivers.

Hope you can work this out, this is a lot of work around for one card!

---

### Post by w4ett on 2008-12-26
As ELF_08 has noted by linking the other forum thread, the 9200 card is no longer supported by the fglrx driver...in fact all cards prior to the 9500 are no longer supported by AMD/ATI in the current XServer.  The correct driver to use is the xorg-driver-ati which is automatically installed.  You will need to purge all the attempts to install the proprietary driver and revert to using the open source driver.

P.S.  I have one myself... :(

---

### Post by ELF_O8 on 2008-12-26
> **w4ett said:**
> As ELF_08 has noted by linking the other forum thread, the 9200 card is no longer supported by the fglrx driver...in fact all cards prior to the 9500 are no longer supported by AMD/ATI in the current XServer.  The correct driver to use is the xorg-driver-ati which is automatically installed.  You will need to purge all the attempts to install the proprietary driver and revert to using the open source driver.

P.S.  I have one myself... :(

Well dang if that doesn't suck for DarkGekko; all this work around and installing only to find that the driver is no longer supported. :(

---

### Post by moredhel on 2008-12-26
> **ELF_O8 said:**
> Well dang if that doesn't suck for DarkGekko; all this work around and installing only to find that the driver is no longer supported. :(

I would say on the contrary - I found out that the 9200 has full 3d support in the ati driver, which is far better than what I have (5200 nvidia - unsupported, unusable in kde4 because the version of the driver that fixed it isn't for my card :@).

Looking over more documentation it seems that xrandr 1.2 is fully supported and so you should definitely use it as soon as everything is back to normal.

---

### Post by DarkGekko on 2008-12-26
Gah, nothing is ever simple is it! Thanks for the various links, be they bearers of bad news or not!

OK, so the plan is to resort to the open source drivers. You mentioned purging all attempts to install the proprietary drivers, is there a recommended way of doing this?

Cheers,

James

---

### Post by w4ett on 2008-12-26
> **moredhel said:**
>  I found out that the 9200 has full 3d support in the ati driver,

This is very correct....The open source driver provides around 800-900 FPS in glxgears on my install, and Compiz Fusion is fully usable.  

My main gripe is that AMD/ATI no longer supports cards that are still available for sale in the retail marketplace.  Planned obsolescence is such a horrible practice. :P

---

### Post by ELF_O8 on 2008-12-26
What I meant was: We've been trying all these things when the answer was very simple, not that his driver didn't exist.

---

### Post by w4ett on 2008-12-26
> **DarkGekko said:**
> OK, so the plan is to resort to the open source drivers. You mentioned purging all attempts to install the proprietary drivers, is there a recommended way of doing this?

```
sudo apt-get remove --purge xorg-driver-fglrx
```

Then boot into recovery mode and:

```
xfix
```

---

### Post by DarkGekko on 2008-12-26
Well, some good news! Purged it and did xfix and I no longer get a low graphics error message at startup! :) Whats the plan from here then? 

James

EDIT: Also just to let you know, xrandr is now detecting both monitors again!

---

### Post by w4ett on 2008-12-26
> **DarkGekko said:**
> Well, some good news! Purged it and did xfix and I no longer get a low graphics error message at startup! :) Whats the plan from here then? 


Now you should be able to enable the second monitor from Screen Resolution .

---

### Post by ELF_O8 on 2008-12-26
> **DarkGekko said:**
> Well, some good news! Purged it and did xfix and I no longer get a low graphics error message at startup! :) Whats the plan from here then? 


Ahh, we're almost done finally. I think the Screen Resolution app should be detecting both monitors now then!

---

### Post by DarkGekko on 2008-12-26
Yup, unticking "Mirror screens" suddenly reveals a second monitor on the dialogue box!

---

### Post by w4ett on 2008-12-26
Sounds like you are well on your way...Congrats :popcorn:

Happy Holidays!!

---

### Post by ELF_O8 on 2008-12-26
> Yup, unticking "Mirror screens" suddenly reveals a second monitor on the dialogue box!
Is it safe to assume, then, that all is well with your install?

---

### Post by DarkGekko on 2008-12-26
Urk, seems like it was too soon to celebrate :(. The screen res dialogue now can only see one monitor, labeled unknown, as can xrandr.


James

---

### Post by moredhel on 2008-12-26
can you pastebin me /var/log/Xorg.0.log please?

---

### Post by ELF_O8 on 2008-12-26
Have you rebooted recently?

---

### Post by DarkGekko on 2008-12-26
[http://dpaste.com/102751/](http://dpaste.com/102751/)

There you go! 

James

EDIT: Yeah, I had to go out for a bit and without thinking hit shutdown. Would have been safer to leave the thing on wouldn't it...

---

### Post by ELF_O8 on 2008-12-26
> Build Operating System: Linux 2.6.24-19-server i686 Ubuntu


Does this mean he is running the Server Edition or is that normal output?

EDIT: Nevermind, same readout in mine :)

---

### Post by moredhel on 2008-12-26
It's normal, I gave him the cd personally ;)

Okay from that it looks like your are using the VESA driver not the radeon one - just look at line 122 and the ones below it.

I dunno how to make sure you are/not and if so how to switch. perhaps someone else can help here?

---

### Post by w4ett on 2008-12-26
> **moredhel said:**
> 
I dunno how to make sure you are/not and if so how to switch. perhaps someone else can help here?

in the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or again:

```
xfix
```

---

### Post by moredhel on 2008-12-26
Is there an alternative way to see what it uses at the moment. I ask because if you look back in the thread he has done xfix before :S

---

### Post by w4ett on 2008-12-26
Is this old Piper still at the Cambridge airport?   I use to live on Trumpington Road.  Just curious... lol :P

edit: Dunno why the pic doesn't load!  Direct link: [http://www.flickr.com/photos/sohvimus/3032536024/in/set-72157606423786527/](http://www.flickr.com/photos/sohvimus/3032536024/in/set-72157606423786527/)

---

### Post by w4ett on 2008-12-26
> **moredhel said:**
> Is there an alternative way to see what it uses at the moment. I ask because if you look back in the thread he has done xfix before :S

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This is the "old school" method for resetting xorg.conf

---

### Post by DarkGekko on 2008-12-27
> **w4ett said:**
> Is this old Piper still at the Cambridge airport?   I use to live on Trumpington Road.  Just curious... lol :P

edit: Dunno why the pic doesn't load!  Direct link: [http://www.flickr.com/photos/sohvimus/3032536024/in/set-72157606423786527/](http://www.flickr.com/photos/sohvimus/3032536024/in/set-72157606423786527/)

Certainly is! I work at the flying school that owns her and have flown her myself several times!

Didn't see that one coming!

I'll try the recommended steps re Ubuntu at home on Sunday, I'm at work (a different work) today and dogsitting for the flying school owners tonight, so I wont be back at the PC 'till then.

Cheers,

James

---

### Post by DarkGekko on 2008-12-28
Hi again,

Well, I ran the "old-school method for resetting xorg.conf" ;)

Not sure what you need, so I've posted both xorg.conf, and the log file.

[http://pastebin.com/m4887728](http://pastebin.com/m4887728) < xorg.0.log

[http://pastebin.com/m2d4b3c04](http://pastebin.com/m2d4b3c04) < xorg.conf

Let us know if you need something else, I will however be away between Monday morning and Tuesday afternoon.

Cheers,

James

---

### Post by w4ett on 2008-12-28
Looks like the radeon driver is loading, so all should be good for you now.  To be sure run
```
glxgears
```
in the terminal.....If your gears are spinning...all is ok.  You should get a framerate of around 800 FPS.

---

### Post by DarkGekko on 2008-12-28
> **w4ett said:**
> Looks like the radeon driver is loading, so all should be good for you now.  To be sure run
```
glxgears
```
in the terminal.....If your gears are spinning...all is ok.  You should get a framerate of around 800 FPS.

Well, they be spinning all right! And you say 800 fps...

> james@CRYSTAL:~$ glxgears
7434 frames in 5.0 seconds = 1486.099 FPS
37889 frames in 5.0 seconds = 7577.655 FPS
11293 frames in 5.0 seconds = 2258.265 FPS


How does that look? :guitar:

James

P.S. I had to deice "that old Piper" this morning. Bloody cold!

---

### Post by w4ett on 2008-12-28
Looks like it's sorted..driver wise :popcorn:

> When I plugged the second monitor into the card I did for a while have a clone display, and if I recall correctly this was the case until just after login today. However the second monitor has remained blank and in standby mode since then. I'd like to have the second monitor displaying an extended desktop rather than just a clone.

Now under System>Preferences>Screen Resolution (if you have the second monitor plugged in) you should see both screens...if not use the "Detect Display" and the settings for your desktops.

---

### Post by DarkGekko on 2008-12-28
YES!

Excellent, thanks to all of you for helping me sort this out! :popcorn:

(one very happy) James :)

---

### Post by w4ett on 2008-12-28
> **moredhel said:**
> Is there an alternative way to see what it uses at the moment. I ask because if you look back in the thread he has done xfix before :S

Never did answer this....prior to 8.04 we had to use the ```
dpkg-reconfigure -phigh xserver-xorg
```

to "fix" the xorg.conf file.....now the new method is ```
xfix 
```
Both do basically the same thing.

DarkGekko:  Glad it's sorted...have fun!  

Happy Holidays!

---

### Post by DarkGekko on 2008-12-28
:) Thanks again for all your help!

Just out of interest w4ett did you have any connection to the Mid-Anglia School of Flying? The school that owns G-JASE. Or was it just a commonly seen aircraft?

Thanks again,

James

---

### Post by w4ett on 2008-12-28
> **DarkGekko said:**
> :)Just out of interest w4ett did you have any connection to the Mid-Anglia School of Flying? The school that owns G-JASE.

I was posted to Lakenheath in the 80's and lived in Cambridge  (on Trumpington Road) for several years.  I looked up the A/C Reg and it brought back some fond memories.  Cheers!

---

### Post by Naturofix on 2010-06-03
I've got exactly the same problem with my radeon 9200 SE. Would like to run a second screen on the DVI output but can't get it to connect. I have purged the drivers as stated. 

I'm using Ubuntu 9.10, there is no xfix in the recovery mode. 

What do I do to fix this.

Been working on linux for only 4 months, not been able to get my screens to both work yet, please help.

xrandr

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0*+   60.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

---

