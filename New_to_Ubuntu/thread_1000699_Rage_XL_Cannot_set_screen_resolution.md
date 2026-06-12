---
title: "Rage XL Cannot set screen resolution"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by AmberG on 2008-12-03
Hi, I am a total newbee to Ubuntu and Linux and this is my first post here so please be gentle and forgiving.

Two days ago I installed Ubuntu 8.10 on an old Dell PowerEdge 1600SC with a Rage XL VGA controller connected to a Samsung XIOD monitor.  This previously worked well with MS 2003 server on board but that was MS. I am trying to set this PC up to be a development Apache Web localhost.

The installation went sweetly with no apparent problem - that is until trying to set screen resolution :(

I have tried the obvious:
"Configure Display Settings" -> just gives "unknown" and nothing better than 800x600 - useless
"System/Administration/Hardware Drivers" -> nothing - not a single driver listed and no chance to add one - even if I could find one!
"Applications/System Tools/Device Manager" -> lists the VGA controller correctly as a Rage XL and gives a bundle of settings (no idea what they mean or if they can be changed-too risky)

I have done a quick search on this forum and read through a few posts - I guess I'm not alone in having problems in this area - but all the responses were just gobbledegook to me.
However I have done the following (based on some suggestions found)
```

~$ lshw
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Rage XL
             vendor: ATI Technologies Inc
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 27
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=32 mingnt=8
 
```

```

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.2)

```

All straightforward advice thankfully received
Amber

---

### Post by skymera on 2008-12-03
Is this card ATI or Nvidia?

If so you can install the driver using EnvyNG.

```
 sudo apt-get install envyng-gtk 
```

The core is also available is you want to install through console.

i believe it is:

```
 sudo apt-get install envyng-core 
```

---

### Post by overdrank on 2008-12-03
> **AmberG said:**
> Hi, I am a total newbee to Ubuntu and Linux and this is my first post here so please be gentle and forgiving.

All straightforward advice thankfully received
Amber

Hi and welcome, ATI has dropped support for the older graphics as such as yours. You may try and boot into recovery mode and use the xfix option to correct the graphics issue.
Recovery mode is usually the second choice when booting the grub and after you use the xfix option then you should be offered to boot normally and hopefully this will help.

---

### Post by AmberG on 2008-12-03
> **skymera said:**
> Is this card ATI or Nvidia?

If so you can install the driver using EnvyNG.

```
 sudo apt-get install envyng-gtk 
```

The core is also available is you want to install through console.

i believe it is:

```
 sudo apt-get install envyng-core 
```


It is ATI.

Tried the install of EnvyNG as suggested (and in another response elsewhere on this forum) but nothing appears on any menu (even after reboot) and cannot find it in "Edit Menu"

---

### Post by AmberG on 2008-12-03
> **overdrank said:**
> Hi and welcome, ATI has dropped support for the older graphics as such as yours. You may try and boot into recovery mode and use the xfix option to correct the graphics issue.
Recovery mode is usually the second choice when booting the grub and after you use the xfix option then you should be offered to boot normally and hopefully this will help.

Sorry about the thread title - I thought that was pretty descriptive :(

You have lost me already with the above statement.
ATI dropped support - OK understand that bit but this worked perfectly on MS Windows last week.  So is Linux really that much worse?

Recovery mode? grub? you have lost me.

When I reboot there is alot of rapid screen scrolling messages then very fast into the Ubuntu login window.  I get the chance to drop into the BIOS editor but no idea what else is possible. Is there a key to jump into Recovery mode?

grub? no idea what you are talking about here - I suppose I could google it - but that sounds like I could be playing with fire.

---

### Post by overdrank on 2008-12-03
> **AmberG said:**
> Sorry about the thread title - I thought that was pretty descriptive :(
Your title is good. That statement is in my signature for all to read :)
> **AmberG said:**
> 
You have lost me already with the above statement.
ATI dropped support - OK understand that bit but this worked perfectly on MS Windows last week.  So is Linux really that much worse?
 When I mean drop support for linux for ATI graphics chipset modle 9500 and older.
> **AmberG said:**
> 
Recovery mode? grub? you have lost me.

When I reboot there is alot of rapid screen scrolling messages then very fast into the Ubuntu login window.  I get the chance to drop into the BIOS editor but no idea what else is possible. Is there a key to jump into Recovery mode?

grub? no idea what you are talking about here - I suppose I could google it - but that sounds like I could be playing with fire.
If Ubuntu is the only OS on the system, then when you see grub loading press the esp key then you can boot into recovery mode as I previously posted suggestion. :)

---

### Post by AmberG on 2008-12-03
> **overdrank said:**
> 
 When I mean drop support for linux for ATI graphics chipset modle 9500 and older.

I guess that means a new graphics card then :(
So much for being able to use Linux on "older" machines :(
Not that I consider this machine THAT old (circa 6 yrs).

> If Ubuntu is the only OS on the system, then when you see grub loading press the esp key then you can boot into recovery mode as I previously posted suggestion. :)

OK: that was a bit of a nightmare.
It is the only OS on the system, fully cleaned of everything else and reformatted before install.
Pressed the ESC key and after lots of fast scrolling unreadable info (does this go to a log file somewhere? - or is it just worthless screen gibberish) finally reached an option to "Recovery mode".
Ran xfix, then continue reboot.

This seemed to make matters worse. I now get a message telling me "Ubuntu is running in low graphics mode", as if I didn't know that already.

---

### Post by w4ett on 2008-12-03
> **AmberG said:**
> I guess that means a new graphics card then :(
So much for being able to use Linux on "older" machines :(
........ I now get a message telling me "Ubuntu is running in low graphics mode", as if I didn't know that already.

+1 to Overdrank He has given some good advice, but as in all things in open source realm, there is more than one way to skin a cat :)

Your card should be quite usable with the open source xorg-driver-ati, which SHOULD have been loaded when you installed your system.  Let's try this a different way...in the terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will manually reconfigure X and hopefully load the correct driver.

(Added)  You might also consider using the 8.04 LTS release as well for your server...it has 3 years support for the desktop version and five years for the Server edition. Also the Xserver in 8.04 is a little less "cutting edge" than in 8.10, and might serve your video requirements a little better. :)

---

### Post by AmberG on 2008-12-03
> **w4ett said:**
> Your card should be quite usable with the open source xorg-driver-ati, which SHOULD have been loaded when you installed your system.  Let's try this a different way...in the terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will manually reconfigure X and hopefully load the correct driver.

The cesspool gets deeper :(

I tried that command, which appeared to work - said it overwrote /etc/X11/xorg.conf file

Reboot: now even more on screen garbage ending in a screen lock up :(
managed to break out with a Ctrl+Alt+Del (is that legal?) anyway eventually through to same info box "... low resolution ..." and eventually back to log on.

Reason for 8.10 is that it was supplied on disc as "current best" I am new to Linux and have no idea what else is available and that it had such degenerative graphic options from a previous version.

Having managed to get Apache, PHP, and My SQL installed without any serious problems so far - I am astonished that the basics don't work - or require tinkering inside the box to fix.

Oh and the result of the above on xorg.conf is a totally commented out file with nothing actionable

```

xorg.conf (X.Org X Window System server configuration file)
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
                               [ Read 33 lines ]

```

I read the bit 
> 
Note that some configuration settings that could be done previously in this file, now are automatically configured by the server and settings here are ignored.

as suggesting that changes to this file were a waste of time.

I saw changes to this file suggested elsewhere on the forum and have tried some of them.  It appears that hey too have been wiped by new installs or by the above commands.

---

### Post by overdrank on 2008-12-03
> **AmberG said:**
> The cesspool gets deeper :(

I tried that command, which appeared to work - said it overwrote /etc/X11/xorg.conf file
 That is what the command is designed for to reconfigure your xorg and correct issues.
> **AmberG said:**
> 

Reason for 8.10 is that it was supplied on disc as "current best" I am new to Linux and have no idea what else is available and that it had such degenerative graphic options from a previous version.
This is correct as it is the latest development. Changes are being made for the next LTS long term support edition.

> **AmberG said:**
> 
Oh and the result of the above on xorg.conf is a totally commented out file with nothing actionable

I read the bit 

as suggesting that changes to this file were a waste of time.

I saw changes to this file suggested elsewhere on the forum and have tried some of them.  It appears that hey too have been wiped by new installs or by the above commands.
There has been changes to the way the xorg is used and it started with Hardy. So the addition to the xorg that have worked in  past editions do not always work now.
As w4ett stated you should be able to use the driver that comes with Ubuntu by default. I have  laptop with the ATI 7500 and it works with compiz and all on Hardy. Hardy has a tool ```
gksu displayconfig-gtk
``` that aids in the xorg configuration but it has been removed in Intrepid.
> **AmberG said:**
> 
I guess that means a new graphics card then
So much for being able to use Linux on "older" machines
Not that I consider this machine THAT old (circa 6 yrs).
This is not so, ATI has stopped the support for the older graphics cards not Ubuntu. If you are using the system as a server then a GUI will use more resources. 
We just try to help give you ideas and commands to aid in your issues. Good luck! :)

---

### Post by AmberG on 2008-12-03
Please don't misunderstand
I do appreciate all your offers of help in resolving this.

But please also understand that I am very much new and really do not understand why a feature in a previous version is made incompatible in a newer version - to me that is just one of the big bad things with MS.  It sounds just like one of the typical "I'll code this out of the latest version because everyone will have the latest hardware available"

I was assured that Ubuntu worked out of the box - and in almost every other aspect it appears to do just that.  I'm struggling a bit with permissions and gaining access to files (but that is just a learning issue)

This hardware problem is very serious and is stopping my use of the system - it seems that many programs open windows that are too big for the resolution.

BTW although Apache+PHP+MySQL are loaded this is not a server just a development workstation for web sites (as it was with MS).

It looks like my only option is then to purchase a new graphics card in the hope that it is supported by 8.10, or to bin the lot and go back to an older version of Ubuntu and start the week over again. That just doesn't make any sense as I would be locked into an old version which would be no better than loading Windows 3.1 or 98 instead of Vista.

---

### Post by overdrank on 2008-12-03
> **AmberG said:**
> Please don't misunderstand
I do appreciate all your offers of help in resolving this.

I was assured that Ubuntu worked out of the box - 
This hardware problem is very serious and is stopping my use of the system - it seems that many programs open windows that are too big for the resolution.



Ok I do not know whom assured you it would work out of the box but that is a issue between you and them. :)
Lets see if we can get this resolution issue fixed. What is the specs of the system? If the ati graphics is integrated then it shares the memory of the system.
Edit you may look here also
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by AmberG on 2008-12-03
Thanks, I ihad seen that page before.
just tried again and the results are:
```

~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

```

the instruction
```

~$ xrandr --output LVDS --mode 1024x768

```
appears to do nothing

as does the next one
```

~$ xrandr --addmode S-video 1024x768

```

the rest is gibberish to me
I can't follow the contents of the edit on the xorg.conf which I'm guessing is specific for whatever card - anyway will it not be overwritten as per above?

The spec of the system is:
Dell PowerEdge 1600SC
Dual processor Xeon 2.4GHz
Twin Network (Realtek RTL-8139/8139C/8139C+ & Dell 82540EM Gigabit)
VGA Rage XL 18259
The properties (taken from the Device Magaer Screen - so Ubuntu must be seeing the device - just not driving it correctly?) - it would be nice to be able to copy/paste/print/save from this little but handy program
```

info.parent = /org/freedesktop/Hal/devices/computer
info.product = Rage XL
info.subsystem = pci
info.udi = /org/freedesktop/Hal/devices/pci_1002_4752
info.vendor = ATI Technologies Inc
linux.hotplug_type = 2 (0x2)
linux.subsystem = pci
linux.sysfs_path = /sys/devices/pci0000:00/0000:00:0e.0
pci.device_class = 3 (0x3)
pci.device_protocol = 0 (0x0)
pci.device_subclass = 0 (0x0)
pci.linux.sysfs_path = /sys/devices/pci0000:00/0000:00:0e.0
pci.product = Rage XL
pci.product_id = 18258 (0x4752)
pci.subsys_product_id = 309 (0x135)
pci.subsys_vendor = Dell
pci.subsys_vendor_id = 4136 (0x1028)
pci.vendor = ATI Technologies Inc
pci.vendor_id = 4098 (0x1002)

```

It looks to me as if all those values are editable in the Device Manager window.  But you will know better - I have no inention guessing what they all mean.

---

### Post by mapes12 on 2008-12-04
I too have an ATI Rage XL graphic device on this HP Server tc2120. I had exactly the same problem that you have described after I upgraded from 7.10 to 8.10 and I tried all the fixes on this thread (and more) but just could not get a screen res any higher than 800x600. I spent days trying to fix it but failed. BTW 7.10 worked fine but I wanted to upgrade.

After much googling and digging around on this forum it would appear that the new version of the X server deployed in 8.10 has moved away from being configuarable by editing the xorg.conf file. Therefore, the only way I found to achieve my objectives of a) upgrading and b) getting me screen res to 1024x768, was to install version 8.04 LTS. Even after installing 8.04 the max screen res was 800x600. To fix the problem in Terminal ```
gksudo displayconfig-gtk
```A GUI pops up where you can then select your device, monitor and desired screen res. That fixed the problem for me.

BTW - I tried the above command in 8.10 but it didn't work.

Good luck!

Mark

---

### Post by AmberG on 2008-12-04
Thnx for the the additional info.
Nice to know I'm not the only one suffering.

There is something interesting happening while the system boots up.

While all the garbage scrolls to the screen -

Surely this must go to a log file so it could be read ???

- the screen definitely does a mode change, the charcters become less distinct, then it finally drops out into the ... low resolution message.

I get the impression that something is going wrong during boot (perhaps I've loaded something I shouldn't have)


I also poped out to the "friendly" store to see if I could pick up a cheap video card. Nothing seems to fit the machine any more :(

---

### Post by w4ett on 2008-12-04
/var/log/Xorg.0.log  and /var/log/kern.log will let us see what is going on.

---

### Post by mapes12 on 2008-12-04
> I also poped out to the "friendly" store to see if I could pick up a cheap video card. Nothing seems to fit the machine any moreMe to! This old box only has room for 3.3v PCI cards. Most supported cards are AGP or 5v PCI. Someday I will have to dish out some £'s for a more up to date unit. But ftb it's working fine.

---

