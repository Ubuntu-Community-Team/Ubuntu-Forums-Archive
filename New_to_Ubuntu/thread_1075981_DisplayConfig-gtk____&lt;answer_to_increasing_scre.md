---
title: "DisplayConfig-gtk    &lt;answer to increasing screen resolution ??"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-02-20
I want to increase my flat panel screen resolution beyond the system>preferences> screen resolution max of 800x600. 

Someone said they used Synaptic Package Manager and DisplayConfig-gtk.
My package manager shows a big goose egg for this app. How do I find/retrieve it?


thank You,

Ed

---

### Post by RomeReactor on 2009-02-20
Hi. Which version of Ubuntu do you have? Is it 32 bit or 64? If you're not certain about this last part, open a terminal (Applications->Accessories->Terminal) and run:
```
uname -m
```
If it shows **x86_64**, it's a 64 bit installation; otherwise, it's 32 bit.

If you're using 8.10 (intrepid), displayconfig-gtk was discontinued for this version, but as [this post mentions]("http://ubuntuforums.org/showpost.php?p=6175368&postcount=5") you can still install it by downloading and installing guidance-backends ([32-bit]("http://mirrors.xmission.com/ubuntu/pool/main/k/kde-guidance/guidance-backends_0.8.0svn20080103-0ubuntu16_i386.deb"), [64-bit]("http://mirrors.xmission.com/ubuntu/pool/main/k/kde-guidance/guidance-backends_0.8.0svn20080103-0ubuntu16_amd64.deb")) then [this displayconfig-gtk package]("http://mirrors.xmission.com/ubuntu/pool/main/d/displayconfig-gtk/displayconfig-gtk_0.3.10_all.deb").

---

### Post by ozark_hillbilly on 2009-02-20
Rome Reactor,

Thannk you!

I installed it with no problems. Is this an app that will be listed under Applications now or do i have to invoke it thru Synaptic? Searching Synaptic Mgr for DisplayConfig-gtk gets no results. 

Ubuntu 101,


Ed

P.S.  running 8.10 32 bit desktop

---

### Post by RomeReactor on 2009-02-20
> **ozark_hillbilly said:**
> Rome Reactor,

Thannk you!

I installed it with no problems. Is this an app that will be listed under Applications now or do i have to invoke it thru Synaptic? Searching Synaptic Mgr for DisplayConfig-gtk gets no results. 

Ubuntu 101,


Ed

After you've installed both packages, it will show up in 'Applications->Other->Screens and Graphics'. If you don't see the 'Other' submenu in 'Applications', go to 'System->Preferences->Main Menu' and enable the 'Screens and Graphics' entry there.

If you haven't installed the packages yet, make sure you get the 32 bit version of guidance-backends (see my previous post) and install it, *then* install the displayconfig-gtk package.

---

### Post by ozark_hillbilly on 2009-02-20
no msg...figured it out


Ed

---

### Post by RomeReactor on 2009-02-20
You can't enable the submenu if none of the entries inside are enabled first. Just highlight 'Other', and check the box for 'Screens and Graphics'; the 'Other' submenu will enable itself after that.

---

### Post by ozark_hillbilly on 2009-02-20
Rome,

I have learned a TON this past week about Linux/Ubuntu!
It sucks being at ground zero on the learning curve.
The main thing I have figured out is that I haven't even scratched the surface yet on getting a firm grasp of the Linux environment.

Is there a publication that gets one up to speed fairly quickly? Interested in understanding file hiearchy, root commands, etc.

Tks,

Ed

---

### Post by unutbu on 2009-02-20
Here is a free book by Keir Thomas which may help you: [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by RomeReactor on 2009-02-20
For the filesystem hierarchy, you can read [this page]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/"); to get acquainted with the terminal, try [Linux Command]("http://linuxcommand.org/"). You can also give [Full Circle]("http://fullcirclemagazine.org/") a read.

Have fun :popcorn:

---

### Post by ozark_hillbilly on 2009-02-20
Rome,

Thanks for references.....

changing to higher resolution for monitor was not a pretty thing to behold. System booted up in low graphics mode and gave me opportunity to troubleshoot and review. I am in too deep for now I'm thinkin. I don't have an Nvidia graphics card but only a nvidia chipset on the mobo. I have to get a driver installed off LGE disk or something. This is gonna take some time to figure out. Just wanted to boost the freakin' screen res to something over 800x600 and I get alot of grief....

Persistence will pay off eventually.

Ed

---

### Post by RomeReactor on 2009-02-21
It seems we may have tackled this problem form the wrong angle; to find out which video chipset your motherboard has, run this from the terminal:
```
lspci | grep VGA
```
If you haven't already, go to 'System->Administration->Hardware Drivers' and check the appropriate case for your video chipset (most likely labeled "Recommended". Then reboot, and post back how it goes.

Hang in there Ed.

---

### Post by ozark_hillbilly on 2009-02-21
Rome,

Here is result:

ed@House:~$ lspci | grep VGA
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)

Also when I went to Hardware Drivers and attempted to install drivers i had a choice between nvidia accelerated graphic driver versions 173 and 177 (Recommended). It burped on 177 so i installed 173 successfully.

System called for restart to activate driver. On reboot everything came up and then my LCD display went to a blank screen with the message "Analog out of range" and the values 80.8 kHz and 65 Hz. I then booted up into recovery mode and did a normal boot after trying a "x server fix" in recovery mode. 

That's all i know for now. Time to go snoop around and see if i can cipher anything out. 

After looking at things this is status:

When I go Screen and Graphics under Other it shows for Screen1 model: Plug & Play 800x600 61 hz.

When I do a test it says "configuration test failed. Please verify selected devices & configuration."

xorg.conf doesn't appear to modified now:

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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection



Screen and Graphics preferences: Attempts to add LG manufacturer and LCD 1440x900 don't take. When I do an "add" it locates the driver file i put on my desktop from the LG cd and does an import. It then asks if i want to add the following monitor models: 
LG196W Analog  
LG196W Digital

I do the add and it takes me back to the add/detect screen; selecting detect and it shows the Generic PlugnPlay model. It is not taking the driver or something. I dunno. 

Appreciate your help,

Ed

---

### Post by RomeReactor on 2009-02-21
I don't know if this is still the case, but your problem looks like it's related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/195139"). In the bug report there are links to proposed solutions; [this thread]("http://ubuntuforums.org/showthread.php?t=692658") could be of help, particularly from post #8 onwards.

---

### Post by ozark_hillbilly on 2009-02-22
Rome,

Thanks for Launchpad bug lead. Will get into it later and see what good\damage I can create. Right now I gotta go repair horse fences icestorm created a few weeks ago here in northern Arkansas. Looks like someone took dynamite and blew the tops outta all the trees. Spring won't be too pretty around here this year.

Ed

---

