---
title: "Ubuntu is running in low graphics mode"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by BacchusPaul on 2010-06-10
Hi folks!

I've been running Karmic on my (fairly ancient) PC for a while now, and the other day upgraded to Lucid. Everything was running fine (ish) on Karmic, but I've had some problems since the upgrade.

When I start up, I get a message saying:

Ubuntu is running in low-graphics mode

The following error was encountered. You man need to update your configuration to solve this:

(EE) NOUVEAU(0): Error allocating scanout buffer: 12

I click on OK and it allows me to choose from the following options:

- Run Ubuntu in low-graphics mode for just one session
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login
- Restart X

Running in low-graphic mode means that I can't watch video, which is the main purpose of this computer. Troubleshooting allows me to review the xserver log file (too long to post unless it's necessary) and the startup errors (server is already active for display 0).

Any ideas, folks? I'm aware that I might be giving entirely irrelevant information here, but if someone points me in the right direction, maybe I can post more pertinent stuff.

I'm also willing to entertain workarounds rather than solutions. I'm not particularly reluctant to reformat the machine and start again on Karmic, for instance.

Thanks a million in advance for your help!

---

### Post by nhasian on 2010-06-10
you have an nvidia GPU right?

```
lshw -C display
```

instead of using the NOUVEAU driver, use the nvidia-current instead

```
sudo apt-get install nvidia-current
```

---

### Post by BacchusPaul on 2010-06-10
Thanks!!

One problem, though: I'm none too savvy with Ubuntu, where should I enter this?

