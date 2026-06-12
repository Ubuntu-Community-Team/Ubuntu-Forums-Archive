---
title: "nVidia third party driver help"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by trg383 on 2008-12-05
Hi, and thank you in advance to anyone who can help!
First off, I'm extremely new to linux/ubuntu so my knowledge of even basic things is limited. I'm trying to run guildwars and eventually other windows based games on my system and have come accross a snag when I try to install nVidia's 3rd party driver. 

Quickly after I installed ubuntu, I got a notifier that there was a driver available, clicked and it brought up "Hardware Drivers". Naturally, I attempted to enable it: I clicked on the driver listed in the list, scrolled through the description and then clicked activate. A small dialogue box came up indicating that it was installing, however the cursor/progress meter just cycled side to side for a minute (with the progress at 0%) and then the dialogue box closed. It didn't look like it had done anything, but to be sure I restarted my system, went back to Hardware Drivers and found that it still was not activated. I tried this method a couple of times to no avail.

In one of the many forums I was browsing through, it was suggested that checking whether I can turn on the Extra Visual Effects or not would be a good indicator of my system's ability to play a 3d game like guildwars. This also asked if I wanted to enable the nVidia driver. Same drill though: I put in the password, it popped up the dialogue, the dialogue went away without doing a thing (and the Extra Visual Effects informed me they could not be turned on).

Is there another way to get the driver to install? Does anyone know why it wont? Is there something better I can use?

I'm running ubuntu 8.10 and my graphics card is a gforce 4 ti 4200.

Again, thanks very much to any help/suggestions anyone can provide.

---

### Post by gedit on 2008-12-05
Are you doing this through the Restricted Drivers Manager? If so, try it through "Envy".

[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb)

Installation intructions are here:

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)


"Envy" is a 3rd-party video driver installer. I hope this works! Let me know if you have any problems.

---

### Post by handydan918 on 2008-12-05
That nvidia card needs the legacy driver. i'm not on Ubu just now, so I can't say if they are in the repos, but you can [get them here.]("http://www.nvidia.com/object/unix.html")

---

### Post by 2hot6ft2 on 2008-12-05
Did you have an internet connection at the time? It usually moves side to side then downloads the driver showing a progress bar, then installs it.

Hardware Manager is the best way to install the driver for it but it does require you be online. Another way is to use EnvyNG under Applications>System Tools>EnvyNG it too will require an internet connection to download the driver.

---

### Post by trg383 on 2008-12-05
**gedit**: Envy is throwing an error saying that it isn't compatible with my OS. :(

**handydan918**: I downloaded the driver from nvidia, but can't seem to exit the X server to install. I tried ctrl+alt+f1 and it seemed like it would be stopped since the whole screen was just the text terminal, but it still wouldn't install because the X server was running. Is there more I need to do to close/stop it totally?

**2hot6ft2**: Yep, I have an always on broadband connection. It was like it was trying and gave up for some reason before it could do anything.

Thank you all :)

---

### Post by handydan918 on 2008-12-05
> **trg383 said:**
> 

**handydan918**: I downloaded the driver from nvidia, but can't seem to exit the X server to install. I tried ctrl+alt+f1 and it seemed like it would be stopped since the whole screen was just the text terminal, but it still wouldn't install because the X server was running. Is there more I need to do to close/stop it totally?


Thank you all :)
Try logging out, and at the login screen, try ctrl+alt+f1.

---

### Post by trg383 on 2008-12-05
That still left X running, but I googled a little and found the "sudo /etc/init.d/gdm stop" command, which worked... but...

The installer for the driver informed me that it couldn't interface with my kernel, that there wasn't a precompiled kernel on nvidia's site, and that it couldn't compile one successfully. I'll attach the install log in the off chance that it would help... Thanks a bunch!

---

### Post by Shazaam on 2008-12-05
When you install the driver downloaded (preferably to your desktop) from the nvidia website you need to do this...
1. Install build-essential (through Synaptic)
2. Ctrl+Alt+F1 (drops you to a prompt)
3. Type this in-
```
sudo /etc/init.d/gdm stop
```
(stops the gnome display manager)
4. cd (change directory) to the location of the nvidia driver-
```
cd ~/Desktop
```
(capitol D is important if the driver is on the desktop)
5. Run the installer-
```
sudo sh NVIDIA-DRIVER.run
```
(substitute your driver name for NVIDIA-DRIVER)
6. Reboot.

---

### Post by trg383 on 2008-12-05
I checked Synaptic and build-essential was already installed and up to date. I'd done everything through step 5 before, which was when the installer gave me what happened in my previous post.