(sorry, I'm worse than an Windows user: I'm an OSX user. If it doesn't have a shiny button or icon, then I get utterly baffled).

Thanks for your patience!

---

### Post by BacchusPaul on 2010-06-10
Okay, so I entered that in Terminal and the driver was installed.

Upon restarting the computer checked the harddrive for errors, got to 100% then stopped displaying. I now have no display whatsoever.

---

### Post by BacchusPaul on 2010-06-10
Any ideas, folks?

I'm properly stuck here. Where before I had a computer that was less useful than I wanted it to be, but that I might have been able to deal with, I now have an entirely useless black box.

---

### Post by nhasian on 2010-06-10
please give us the output of the terminal command:

```
lshw -C display
```

---

### Post by BacchusPaul on 2010-06-11
How do I access terminal with the computer not displaying?

When I turn it on I get a big pixely COMPAQ screen (which allows me to choose boot options and such), followed by a big pixelly Ubuntu screen, then it goes black and stops displaying.

The Ubuntu screen is the logo with five dots underneath that turn from white to red.

Is there anything I can press at this point to go to terminal?

---

### Post by anaconda on 2010-06-11
You can boot to recovery more to fix your problem.

press ESC when grub starts loading, and select recovery more from there.
And select drop to commang prompt with networking if it asks what you want..

Another option is to boot a liveCd..

Oh.. and the Ctrl-Alt-F2 should also get you to terminal.... Ctrl-Alt-F7 gets you back to graphical environment..

---

### Post by BacchusPaul on 2010-06-11
When should I be pressing esc? Is the pixelly Ubuntu screen grub loading? I've tried pressing esc there and nothing happens.

ctrl-alt-F2 isn't doing anything after the screen goes black.

---

### Post by Atreus12 on 2010-06-11
> **BacchusPaul said:**
> Hi folks!

I've been running Karmic on my (fairly ancient) PC for a while now

[snip]

(EE) NOUVEAU(0): Error allocating scanout buffer: 12

Running in low-graphic mode means that I can't watch video, which is the main purpose of this computer.

Disclaimer: I'm not much of an xorg / video expert, so maybe someone else can comment on this solution.

I just installed 10.04 on a fairly old computer (an old video card at least), and had the exact same problem you did. Exact same error message, can't play video, etc.

I "fixed" the problem by reverting back to the (now depricated) "nv" video driver, rather than the noveau driver. Now everything works the same as it used to in 9.10

Unfortunately, I think installing the nvidia-current package probably is causing your current problems with 'X' not starting. I would uninstall this package first, and hopefully get back to where you were before. I don't think the nvidia binary driver supports older cards (but I could be wrong).

Once you get that taken care of, here are the steps I took:
```

sudo Xorg -configure

```

Open the generated file (xorg.conf.new) up in an editor, and look for the device section, it should look like this:
```

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV5 [RIVA TNT2/TNT2 Pro]"
	BusID       "PCI:1:0:0"
EndSection

```

The one you're looking for is:
```

	Driver      "nv"

```

If it says this, then copy it into /etc/X11:
```

sudo cp xorg.conf.new /etc/X11/xorg.conf

```

reboot, and cross your fingers.

If it doesn't work, remove the /etc/X11/xorg.conf file, and you should be back to where you were before.

Andrew

---

### Post by BacchusPaul on 2010-06-11
Thanks for your suggestion, Atreus. I'm glad someone has had that problem before. When I googled "(EE) NOUVEAU(0): Error allocating scanout buffer: 12" I got nothing, so it's good to know it's not *that* obscure.

Anyone any ideas how to get back to where I was before I installed the nvidia-current package? Is there any way I can access terminal starting up? Pressing escape is doing nothing.

---

### Post by nhasian on 2010-06-11
i forgot we're dealing with an ancient computer. lets remove the nvidia-current

```
sudo apt-get purge nvidia-current
```

now you can install the drivers for older cards:

```
sudo apt-get install nvidia-96
```

this is for GPUs ranging from GeForce series 2 (except for GeForce2 GTS/GeForce2 Pro, GeForce2 Ti and GeForce2 Ultra) to Geforce series 7 are supported.

otherwise you'll want:

```
sudo apt-get install nvidia-173
```

this is for GPUs ranging from GeForce series 5 to Geforce series 9 are supported.

---

### Post by BacchusPaul on 2010-06-11
Cheers.

I still can't access terminal, though.

If I booted off a Live CD, could I access terminal and make changes, or is everything done under a Live CD boot temporary?

---

### Post by nhasian on 2010-06-11
i understand that your graphical display is not working, but you should still be able to switch to a terminal by pressing Control-Alt-F1 and then logging in with your username and password.  thats probably easier than using CHROOT from the livecd to your hard disk.

---

### Post by dookiebowser on 2010-06-11
> **BacchusPaul said:**
> Cheers.

I still can't access terminal, though.

If I booted off a Live CD, could I access terminal and make changes, or is everything done under a Live CD boot temporary?

grub is the boot loader where it lists the bootable linux kernels and Windows loader (if you have windows installed) on your system. 

i.e. it should display in ANSI (no gui) something like this:

```
Ubuntu, kernel 2.6.34-5.12-generic
Ubuntu, kernel 2.6.34-5.12-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Windows NT/2000/XP (loader)
```

---

### Post by BacchusPaul on 2010-06-11
I've tried ctrl-alt-F1, ctrl-alt-F2, ctrl-alt-F7 and ESC. At no point do any of these combinations have an effect.

Sorry about this, it sounds like a bit of a nightmare problem I've managed to make.

---

### Post by juanoleso on 2010-06-11
don't worry.  over the past two years, I have seen hundreds of threads with the same kind of issue.  Someone should be able to figure it out.

Anyway, in order to get to the grub menu, after you press the power button hold down the shift key and the menu from dookiebrowser's post should come up.  Select one of the options that say "(recovery mode)."  See if that gets you to a terminal.

---

### Post by BacchusPaul on 2010-06-11
Okay, I've managed to get into terminal, and using:

```
sudo apt-get purge nvidia-current
```

I managed to get back to where I was at the start of the thread.

I tried both of these:

```
sudo apt-get install nvidia-96
```

```
sudo apt-get install nvidia-173
```

but neither driver works, both give the same problem I had before with no display whatsoever.

EDIT: I removed both of these drivers after having tried them.

I've tried following Altreus' advice, but

```
sudo xorg -configure
```

gives me:

```
sudo xorg: command not found
```

If I type

```
lshw -c display
```

I get:

```
*-display
description: VGA compatible controller
product: NV6 [Vanta/Vanta LT]
vendor: nVidia Corporation
physical id: 0
bus info: pci1000:01:00.0
version: 15
width: 32 bits
clock: 66MHz
capabilities: bus master cap_list rom
configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
resources: irq:18 memory:f7000000-f7ffffff memory:fc000000-fdffffff(prefe
tchable
```

---

### Post by BacchusPaul on 2010-06-12
Okay, so I've googled around to try to find the driver I need, and I've heard mention of nvidia-glx-71.

[http://www.linuxforums.org/forum/debian-linux-help/150849-need-driver-nvidia-corporation-nv6-vanta-vanta-lt-rev-15-a.html](http://www.linuxforums.org/forum/debian-linux-help/150849-need-driver-nvidia-corporation-nv6-vanta-vanta-lt-rev-15-a.html)

[http://ubuntuforums.org/archive/index.php/t-1040995.html](http://ubuntuforums.org/archive/index.php/t-1040995.html)

However some other users seem to be having issues with it:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1192373](http://www.uluga.ubuntuforums.org/showthread.php?t=1192373)

My GPU  is listed here as being supported by this driver:

[http://packages.ubuntu.com/intrepid/nvidia-glx-71](http://packages.ubuntu.com/intrepid/nvidia-glx-71)

Should I go ahead and install this? It's not listed for me in Synaptic Package Manager. Will it install under terminal if it isn't?

---

### Post by waynefoutz on 2010-06-12
> **BacchusPaul said:**
> 
My GPU  is listed here as being supported by this driver:

[http://packages.ubuntu.com/intrepid/nvidia-glx-71](http://packages.ubuntu.com/intrepid/nvidia-glx-71)

Should I go ahead and install this? It's not listed for me in Synaptic Package Manager. Will it install under terminal if it isn't?

That driver is for Intrepid, a now obsolete version of Ubuntu.

try this after logging on in recovery mode.

```
sudo dpkg-reconfigure xserver-xorg
```

This should get you back to square one so you can at least see your display again.

---

### Post by BacchusPaul on 2010-06-12
I'm back at square one now. I just need the driver, or is there anyway of configuring the current driver (nouveau) to work properly?

---

### Post by BacchusPaul on 2010-06-12
Also: should I be blacklisting the nouveau driver before trying to install any new driver (such as the ones that were suggested earlier in this thread)?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Atreus12 on 2010-06-14
> **BacchusPaul said:**
> 

I've tried following Altreus' advice, but

```
sudo xorg -configure
```

gives me:

```
sudo xorg: command not found
```


Sorry about the delayed response! The command was not found, because it is a capital 'X'. Here are the steps you need to take if you want to give this another shot (should take ~2 minutes)

Log out (of the graphical session)

Press Ctrl+Alt+F1 (to pull up a text based login prompt)

Login (to the text-based session)

Temporarily stop X from running:
```
sudo service gdm stop
```

Generate a new xorg config file:
```
sudo Xorg -configure
```

Start X:
```
sudo service gdm start
```

Login to the normal/graphical session (Ctrl + Alt + F7 or F8 )

Now you can inspect the generated configuration file (found in your home directory, named xorg.conf.new)

If you're ready to give it a try, copy it to /etc/X11/xorg.conf
```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```

Now reboot and see what happens. If things go badly, just remove the configuration file:
```
sudo rm /etc/X11/xorg.conf
```

Note that all this stuff is case sensitive, so watch out for that. To make things easier, you can auto-complete commands/locations on the command line by pressing the 'tab' key.

Good luck!

---

### Post by manolomanolo on 2010-07-08
Hi to all.

Same problem here. Upgraded to 10.04 from 9.10 on an old desktop computer (pentium III)
```
"(ee) nouveau(0): error allocating scanout buffer: -12"
```

but with slightly different hardware
```
  *-display
       description: VGA compatible controller
       product: NV6 [Vanta/Vanta LT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:5 memory:f8000000-f8ffffff memory:fa000000-fbffffff(prefetchable) memory:f9ff0000-f9ffffff(prefetchable)
```

Any suggestion,please?
Thanks.

---

### Post by manolomanolo on 2010-07-08
This solved my problem, without making mess.

[http://ubuntuforums.org/showpost.php?p=9424728&postcount=1](http://ubuntuforums.org/showpost.php?p=9424728&postcount=1)

---

### Post by manolomanolo on 2010-07-09
Well, the error message has disappeared but it is quite impossibile to see Youtube videos. Audio is good but video is very very slow and scratchy.

Any suggestion, please?
Thanks.

---

### Post by cascade9 on 2010-07-09
You're using the nouveau drivers, so I'm not suprised that the video is "very slow and scratchy". 

Things might eb ebtter with the nvidia drivers.....but I'm not sure if ubuntu has the 71.xx drivers you need for the old vanta. You can try going -system-> administration-> hardware drivers to see if they are avaible. 

BTW, I'm pretty sure you will need to remove the nouveau drivers before you try installing the nvidia drivers.

---

### Post by manolomanolo on 2010-07-09
This didn't help either:

[http://ubuntuforums.org/showpost.php?p=9211609&postcount=35](http://ubuntuforums.org/showpost.php?p=9211609&postcount=35)

So, i am not using nouveaou drivers anymore but the problem (slow and scratchy video) persist.

any suggestion, please?

---

### Post by manolomanolo on 2010-07-14
Up

---