---

### Post by anewguy on 2008-12-05
I had that problem on my old nVidia card - had the exact same error when trying to use the driver source from nVidia or via envy (which was getting the same driver and the same error).  It may not work for you, but I had to tell envy that I wanted a previous driver by selecting something other than the newest on the list.

Also, what is the model of your video card, as that makes a difference as to whether those drivers will work or if you need to get the old drivers.  To try it, via synaptic package manager, select all of the packages that say they are for the nvidia legacy cards/drivers - this should uninstall your current nvidia driver (if one exists) and install the legacy drivers.

Dave ;)

---

### Post by Gregz on 2008-12-06
I have the same problem. Whenever I try  driver updates it will download and install until reboot. Then I go back to low graphics. Couple years ago had same problem with Open Suse doing same thing. Thought they fixed this though?????

---

### Post by trg383 on 2008-12-06
I'm not seeing anything in Synaptic that refers to Legacy drivers... there are a handfull of nvidia related packages, but I'm not sure what's safe to remove.

My vid card according to lspci is "01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a2)"
I'm pretty sure it's an ASUS V9280 VS, if that helps narrow it down at all...
In trying out all options at hand, the driver nVidia lists as LinuxIA32 for 173.14.xx series told me that my card (it named the GeForce4 Ti 4200) was supported by the 96.43.xx series driver.

The prob I'm still having is that it cannot interface with the kernel or compile a new one (I think? I'm not sure if it's compiling a kernel or an interface to the kernel.. it's failing to compile something though when I try installing the driver I downloaded from nvidia)

---

### Post by anewguy on 2008-12-06
Would it be possible for you to post the following:

(1) how you downloaded the file you are trying to compile, the location and name

(2) what you did after you downloaded this file - perhaps unpacked it, then....try to include each step as that can be important in finding a solution.

(3) assuming you had to do most if this in a terminal window, did you preface everything with "sudo "?  I only ask as sometimes it isn't apparent that something needs to be run as the super user, and it's usually easier to tell someone to do them all with "sudo " then to pick out the individual ones that actually need it (we can do that if you want).

I'm in Windows right now - I'll go over to Linux in a minute and check synaptic for the packages and post back if it is different from what you found.

dave ;)

EDIT: have you seen this post? [http://packages.ubuntu.com/intrepid/nvidia-glx-71]("http://packages.ubuntu.com/intrepid/nvidia-glx-71")

or

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by trg383 on 2008-12-06
Sure. Though I wasn't trying to compile anything myself, it was something an installer told me it was trying to do.
1) I downloaded NVIDIA-Linux-x86-96.43.07-pkg1.run from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) just with my web browser and left it on my desktop.
2) I used ctrl + alt + f1 to get to the terminal.
3) I used sudo /etc/init.d/gdm stop to stop the X server.
4) I cd'd to Desktop
5) I used sudo sh NVIDIA*.run to run the driver installer that I'd downloaded
The remainder of what I did was within the install program (and copied from the log file that I'll also attach, it's on an earlier post in this thread, but I'll put it here just for ease of locating it).
 
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
6) I selected yes in response.

-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
7) I said ok.

-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
8] I said okay a couple times and exited.

I was just reading through the [README]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/README/README.txt") that, in my sleep deprived state had completely missed. It said that I might need to install the kernel source so the installer can use it. I'm not sure how to find the right version of that to install. It also said that if it needs to compile I'd need a /usr/bin/ld file to link to my kernel; I have a file there, but I have no idea how to check if it's the right one (though I assume that it is). The only Q in the common problems Q&A (still in the readme) that seemed to apply is: 
"Q. I cannot build the NVIDIA kernel module, or, I can build the NVIDIA kernel module, but modprobe/insmod fails to load the module into my kernel. What is wrong?

A. These problems are generally caused by the build using the wrong kernel
   header files (i.e. header files for a different kernel version than the one you are running). The convention used to be that kernel header files should be stored in '/usr/include/linux/', but that is deprecated in favor of '/lib/modules/RELEASE/build/include' (where RELEASE is the result of 'uname -r'. The 'nvidia-installer' should be able to determine the location on your system; however, if you encounter a problem you can force the build to use certain header files by using the --kernel-include-dir option. For this to work you will of course need the appropriate kernel header files installed on your system. Consult the documentation that came with your distribution; some distributions do not install the kernel header files by default, or they install headers that do not coincide properly with the kernel you are running."

I know that might not apply; I don't know what modprobe or insmod are. If it does though, do I need to run the installer via "sudo sh NVIDIA*.run --kernel-include-dir" or does that mean something else? I'm not super familiar with applying options at the command line.

I have not seen those two threads, I'll look at them in more detail, though at first glance, they did confirm that my GPU is supported by the driver I downloaded. I can try uninstalling nvidia packages that were already there and try using the util (System > Administration > Hardware Drivers) again, but I'm scared that I might uninstall something that will leave me stuck at the terminal not knowing what to do. Also, I did try installing the driver using this method before I did anything else.

Sorry this is rather long, I wanted to get all the info that I thought might be relevant up there. I tried to include as much of the readme as seemed relevant to me in the hopes of saving others from having to wade through it. Thanks so much for taking the time to read through this and help, I'm very lost. Also, sorry it took me so many hours to respond, I was sleeping.

EDIT: I'm going to try using EnvyNG (I had the older Envy and didn't realise there was a newer) and, if that fails, try the steps at [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) including installing the kernel-source, just in case.

**EDIT2:** Here's what I've tried since this post:
I installed EnvyNG and used it to uninstall a copy of what looked like the driver I was trying to install (maybe I shouldn't have). Thinking that getting rid of this might make it possible for me to use the Hardware Drivers utility (System->Administration->Hardware Drivers), I tried. It worked, installed the recommended driver (only one listed). I rebooted and had to go to low-graphics mode. So I disabled the driver (in Hardware Drivers) and tried installing the driver with EnvyNG. This also installed without error, but when I rebooted I once again had to go to low-graphics mode. So, I went through every step on [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) to the letter and it gave me the same compiling error that's in the log I attached previously (nvidia-installer.txt).

---

### Post by anewguy on 2008-12-06
not sure what's going on there - maybe you should try the following before running it again:

sudo apt-get install build-essential linux-headers-`uname -r`

as it could be you are just missing the linux header files.  On my keyboard those single-quote lokking characters are actually forward facing and are on a key next to the "1" key on the main part of the keyboard.

I know in the nvidiamanual as pointed to, they do have a section there on being sure you have disabled the restricted driver and removed all of the nvidia-glx stuff first.  You may want to try that, then rerun envyng.  Once it has finished (if it runs successfully) you should be all set - no need to mess with the restricted driver, etc..

Let me know if that helps or not.

Dave ;)

---

### Post by trg383 on 2008-12-06
The headers were already installed and up to date when I tried installing them.

The only nvidia file that was there and needed removal was nvidia-settings. I was hopeful when I noticed I'd overlooked it. Even after I removed it though, EnvyNG appeared to work and install the driver but when I rebooted I ended up in low-graphics mode and had to revert to the default settings again.

Oh, and I did make sure to disable "nv nvidia_new" by adding it to the linux-restricted-modules-common file... unless that's not what you mean by disabling the restricted driver.

---

### Post by anewguy on 2008-12-06
Sounds like it is working except for your resolution.  After envyng finishes and you reboot, post your xorg.conf file back here please - we may be able to work with it.  I'm assuming by going back to the default you mean either no device declared or using the VESA driver?  At any rate, if you could post back your xorg.conf after envyng we'll try to go from there.  And yep - what you did is what I meant by disabling the restricted driver.

Dave ;)

---

### Post by trg383 on 2008-12-06
Here's my xorg.conf after the install + reboot.
Thank you :)

---

### Post by kcy29581 on 2008-12-06
Hi OP,

I install the official NVIDIA driver all the time at home and work, and here is how I do it:

[LIST]
[*]Install build-essential (tools to build packages/compile/etc)
[*]Install xserver-xorg-dev (libraries to build driver modules)
[*]At login screen press CTRL+ALT+F1 (takes you to the terminal)
[*]Log in using your user name/password
[*]Type > sudo service gdm stop (kills X server)
[*]Now you can install the NVIDIA driver using > sudo sh *NVIDIA driver you downloaded*
[/LIST]

---

### Post by trg383 on 2008-12-06
kcy29581, 
It still wouldn't compile the interface. I was missing xserver-xorg-dev but it didn't make a difference. Thank you though!

---

### Post by anewguy on 2008-12-07
Looks like the monitor needs to be defined in xorg.conf - needs refresh rates and the various modes for the desired resolutions.  Once you are at this point, do not go back to the old - instead try running sudo dpkg -reconfigure xserver-xorg (I think that's the rights syntax).  It *should* let you set up your video (nvidia) and monitor settings - if not, try running nvidia-settings.

Dave ;)

---

### Post by trg383 on 2008-12-07
hmm, sudo dpkg-reconfigure xserver-xorg was letting me configure my keyboard, but not my monitor. nvidia-settings was telling me that x wasn't using a nvidia driver and I need to run nvidia-xconfig and restart. nvidia-xconfig seemed to work, but restarting was automatically cancelling out the nvidia driver or something, due to it not working (the only ways I could complete loading the gui was to select the default configuration which I guess uses the native drivers or run in low-graphics mode, which also seemed to use native drivers).

I do have a vague memory now of my monitor being unrecognizeable on a redhat distro that I tried using around four or five years ago, which was keeping me from using full resolution. I didn't end up using redhat for long because of too many hardware issues so I never figured how to resolve the monitor issue. It's a Samsung SyncMaster 760V TFT if that makes any difference. I dunno.

---

### Post by anewguy on 2008-12-07
I was just checking my stuff now but have to leave for a friend's place.  I'll see if the technical specs for your monitor (horiz/vert rate, resolutions) are available somewhere on the web and get back to you - probably won't be until Monday night though.

Dave ;)

---

### Post by Gregz on 2008-12-08
> **kcy29581 said:**
> Hi OP,

I install the official NVIDIA driver all the time at home and work, and here is how I do it:

[LIST]
[*]Install build-essential (tools to build packages/compile/etc)
[*]Install xserver-xorg-dev (libraries to build driver modules)
[*]At login screen press CTRL+ALT+F1 (takes you to the terminal)
[*]Log in using your user name/password
[*]Type  (kills X server)
[*]Now you can install the NVIDIA driver using 
[/LIST]








That works til I get to compiling the kernel will not do it. Says missing source,missing tree,missing directory,ect... If I could figure out the source problem maybe this thing would go in...

---

### Post by trg383 on 2008-12-09
Thanks Dave, 
No rush, I'm currently swapping between ubuntu and winxp so I can do what needs doing. I can try looking up the info as well, or even get most of it from the settings on my xp side, I'm just not sure exactly how to put it into the config file.

---

### Post by anewguy on 2008-12-11
Sorry I have gotten back to you - I've been very busy and now am sick to top it off!

Once you find the settings for your monitor, we can help you with the syntax for loading them.  You can also try looking on Yahoo! or Google for xorg.conf syntax and I'm sure you'll get plenty of hits if you want to try it on your own.

I'll check back when I'm feeling better - I need to go to bed and try to sleep for a while.

dave

---

### Post by anewguy on 2008-12-11
Thought I'd ask a quick question while I'm trying to feel better:

did you install envyng via synaptic package manager, or did you download it from the envy/envyng site?


Dave ;)

---

### Post by anewguy on 2008-12-11
Okay, I found a link which should help you - it's for an older release but the principles,etc., are the same.

[http://www.justlinux.com/forum/showthread.php?p=780441]("http://www.justlinux.com/forum/showthread.php?p=780441")

You'll need to remove any driver already installed (envy[ng] didn't install one as it bombed in the make) - you may want to use envy[ng] and the uninstall option to clear any existing driver.  Then install all of the nvidia-glx, then modify your xorg.conf to say "nv" for the device driver.  That should get you to where you see a NVidia splash screen when you boot or login (I can't remember where it shows with mine).  Once you get to there, you'll know you have the correct driver installed and working.

Once you are at that point, we can work on resolution and the vert/horiz clocks.

Dave ;)

---

### Post by anewguy on 2008-12-13
Oops - looks like perhaps I was steering you in the wrong direction with the old nvidia-glx information.  The release notes for 8.10 state the following:

nVidia "legacy" video support
The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. 

ATI "fglrx" video support
The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see bug 284408 for more information 

X.Org Input Devices
The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 

X.Org evdev xmodmap incompatibility
The X keycodes generated with the new evdev input driver in X.Org 1.5 are not compatible with those generated in Ubuntu 8.04 LTS and before. If you have configured keybindings for your user with a ~/.Xmodmap file, you will need to convert or disable it by hand on upgrade.


Note that it says the free nv driver does not support 3-d acceleration - that would put a kink into some of your game playing.

Dave

---

### Post by trg383 on 2008-12-22
Sorry I've been MIA so long on my own thread. hmm... does that mean I cannot get 3d support to work with this gpu at all? that stinks, but I'm glad to know so I can stop trying. Thank you for all the help! I guess until I build a new box I'll keep dual booting for gaming. In any event, I'm going to be MIA for a few weeks starting tomorrow. 

I hope you're fully recovered and have a happy holiday, Dave!

---

